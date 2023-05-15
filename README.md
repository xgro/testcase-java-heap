# Testcase-java-heap
test for JAVA heap memory


## Prequisite
### (oldjava) openjdk 1.8.0_92

**Description**  

`UseContainerSupport` 백포팅 적용 이전 버전을 테스트 하기 위한 이미지입니다.

```dockerfile
FROM openjdk:8u92-jdk-alpine
COPY /src /src/
RUN mkdir /app && ls /src && javac /src/main/java/com/heapsizing/PrintXmxXms.java -d /app
ENV JAVA_OPTS=""
CMD java -version && java $JAVA_OPTS -cp /app \
    com.heapsizing.PrintXmxXms
```   
   
**Commands** 

도커 이미지를 빌드하고, 실행하기 위한 커맨드 입니다. 

- _**Build**_   
```docker build -f Dockerfile.oldjava -t oldjava .```

- _**RUN**_   
```docker run -it --rm oldjava```



### (newjava) openjdk 1.8.0_212

**Description**  

`UseContainerSupport` 백포팅 적용 버전을 테스트 하기 위한 이미지입니다.

```dockerfile
FROM openjdk:8-jdk-alpine
COPY /src /src/
RUN mkdir /app && ls /src && javac /src/main/java/com/heapsizing/PrintXmxXms.java -d /app
ENV JAVA_OPTS=""
CMD java -version && java $JAVA_OPTS -cp /app \
    com.heapsizing.PrintXmxXms
```   
   
**Commands** 

도커 이미지를 빌드하고, 실행하기 위한 커맨드 입니다. 

- _**Build**_   
```docker build -f Dockerfile.newjava -t newjava .```

- _**RUN**_   
```docker run -it --rm newjava```
