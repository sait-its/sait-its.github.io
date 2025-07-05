### What is Cloud Native

- Cloud native refers to a specific approach to building, deploying, and managing applications in cloud environments, leveraging the inherent capabilities of cloud computing platforms.
- It uses technologies such as *containers*, *Kubernetes*, *immutable infrastructure*, and *microservices* to develop scalable applications that are built to run in the cloud.

Definitions: [Wikipedia](https://en.wikipedia.org/wiki/Cloud-native_computing), [CNCF](https://github.com/cncf/toc/blob/main/DEFINITION.md), [AWS](https://aws.amazon.com/what-is/cloud-native/), [Azure](https://cloud.google.com/learn/what-is-cloud-native)

---

### Essential Elements

- **It is containerized**. Each part (applications, processes, etc.) is packaged in its own container. This facilitates reproducibility, transparency, and resource isolation.
- **It is dynamically managed**. Containers are actively orchestrated to optimize resource utilization.
- **It is microservices-oriented**. Applications are segmented into microservices, which significantly increases their overall agility and maintainability.

---

### Cloud-native Application Benefits

- Saves money by monitoring and scaling application resources through cloud orchestration, i.e., container schedulers
- Allows teams to ship updates and drive value for customers more quickly
- Aligns operations with business goals
- Reduces time spent on maintenance, meaning more time can be spent focusing on business goals

---

### Common Cloud-native Challenges

- Managing multiple versions of software across different cloud providers
- Scaling applications up and down quickly
- Managing complexity as more services and components are added to the mix
- Dealing with ephemeral infrastructure, which can make debugging and troubleshooting difficult
- Ensuring efficient use of resources, as the pay-as-you-go model of the cloud can quickly get expensive
- Making sure all components work together seamlessly

---

### Common Cloud-native Challenges

- The key to cloud-native development is to use tools like Kubernetes, Docker containers, and Terraform/Ansible to automate deployment, configuration management, and infrastructure provisioning.
- Organizations need to be aware of these challenges and have the necessary strategies and solutions in place to address them as they arise.

---

### Terms (A Lot of Jargon)

- Containerization: Containerization is the process of packaging applications and dependencies as images and then running them as containers.
- Orchestration: an orchestrator is a system that deploys applications and dynamically responds to changes.
- Microservices: applications are built from many small, specialized, independent parts that work together to form a useful application.

---

### Terms (A Lot of Jargon)

- Immutable infrastructure: an IT infrastructure management approach where components are not modified after deployment.
- Cloud native: cloud-native applications possess cloud-like features such as auto-scaling, self-healing, automated updates, rollbacks, and more. Simply running a regular application in the public cloud does **NOT** make it cloud-native.
- Kubernetes is an orchestrator of containerized cloud-native microservices applications.

---

### Building Blocks - Containers

- [Containers](https://about.gitlab.com/blog/2017/11/30/containers-kubernetes-basics/) are an [alternative way to package applications](https://searchitoperations.techtarget.com/tip/What-are-containers-and-how-do-they-work) versus building for virtual machines (VMs) or physical servers directly.
- Everything needed to run an application (such as code, system libraries, and settings) is included in a container image — a lightweight, standalone, executable package of software.
- Containers can run inside of a VM or on a physical server. Containers hold an application’s libraries and processes, but don't include an operating system, making them lightweight.

---

### Building Blocks - Containers

- In the end, fewer servers are needed to run multiple instances of an application, which reduces cost and makes them easier to scale.
- Some other [benefits of containers](https://tsa.com/top-5-benefits-of-containerization/) include faster deployment, better portability and scalability, and improved security.

---

### Building Blocks - Orchestrators

- Once the containers are set, an orchestrator is needed to get them running.
- Container orchestrators direct how and where containers run, fix any that go down, and determine if more are needed.
- When it comes to container orchestrators, also known as schedulers, Kubernetes is the clear-cut [market winner](https://about.gitlab.com/blog/2018/08/02/top-five-cloud-trends/).

---

### Building Blocks - Microservices

- To make apps run more smoothly, they can be broken down into smaller parts, or microservices, to make them easier to scale based on load.
- Microservices infrastructure also makes it easier and faster for engineers to develop an app. Smaller teams can be formed and assigned to take ownership of individual components of the app’s development, allowing engineers to code without potentially impacting another part of the project.
- More on microservices later.

---

### Monolithic Architecture

- With monolithic architectures, all processes are tightly coupled and run as a single service. This means that if one process of the application experiences a spike in demand, the entire architecture must be scaled.
- Adding or improving a monolithic application’s features becomes more complex as the code base grows. This complexity limits experimentation and makes it difficult to implement new ideas.
- Monolithic architectures add risk for application availability because many dependent and tightly coupled processes increase the impact of a single process failure.

---

#### Advantages of Monolithic Architecture

- **Simple to Develop and Deploy**: Developers can get started and keep adding code modules as needed, and the entire application code base and dependencies can be installed in a single environment, making deployment more straightforward
- **Enhanced Performance**: The unified structure of monolithic architecture allows for efficient data exchange mechanisms within the system, potentially leading to enhanced performance.

---

#### Advantages of Monolithic Architecture

- **Less Network Latency and Security Issues**: There are fewer network calls between different parts of the application. This reduces network latency and can lead to fewer security issues.
- **Focus on One Application**: Monolithic architecture allows developers to concentrate on a single application, with all code located in one place. This can make debugging and tracing data movement within the same programming environment easier.

---

#### Disadvantages of Monolithic Architecture

- **Difficult to Manage as it Grows**: As the application grows, it can become complex and challenging to update or change over time. 
- **Entire Redeployment for Small Changes**: When developers introduce new changes to a monolithic application, they must retest and redeploy the entire system on the server.
- **Lack of Scalability and Flexibility**: The entire application must be scaled as requirements change, leading to resource wastage because not all parts of the application need to be at peak capacity.

---

#### Disadvantages of Monolithic Architecture

- **Difficult to Adopt New Technology**: Monolithic architecture limits the ability to introduce new features and technologies in existing applications. There are multiple dependencies that slow down progress.
- **Less Reliability**: A minor error in the code base can cause the whole application to fail, presenting a single point of failure. 

---

### Microservices Architecture

- With a microservices architecture, an application is built as independent components that run each application process as a service.
- These services communicate via a well-defined interface using lightweight APIs. Services are built for business capabilities and each service performs a single function.
- Because they are independently run, each service can be updated, deployed, and scaled to meet demand for specific functions of an application.

---

#### Advantages of Microservices Architecture

- **Agility in Development**: Microservices allow for faster development and deployment cycles, as individual services can be developed, tested, and deployed independently.
- **Flexible Scaling**: Individual services can be scaled independently based on demand, allowing for more efficient use of resources.
- **Supports Horizontal Scaling**: Microservices support distributed systems where each component receives its own computing resources, allowing for independent scaling.

---

#### Advantages of Microservices Architecture

- **Different Technology per Microservice**: The independence of microservices allows developers to use different technologies and frameworks for different services, fostering innovation and flexibility.
- **System Remains Intact if One Microservice Fails**: The failure of a single microservice does not bring down the entire system, enhancing overall reliability.

---

#### Disadvantages of Microservices Architecture

- **More Complex**: Microservices require more planning, design, and coordination, making the architecture more complex to implement and manage.
- **Complicated Independent Deployment**: Each microservice must be deployed independently, which can be more challenging and time-consuming.

---

#### Disadvantages of Microservices Architecture

- **Network latency**: The communication between microservices can lead to increased network usage and latency, potentially affecting performance.
- **Less Secure and Difficult Debugging**: Security can be more challenging to manage across multiple independent services, and debugging may require coordinated efforts across different parts of the system.

---

### Monolithic vs. Microservices

![mono-vs-micro](./cloud-native.assets/mono-vs-micro.jpg) 

---

### From Monolithic to Microservices

- Monolithic architecture is a great way to get your business started. It’s easy to implement and helps you ship quicker. But as you scale, onboard more customers, and have more features to work with, the same architecture can become difficult to maintain.
- The same was the case with [Uber](https://www.uber.com/en-IN/blog/service-oriented-architecture/) which decided to revamp its architecture using the [Service-Oriented Architecture (SOA) principles](https://aws.amazon.com/what-is/service-oriented-architecture/) — an older variant of the microservice approach.

---

### From Monolithic to Microservices

![mono-to-micro](./cloud-native.assets/mono-to-micro.png) 

Credit: [AWS](https://aws.amazon.com/microservices/)

---

### Microservices

![microservices-logical](./cloud-native.assets/microservices-logical.png) 

Credit: [Microsoft](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/microservices)

---

### Best practices of Microservices

- Model services around the business domain.
- Decentralize everything. Individual teams are responsible for designing and building services. Avoid sharing code or data schemas.
- Data storage should be private to the service that owns the data. Use the best storage for each service and data type.
- Services communicate through well-designed APIs. Avoid leaking implementation details. APIs should model the domain, not the internal implementation of the service.

---

### Best practices of Microservices

- Avoid coupling between services. Causes of coupling include shared database schemas and rigid communication protocols.
- Offload cross-cutting concerns, such as authentication and SSL termination, to the gateway.
- Keep domain knowledge out of the gateway. The gateway should handle and route client requests without any knowledge of the business rules or domain logic. Otherwise, the gateway becomes a dependency and can cause coupling between services.

---

### Best practices of Microservices

- Services should have loose coupling and high functional cohesion. Functions that are likely to change together should be packaged and deployed together. If they reside in separate services, those services end up being tightly coupled, because a change in one service will require updating the other service. Overly chatty communication between two services may be a symptom of tight coupling and low cohesion.
- Isolate failures. Use resiliency strategies to prevent failures within a service from cascading.

---



### Key Takeaways

- 

---

### Key Takeaways

- 

---

### Sources:

- https://about.gitlab.com/topics/cloud-native/
- https://aws.amazon.com/microservices/
- https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/microservices
- https://dashbird.io/knowledge-base/well-architected/monolith-vs-microservices/