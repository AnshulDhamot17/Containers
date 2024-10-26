# Understanding Container Technologies

## Table Of Contents

1. [Container](#container)
2. [Container Runtime](#container-runtime)
3. [Container Registry](#container-registry)
4. [Container Image Formats](#container-image-formats)
5. [Image Building](#image-building)
6. [Image Running](#image-running)
7. [Rootless Containers](#rootless-containers)
8. [Daemonless Containers](#daemonless-containers) 
9. [Summary](#summary)
  
## Container

<img src="./images/Container.png" alt="Description of Image" width="400" height="300"/>

A **container** is a lightweight package that holds everything an application needs to run. It includes the app's code, all the tools and libraries the app needs to work, and settings, ensuring the app runs the same way on any system. Containers help developers easily share and deploy applications without worrying about compatibility issues.

**Example**: Imagine you are cooking a meal. You pack all the ingredients, the recipe, and the cooking tools into one box. Now, no matter where you go your kitchen, a friend’s house, or even a different country you can make the exact same meal because you have everything you need in that box.
In the same way, a container holds everything an app needs, so it will work the same no matter where you run it on your computer, a server, or in the cloud.

## Container Runtime

<img src="./images/cr.png" alt="Description of Image" width="400" height="300"/>

A **container runtime** is the software responsible for running containers. In simple terms, it's like an engine that makes sure containers can start, stop, and manage themselves on your system.

**How does it work?**  

* Imagine you have a box containing an application and all its necessary files. The container runtime is responsible for opening that box, executing the application, and managing resources such as CPU and memory for the application.

* It also ensures the application is isolated from the rest of the system, so it can run without interfering with other applications on the machine.

**There are two types of container runtimes:**

1. **Low-level container runtimes (also called "OCI runtimes"):** These are the most basic container runtimes, responsible for directly interacting with the operating system to start and run containers. They don’t manage anything beyond launching containers.

* **Example:** runc, crun, Youki

* **How it works:** Think of it like an engine that powers a car. It doesn't care about the shape of the car or its design, it just runs it. These runtimes take instructions from higher-level tools, set up the container’s environment, and start the container.

**OCI**- OCI stands for **Open Container Initiative**. It’s an organization that creates standards for how containers should work, making it easier for different software tools to work together. 

2. **High-level container runtimes (also called "container management tools"):** These runtimes handle more than just starting a container. They manage the entire container lifecycle, including pulling container images, managing storage, networking, and sometimes even coordinating and organizing multiple containers to work together.

* **Example:** containerd, CRI-O (Container Runtime Interface - Open)
  
* **How it works:** Imagine a car, but this time you not only have an engine (low-level runtime) but also a dashboard that helps you control the car, manage fuel, speed, and even check the tire pressure. High-level runtimes work on top of low-level ones to make it easier to manage containers.

## Container Registry

<img src="./images/registry.png" alt="Description of Image" width="400" height="300"/>

A **container registry** is like a storage space where container images are kept. These images are ready to use packages that contain everything needed to run a piece of software, like code, libraries, and settings.

**How it works:** 

* You build a container image (which is like creating a snapshot of your software environment).
  
* Then, you push (upload) that image to a container registry, where it's saved.

* Later, when you want to use that image (on another computer, or in a cloud), you can pull (download) it from the registry and run it.

Think of it like an app store for containers: you upload images (like apps) and others can download them when needed. Popular container registries include Docker Hub, Google Container Registry (GCR), and Amazon Elastic Container Registry (ECR).

## Container Image Formats

Just like there are different formats for storing files (PDF for documents, JPG for photos), **container image formats** are the way container blueprints are packaged. These formats describe how the contents of a container (files, code, and everything an app needs) are organized and stored. The container image format ensures that these blueprints can be shared, moved, or run easily on any system that supports containers. The image format doesn’t change how the app works but helps systems understand how to run the app inside the container.

**Example:** Imagine if you had a cooking recipe book that came in a different format (print, PDF, or online). The format is different, but the instructions remain the same, so you can still cook the meal. Similarly, a container image format doesn’t change the app, but it organizes how the information is stored and used.
The most common container image format is OCI (Open Container Initiative), which ensures compatibility between different systems.

## Image Building

**Image building** is the process of creating the container image, which is the blueprint or template of an app. It’s like following a recipe to bake a cake. You take all the ingredients (the app’s files, code, and necessary software) and pack them together in a way that makes them ready to run anywhere.
Once the image is built, it can be stored in a registry, so others can use it without needing to worry about how to set up or install the app. Building an image ensures that the app always runs in the same way, no matter where it’s used.

**Example:** Imagine you are baking a cake. You gather all the ingredients (flour, sugar, eggs), mix them according to the recipe, and bake it. Once the cake is baked, it’s ready for anyone to enjoy. Similarly, when you build a container image, you are preparing everything needed to run the app.
Tools like Docker are commonly used to build images.

**How it works:** 

1. **Starting with a Base:** Think of a cake. Every cake starts with a basic layer, like a sponge. For a container image, this base is usually a simple operating system, like Linux. It’s like the cake’s foundation, ready to have more layers added.
   
2. **Adding Layers of Instructions:** Now, to make the cake special, you add different ingredients in layers, like frosting or fruit. In a container image, each layer could be installing a program, adding files, or setting up settings for the app. Each of these steps adds something new to the base.
   
3. **Using a Recipe (Dockerfile):** Just like a cake needs a recipe to know what to add and how to build it, a container image needs a Dockerfile. This file is like the recipe, it tells the computer what ingredients to add and in what order, so the image is set up correctly.
   
4. **Building Blocks (Layers):** Each step of making the container image is like building up the cake, layer by layer. If you change one ingredient (like more sugar), you only need to fix that part, not the entire cake. In the same way, the system only updates the parts of the image that need changing, saving time.
   
5. **Final Image:** The final container image is like a finished cake that has everything it needs inside and is ready to be shared and enjoyed. Just like a cake is ready to be eaten anywhere, the image has everything packed inside to run an application on any computer.

## Image Running

**Image running** is when you take a container image (the blueprint) and actually start it up so it can do its job. When the image runs, it becomes an active container (a working app).
The running container is isolated, meaning it doesn’t interfere with other apps or containers, even if they’re running on the same computer.

**Example:** **Container Image as a Cake in the Fridge:**

* Think of a cake you have already baked and stored in the fridge. This cake has all its ingredients perfectly put together, so it’s ready to enjoy whenever you want. You don’t have to go through the steps of baking or adding ingredients again because all the work to make the cake is complete.

* In the same way, a container image is a ready-made package. It contains everything an application needs to run like the code, libraries, and settings. Just as the cake in the fridge doesn’t need further preparation, the container image has everything set up and stored, ready to be used anytime.

**Running the Container as Eating a Slice of Cake:**

* Now, say you’re hungry, and you want a slice of cake. You go to the fridge, take out the cake, cut a slice, and start enjoying it. This process of slicing and eating makes the cake active in a sense because now you are interacting with it by eating.

* In technical terms, running a container is similar. When you run a container, you are taking that stored ready to go container image and making it active meaning you start it up so you can interact with the application within it.

## Rootless Containers

**Rootless containers** are containers that you can run without needing to have special permissions (root access) on your computer. 

1. When you run containers with root access, you are giving them the ability to make significant changes to the system. If something goes wrong (like a security issue), a hacker could take control of the whole system. Rootless containers reduce this risk by running as a regular user, which has limited permissions.

2. With rootless containers, you don’t need to ask an administrator for permission or access. Anyone can run these containers, making it easier for developers and users to experiment and develop applications without waiting for special access. 

3. Rootless containers ensure that even if something goes wrong in one container, it doesn’t affect the host system or other containers. This isolation is crucial for safe application development and deployment.

**Example :** A developer can run a rootless container on their local machine to test an application without needing administrative access. This is particularly useful in environments like shared servers or cloud instances where users have restricted permissions.

## Daemonless Containers

**Daemonless containers** are containers that you can run and control directly, without needing a background service, called a daemon to manage them. 

**Daemon -** A **daemon** is a background program that runs on your computer, helping with specific tasks that usually need to keep running continuously. When you start a container using Docker, a background service (the Docker daemon) runs constantly, handling container operations like starting, stopping, and monitoring the container’s state.

1. Instead of having a daemon always running to manage containers, daemonless containers work independently. When you start a container, it just runs directly without a separate program overseeing it. Once the container starts, it manages itself until it’s stopped.

2. You control everything directly. Each command you give like start, stop, or inspect is processed immediately by the container runtime, and then it’s done. This means there’s no middleman that stays running in the background, consuming system resources.

3. By removing the need for a daemon, daemonless containers save system resources. There’s no extra program using CPU or memory just to keep track of things, making it more efficient, especially for systems that don’t need to run multiple containers continuously.

**Example:** Docker Vs Podman

1. **Docker:** When you run a container with Docker, the Docker daemon is responsible for managing containers. This daemon keeps running in the background, tracking the containers’ state and handling new commands.

2. **Podman (Daemonless):** Podman doesn’t need a daemon. Each container command start, stop, etc. runs directly without any ongoing background process. You don’t have an assistant working in the background you are just giving direct commands, and each container handles itself.

## Summary

The container ecosystem makes it easier and faster for developers to create and share applications. It uses special packages that include everything an app needs to run, ensuring that it works the same way no matter where it's used on a developer's computer, a server, or in the cloud.
Because of this, developers can build reliable and efficient applications without as many problems. This approach helps them work more quickly, find and fix fewer bugs, and ultimately provide a better experience for users.



   















