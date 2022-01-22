---
layout: default
title:  "Kafka Intro"
date:   2022-01-21 12:00:00 +0100
categories: techarticle
---

The components of Kakfa: consumer, producer, broker and zookeeper.  Diagrams below shows how they glue together:

{% assign image_files = site.static_files | where: "image", true %}
{% for myimage in image_files %}
  <img src="{{ myimage.path }}" alt="Italian Trulli">
{% endfor %}
