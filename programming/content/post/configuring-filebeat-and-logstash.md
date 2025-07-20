---
title: "Configuring Filebeat and Logstash with Opensearch"
date: 2025-07-20T17:34:16+02:00
math: false
tags: [filebeat, logstash]
categories: [soc]
---

In this post we will make Opensearch work with Filebeat and logstash to send, parse and analyze logs.

## Installing Filebeat and Logstash

Download Filebeat [here](https://www.elastic.co/downloads/beats/filebeat) and Logstash [here](https://www.elastic.co/downloads/logstash).


## Configurations


In **filebeat.yml**, enter the following:

```bash
filebeat.inputs:
- type: filestream
  id: my-filestream-id
  enabled: true  
  paths:
    - C:\logs\*.log 

output.logstash:
  hosts: ["localhost:5044"]
```
In **paths**, you can specify any path were you will be storing your logs. Since this is a simple tutorial for testing the setup, I created a logs folder in C, were I manually added some sample logs.


In **logstash.conf**, enter the following:

 
```bash
input {
  beats {
    port => 5044
  }
}

output {
  stdout { codec => rubydebug }
  opensearch {
    hosts => ["https://localhost:9200"]
    user => "OPENSEARCH_USER"
    password => "OPENSEARCH_PASSWORD"
    ssl => true
    ssl_certificate_verification => false
    index => "filebeat-%{+YYYY.MM.dd}"
  }
}
```

## Running

In the filebeat installation path, execute:

```bash
.\filebeat.exe -e -c filebeat.yml
```

in the bin subdirectory of the logstash installation path, execute:

```bash
.\logstash.bat -f ..\logstash.conf
```

If everything is correct, when you add some logs to the specified directory in filebeat.yml, you should see them in the console of logstash, and then they should be sent to Opensearch. You can create an index pattern by going to Management -> Dashboards Management and selecting the filebeat-%{+YYYY.MM.dd} index.

![Opensearch](https://jackleila.github.io/programming/images/opensearch_logstash_filebeat.png)
