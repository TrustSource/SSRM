# EOS Responsibilities

In this section we will outline our responsibilities and the measures we implement to cope with them. 

## Overview of our Responsibilities

TrustSource sees it as its responsibility to provide a seamless use experience. We have designed the service for zero downtime. For over three years now, we were able to keep this promise. 

Together with our operating partner AWS we defined a Shared Security Responsibility Model, that clarifies the responsibilities of each side. Since this allows smooth operations, we decided to provide such a guidance for our application and our users as well.

AWS takes care for the security **of** the cloud, while we take care for the security **in** the cloud. The same pattern applies for our relationship: While we take care for the security **of** the application, you will have to take care for the security **in** the application.  

### Measures to protect security of the cloud

AWS provides a set of certifications for their infrastructure to ensure sound and reliable operations of the hardware as the foundation for their business. Almost all their services, at least all the services that we used to provide the application, are compliant with the following security standards (certified by 3rd party):

- SOC 1/SSAE 16/ ISAE 3402 (formerly SAS 70 Type II)
- SOC 2
- SOC 3
- FISMA, DIACAP, FedRAMP
- PCI DSS Level 1
- ISO 27001 Level 1
- ITAR
- FIPS 140-2

The comprehensive security concepts of the datacenter operators guarantee, that data will be protected from theft or damage due to environmental events. All data centers are protected by security staff 24/7 365 days a year. All sensitive internal areas are surveilled by cameras. 2 factor perimeter access control ensures that only authorized people will be able to access. All datacenters provide connectivity to at least two internet providers to ensure relibale availability.

Our partner guarantees the following measures:

#### Power:
All datacenters provide several availability zones, meaning that each zone can be operated without restrictions even if another zone fails. UPS and voltage filters as well as redundant Diesel generators ensure continuous power supply.

#### Air Conditioning and Temerature:
All datacenters organize air conditioning in a way that conditions remain optimal for the operations of servers. Specific staff surveills and organizes the correct conditions concerning temperature and humidity. 

#### Administration:
AWS monitors and continuously maintains all critical systems to keep server operations up and running. Maintenance is done on a prveentive level to reduce failure and outage times.   

#### Decomissioning of Storage:
whenever a storage device will be decommisioned, AWS will execute a decomissioning procedure following the Department of Defense operating manual (5220.22-M) or NIST 800.88 described procedure. Thus it is ensured, that no data remmance may lead to data loss.  


### Measures we established to protect security in the cloud

