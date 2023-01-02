---
layout: post
title: "Dockerfile Basics"
date: 2023-01-02 09:00:00 +0100
categories: Devops
---

#### Dockerfile Commands

* `FROM` - This is a mandatory beginning command for Dockerfiles.  It pulls any base image and assigns an alias to it if specified.  It is possible to use an ARG command prior to the first FROM.  However the variable cannot be used pass the FROM.  A preceding ENV would usually be used to declare a version of the image to be pulled by the FROM statement eg:

{% highlight docker linenos %}
ARG IMG_VER=1.0.0
FROM BaseImage:${IMG_VER} as basestep
ARG IMG_VER
{% endhighlight %}

The second declaration of IMG_VER is because it has to be redeclared after the FROM in case the default value needs to be accessed.  When redeclared with no value, it is assigned the value from the previous declation ie 1.0.0

* `COPY` - the only commands that runs on the local machine where the docker file is being executed.  All other commands eg RUN will be within the container.  `COPY` is usually used to copy source code from the local machine to the container where the code will be built.  `--from` switch can be used to modify the source stage of the copy instruction.  The `--from` can be a previous build layer eg:

{% highlight docker linenos %}
FROM buildtools AS build

FROM BaseImage AS basestep
COPY --from=build /app
{% endhighlight %}
