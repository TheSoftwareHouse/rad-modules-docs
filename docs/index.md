---
id: index
title: Getting started
---

## About RAD modules

There are many digital systems worldwide. Each system was developed to solve some business requirements, despite each system is different they all have common (modules) to achieve their requirements e.g

1. Module to handle users and users policy,
2. Module for sending emails,
3. Module for running scheduled jobs,
4. Module for pushing notifications,

RAD modules were developed to simplify the development process so developers can focus only on business requirements.

For example, your app needs to send an email after some operation but you don't have implemented the mailing module jet. No worries you can pull our service and use it in your app. Things you need to do are only a few steps:

1. Pull our docker image of mailing service
2. Add service to yours docker-compose file
3. Set necessary env variables
4. Call methods from your app to new mailing service via HTTP methods

Our modules are fully configurable so you can change things you want or things you don't need.

If you want to read more about our RAD modules please check the description of each module.

In case of issues feel free to add a new issue on our github.
