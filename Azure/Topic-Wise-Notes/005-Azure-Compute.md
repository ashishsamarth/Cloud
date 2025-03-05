Azure-Compute
-----------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
**VM Scale Sets**
-----------------------------------------------------------------------------------------------------------------------------------------------------------
VM Scale Sets is a collection of load-balanced VMs that can be used to build highly scalable services. 
For example: we can have a set of web servers that can scale horizontally based on the load. The advantage of using VM Scale Sets as opposed to manually setting up VMs is that VM Scale Sets can be launched and managed using centralized templates. It
comes with a load balancer by default, so we don't have to set it up manually. It also takes care of automatic scale out and scale in based on the load. In addition, VM Scale Sets have higher reliability as the workload is spread across multiple servers. Even if a few nodes fail, VM Scale Sets can quickly bring up additional nodes to replace the capacity. VM Scale Sets can be configured across availability zones to improve the availability even more

**Azure App Service**: 
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Azure App Service allows you to develop and host web apps, mobile apps, and APIs using a wide selection of languages such as .NET, Java, Node.js, Python, ASP.NET, and more. These are fully managed services that provide support for the entire life cycle of
apps such as development, CI/CD, releases, maintenance, debugging, and scaling. Azure App Service is backed by enterprise-grade security and compliance.

**Azure Kubernetes Service**: 
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Kubernetes is an open source container orchestration software. Azure Kubernetes Service (AKS) is a PaaS version of Kubernetes that's hosted on Azure. AKS provides a complete life cycle management for containerized apps, starting from development (using Visual Studio, code, and other Kubernetes tools), through to CI/CD (integration with GitHub), deployment, scaling, telemetry, logging, monitoring, and more. AKS also supports Docker images, which are widely used for containerization.

**Azure Functions**: 
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Azure Functions is a perfect example of a serverless technology and is a SaaS. Serverless doesn't mean that there are no servers, it just means that you don't have to deploy, maintain, or upgrade your servers (VMs); someone else is doing it for you in the
background and abstracting the details from you. You can use functions to write your processing logic based on event triggers and bindings such as a transaction in a database, an IoT event, and a REST call. 
The blocks of code you write are called functions. All you need to do is open the Azure Functions Notebook Interface and write your logic (code) directly in it. There are function extensions available in the many languages that support integration with Development, CI/CD, and DevOps tools.

**Azure Service Fabric**: 
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Service Fabric is a very powerful cluster technology that takes care of app deployment, scaling, upgrades, and maintenance for microservice-based applications. It can take care of the entire life cycle management process for applications. This is similar to AKS but for non-containerized applications. Many of the core Azure services themselves run on top of Service Fabric. Service Fabric is an open source project and has very high reliability and availability