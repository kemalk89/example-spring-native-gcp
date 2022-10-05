# Requirement
Build a Spring Boot Application and run on Google Platform App Engine. 
In our application we also need the GCP Secret Manager.

# Local Environment
- macOS Monterey v12.6
- The command ``java -version`` logs following output in the terminal:
```
openjdk version "17.0.4" 2022-07-19 LTS
OpenJDK Runtime Environment GraalVM 22.2.0 (build 17.0.4+8-LTS)
OpenJDK 64-Bit Server VM GraalVM 22.2.0 (build 17.0.4+8-LTS, mixed mode, sharing)
```

# Solution approach
It is absolutely possible to fulfill the requirements above by using Spring Boot. Unfortunately we have high cold start times (around 10 seconds).
In a serverless environment where instances starts up and shuts down frequently this is not ideal.

### Adding Spring Native

How to optimize cold start times? There are several strategies. One of them is trying to build a native executable using Spring native.
Therefore we can follow the Spring Native Getting Started guide - in our case the **Getting started with Native Build Tools** guide: https://docs.spring.io/spring-native/docs/current/reference/htmlsingle/#getting-started-native-build-tools

After finishing the guide everything is working as expected. (With Spring-Boot-only start time was 954ms. With Spring Native it is 0ms.)

### Adding Google Platform App Engine
Now lets add Google Platform App Engine into the application. On https://start.spring.io/ we can add dependency GCP Support.
(This step will force us to downgrade spring-boot-starter-parent to 2.6.12.)

> During build you can see a warning from DefaultCredentialsProvider like "No core credentials are set". This happens because you are not authenticated
to google cloud. Just ignore it, because the application will work fine.

After adding GCP Support everything is still working as expected. (With Spring-Boot-only start time was 970ms. With Spring Native it is 74ms.)

### Adding Secret Manager
Here you can read how to add Secret Manager https://docs.spring.io/spring-cloud-gcp/docs/current/reference/html/secretmanager.html#_secret_manager.

# Problem



