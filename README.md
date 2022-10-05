# Intro
The project tries to build a Spring Boot Application and run on Google App Engine.
This is working absolutely fine but of course cold start times are very high (around 10 seconds). In a serverless environment this is not ideal.

How to optimize that? We could try to build a native executable. Therefore we can use the experimental Spring native feature.

# Local Environment
- macOS Monterey v12.6
- The command ``java -version`` logs following output in the terminal:
```
openjdk version "17.0.4" 2022-07-19 LTS
OpenJDK Runtime Environment GraalVM 22.2.0 (build 17.0.4+8-LTS)
OpenJDK 64-Bit Server VM GraalVM 22.2.0 (build 17.0.4+8-LTS, mixed mode, sharing)
```

