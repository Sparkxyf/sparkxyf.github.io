---
layout: post
title: 运用shade实现flink-cdc的兼容
categories: 技术琐碎
description: shade技术在flink-cdc的应用
keywords: flink, shade, maven
---

初学flink，有些概念还在摸索，如果有错误，请指教，不吝感激。

因为一些业务需要，公司采用了flink框架，希望继承flink-cdc，因为flink是1.15版本，虽然flink-cdc只支持到1.14，但是还是抱着尝试的心理试一下可不可以兼容。

因为flink-cdc使用的是flink1.13的版本，两者的guava版本不一致，不能运行，所以可以对flink-cdc制作shade包解决依赖冲突问题。

新建一个maven项目，pom如下：

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.sparkxyf</groupId>
	<artifactId>mysql-cdc-shade</artifactId>
	<version>1.0-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>Flink Quickstart Job</name>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<flink.version>1.15.0</flink.version>
		<target.java.version>1.8</target.java.version>
		<scala.binary.version>2.12</scala.binary.version>
		<maven.compiler.source>${target.java.version}</maven.compiler.source>
		<maven.compiler.target>${target.java.version}</maven.compiler.target>
		<log4j.version>2.17.1</log4j.version>
	</properties>

	<repositories>
		<repository>
			<id>apache.snapshots</id>
			<name>Apache Development Snapshot Repository</name>
			<url>https://repository.apache.org/content/repositories/snapshots/</url>
			<releases>
				<enabled>false</enabled>
			</releases>
			<snapshots>
				<enabled>true</enabled>
			</snapshots>
		</repository>
	</repositories>

	<dependencies>
		<dependency>
			<groupId>com.ververica</groupId>
			<artifactId>flink-connector-mysql-cdc</artifactId>
			<version>2.2.1</version>
			<scope>compile</scope>
		</dependency>

	</dependencies>

	<build>
		<plugins>

			<!-- Java Compiler -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.1</version>
				<configuration>
					<source>${target.java.version}</source>
					<target>${target.java.version}</target>
				</configuration>
			</plugin>

			<!-- We use the maven-shade plugin to create a fat jar that contains all necessary dependencies. -->
			<!-- Change the value of <mainClass>...</mainClass> if your program entry point changes. -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-shade-plugin</artifactId>
				<version>3.1.1</version>
				<executions>
					<!-- Run shade goal on package phase -->
					<execution>
						<phase>package</phase>
						<goals>
							<goal>shade</goal>
						</goals>
						<configuration>
							<relocations>
								<relocation>
									<pattern>org.apache.flink.shaded.guava18</pattern>
									<shadedPattern>com.spark.shaded.guava18</shadedPattern>
								</relocation>
							</relocations>
							<artifactSet>
								<excludes>
									<exclude>org.apache.flink:flink-shaded-force-shading</exclude>
									<exclude>com.google.code.findbugs:jsr305</exclude>
									<exclude>org.slf4j:*</exclude>
									<exclude>org.apache.logging.log4j:*</exclude>
								</excludes>
							</artifactSet>
							<filters>
								<filter>
									<!-- Do not copy the signatures in the META-INF folder.
									Otherwise, this might cause SecurityExceptions when using the JAR. -->
									<artifact>*:*</artifact>
									<excludes>
										<exclude>META-INF/*.SF</exclude>
										<exclude>META-INF/*.DSA</exclude>
										<exclude>META-INF/*.RSA</exclude>
										<exclude>META-INF/versions/11/module-info.class</exclude>
									</excludes>
								</filter>
							</filters>
							<transformers>
								<transformer implementation="org.apache.maven.plugins.shade.resource.ServicesResourceTransformer"/>
								<transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
									<mainClass>com.sparkxyf.MysqlCdcShade</mainClass>
								</transformer>
							</transformers>
						</configuration>
					</execution>
				</executions>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-deploy-plugin</artifactId>
			</plugin>
		</plugins>

	</build>
</project>

```

> 注意其中的mainClass替换成自己的
>
> maven deploy是为了方便自己推送到私有仓库，方便同事使用。

引入自己的flink-cdc-shade

```xml
<dependency>
	<groupId>com.sparkxyf</groupId>
	<artifactId>mysql-cdc-shade</artifactId>
	<version>1.0-SNAPSHOT</version>
</dependency>
```

