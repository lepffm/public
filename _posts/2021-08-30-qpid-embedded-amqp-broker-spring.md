---
layout: post
title: "Using Qpid for amqp local environment on Spring"
tags: [dev, amqp]
---
# subject
Qpid J-Broker - Embedded AMQP Java Brokder. alternative RabbitMQ  

# purpose
use local inmemroy AMQP broker 

# description
Qpid is alternatives to RabbitMQ in case of Local Development Environment

# Intro
Qpid
https://qpid.apache.org/


pom.xml
scope : provided -> use only local
```
<dependencies>
  <dependency>
    <groupId>org.apache.qpid</groupId>
    <artifactId>qpid-broker-core</artifactId>
    <version>8.0.5</version>
    <scope>provided</scope>
  </dependency>
  <dependency>
    <groupId>org.apache.qpid</groupId>
    <artifactId>qpid-broker-plugins-amqp-0-8-protocol</artifactId>
    <!--<artifactId>qpid-broker-plugins-amqp-1-0-protocol</artifactId>-->
    <version>8.0.5</version>
    <scope>provided</scope>
  </dependency>
  <dependency>
    <groupId>org.apache.qpid</groupId>
    <artifactId>qpid-broker-plugins-memory-store</artifactId>
    <version>8.0.5</version>
    <scope>provided</scope>
  </dependency>
</dependencies>
```
Configuration.java
```
import org.apache.qpid.server.SystemLauncher;
@Configuration
public class Configuration{
  private SystemLauncher launcher = new SystemLauncher();
  @PostConstruct
  public void postConstruct(){
    try{
      start();
    }catch(Exceptin e){
      // ignore it
    }
  }
  @PreDestroy
  public void preDestroy(){
    try{
      launcher.shutdown();
    }catch(Exception e){
      // ignore it
    }
  }
  private void start() throws Exception {
        Map<String, Object> attributes = new HashMap<>();
        attributes.put("type", "Memory");
        attributes.put("initialConfigurationLocation", findResourcePath("qpid-config.json"));
        attributes.put("startupLoggedToSystemOut", false);
        launcher.startup(attributes);
    }
    private String findResourcePath(final String fileName) {
        return Configuration.class.getClassLoader().getResource(fileName).toExternalForm();
    }
}
```

qpid-config.json
```
{
  "name": "EmbeddedBroker",
  "modelVersion": "8.0",
  "authenticationproviders": [
    {
      "name": "local",
      "type": "Plain",
      "secureOnlyMechanisms": [],
      "users": [{"name": "guest", "password": "guest", "type": "managed"}]
    }
  ],
  "ports": [
    {
      "name": "AMQP",
      "port": "${qpid.amqp_port}",
      "authenticationProvider": "local",
      "virtualhostaliases": [
        {
          "name": "defaultAlias",
          "type": "defaultAlias"
        }
      ]
    }
  ],
  "virtualhostnodes": [
    {
      "name": "default",
      "defaultVirtualHostNode": "true",
      "type": "Memory",
      "virtualHostInitialConfiguration": "{\"type\": \"Memory\",\"nodeAutoCreationPolicies\":[{\"patterns\":\".*\",\"createdOnPublish\":\"true\",\"createdOnConsume\":\"true\",\"nodeType\":\"queue\"}]}"
    }
  ]
}
```

# reference
https://cwiki.apache.org/confluence/display/qpid/How+to+embed+Qpid+Broker-J 
https://stackoverflow.com/questions/30918557/embedded-amqp-java-broker 
