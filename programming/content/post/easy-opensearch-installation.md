---
title: "Easy Opensearch Installation"
date: 2025-07-20T14:50:37+02:00
math: false
tags: [opensearch]
categories: [soc]
---

# Opensearch quickly installation guide

This post is a small summary of how to quickly get started with Opensearch. The installation is done with Docker using the docker compose file found in the [official repo](https://github.com/opensearch-project/opensearch-build/tree/main/docker/release/dockercomposefiles).

In the recent versions of Opensearch you need to specify the OPENSEARCH_INITIAL_ADMIN_PASSWORD as an enviromental variable, otherwise it will not work.

Something important is, the documentation specifies that you need to ensure that vm.max_map_count is set to at least 262144. To do this using Docker and WSL2:

Enter the WSL environment where Docker actually runs your containers:

```bash
wsl -d docker-desktop
```

Run:

```bash
sysctl -w vm.max_map_count=262144
```

Then you can run 

```bash
docker-compose up
```

And after the containers start up, the nodes and dashboard are accessible in http://localhost:9200/ and http://localhost:5601/

# Playing around

You can import some sample data to take a look at how Opensearch dashboard works. In the next tutorials, I will explain how to configure Logstash and Filebeat.

![Opensearch](https://jackleila.github.io/programming/images/opensearch.png)
