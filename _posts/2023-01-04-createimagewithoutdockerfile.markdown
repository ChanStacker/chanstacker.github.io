---
layout: post
title: "Creating images without a dockerfile"
date: 2023-01-04 09:00:00 +0100
categories: Devops
---

#### Creating an image without dockerfile

* Even though the conventional way to create a docker image would be through a dockerfile, it is possible to create an image from an existing container.
* Basically the image will be a snapshot of the container along with changes that have been made to it.
* Let's pull latest Alpine to start with:
{% highlight batchfile linenos %}
docker pull alpine:latest
{% endhighlight %}
* Create a container from the Alpine:latest image, name it chan-alpine and start a bash shell into the container
{% highlight batchfile linenos %}
docker container run -it --name chan-alpine alpine:latest /bin/sh
{% endhighlight %}
* Container shows up in the list of started containers
![minimal-api](/assets/img/20230104_dockerimagecheckcontainer.png){:class="img-centered"}
* Let's install git on this container by running the command below on the shell:
{% highlight batchfile linenos %}
apk add git
{% endhighlight %}
![minimal-api](/assets/img/20230104_dockerimageinstallgit.png){:class="img-centered"}
* Now that we have a container running alpine and git installed, let's create an image of this set up using `docker container commit` and passing it the name of the alpine container and a name for the resulting image which we will call `chan-alpine-image`
{% highlight batchfile linenos %}
docker container commit chan-alpine chan-alpine-image
{% endhighlight %}

* Listing the images now show our custom image:
![minimal-api](/assets/img/20230104_dockerimagecustomimage.png){:class="img-centered"}

* At this stage, let's create a container from our custom image and confirm that it comes pre-installed with git by simple running the git CLI:

{% highlight batchfile linenos %}
docker container run chan-alpine-image git
{% endhighlight %}

And the output shows the help menu of the Git CLI:
![minimal-api](/assets/img/20230104_dockerimagerungit.png){:class="img-centered"}



