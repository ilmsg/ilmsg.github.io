---
layout: post
title:  "Spring Boot Cloud Server and Client"
date:   2024-03-13 11:49:16 +0700
categories: spring boot cloud
---

spring cloud eureka server

![/assets/images/2024-05-11_125130.png](/assets/images/2024-05-11_125130.png)

ไพล์ `pom.xml` จะเพิ่ม dependencies ที่เป็น eureka server เข้ามา

    <dependencies>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
        </dependency>
    </dependencies>

ไพล์ `application.properties` ตั้งค่าไว้แบบนี้

    spring.application.name=spring-cloud-eureka-server
    
    eureka.client.register-with-eureka=false
    eureka.client.fetch-registry=false
    server.port=8761

ไพล์ `SpringCloudEurekaServerApplication.java`  เราจะเพิ่ม Annotations `@EnableEurekaServer` เข้ามาตัวนึง

    package com.ilmsg.springcloudeurekaserver;

    import org.springframework.boot.SpringApplication;
    import org.springframework.boot.autoconfigure.SpringBootApplication;
    import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;

    @EnableEurekaServer
    @SpringBootApplication
    public class SpringCloudEurekaServerApplication {
        public static void main(String[] args) {
            SpringApplication.run(SpringCloudEurekaServerApplication.class, args);
        }
    }

---

spring cloud cart service `pom.xml`

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
        </dependency>
    </dependencies>

---

spring cloud payment service `pom.xml`

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
        </dependency>
    </dependencies>

