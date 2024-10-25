# Understanding Container Technologies

## Container

<img src="./images/Container.png" alt="Description of Image" width="400" height="300"/>

A container is a lightweight package that holds everything an application needs to run. It includes the app's code, all the tools and libraries the app needs to work, and settings, ensuring the app runs the same way on any system. Containers help developers easily share and deploy applications without worrying about compatibility issues.

**Example**: Imagine you’re cooking a meal. You pack all the ingredients, the recipe, and the cooking tools into one box. Now, no matter where you go your kitchen, a friend’s house, or even a different country you can make the exact same meal because you have everything you need in that box.
In the same way, a container holds everything an app needs, so it will work the same no matter where you run it on your computer, a server, or in the cloud.

## 1. Container Runtime

A container runtime is the software responsible for running containers. In simple terms, it's like an engine that makes sure containers can start, stop, and manage themselves on your system.

**How does it work?**  

* Imagine you have a box containing an application and all its necessary files. The container runtime is responsible for opening that box, executing the application, and managing resources such as CPU and memory for the application.

* It also ensures the application is isolated from the rest of the system, so it can run without interfering with other applications on the machine.

**There are two types of container runtimes:**

1. **Low-level container runtimes (also called "OCI runtimes"):** These are the most basic container runtimes, responsible for directly interacting with the operating system to start and run containers. They don’t manage anything beyond launching containers.

* **Example:** runc, crun, Youki

* **How it works:** Think of it like an engine that powers a car. It doesn't care about the shape of the car or its design, it just runs it. These runtimes take instructions from higher-level tools, set up the container’s environment, and start the container.

**OCI**- OCI stands for **Open Container Initiative**. It’s an organization that creates standards for how containers should work, making it easier for different software tools to work together. 

2. **High-level container runtimes (also called "container management tools"):** These runtimes handle more than just starting a container. They manage the entire container lifecycle, including pulling container images, managing storage, networking, and sometimes even coordinating and organizing multiple containers to work together.

* **Example:** containerd, CRI-O
* **How it works:** Imagine a car, but this time you not only have an engine (low-level runtime) but also a dashboard that helps you control the car, manage fuel, speed, and even check the tire pressure. High-level runtimes work on top of low-level ones to make it easier to manage containers.

## 2. Container Registry

A container registry is like a storage space where container images are kept. These images are ready-to-use packages that contain everything needed to run a piece of software, like code, libraries, and settings.

**How it works:** 

* You build a container image (which is like creating a snapshot of your software environment).
  
* Then, you push that image to a container registry, where it's saved.

* Later, when you want to use that image (on another computer, or in a cloud), you can pull it from the registry and run it.








