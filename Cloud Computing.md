# Cloud Computing

#### Scalability in Cloud
* Cloud Computing allows you to easily add and remove resources as you need them
* There are two types of scaling:
    * Vertical scaling allows you to change the power of your existing instance. You could get a more powerful server for example
    * With horizontal scaling, you are simply increasing the number of instances you're using, sharing the workload across multiple devices

### Cloud Services Models
* Infrastructure as a Service (IaaS) - offers cloud infrastructure
* Platform as a Service (PaaS) - offers infrastructure and software for application development
* Software as a Service (SaaS) - offers ready-to-use applications in the cloud

![Cloud Services Models](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Cloud-Services-Models.PNG "Cloud Services Models")

* FaaS (Function as a Service) is a variation on SaaS, except that now you're only concerned with a single function, or part of the software
* For example, you can run identity authentication, or payment transactions
* FaaS often uses a billing model called "serverless"
* This is slightly misleading because the computations are still run on a server - what it means is that you pay for the service rather than paying to rent servers
* Serverless architecture is where managing the server and allocating resources is handled by the cloud 

### The Cloud Pyramid: Abstraction vs Control
![Cloud Pyramid](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Cloud-Pyramid.PNG "Cloud Pyramid")

### Cloud Deployment Models
#### Private Cloud
* The private cloud model is private by design and designated for exclusive use by its tenants
* This means to access a private cloud, you need to connect to a network link, which means special network access needs to be set up by IT
* An organization may hire a third party to host their private cloud infrastructure or host it themselves
* Private cloud is different from on-premise in the following ways:
   * The infrastructure in this model adheres to cloud principles, meaning it uses virtualization that allows on-demand compute resources
   * Private cloud can also be located off-premises

#### Public Cloud
* The cloud infrastructure is shared and open for use by the general public
* The infrastructure is owned and managed by a cloud service provider, like AWS or Azure
* Public clouds are Internet accessible, hence organizations can get started quickly with minimal investment

#### Hybrid Cloud
* This is when an organization uses a combination of two or more distinct models
* The different models interact with each other via a network link and can share data and services
* It's more of a question of where data and services are physically stored
* For example, you could store sensitive patient data on a private cloud for security reasons and use an application on the public cloud, like a business intelligence tool, to process it
* Hybrid clouds are useful in the case of cloud bursting. This is when a private cloud is overwhelmed by demand and hits capacity
* To avoid disruption of service to users, traffic is moved to a public cloud instance. This allows organizations to cost-effectively handle periodic spikes with pay-per-use pricing

### Cloud Providers
#### 1. AWS
* AWS launched in 2006, two years before Google Cloud (2008) and four years before Microsoft Azure (2010); hence is the market leader
* For Personal Cloud, AWS offers Amazon drive and Amazon photos
* For Professional Cloud, AWS offers:
   * Simple Storage Service (S3) for file storage
   * Elastic Compute Cloud, (EC2) for computation
   * Relational Database Service (RDS) for databases
   * Redshift - analytics and data warehousing
   * Kinesis - real time data movement and analytics
   * SageMaker - predictive analytics and machine learning

#### 2. MS Azure
* For Personal Cloud, MS offers OneDrive
* For Professional Cloud, Azure offers:
   * Azure Blob Storage for file storage
   * Azure Virtual Machines for computation
   * Azure SQL Database for databases
   * Data Lake Storage - store data before cleaning
   * Stream Analytics - real time analytics
   * Azure Machine Learning - train and deploy ML models

#### 3. Google Cloud
* For Personal Cloud, Google offers Google Drive and Google Photos
* For Professional Cloud, Google offers:
   * Google Cloud Storage for file storage
   * Google Cloud Compute Engine for computation
   * Google Cloud SQL for databases
   * Big Query - data warehouse
   * Dataflow - batch and stream data processing
   * AutoML - ML model training and development
* Google Cloud acknowledges that multicloud - which is a combination of different cloud provider services - is the future and that consumers don't want to be locked in
* In 2019, Google launched Google Cloud Anthos, which lets you deploy and run hybrid multicloud solutions, combining on-premise servers and several cloud providers, all in one place
