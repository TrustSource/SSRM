# Data Integrity 

This section addresses all sort of data that goes into the system. The first section addresses general aspects 

## Inbound Quality

TrustSource provides you with a preset of tooling, configured to allow the effortless execution of compliance and security tasks associated with the use of open source. To ensure proper results, the provided materials must satisfy three requirements. The must be complete, correct and free of manipulation. To achieve  these requirements, 

### Completeness

To provide a compliant documentation, it is essential to be complete. TrustSource provides different means to support the goal of completeness: 

* SCA for creation of SBOMs on source code during compilation
* SCA for analysis of Docker Containers
* Repository analysis for license discovery
* Management of Infrastructure components
* Administration of 3rd party components (COTS)
* Link of modules into re-used code
* Link between Meta-Data and binaries

However, it is in the responsibility of the user to thrive for completion. There is currently no way for TrustSource to verify completeness. We might hint on missing components based on identified applied well known solutions. But we can't distinguish whether a component has been left out by accident or intention. Thus it remains in the responsibility of the project owner to testify conpleteness.

### Correctness

Another important aspect is correctness. TrustSource collects and provides meta-data provided by 3rd parties. Our goal is to simplify the collection and clearance of all this meta data. That's why we have added all the tooling and clearance support tasks and tools. However, there remain cases were it is not always clear which license a particular piece of code follows. Some components even allow the choice of the license to use. 

These situations require license conclusion. Decisions on which license is concluded are in your responsibility. 

The same applies to declared licenses. TrustSource indicates what type of license is known for a particular component. It also provides the option to verify this declaration with a press of a button - thus deepscan will download the repository, assess the sources for license indications and provide the findings. But it remains your responsibility, to make the decision out of it and accept the information as compliant or not. 

### Integrity

TrustSource will take care that all data uploaded and provided to TrustSource remains full integrity. It also takes the responsibility of providing tools creating inbound artifacts. For these tools we take the responsibility that all information found will be correct and formats produced will be fine and accepted by TrustSource. 

However, it is possible to produce scans, store them locally, manipulate or remove entries from the findings lists and upload these manipulated scans to TrustSource. Given a component with strong copyleft license is removed, TrustSource will not be able to identify this missing component and hence, not be able to alert you, if this would not suit your goals.

TrustSource provides upload authentication through API keys (see [API key management](https://support.trustsource.io/hc/en-us/articles/8624792507922-How-to-manage-API-keys)) and allows integration into automated executions, thus preventing manipulation. However, it is in your responsibility, that the uploaded data will not be manipulated. 

## Uploading Scans

### Our Responsibility

It is TrustSource's responsibility to ensure the upload is technically possible, meaning a service endpoint will be available, given  authentication and authorisation can be successfully performed. 

In addition it is TrustSource's responsibility to ensure that data uploaded, will be processed properly, provided the data is in the correct format and size. If the latter is not given, it is TrustSurce's responsibility to discard the uploaded data and prevent system failure as well as keep the integrity of the data and availability of the system.


### Your Responsibility

We aim to cope with sudden load increases. However, despite a sound capablity to cope with such increases there always will be a number of requests that is high enough to exceed provided capacity. If you can forsee that you will require an extraordinary amount of requests in a short amount of time, it would be in your responsibility to alert our operations team upfront. We would recommend to get a notification if you plan to send more than 10 SBOMs / sec for a period a several minutes. Please reach out to your client representative or open a ticket with our support.


### Capturing the right Dependencies

It is important to understand that scanning a repository is not sufficient to determine the composition of a software. During build time, additional components may be added by the compiler. We differentiate between **Direct Dependencies**, which are directly described as dependencies and **Transitive Dependencies**, which are added by these direct depdencies. 

Our scanners are ecosystem specific and work different to collect what is used to build the service. They collect, what will is used to build the solution. This is, why we are able to show the **Transitive Dependencies** as well as the path, from where they entered the solution.

If you decide to use a 3rd party scanner, make sure you will pic one that also will take care of the transitive views.

However, besides the production relevant dependencies, often tooling is added which is required for testing, metering or other purposes. We summarize these dependencies as **DEV Dependencies**.

Please ensure, that your SBOMs used for release will *not* contain these unnecessary dependencies!

They will create a huge amount of work and add complexity that is not required. That is why we skip them in general. If you want to manage these services as well, you may add them. For some ecosystems we have added the capability to switch them explicitely on during scanning, see e.g. [TrustSource Node scanner](https://github.com/trustsource/ts-node-client)) But we higly recommend to provide specific "*test projects*" for these scans, so they can be managed but will not interfere with your release process.

All that said, it must be clear, that it is your responsibility to determine the completeness of what is scanned. 

### Scanning Containers

Docker is haven for developers. Allowing to build layers independently and pushing alltogether around changed development and especially operations exceptionally. However, as you may imagine, the comfortable it is, that many risks it bears.

Who knows, what has been put into an image? Who trusts images on docker hub? It is reported that studies found **hub images to carry some sort of cryptomining, spy- or malware [1]. Better not trust any image you have not built by yourself!** 

Therefor we recommend to provide a sort of a golden basic image, which you re-use across your solutions. You may create an SBOM and a release per layer, using the former layer as a linked module.   

[1] see https://howtoremove.guide/docker-hub-cryptomining-malware/ or https://unit42.paloaltonetworks.com/cryptojacking-docker-images-for-mining-monero/


### Scanning Binaries

The TrustSource platform currently does not support tooling for the scanning of binaries. You may ask EACG to support on that task or just provide an SBOM created by any binary scanner of your choice you want to associate with your projects. TrustSource will be able to import the information found and thus inject it into your solution SBOM. 

To identify binaries within your code base, we suggest to use the OpenSSF test on binaries. To execute such a test, you may either scan your repository using OpenSSF scorecard locally or use the [TrustSource OpenSSF Scorecard Service](https://support.trustsource.io/scorecard) 

If you seek support in scanning binaries, feel free to reach out to [EACG](https://www.eacg.de), our mother company. They have the resources and skills available to assist you with that task.

## Uploading SBOMs

TrustSource provides the capability to upload SBOMs. These SBOMs will be treated the same way as TrustSource scans. You may select the project and module you want to push the SBOM to. It is possible to select either **CycloneDX** or **SPDX** format for the import.

**PLEASE NOTE:** TrustSource will reject every upload >10 MB. If you want to upload larger SBOMs, please contact our [Support](maito:support@trustsource.io) or see our [knowledgebase](https://support.trustsurce.io)

Completeness and correctness of the SBOM contents as well as providing a valid SBOM format is your repsonisbiity.

Assessing the contents of the SBOM and adding the data into the overall compliance flow is the responsibility of TrustSource.

