:data-transition-duration: 300
:css: css/presentation.css
:data-rotate-x: 360
:skip-help: true

.. title:: Introduction to Docker

.. header::

   .. image:: images/logo.jpg

.. footer::

    Introduction to Docker

Docker
======

Sopra Steria, Microservices and Container Platform Community

2017-08-22

----

whoami
======

::

   # getent passwd ssm
   ssm:x:1000:1000:Stig Sandbeck Mathisen:/home/ssm:/bin/zsh

* Lead Infrastructure Engineer
* Team Leader @ TOD
* Debian Developer
* Red Hat Certified Architect

----

What is Docker
==============

Docker is a way to...

* Package software
* Publish software
* Isolate software

----

How does it work?
=================

* Static disk image with application and all dependencies
* External configuration and data storage
* Separate networking
* Separate storage
* Separate users and groups

----

What problems does it solve?
============================

* Reproducability
* Transparency
* "It works on my laptop"

----

A short history of containers
=============================

* 1999: FreeBSD jail
* 2001: Linux-Vserver (...)
* 2004: Solaris zones
* 2013: Docker
* Standardised containers  <---- YOU ARE HERE

----

Docker on the Command Line
==========================

The "docker" command.

----

How do I use this thing?
------------------------

Instant linux instance:

.. code-block:: shell-session

   # docker run -it centos:7

   # docker run -it debian:unstable

----

Building images
---------------

.. code-block:: shell-session

  # docker build .

  # docker build -t myapp:test .

  # docker tag registry.example.com/myapp:v1 myapp:test

----

Pulling and pushing images
--------------------------

.. code-block:: shell-session

   # docker pull debian:9

   # docker pull registry.example.com/base:latest

   # docker push registry.example.com/myapp:latest

----

Running images
--------------

----

Building Docker images
======================

----

Start with a base OS
--------------------

.. code-block:: docker

   FROM centos:7

.. image:: images/docker-1.png
   :class: figure


----

Include a runtime environment
-----------------------------

.. code-block:: docker

   FROM centos:7
   RUN yum -y install jre...

.. image:: images/docker-2.png
   :class: figure


----

Add your application
--------------------

.. code-block:: docker

   FROM centos:7
   RUN yum -y install jre...
   ADD https://artifactory.example.com/app.jar /srv/app.jar
   CMD java -jar /srv/app.jar

.. image:: images/docker-3.png
   :class: figure

----

An docker container
-------------------

.. code-block:: shell-session

  # docker run -it myapp

.. image:: images/docker-4.png
   :class: figure


----

Storage
=======

All docker containers have a writable layer.

Data written to container.

* Same lifetime as the container
* Managed by the storage driver
* Storage driver has performance overhead

Use a data mount.

----

Volumes
-------

* Persistent storage
* Managed by docker (/var/lib/docker/...)

----

Bind mounts
-----------

* Persistent storage
* Mounted from anywhere on the host filesystem

----

tmpfs mounts
------------

* For performance
* Mounted from host tmpfs
* Stored in memory (or swap)
* Same lifetime as container

----

Networking
==========

Most developer setups share network with the host.

Can be as complex as you want, and even more.

----

Demo
====

----

That's it
=========

Thank you!
