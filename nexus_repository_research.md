<img src="https://www.sonatype.com/hubfs/2023%20New%20Site%20Assets/nexus-repository-logo.png">

# `Nexus Repository`
## `I> Overall`
### `1.1. Introduction`
Nexus Repository is an open source repository that supports many artifact formats, including Docker, Java™, and npm. With the Nexus tool integration, pipelines in your toolchain can publish and retrieve versioned apps and their dependencies by using central repositories that are accessible from other environments.
### `1.2. Highlights of Nexus`
- Install and work well in local LAN
- Absolute security if not public
- Easy shared version, easy to upgrade
- Very good web user interface
- Easy to maintain, almost no administrative costs
- Exploit from Maven activates immediately
### `1.3. Features`
- Universal Repository Support
- Private Hosted Repositories
- On-Demand Proxying, Grouping
- Global Component Search
- Role-Based Access Controls
- Repository Health Check
- REST APIs
- Automated Cleanup Policies
- Community Support

## `II> How to use with Docker ?`
Nexus Repository supports Docker registries with the Docker repository format for hosted and proxy repositories. You can expose these repositories to the client-side tools directly or as a repository group, which is a repository that merges and exposes the contents of multiple repositories in one convenient URL. This allows you to reduce time and bandwidth usage for accessing Docker images in a registry as well as share your images within your organization in a hosted repository. Users can then launch containers based on those images, resulting in a completely private Docker registry with all the features available in the repository manager.

***Install by docker:*** 
- Step 1: Pull image ```docker pull sonatype/nexus3```
- Step 2: Create and run container
```
# Create container nexus3 run in port 8081 and 8082 (port 8082 is used for reporistories)
docker run -d -p 8081:8081 -p 8082:8082 --name nexus sonatype/nexus3
```
- Step 3: Access 127.0.0.1:8081 change password and create Repository

***Push to Nexus Repository:*** 
To push an image to Nexus Repository at first we have to tag an image to target link of repository
```
# Link image to repo link
docker tag <imageId or imageName> <nexus-hostname>:<repository-port>/<image>:<tag>
```
After tag image to target link we can push image to repository
```
# push image
docker push <nexus-hostname>:<repository-port>/<image>:<tag>
```

***Pull image from Nexus Repository:*** 
To pull image from Nexus Repository we just pull by basic syntax pull of docker
```
docker pull <nexus-hostname>:<repository-port>/<image>
```