<img style="background-color: black; padding: 16px; border-radius: 10px;" src="https://quarkus.io/assets/images/quarkus_logo_horizontal_rgb_600px_reverse.png"/>

# **`Quarkus Framework`**
## `I> Overall`
### `1.1. Introduction`
Traditional Java stacks were engineered for monolithic applications with long startup times and large memory requirements in a world where the cloud, containers, and Kubernetes did not exist. Java frameworks needed to evolve to meet the needs of this new world.
Quarkus was created to enable Java developers to create applications for a modern, cloud-native world. Quarkus is a Kubernetes-native Java framework tailored for GraalVM and HotSpot, crafted from best-of-breed Java libraries and standards. The goal is to make Java the leading platform in Kubernetes and serverless environments while offering developers a framework to address a wider range of distributed application architectures.

### `1.2. Features`
#### `1.2.1. Container First`
Quarkus tailors your application for GraalVM and HotSpot. Amazingly fast boot time, incredibly low RSS memory (not just heap size!) offering near instant scale up and high density memory utilization in container orchestration platforms like Kubernetes

#### `1.2.2. Unifies imperative and reactive`
Combine both the familiar imperative code and the reactive style when developing applications.

#### `1.2.3. Community and Standards`
Quarkus provides a cohesive, fun to use, full-stack framework by leveraging a growing list of over fifty best-of-breed libraries that you love and use. All wired on a standard backbone.

#### `1.2.4. Kube-Native`
The combination of Quarkus and Kubernetes provides an ideal environment for creating scalable, fast, and lightweight applications. Quarkus significantly increases developer productivity with tooling, pre-built integrations, application services, and more.

#### `1.2.5. Developer Joy`
A cohesive platform for optimized developer joy with unified configuration and no hassle native executable generation. Zero config, live reload in the blink of an eye and streamlined code for the 80% common usages, flexible for the remainder 20%.

## `II> How To Create Project With Quarkus`
### `2.1. Requirements`
*`JDK:`* JDK 11 or greater is required
### `2.2. Create From WebSite`
- Step 1: Go to site https://code.quarkus.io/
- Step 2: Fill information about project in form
- Step 3: Select dependencies for project
- Step 4: Click generate application and download zip file 
- Step 5: Unzip zip file, open in ide and start project
### `2.3. Create From CMD`
- Step 1: Install Quarkus 
```
curl -Ls https://sh.jbang.dev | bash -s - trust add https://repo1.maven.org/maven2/io/quarkus/quarkus-cli/
curl -Ls https://sh.jbang.dev | bash -s - app install --fresh --force quarkus@quarkusio
```
- Step 2: Init project
```
quarkus create && cd code-with-quarkus
``` 
- Step 3: Run project
```
quarkus dev
```

## `III> Compare With Spring Boot`
### `3.1. Similar`
- Both are Java Framework
- Support initing project faster
- Syntax is so relative similar

### `3.2. Differences`
| Comparison |      Spring Boot      |  Quarkus |
|------------|-----------------------|----------|
| Dependencies |  Uses a robust Dependency Injection Container (DI). With its help, developers can lose some components and move the responsibility of managing these components to the container. | Uses CDI that helps connect together the web tier and transactional tier. |
| Speed | Has slower Boot time than Quarkus.| Has faster boot time than Spring Boot. |
| Front-End Development | Based on Spring MVC and includes such solid Java templates as ThymeLeaf. | Quarkus allows using both basic front-end options and experimental ones.|
|Reactive App| Using Reactor’s Mono and Flux, Spring Boot helps create excellent reactive apps Quarkus and Spring Boot for Business | Since Quarkus has a reactive engine, it helps build reactive systems. For this aim, the framework often uses Mutiny. |
| Features | Spring Boot have more feature than Quarkus | Quarkus have less feature than Spring Boot | 
| Support | Spring Boot have more support than Quarkus| Quarkus have just released in 2019, therefore it hasn't more support| 

## `IV> Researchs For Project`
### `4.1. How to use MongoDB in Quarkus`
#### `4.1.1. Dependencies`
We have add these dependencies into project to use basic mongoDB
- ***With Maven*** 
```
<dependency>
    <groupId>io.quarkus</groupId>
    <artifactId>quarkus-mongodb-client</artifactId>
</dependency>
```
- ***With Gradle*** 
```
implementation("io.quarkus:quarkus-mongodb-client")
```

If you want to use MongoDB in project as JPA with Entity and Repository add these dependencies
- ***With Maven*** 

```
<dependency>
    <groupId>io.quarkus</groupId>
    <artifactId>quarkus-mongodb-panache</artifactId>
</dependency>
```

- ***With Gradle*** 
```
implementation("io.quarkus:quarkus-mongodb-panache")
```
#### `4.1.2. Configuation`
To connect to MongoDB we have to add relevant configuration properties to file `application.properties`
```
# configure the MongoDB client for a replica set of two nodes
quarkus.mongodb.connection-string = mongodb://mongo1:27017,mongo2:27017
# mandatory if you don't specify the name of the database using @MongoEntity
quarkus.mongodb.database = person
```
### `4.2. How to use Kafka in Quarkus`