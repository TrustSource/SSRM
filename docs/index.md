# Shared Security Responsibility Model - Guidance for TrustSource Users

The **Shared Security Responsibility Model (SSRM)** is a model to describe the distribution of responsibility. YOU, as the user of TrustSource, want to have your data processed in a secure way. We, as the provider, aim to achieve this. But we both have to work together, to succed. This SSRM Guidance has been provided, to clarify each partie's responsibilities, as well as to support YOU in understanding and coping with YOUR responsibilities.

Feel free to reach out anytime, to clarify questions through mail under ```support @ trustsource.io``` or contact your account representative.

## The Shard Security Responsibility

TrustSource helps in providing Security and Compliance for software applications. In scope of this, TrustSource itself has the aim to be secure und compliant itself. TrustSource has a strong set of security policies to achieve this. This will support what we call **Security of the Application**.
However, to provide a secure solution, it is not only done with a secure application. Also the use of the application comes with a certaiin responsibility, which we call **Security in the Application**.
This document outlines these two aspects and gives guidance on how to achieve this goal. As a simple guideline you may assuem that we and our partners will ensure the **Security of the application** while it remains YOUR responsibility to ensure **Security in the application**.

## Scope

This document addresses the use of TrustSource in general. It will not distinguish between different versions or editions. It is written with the Software as a Service hosted by EACG Operation Services in mind. If you operate TrustSource or parts of it in another constellation the guidance may not apply. Check with your account representative, if you are not sure, whether it applies to your case.

## Table of Contents

This document is structured into six sections with differnt focus:

 1. This Introduction, which guides you through the idea and reading hints
 2. [EACG Operations Services GmbH Responsibilities](/SSRM/eos/) - here you will find information about the controls and protection we  take care of. 
 3. [Access Security](/SSRM/accessSecurity/) - this describes how access security is organized, and how you will be able to achieve a maximum of access control
 4. [Data Integrity](/SSRM/dataIntegrity/) - here you get insights on our data management and will learn what you may do to ensure integrity from your side
 5. [Artefact Integrity](/SSRM/artefactIntegrity/) - this gives an overview of what is produced and what you may do to improve integrity of your data
 6. [Handling Alerts](SSRM/handlingAlerts/) - Trustsource does not only take data. It is also producing information to act upon. You should be aware of this data an ensure activity will be taken. This chapter will help you to understand what is possible and how to arrange notifications.

## How to read the document

If you are a new user and have endless time, we suggest to read everyting from beginning to start. But most likely you already denied the second condition and thus are seeking a way to reduce the effort to achieve your goal. In this case follow one of the role-specific paths outlined here:

- System Administrator / Operations 

You most likely will have to go through chapters 3, 4 and the intro to 5. Depending on your organisation, it be useful to also get an idea of the alert options described in Chapter 6. Please do not forget to look into the following subsection of this page. There are some geenral contact and communication links.

- Data Security or Data Protection Officer

You may focus chapter 2 and the intro to chapter 4.

- Security Architect concerned about TrustSource Security

Focus on chapter 2. There you will learn about our ITSM and protection mechanisms. In addition have a look at chapter 3, Access Security.

- Project or Product Manager

Be sure to get an idea of 3 but focus on chapters 4 and 6.

- Compliance Manager

You should also get an idea of 3. Main interest should be on chapters 4 and 5. 

- Developer

You may focus on the introductions of chapters 3, 4, 5 and 6. The details you may add upon demand.

## Further Sources of Knowledge

You should be aware of the different sources you may tap to learn about TrustSource:

- Tools: TrustSource is a large aggregation of services and tools. Many of our tools are provided as opensource and can be found on [Github](https://github.com/trustsource)
- System Monitoring: at the bottom of each screen you will find a link to our public [System Monitoring](https://status.trustsource.io)
- System Management Notifications: in the above linked page you will be able to subscribe to a newsletter, where will announce changes and system updates. 
- Knowledge Base: at the top right of the application there is a link to our online [Knowledge base](https://support.trustsource.io)
- FAQ: the Knowledgebase is available to everyone and contains information on compliance, establishing Compliance processes, setting up an OSPO, integrating different programming languages / CI/CD flows with TrustSource, how to handle use cases within TrustSource, etc.
- If you are a subscribed to TrustSource you also are eligible to may write an email to our support team at [support@trustsource.io](mailto://support@trustsource.io)
- Direct contact: You will find our contact details, at our website under [www.trustsource.io/contact](https://www.trustsource.io/contact)

# License

This documentation is provided under CC-BY-SA-4.0. You may clone or fork this repository and create you own Shared Responsibility Model (SSRM) based on these documents. But please make sure to remove all references to TrustSource and EACG except an attribution notice. EACG as well as TrustSource and the corresponding logos are protected Trademarks and should not be used without a written approval by any third party.

This documentation may change. We will notify changes through the systems management notification mailing list.

