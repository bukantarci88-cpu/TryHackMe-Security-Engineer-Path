# Eng 3.7. Virtualization and Containers

#### **Task 1 - Introduction**

Virtualization abstracts physical hardware to partition isolated virtual machines, enabling scalable cloud architectures, atomic testing environments, and secure, compartmentalized research labs.

#### **Task 2 - What is Virtualization**

 Virtualization comes from a need of the following:

- **Decrease expenses:** Physical servers can be expensive, and virtualization can decrease the number of servers or other hardware, or even completely remove physical hardware from a company's infrastructure.
- **Scale:** Without properly implemented DevOps, it may be hard for a company to scale resources as server usage increases. Virtualization makes this process easier and can delegate a server's resources to lab machines as needed based on usage.
- **Efficiency:** Like scaling, virtualization can also make it easier to decrease the resources allocated to a lab machine if there is reduced usage.

**Virtualization Technology:** Virtualization software inserts an abstraction layer over physical hardware to partition a single host into multiple independent virtual machines running isolated guest operating systems atop allocated logical resources.

**Answer the questions below**

> Is scalability a primary benefit of virtualization?
> 

Y

> What is the operating system of a lab machine often referred to as?
> 

guest OS

#### **Task 3 - Hypervisors**

A hypervisor is a virtualization management platform that establishes an abstraction layer between physical hardware and virtual machines, categorized into Type-1 bare-metal hypervisors running directly on hardware and Type-2 hosted hypervisors operating as software applications atop a host operating system.

Type 1 hypervisors operate directly on physical hardware as dedicated, lightweight operating systems, eliminating host OS overhead to maximize resource allocation, scale, and performance for enterprise virtual machines.

**Type 2 hypervisors**, Type 2 hypervisors operate as software applications atop a pre-existing host operating system, utilizing graphical user interfaces to provide localized virtual machine management tailored for individual developers and desktop environments rather than enterprise scalability.

**Answer the questions below**

> What type of hypervisor is VirtualBox considered?
> 

type 2

> What are type 1 hypervisors also known as?
> 

bare metal hypervisors

#### **Task 4 - Containers**

Containerization leverages container engines to share the host operating system kernel while logically abstracting filesystems, process spaces, and compute allocations, providing lightweight, highly portable, and resource-efficient virtualization compared to traditional hypervisors.

**Answer the questions below**

> Are containers completely abstracted from the host operating system?
> 

N

#### **Task 5 - Docker**

Docker utilizes container engines, immutable base images defined via declarative Dockerfiles, and runtime flags like `-d` and `-p` to build, detach, and expose lightweight, reproducible containerized applications across environments.

```bash
docker run -p 5000:5000 -d cryillic/thm_example_app
```

To verify that the web server is running in the Docker container, we can scan the container or access the designated port in a web browser. 

**Answer the questions below**

> What flag is obtained at MACHINE_IP:5000 (opens in new tab) after running the container?
> 

THM{this_is_running_in_docker}

<img width="690" height="287" alt="image" src="https://github.com/user-attachments/assets/895e6e27-40dc-47ed-97b9-1c7c9ec735f0" />


#### **Task 6 - Kubernetes**

Kubernetes is an advanced container orchestration platform that automates the deployment, scaling, networking, and lifecycle management of containerized applications across distributed cluster infrastructure.

- **Horizontal scaling**: Unlike traditional "vertical" scaling, "horizontal" scaling refers to adding devices or machines to handle increased workload, rather than adding logic resources such as CPU or RAM.
- **Extensibility**: Clusters can be modified dynamically without affecting containers outside of the intended group.
- **Self-healing**: K8s can automatically restart, replace, reschedule, and kill containers that are not properly functioning based on user-defined health checks.
- **Automated rollouts and rollbacks**: K8s can progressively roll out changes to containers. As changes are made, it will monitor the application's health and decide whether to continue the rollout or rollback. This ensures the constant uptime of your cluster even if some containers fail.

**Answer the questions below**

Before proceeding, ensure all clusters are started by opening a terminal and running minikube start.

<img width="652" height="172" alt="image 1" src="https://github.com/user-attachments/assets/b8f2c669-d15a-4bce-b735-5aade4fd47c8" />


> How many pods are running on the provided cluster?
> 

1

<img width="632" height="46" alt="image 2" src="https://github.com/user-attachments/assets/f76a1ef3-caf4-4cfa-b888-519539a0222b" />


> How many system pods are running on the provided cluster?
> 

7

<img width="653" height="306" alt="image 3" src="https://github.com/user-attachments/assets/e0f93318-a910-419a-9f01-1fc2698ed613" />


> What is the pod name on the provided cluster?
> 

hello-tryhackme-66c4d4d69d-gb9nz

<img width="653" height="306" alt="image 3" src="https://github.com/user-attachments/assets/91197920-d455-491e-bef6-d186531b67b1" />


> What is the deployment name on the provided cluster?
> 

hello-tryhackme

<img width="532" height="52" alt="image 4" src="https://github.com/user-attachments/assets/91da8441-8ee5-4d7b-a4cb-9beb9f1706e8" />


> What port is exposed by the service in question 5?
> 

443

<img width="615" height="52" alt="image 5" src="https://github.com/user-attachments/assets/c268bbdb-0106-4e07-ad88-f30b920392c7" />


> How many replica sets are deployed on the provided cluster?
> 

1

<img width="527" height="65" alt="image 6" src="https://github.com/user-attachments/assets/bf6d1278-42c6-42ba-b875-12bc1f8cc026" />


> What is the replica set name on the provided cluster?
> 

hello-tryhackme-66c4d4d69d

<img width="527" height="65" alt="image 7" src="https://github.com/user-attachments/assets/4d05e9da-46d1-453b-bfb6-6beddd1b682d" />


> What command would be used to delete the deployment from question 5?
> 

kubectl delete deployment hello-tryhackme