From our side, we take the responsibility to ensure smooth operations of our our solution. This comprises not only a secure application design following all known [architecture best practises](https://aws.amazon.com/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc&wa-guidance-whitepapers.sort-by=item.additionalFields.sortDate&wa-guidance-whitepapers.sort-order=desc) but also a high degree of automation in deployment and operations.

#### Architectural Design

We make use of the availability zone concept by distributing our services across three availability zones. This does not mean, that services alwas are operated in every three zones, but the deployment, the rights and the data are spread across the three zones, so that failure of up to two zones will not negatively impact the operations of our services. 

The network design follows common best practises for cloud based applications. Thus we operate a multilayered, segmented network with only a handful of endpoints being available in the public zone. Access to private zones is limited to specific roles and only possible through specific access gates. At these gates we monitor the traffic closely and search for anomalies. Communication between clients and the application uses TLS v1.3 encryption to seurce data in motion between the client and the server.

The aplication itself is operated as a service across serval kubernetes clusters. The clusters allow internal failover. Thus if a cluster member fails, the services operated on the corresponding POD will automatically be restarted on another, stil functional or new cluster member. Since the application it self is stateless, the maximal loss will be the failing transaction at the momement of failure, if it cannot be re-run.

The service also measures availability and increases the amount of instances to cope with higher transactional demands. The scaling is organised in several steps, preventing over-scaling and also maintains metrics to automatically down-scale if demand reduces again. Access to the applications is possible only from specified network segments and sources.

Each service operated in the context of TrustSource has its own identity and access policy. To invoke any service a specfic role or group membership is required. These roles or memberships differ by service and are provided on a needs basis. 

#### Web Application Firewall

We operate a web application. This means the application is accessible over the public internet. To prevent unwanted visitors from accessing the application, we operate a Wab application firewall (WAF). The WAF reduces the number of ports that can be called from outside as well as some protection from DoS attacks. In addition the WAF filters and (technically) inspects traffic. 

#### Observability

The complete infrastructure is instrumented and operated in a way, that metrics are collected in a highly available fail-over secured data location. The dashboard and alarms use high available infrastructure provided by our hosting partner to monitor and assess logs as well as service availability. The same infrastructure is used to analyze teh network traffic inside and towards the services. Unexpected routes or unusual transfers are identified and will alert our operations team for further investigations.

#### Key Management

We make use of Key Management Systems (KMS). Thus all  keys used within the application will be stored in a key store with access logs and access protection policies. Thus it is possible to trace key access and get alerted on unauthenticated key access.

We make extensive use of keys. For example will scan results, uploaded and stored for later analysis, be encrypted using company specific keys. Thus even if for some reason the protected storage would become accessible by a third party, data will remain encrypted with the key hidden in the KMS.

#### Separated Environments

One of the most important security measures is the separation of our different system environments. There is one for te develeopment and testing and another one specific for production. This separation allows to make use of different keys, limit access further and completely seggregate poduction data from testing environments. Developers do not have access to our production environment. 

#### Secure Development

All our developments make use of modern CI/CD practises. Based on `pre-commit` we have a set of language specific and some language agnostic tests that we apply on each commit. This comprises the following types of tests:
* formal linting for specific file types (YAML, JSON, MD, etc.)
* language specific linting to cope with coding quality
* language specfic SAST testing
* language specfifc fuzzing (coverage guided)
* default checks (hardcoded credentials etc.)
In addition our developers best practises require the developers to maintain a CHANGELOG for each repository. New components will be added using our TrustSource for Security and Compliance Management. Thus we could claim to be ISO-5230 (OpenChain) compliant. (The completion of the questionnaire remains a open tasks!) 
It is part of the **Definition of Done**, to provide a scripted deployment accompanied with tests to verify proper functionality. The duplication of environments allows a sound preparation and testing by the developer. Once a feature is finalized, a pull request needs to be executed, triggering a peer review. The merged code will be signed and the signature becomes part of the change long. So that it can be verified during deployment that only the right sources will be deployed.

#### Secured Deployment

While deployments to the development environments can be done by the developers themselves, chages to the production environment can only be performed by the operations team. Installing a four eyes principle may not be the best practise of modern deployment, but TrustSource is not only a SaaS, it also has a compliance responsibility. This comprises providing an immutable trace of events that lead to changes on configurations and / or data on client side. technical manipulation of this data must be prevented. 

TrustSource is built based on MongoDB, a document database. The services have been designed to tolerate unknown data elements without failing (e.g. using projections). Thus even structural updates can be provided incremental. While one service already populates data to the database, another service still cannot handle the data but still will be able to operate the documents. A proper semantic co-ordination is part of the release-management process.  

Depending on the character of the change, it will be possible to start deploying in a canary mode. However, since all deployments are scripted and executed towards the environment using a transaction manager, rollback will always be a valid option. 

#### BCM

For the unlikely event of complete region outage, we backup data into a second region (currently Ireland) and have a defined procedure on how to rebuild infrastructure within two hours from failure. This procedure is tested on an annual base (ramping up the complete infratsructure in a new datacenter). The results are logged and reviewed for further improvements and adjustments. 

## Our Partners

To provide TrustSource at an affordable subscritpion price, we operate it on AWS. Thus we rely partly on the professionalism of our 3rd party certified partner. A detailed description of what AWS brings to the table when it comes to the provisioning of datacenter services and how this is organised can be found in [this document](!https://aws.amazon.com/compliance/data-center/controls/).

In addition we work with MongoDB, providing us with Cluster and Database management software. The clusters are operated by us on top of our AWS infrastructure without Mongo having access to neither our code nor access to the data. This data, under no circumstances, contains any customer data or PII. Mongo Atlas will receive only technical usage statistics on database metrics, such as durations of transactions, number of bytes read, etc..

We have closed the standard data processing agreement following the European standards with AWS. If you are planning to become our customer and we conclude serious negotiations, you will have signed an NDA with your account representative. Under these prerequisites, you will be able to get a copy of this contract. 

