# Integrity of Outbound Artifacts

One of the main reasons to use TrustSource is the need to produce **Outbound Artifacts**. These artifacts comprise:

1. Software Bill of Materials (SBOM) - a list of ingredients a software consists of concerning a particular version
2. Vulnerability Exploitability Exchange (VEX) - documents the current status of vulnerabilities concerning a particular product/version
3. Notice files - legal documentation, to cope with the need of legal documentation 
4. SOUP lists - lists used to document Software of unknown Provenance 

Depeding on the document, the requirements 

## Software Bill of Materials

TrustSource allows to combine several elements in a **Software bill of material (SBOM)**. It may contain:

- Software components and their transitive dependencies
- Infrastructure components 
- 3rd party services
- Common of the Shelf (COTS) components, e.g. closed source such as Oracle or SAP.

Per each component data following the NTIA requirements for SBOMs can be colleted and added to the entry. In addition, further information as required by the Medical Device Directive, respectively ISO 62326 can be added to the components. 

TrustSource does not only provide the tooling to collect all that information and mechanisms to generate the reports or versionable documents. We also support the data collection for open source components by integrating with the different eco-systems and pulling the data where possible.

However, not all these searches will in all cases be successful. Thus data may be missing or outdated. One of the most difficult cases to detect are abandonded or stale repositories where the newer versions are hosted in another repository, Such *moves* are difficult to detect. However, if you come across such a situation, please send a mail to our support, they will know how to handle and resolve the case. We see it as our responsibility to provide you with the best collection of data possible.

In addition, we provide the means of infrastructure, services and COTS. None of these have meta data publicly available or a sort of public meta data repository such as *maven* or *pypi*. Therefor it remains in your responsibility to collect and manage this information. TrustSource will try to support you by giving hints where it susüects components or feels information might be missing, but it has no source to resolve the task for you.

Therefor it remains in your repsonisbility to verify that SBOMs are complete, meaning that they contain all components of the application. 

## Vulnerability Exploitability Exchange Documents

The idea of the **Vulnerability Exploitability Exchange (VEX)** documents is, to provide a docuemnt allowing for automation of the cumbersome manual analysis and followup of vulnerability management. VEX has been introduced as part of the [OASIS Common Security Advisory Framework (CSAF) 2.0](https://https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html)., mainly driven by NTIA and German BSI. These documents shall be machine readable and allow the automated consumption of handling advisories concerning vulnerabilities.

The idea is, that a user will not have to verify all potential matchings anymore and chase around to get information from its software vendors on how or whether to patch a particular product version. Intstead the user shall download the latest VEX and see the status concerning the vulnerability. 

TrustSource aims to support software and hardware vendors in resolving this upcoming responsibility. Therefor it will be possible to create, distribute and maintain VEX dcouments based upon specific release information. Each release can be supplied with a specific API key, that allows to pull the release-specific VEX document in its current status. Thus a vendor will only need to provide the API-Key (e.g. via QR code) with his Software version and the user may pull the corresponding document to learn how to deal with the vulnerability. It is in TrustSource's repsonisbility to provide the mechanisms to support this behavior.

However, there is still the descision on how to treat an identified vulnerability. This decision as well as the documentation on what to do remains in the responsibility of the user. TrustSource will notify the user (see Vulnerability Alert), if new Known Vulnerabilities will occur in the code scanned by and managed through TrustSource. But the analysis on whether the vulnerability is really criitcal or requires treatement remains with You. 

PLEASE NOTE: It is also possible that you recognise during penetration testing or some upgrades new vulnerabilities in your own code. Currently you may add these to your components and/or solutions manually. These can then also be managed in VEX documents. currently it is not possible to publish such vulnerabilities directly to NVD. We are evaluating this porocess, but it is in YOUR responsibility to arrange the according steps.

## Notice Files

The **Notice File** is the legal documentation of your delivered solution (hardware, software, 3rd party services, etc). It organises compliance through resolving obligations. This comprises attribution requirements, change notifications and the presentation of license texts, etc. 

TrustSource determines based on the business and legal circumstances defined on the project and module settings the legal obligations according to the corresponding license. To achieve this, TrustSource organises a legal solver , a license database and the documentation of the legal circumstances. The solver takes these input together with the status of the component (coupling and modification state) and determines the resulting obligations. These obligations are used to generate the skeleton of the corrsponding Notice file. 

It is TrustSource's responsibility, that the mechanism generating the skeleton is working properly. TrustSource has worked with CMS, a legal consulting firm, to resolve the license obligations. These are stored in the license database, which is used by the solver to determine the obligations. However, it is in TrustSource's responsibility to ensure licenses are provided. 

From time to time it may happen that new or unknown licenses appear. In this case TrustSource will issue a warning and show that "*License could not be macthed*". It is in YOUR responsibility to resolve such cases. The simplest way is to forward the component key to TrustSource Support and request analysis of the corresponding component. If the component is a public component, our agents will take care and let you know, when the resolution is completed. Typically this should be possible within 48hrs business time.

You also may take action by yourself. TrustSource provides two means to assess license informatin and operates a shared component database to collect clearing information on open source components. The first source for meta data are the package management systems. In general these systems contain a basic set of declared license information. Unfortunately this information is not always complete and/or correct. Sometimes it may happen, that mantainers overlook a component or license which may infect the rest of the components. Thus a component declared as Apache may actually result in being GPL2.

To cope with such issues, TrustSource also provides the capability to run a "*DeepScan*" on a repository. This scan asssess all text files in a repository and identifies all license texts. [DeepScan](https://deepscan.trustsource.io) is available in different flavours:  
- a limited version for public repositories is available as [public SaaS](https://deepscan.trustsource.io) soultion
- a full blown SaaS implementation for private repositories is availabe embedded in [TrustSurce](https://app.trustsource.io)
- a full featured CLI version is available at [Github](https://github.com/trustsource/ts-deepscan) for download, this also can be installed through pip "ts-deepscan"

It is TrustSource's responsibility to provide the solutions and ensure, that they work. It is in YOUR responsibility, to make use of these tools to determine the correctness and completeness of the information provided within the Notice File.

## Software of unknown provenance

Documentation of **Software of unknown provenance (SOUP)** is a requirement primarily known in the Medical Industries. It is a collection of all software components that are not developed inhouse. This comprises Common of the Shelf (COTS) solutions purchased from 3rd parties as well as Open Source components. 

TrustSource provides - in the medical edition - a capability to assemble these lists and maintain the meta data of these componnets. The process to maintain this data is in YOUR responsibility.   

## Binary Links

Trustsource allows to create a link between the meta data provided in the Notice File or SBOM with a specific binary artifact. This can be done trough the UI or by API. It is in YOUR responsibility to arrange the correct matching.

