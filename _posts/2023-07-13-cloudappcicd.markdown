---
layout: post
title: "CI/CD pipeline of a Containerised App"
date: 2023-07-13 06:00:00 +0100
categories: kubernetes
---

#### Setting up the CI/CD pipeline for a cloud application

* The CI/CD pipeline of conventional applications have some standard steps usually along the line of:
Build --> Run Unit Tests --> Run Integration Tests --> Create nuget package and publish --> Create deployment --> Trigger deployment (to optional environments)
* When working on Cloud applications, there are now some extra steps to include if one wants a fully automated CI/CD
* `Teamcity` as a continuous integration server, does a great job at keeping up with the requirements and natively includes a variety of build runners, registery integration and deployment triggers.
* As such, using a combination of the below tools allows for a fully automated pipeline:
    - Rancher
    - Teamcity Docker support
    - Nexus image repo
    - Octopus deploy
* In a multistage build process, different build target can be called by different Teamcity build step in the same configuration.  Teamcity will `cache` the output from each stage and load it on the following build step.  Therefore distinct steps can be created for building the solution, running unit tests, building and publishing images and triggering a deployment in an efficient way which does not repeat the steps.

#### .Net cloud app build steps
1.  Solution build - Teamcity detects a check-in and starts a build based on the policy.  Using the `Docker` runner type and the `build` command to build the image - image tag and platform type (Linux/Windows) selected at this stage.  This stage builds an image on top of the .Net sdk.
2.  Unit test run - Similar configuration to the above build step and reusing the Dockerfile but also running the unit tests this time.
3.  Test result publication - requires it's own step to copy the test results from above step into a specified location.  This is an important step in so far as to export the test results from the container to Teamcity for display in a common format TRX (Visual studio test result in XML format).
Note that all 3 steps so far are using the `Docker build` commands with different `--target`
4.  Test results grouping - run a touch command on all the TRX files so that the date times are aligned and hence will be well grouped in the Teamcity build display.
5.  Docker image release build - this step will build the image on top of the .Net runtime, using the `docker` runner type.
6.  Docker image push - using the `docker` runner type with command `push`
7.  Kubernetes Yaml Pack - using the Octo CLI, the Yaml kuberntes file is packaged into a nuget - see `octo pack` in Octopus documentation. This step runs a `Command line` runner type.
8.  Kubernetes Yaml Publish - Running as a `Command line` runner type, run a `dotnet nuget push` to publish the nupkg from previous step to repo.
9.  Octopus release create - Now that both the image and Yaml file are available from a repo, Nexus in this case, this command line step uses the `Octo` cli to create a release on Octopus Deploy.
10.  Build clean up - this is more a maintenance stage, running a script to clean up all intermediary images created during the multistage build process.  Though it will be running `docker rmi` command, the runner type is `Command line` to allow flexibility for a custom script.

{% highlight docker linenos %}
{% raw %}
intermediary_images=$(docker images --format '{{.Repository}:{{.Tag}}}' | grep 'some common line')

if [! -z "$intermediary_images" ]
    then docker rmi $intermediary_images
fi
{% endraw %}
{% endhighlight %}


