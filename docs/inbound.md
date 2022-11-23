# Integrity of Inbound Data

This section addresses all sort of data that goes into the system. The first section addresses general aspects 

## Inbound Quality

TrustSource provides you with a sound 

### Completeness

To provide a compliant documentation, it is essential to be complete. TrustSource provides different means to support the goal of completeness: 
* SBOMs
* Infrastructure components
* 3rd party components (COTS)
* Filebased assessments
* Lnk between Meta-Data and binaries
However, it is in the repsonsibility of the system designer to thrive for completion. There is currently no way for TrustSource to verify completeness. We might hint on missing components based on identified solutions. But we can't distinguish whether a component has been left out by accident or intention. 

### Correctness

Another important aspect is correctness. TrustSource collects and provides meta-data provided by 3rd parties. Our goal is to simplify the collection and clearance. That's why we have added all the tooling and clearance support tasks and tools. However, there remain cases were it is not always claer which license a particular piece of code follows. These situations require license conclusion. Decisions on which license is concluded are in Your responsibility.

The same applies to declared licenses. TrustSource indicates what type of license is known for a particular component. It also provides the option to verify this declaration with a press of a button - thus deepscan will download the repo and assess the sources in the background and provide the results, as well as the concluded / effective licenses. It remains in Your responsibility, to verify this conclusion in critical cases. 

### Integrity

## Uploading Scans

### Our Responsibility

It is TrustSource's responsibility to ensure the upload is technically possible, meaning a service endpoint will be available, given  authentication and authorisation can be successfully performed. 

In addition it is TrustSource's responsibility to ensure that data uploaded, will be processed properly, provided the data is in the correct format and size. If the latter is not given, it is TrustSurce's responsibility to discard the uploaded data and prevent system failure as well as keep the integrity of the data and availability of the system.


### Your Responsibility

We aim to cope with sudden load increases. However, despite a sound capablity to cope with such increases there always will be a number of requests that is high enough to exceed provided capacity. If you can forsee that you will require an extraordinary amount of requests in a short amount of time, it would be in your responsibility to alert our operations team upfront. We would recommend to get a notification if you plan to send more than 10 SBOMs / sec for a period a several minutes. Please reach out to your client representative or open a ticket with our support.


### Capturing the right Dependencies

Dev vs. Prod

### Scanning Containers

### Scanning Binaries

The TrustSource platform currently does not support tooling for the scanning of binaries. You may ask EACG to support on that task or just provide an SBOM you want to associate with your projects. TrustSource will be able to import the information found. 

## Uploading SBOMs

## Uploading Threat Models

