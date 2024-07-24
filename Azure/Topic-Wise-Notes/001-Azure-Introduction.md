Azure-Introduction
-----------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Azure provides a wide array of services and technologies that can easily fulfill most realworld use cases. The services provided by Azure can be categorized like so.

**Infrastructure as a Service (IaaS)**: 
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    In IaaS, you get the bare infrastructure such as VMs, VNets, and storage, and you need to build the rest of the application stack yourself. This option gives the most flexibility for the
    developers in terms of OS versions, library versions, custom patches, and so on
-----------------------------------------------------------------------------------------------------------------------------------------------------------    

**Platform as a Service (PaaS)**: 
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    In PaaS, the software platforms are pre-installed and pre-configured. These are managed services in the sense that Azure manages the life cycle of this software for you. 
    Examples include Azure SQL Server, Azure Databricks, and Azure Kubernetes Service. You will still be able to tune the software to some level, but you might not have the flexibility of choosing particular versions, patches, and so on.
-----------------------------------------------------------------------------------------------------------------------------------------------------------    

**Software as a Service (SaaS), also known as Function as a Service (FaaS)**:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    What other platforms call Software as a Service (SaaS), Azure refers to as Function as a Service (FaaS). In SaaS or FaaS, you don't get to see any of the software installation details. You usually have a notebook-like user interface or an API interface for directly submitting your jobs; the cloud service provider takes care of instantiating the service, scaling the service and running the jobs for you. This is the easiest and quickest way to get started but the most restrictive in terms of software setup. 
    Examples include Azure Functions, Azure Synapse SQL Serverless, and so on
-----------------------------------------------------------------------------------------------------------------------------------------------------------    

![Github Image](/Azure/Assets/Azure-Cloud/Assets-Breakdown-of-Azure-Offerings.JPG)    

