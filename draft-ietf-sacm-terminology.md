---
title: Security Automation and Continuous Monitoring (SACM) Terminology
abbrev: SACM Terminology
docname: draft-ietf-sacm-terminology-latest
stand_alone: true
ipr: trust200902
area: Security
wg: SACM Working Group
kw: Internet-Draft
cat: info
coding: us-ascii
pi:
  toc: yes
  sortrefs: yes
  symrefs: yes

author:
- ins: H. Birkholz
  name: Henk Birkholz
  org: Fraunhofer SIT
  abbrev: Fraunhofer SIT
  email: henk.birkholz@sit.fraunhofer.de
  street: Rheinstrasse 75
  code: '64295'
  city: Darmstadt
  country: Germany
- ins: J. Lu
  name: Jarrett Lu
  org: Oracle Corporation
  email: jarrett.lu@oracle.com
  street: 4180 Network Circle
  code: '95054'
  city: Santa Clara
  region: CA
  country: USA
- ins: J. Strassner
  name: John Strassner
  org: Huawei Technologies
  email: john.sc.strassner@huawei.com
  street: 2330 Central Expressway
  code: 95138
  city: Santa Clara
  region: CA
  country: USA
- ins: N. Cam-Winget
  name: Nancy Cam-Winget
  org: Cisco Systems
  email: ncamwing@cisco.com
  street: 3550 Cisco Way
  code: '95134'
  city: San Jose
  region: CA
  country: USA
- ins: A. Montville
  name: Adam Montville
  org: Center for Internet Security
  abbrev: CIS
  email: adam.w.montville@gmail.com
  street: 31 Tech Valley Drive
  city: East Greenbush
  code: '12061'
  region: NY
  country: USA

normative:
  RFC6933:
  RFC5792:

informative:
  I-D.ietf-i2nsf-terminology: i2nsft
  I-D.ietf-sacm-vuln-scenario: vulnass
  RFC3444:
  RFC4949:
  RFC5209:
  RFC6192:
  I-D.ietf-netmod-entity: yang-hw
  X.1252:
    title: "ITU-T X.1252 (04/2010)"


--- abstract

This memo documents terminology used in the documents produced by SACM (Security Automation and Continuous Monitoring).

--- middle


# Introduction

Our goal with this document is to improve our agreement on the terminology used in documents produced by the IETF Working Group for Security Automation and Continuous Monitoring.  Agreeing on terminology should help reach consensus on which problems we're trying to solve, and propose solutions and decide which ones to use.

# Terms and Definitions

This section describes terms that have been defined by other RFC's and defines new ones.  The predefined terms will reference the RFC and where appropriate will be annotated with the specific context by which the term is used in SACM. Note that explanatory or informational augmentation to definitions are segregated from the definitions themselves. The definition for the term immediately follows the term on the same line, whereas expositional text is contained in subsequent paragraphs immediately following the definition.

Assertion:

: Defined by the ITU in {{X.1252}} as "a statement made by an entity without accompanying evidence of its validity".

Assessment:

: Defined in {{RFC5209}} as "the process of collecting posture for a set of capabilities on the endpoint (e.g., host-based firewall) such that the appropriate validators may evaluate the posture against compliance policy."


Asset:

: Is a system resource, as defined in {{RFC4949}}, that may be composed of other assets.

: TODO: Should we change "asset" to "SACM asset" or something like that?

Asset Management:

: The process by which assets are provisioned, updated, maintained and deprecated.

Attribute:

: Is a data element, as defined in {{RFC5209}}, that is atomic.

: TODO: Should we change "Attribute" to "SACM Attribute" or something like that?

Authentication:

: Defined in {{RFC4949}} as "the process of verifying a claim that a system entity or system resource has a certain attribute value."

Authorization:

: Defined in {{RFC4949}} as "an approval that is granted to a system entity to access a system resource."


Capability:

: A set of features that are available from a SACM Component.

: See also "capability" in {{-i2nsft}}.


Collection Result:

: Is a composition of one or more content elements carrying information about a target endpoint, that is produced by a collector when conducting a collection task.

Collection Task:

: A targeted task that collects attributes and/or corresponding attribute values from target endpoint.

: There are four types of frequency collection tasks can be conducted with:

: ad-hoc, e.g. triggered by a unsolicited query

: conditional, e.g. triggered in accordance with policies included in the compositions of workflows

: scheduled, e.g. in regular intervals, such as every minute or weekly

: continuously, e.g. a network behavior observation

: There are three types of collection methods, each requiring an appropriate set of functions to be included in the SACM component conducting the collection task:

: Self-Reporting: A SACM component located on the target endpoint itself conducts the collection task.

: Remote-Acquisition: A SACM component located on an Endpoint different from the target endpoint conducts the collection task via interfaces available on the target endpoint, e.g. SNMP/NETCONF or WMI.

: Behavior-Observation: A SACM component located on an Endpoint different from the target endpoint observes network traffic related to the target endpoint and conducts the collection task via interpretation of that network traffic.

Collector:

: A piece of software that acquires information about one or more target endpoints by conducting collection tasks.

Configuration:

: A non-volatile subset of the endpoint attributes of a endpoint that is intended to be unaffected by a normal reboot-cycle.

: TODO: why non-volatile? (does volatility even matter?)

Configuration Drift:

: The disposition of endpoint characteristics to change over time.

Consumer:

: Is a SACM Role that contains functions to receive information from other SACM Components.

Content Element:

: Content elements constitute the payload data (SACM content) transferred via statement Subjects emitted by providers of information. Every content element Subject includes a specific content Subject and a corresponding content metadata Subject.

Content Metadata:

: Data about content Subjects. Every content-element includes a content metadata Subject. The Subject can include any information element that can annotate the content transferred. Examples include time stamps or data provenance Subjects.

Control Plane:

: Typically used as a term in the context of routing, e.g. {{RFC6192}}. In the context of SACM, the control plane is an architectural component providing common control functions to all SACM components, including authentication, authorization, (capability) discovery or negotiation, registration and subscription. The control plane orchestrates the flow on the data plane according to imperative guidance (i.e. configuration) received via the management plane. SACM components with interfaces to the control plane have knowledge of the capabilities of other SACM components within a SACM domain.

Controller:

: A controller is a SACM Role that is assigned to a SACM component containing control plane functions managing and facilitating information sharing or execute on security functions.

: There are three types of SACM controllers: Broker, Proxy, and Repository. Depending on its type, a controller can also contain functions that have interfaces on the data plane.

Data Confidentiality:

: Defined in {{RFC4949}} as "the property that data is not disclosed to system entities unless they have been authorized to know the data."

Data In Motion:

: Data that is being transported via a network; also referred to as "Data in Transit" or "Data in Flight".

: Data in motion requires a data model to transfer the data using a specific encoding. Typically, data in motion is serialized (marshalling) into a transport encoding by a provider of information and deserialized (unmarshalling) by a consumer of information. The termination points of provider of information and consumer of information data is transferred between are interfaces. In regard to data in motion, the interpretation of the roles consumer of information and provider of information depends on the corresponding OSI layer (e.g. on layer2: between interfaces connected to a broadcast domain, on layer4: between interfaces that maintain a TCP connection). In the context of SACM, consumer of information and provider of information are SACM components.

: The SACM architecture and corresponding models focus on data in motion.

: TODO do we really need this last sentence?

Data At Rest:

: Data that is stored.

: Data at rest requires a data model to encode the data to be stored. In the context of SACM, data at rest located on a SACM component can be provided to other SACM components via discoverable capabilities.

: In the context of SACM, data models for data at rest are out of scope.

: TODO do we really need this last sentence?

Data Integrity:

: Defined in {{RFC4949}} as "the property that data has not been changed, destroyed, or lost in an unauthorized or accidental manner."

Data Origin:

: The SACM Component that initially acquired or produced data about an endpoint.

Data Plane (fix statement):

: Is an architectural component providing operational functions enabling information exchange that is not command and control or management related.

: Typically used as a term in the context of routing (and used as a synonym for forwarding plane, e.g. {{RFC6192}}). In the context of SACM, the data plane is an architectural component providing operational functions to enable a SACM component to provide and consume SACM statements and therefore SACM content, which composes the actual SACM content. The data plane in a SACM domain is used to conduct distributed SACM tasks by transporting SACM content via specific transport encodings and corresponding operations defined by SACM data models.

: TODO - what is the meaning "fix statement"?

Data Provenance:

: An historical record of the sources, origins and evolution, as it pertains to data, that is influenced by inputs, entities, functions and processes.

: Additional Information - In the context of SACM, data provenance is expressed as metadata that identifies SACM statements and corresponding content elements a new statement is created from. In a downstream process, this references can cascade, creating a data provenance tree that enables SACM components to trace back the original data sources involved in the creation of SACM statements and take into account their characteristics and trustworthiness.

Data Source:

: Is an endpoint from which a particular set of attributes and/or attribute values have been collected.

Endpoint:

: Defined in {{RFC5209}} as "any computing device that can be connected to a network."

: Additional Information - The {{RFC5209}} definition continues, "Such devices normally are associated with a particular link layer address before joining the network and potentially an IP address once on the network.  This includes: laptops, desktops, servers, cell phones, or any device that may have an IP address."

: To further clarify the {{RFC5209}} definition, an endpoint is any physical or virtual device that may have a network address.  Note that, network infrastructure devices (e.g. switches, routers, firewalls), which fit the definition, are also considered to be endpoints within this document.

: Physical endpoints are always composites that are composed of hardware components and software components. Virtual endpoints are composed entirely of software components and rely on software components that provide functions equivalent to hardware components.

: The SACM architecture differentiates two essential categories of endpoints: Endpoints whose security posture is intended to be assessed (target endpoints) and endpoints that are specifically excluded from endpoint posture assessment (excluded endpoints).

: Based on the definition of an asset, an endpoint is a type of asset.

Endpoint Attribute:

: Is a discreet endpoint characteristic that is computably observable.

Endpoint Characteristics:

: The state, configuration and composition of the software components and (virtual) hardware components a target endpoint is composed of, including observable behavior, e.g. sys-calls, log-files, or PDU emission on a network.


Endpoint Characterization:

: The description of the distinctive nature of an endpoint, that is based on its characteristics.

Endpoint Characterization Task:

: The task of endpoint characterization that uses endpoint attributes that represent distinct endpoint characteristics.

Endpoint Classification:

: The categorization of of the endpoint into one or more taxonomic structures.

: Endpoint classification requires declarative guidance in the form of an endpoint profile, discovery results and potentially collection results. Types, classes or the characteristics of an individual target endpoint are defined via endpoint profiles.

Endpoint Classification Task:

: The task of endpoint classification that uses an endpoint's characteristics to determine how to categorize the given endpoint into one or more taxonomic structures.

Endpoint Label:

: A unique label associated with a unique endpoint.

: Endpoint specializations have corresponding endpoint label specializations. For example, an endpoint label used on a SACM Component is a SACM Component Label.


Endpoint Management Capabilities:

: Are enterprise IT capabilities that, collectively, manage endpoint identity, endpoint information, and associated metadata.

Evaluation Task:

: A task by which an endpoint's asserted attribute value is evaluated against a policy-compliant attribute value.

Evaluation Result:

: The resulting value from having evaluated a set of posture attributes.


Expected Endpoint Attribute State:

: The policy-compliant state of an endpoint attribute that is to be compared against.


Guidance:

: Input directing SACM processes or tasks.

: There are two types of guidance:

: Declarative Guidance: Guidance that defines the configuration or state an endpoint is supposed to be in, without providing specific actions or methods to produce that desired state. Examples include Target Endpoint Profiles or network topology based requirements.

: Imperative Guidance: Guidance that prescribes specific actions to be conducted or methods to be used in order to achieve an outcome. Examples include a targeted Collection Task or the IP-Address of a SACM Component that provides a registration function.


Endpoint Hardware Inventory:

: The set of hardware components that compose a specific endpoint representing its hardware configuration.


Information Element:

: A representation of information about physical and virtual “objects of interest”.

: Information elements are the building blocks that constitute the SACM information model. In the context of SACM, an information element that expresses a single value with a specific name is referred to as an Attribute (analogous to an attribute-value-pair). A set of attributes that is bundled into a more complex composite information element is referred to as a Subject. Every information element in the SACM information model has a unique name. Endpoint attributes or time stamps, for example, are represented as information elements in the SACM information model.

Information Model:

: An abstract representation of data, their properties, relationships between data and the operations that can be performed on the data.  

: While there is some overlap with a data model, {{RFC3444}} distinguishes an information model as being protocol and implementation neutral whereas a data model would provide such details. The purpose of the SACM information model is to ensure interoperability between SACM data models (that are used as transport encoding) and to provide a standardized set of information elements for communication between SACM components.

Interaction Model:

: The definition of specific sequences regarding the exchange of messages (data in motion), including, for example,  conditional branching, thresholds and timers. An interaction model, for example, can be used to define operations, such as registration or discovery, on the control plane. A composition of data models for data in motion and a corresponding interaction model is a protocol.

: TODO - Do we really need this definition? And, it sounds a lot like process or workflow.

Internal Collector:

: Internal Collector: a collector that runs on a target endpoint to acquire information from that target endpoint.

Management Plane:

: Is an architectural component providing common functions to steer the behavior of SACM components, e.g. their behavior on the control plane.

: Prominent examples include: modification of the configuration of a SACM component or updating a target endpoint profile that resides on an evaluator. In essence, guidance is transported via the management plane. Typically, a SACM component can fulfill its purpose without continuous input from the management plane. In contrast, without continuous availability of control plane functions a typical SACM component could not function properly. In general, interaction on the management plane is less frequent and less regular than on the control plane. Input via the management plane can be manual (e.g. via a CLI), or can be automated via management plane functions that are part of other SACM components.

Metadata:

: Data about data.

: In the SACM information model, data is referred to as Content. Metadata about the content is referred to as Content-Metadata, respectively. Content and Content-Metadata are combined into Subjects called Content-Elements in the SACM information model. Some information elements defined by the SACM information model can be part of the Content or the Content-Metadata. Therefore, if an information element is considered data or data about data depends on which kind of Subject it is associated with. The SACM information model also defines metadata about the data origin via the Subject Statement-Metadata. Typical examples of metadata are time stamps, data origin or data source.

: TODO - do we really need this term?

: Examples include: physical Ethernet port with a MAC address, layer 2 VLAN interface with a MAC address, layer 3 interface with multiple IPv6 addresses, layer 3 tunnel ingress or egress with an IPv4 address.


Posture:

: Defined in {{RFC5209}} as "configuration and/or status of hardware or software on an endpoint as it pertains to an organization's security policy."

: This term is used within the scope of SACM to represent the configuration and state information that is collected from a target endpoint in the form of endpoint attributes (e.g. software/hardware inventory, configuration settings, dynamically assigned addresses).  This information may constitute one or more posture attributes.

Posture Attributes:

: Defined in {{RFC5209}} as "attributes describing the configuration or status (posture) of a feature of the endpoint.  A Posture Attribute represents a single property of an observed state.  For example, a Posture Attribute might describe the version of the operating system installed on the system."

: Within this document this term represents a specific assertion about endpoint configuration or state (e.g. configuration setting, installed software, hardware) represented via endpoint attributes.  The phrase "features of the endpoint" highlighted above refers to installed software or software components.

: TODO - Does this definition of posture attributes jive with the generic attribute definition? Or, are these perhaps synonymous and "Attribute" should say "see posture attribute".

Provider:

: A provider is a SACM role assigned to a SACM component that provides role-specific functions to provide information to other SACM components.


Repository:

: A repository is a controller that contains functions to consume, store and provide information of a particular kind.

: Such information is typically data transported on the data plane, but potentially also data and metadata from the control and management plane.  A single repository may provide the functions of more than one specific repository type (i.e. configuration baseline repository, assessment results repository, etc.)

SACM Broker Controller:

: A SACM Broker Controller is a controller that contains control plane functions to provide and/or connect services on behalf of other SACM components via interfaces on the control plane.

: A broker may provide, for example, authorization services and find, upon request, SACM components providing requested services.

SACM Component:

: Is a component, as defined in {{-i2nsft}}, that is composed of SACM capabilities.

SACM Component Discovery:

: The task of brokering appropriate SACM components according to their capabilities or roles on request.

: TODO - is this right? The definition seems to describe a discovery service rather than an act of discovery; which do we mean?

: Input: Query

: Output: a list of SACM components including metadata

: TODO - why do we need the input/output items?

SACM Component Label:

: A specific endpoint label that is used to identify a SACM component.

: In content-metadata, this label is called data origin.

SACM Content:

: The payload provided by SACM components to the SACM domain on the data plane.

: SACM content includes the SACM data models.

SACM Domain:

: Endpoints that include a SACM component compose a SACM domain.

: (To be revised, additional definition content TBD, possible dependencies to SACM architecture)

SACM Interface:

: An interface, as defined in {{-i2nsft}}, that provides SACM-specific operations.

: {{-i2nsft}} defines interface as a "set of operations one object knows it can invoke on, and expose to, another object," and further defines interface by stating that an interface "decouples the implementation of the operation from its specification. An interface is a subset of all operations that a given object implements. The same object may have multiple types of interfaces to serve different purposes."

: In the context of SACM, SACM Functions provide SACM Interfaces on the management, control, or data plane. Operations a SACM Interface provides are based on corresponding data model defined by SACM. SACM Interfaces are used for communication between SACM components.

SACM Proxy Controller:

: A SACM Proxy Controller is a controller that provides data plane and control plane functions, information, or services on behalf of another component, which is not directly participating in the SACM architecture.

SACM Role:

: Is a role, as defined in {{-i2nsft}}, that requires the SACM Component assuming the role to bear a set of SACM functions or interfaces.

SACM Statement:

: Is SACM component output that represents an assertion.

Security Automation:

: The process of which security alerts can be automated through the use of different components to monitor, analyze and assess endpoints and network traffic for the purposes of detecting miss-configurations, miss-behaviors or threats. Security Automation is intended to identify target endpoints that cannot be trusted (see "trusted" in {{RFC4949}}. This goal is achieved by creating and processing evidence (assessment statements) that a target endpoint is not a trusted system {{RFC4949}}.

Software Package:

: A generic software package (e.g. a text editor).

Software Component:

: A software package installed on an endpoint, including a unique serial number if present (e.g. a text editor associated with a unique license key).

Software Instance:

: A running instance of the software component (e.g. on a multi-user system, one logged-in user has one instance of a text editor running and another logged-in user has another instance of the same text editor running, or on a single-user system, a user could have multiple independent instances of the same text editor running).

State:

: A volatile subset endpoint attributes of a (target) endpoint that is affected by a reboot-cycle. Local state is created by the interaction of components with other components via the control plane, via processing data plane payload, or via the functional properties of local hardware and software components. Dynamic configuration (e.g. IP address distributed dynamically via an address distribution and management services, such as DHCP) is considered state that is the result of the interaction with another component that provides configuration via the control plane (e.g. provided by a DHCP server with a specific configuration).

: Examples: The static association of an IP address and a MAC address in a DHCP server configuration, a directory-path that identifies a log-file directory, a registry entry.

Statement:

: A statement is a subject defined in the SACM information model.

: When a statement is used to provide content to a SACM domain, it is a top-level subject that bundles Content Elements into one subject and includes  metadata about the data origin.

Subject:

: A composite information element. Like Attributes, subjects have a name and are composed of attributes and/or other subjects. Every IE that is part of a subject can have a quantitiy associated with it (e.g. zero-one, none-unbounded). The content IE of a subject can be an unordered or an ordered list.

: In contrast to the definitions of subject provided by {{RFC4949}}, a subject in the scope of SACM is neither "a system entity that causes information to flow among objects or changes the system state" nor "a name of a system entity that is bound to the data items in a digital certificate".

: In the context of SACM, a subject is a semantic composite of information elements about a system entity that is a target endpoint. Every acquirable subject---as defined in the scope of SACM---about a target endpoint represents and therefore identifies every subject---as defined by {{RFC4949}}---that is a component of that target endpoint. The semantic difference between both definitions can be subtle in practice and is in consequence important to highlight.

Supplicant:

: A SACM component seeking to be authenticated via the control plane for the purpose of participating in a SACM domain.

System Resource:

: Defined in {{RFC4949}} as "data contained in an information system; or a service provided by a system; or a system capacity, such as processing power or communication bandwidth; or an item of system equipment (i.e., hardware, firmware, software, or documentation); or a facility that houses system operations and equipment.

Target Endpoint:

: A target endpoint is an "endpoint under assessment" (even if it is not actively under assessment at all times) or "endpoint of interest". Every endpoint that is not specifically designated as an excluded endpoint is a target endpoint. A target endpoint is not part of a SACM domain unless it contains a SACM component (e.g. a SACM component that publishes collection results coming from an internal collector).

: A target endpoint is similar to a device that is a Target of Evaluation (TOE) as defined in Common Criteria and as referenced by {{RFC4949}.

: In respect to {{RFC4949}} a target endpoint is an information system and therefore a composite that is a system entity composed of system components or system entities, respectively.

Target Endpoint Characterization Record:

: A set of endpoint attributes about a target endpoint that was encountered in a SACM domain, which are associated with a target endpoint by being included in the corresponding record. A characterization record is intended to be a representation of an endpoint. It cannot be assured that a record distinctly represents a single target endpoint unless a set of one or more endpoint attributes that compose a unique set of identifying endpoint attributes are included in the record. Otherwise, the set of identifying attributes included in a record can match more than one target endpoints, which are - in consequence - indistinguishable to a SACM domain until more qualifying endpoint attributes can be acquired and added to the record. A characterization record is maintained over time in order to assert that acquired endpoint attributes are either about an endpoint that was encountered before or an endpoint that has not been encountered before in a SACM domain. A characterization record can include, for example, acquired configuration, state or observed behavior of a specific target endpoint. Multiple and even conflicting instances of this information can be included in a characterization record by using timestamps and/or data origins to differentiate them. The endpoint attributes included in a characterization record can be used to re-identify a distinct target endpoint over time. Classes or profiles can be associated with a characterization record via the Classification Task in order to guide collection, evaluation or remediation tasks.

Target Endpoint Characterization Task:

: An ongoing task of continuously adding acquired endpoint attributes to a corresponding record. The TE characterization task manages the representation of encountered target endpoints in the SACM domain in the form of characterization records. For example, the output of a target endpoint discovery task or a collection task can be processed by the characterization task and added to the record. The TE characterization Task also manages these representations of target endpoints encountered in the SACM domain by splitting or merging the corresponding records as new or more refined endpoint attributes become available.

: Input: discovered target endpoint attributes, endpoint attribute collection, existing characterization records

: Output: target endpoint characterization records

Target Endpoint Classification Task:

: The task of associating a class from an extensible list of classes with an endpoint characterization record. TE classes function as imperative and declarative guidance for collection, evaluation, remediation and security posture assessment in general.

: Input: endpoint characterization records (without classification), guidance (how to classify a record)

: Output: endpoint characterization records (with classification)

Target Endpoint Discovery Task:

: The ongoing task of detecting previously unknown interaction of a potential target endpoint in the SACM domain. TE Discovery is not directly targeted at a specific target endpoint and therefore an un-targeted task. SACM Components conducting the discovery task as a part of their function are typically distributed and located, for example, on infrastructure components or collect from those remotely via appropriate interfaces. Examples of infrastructure components that are of interest to the discovery task include routers, switches, VM hosting or VM managing components, AAA servers, or servers handling dynamic address distribution.

: Input: endpoint attributes acquired via local or remote interfaces

: Output: endpoint attributes including metadata such as data source or data origin

Target Endpoint Identifier:

: The target endpoint discovery task and the collection tasks can result in a set of identifying endpoint attributes added to a corresponding Characterization Record. This subset of the endpoint attributes included in the record is used as a target endpoint identifier, by which a specific target endpoint can be referenced. Depending on the available identifying attributes, this reference can be ambiguous and is a "best-effort" mechanism. Every distinct set of identifying endpoint attributes can be associated with a target endpoint label that is unique in a SACM domain.

Target Endpoint Label:

: A specific endpoint label that refers to a target endpoint identifier used to identify a specific target endpoint (also referred to as TE label).  In content-metadata, this label is called data source.

Target Endpoint Profile:

: A bundle of expected or desired component composition, configurations and states---therefore a composition of information elements that constitute declarative guidance---associated with a target endpoint.

: The corresponding task by which the association with a target endpoint takes places is the endpoint classification task. The task by which an endpoint profile is created is the endpoint characterization task. A type or class of target endpoints can be defined via a target endpoint profile. Examples include:  printers, smartphones, or an office PC.

: In respect to {{RFC4949}}, a target endpoint profile is a protection profile as defined by Common Criteria (analogous to the target endpoint being the target of evaluation).

SACM Task:

: A SACM task is conducted by one or more SACM functions that reside on a SACM component (e.g. a collection task or endpoint characterization). A SACM task can be triggered by other operations or functions (e.g. a query from another SACM component or an unsolicited push on the data plane due to an ongoing subscription). A task is part of a SACM process chain. A task starts at a given point in time and ends in a deterministic state. With the exception of a collection task, a SACM task consumes SACM statements provided by other SACM components. The output of a task is a result that can be provided (e.g. published) on the data plane. There following tasks are defined by SACM:

: Target Endpoint Discovery
: Target Endpoint Characterization
: Target Endpoint Classification
: Collection
: Evaluation [TBD]
: Information Sharing [TBD]
: SACM Component Discovery
: SACM Component Authentication [TBD]
: SACM Component Authorization [TBD]
: SACM Component Registration [TBD]  

Timestamps :

: Defined in {{RFC4949}} as "with respect to a data object, a label or marking in which is recorded the time (time of day or other instant of elapsed time) at which the label or marking was affixed to the data object" and as "with respect to a recorded network event, a data field in which is recorded the time (time of day or other instant of elapsed time) at which the event took place.".

: This term is used in SACM to describe a recorded point in time at which, for example, an information element is created or updated on a target endpoint, and observed, transmitted or processed by a SACM component. Timestamps can be created by target endpoints or SACM components and are associated with SACM statements provided or consumed by SACM components. Outside of the domain of SACM components the assurance of correctness of time stamps is typically significantly lower than inside a SACM domain. In general, it cannot be simply assumed that the source of time a target endpoint uses is synchronized or trustworthy.

Virtual Component:

: A target endpoint can be composed entirely of logical system entities (see {{RFC4949}}. The most common example is a virtual machine/host running on a target endpoint.

: Effectively, target endpoints can be nested and at the time of this writing the most common example of target endpoint characteristics about virtual components is the EntLogicalEntry in {{RFC6933}}.

Vulnerability Assessment:  

: The process of determining whether a set of endpoints is vulnerable according to the information contained in the vulnerability description information.

Vulnerability Description Information:

: Information pertaining to the existence of a flaw or flaws in software, hardware, and/or firmware, which could potentially have an adverse impact on enterprise IT functionality and/or security.  Vulnerability description information should contain enough information to support vulnerability detection.

Vulnerability Detection Data:

: A type of imperative guidance extracted or derived from vulnerability description information that describes the specific mechanisms of vulnerability detection that is used by an enterprise's vulnerability management capabilities to determine if a vulnerability is present on an endpoint.

Vulnerability Management Capabilities:  

: An enterprise IT department's ability to manage endpoint vulnerabilities and associated metadata on an ongoing basis by ingesting vulnerability description information and vulnerability detection data, and performing vulnerability assessments.

Vulnerability assessment capabilities:

: An enterprise IT department's ability to determine whether a set of endpoints is vulnerable according to the information contained in the vulnerability description information.

Workflow:

: A workflow is a modular composition of tasks. A workflow can contain loops, conditionals, multiple starting points and multiple endpoints. The most prominant workflow in SACM is the assessment workflow.

#  IANA Considerations

This memo includes no request to IANA.

#  Security Considerations

This memo documents terminology for security automation.  While it is about security, it does not affect security.

#  Acknowledgements

#  Change Log

Changes from version 00 to version 01:

* Added simple list of terms extracted from UC draft -05.  It is expected that comments will be received on this list of terms as to whether they should be kept in this document.  Those that are kept will be appropriately defined or cited.


Changes from version 01 to version 02:

* Added Vulnerability, Vulnerability Management, xposure, Misconfiguration, and Software flaw.


Changes from version 02 to version 03:

* Removed Section 2.1.  Cleaned up some editing nits; broke terms into 2 sections (predefined and newly defined terms).  Added some of the relevant terms per the proposed list discussed in the IETF 89 meeting.



Changes from version 03 to version 04:

* TODO


Changes from version 04 to version 05:

* TODO


Changes from version 05 to version 06:

* Updated author information.

* Combined "Pre-defined Terms" with "New Terms and Definitions".

* Removed "Requirements language".

* Removed unused reference to use case draft; resulted in removal of normative references.

* Removed introductory text from Section 1 indicating that this document is intended to be temporary.

* Added placeholders for missing change log entries.


Changes from version 06 to version 07:

* Added Contributors section.

* Updated author list.

* Changed title from "Terminology for Security Assessment" to "Secure Automation and Continuous Monitoring (SACM) Terminology".

* Changed abbrev from "SACM-Terms" to "SACM Terminology".

* Added appendix The Attic to stash terms for future updates.

* Added Authentication, Authorization, Data Confidentiality, Data Integrity, Data Origin, Data Provenance, SACM Component, SACM Component Discovery, Target Endpoint Discovery.

* Major updates to Building Block, Function, SACM Role, Target Endpoint.

* Minor updates to Broker, Capability, Collection Task, Evaluation Task, Posture.

* Relabeled Role to SACM Role, Endpoint Target to Target Endpoint, Endpoint Discovery to Endpoint Identification.

* Moved Asset Targeting, Client, Endpoint Identification to The Attic.

* Endpoint Attributes added as a TODO.

* Changed the structure of the Change Log.


Changes from version 07 to version 08:

* Added Assertion, Collection Result, Collector, Excluded Endpoint, Internal Collector, Network Address, Network Interface, SACM Domain, Statement, Target Endpoint Identifier, Target Endpoint Label, Timestamp.

* Major updates to Attributes, Broker, Collection Task, Consumer, Controller, Control Plane, Endpoint Attributes, Expected Endpoint State, SACM Function, Provider, Proxy, Repository, SACM Role, Target Endpoint.

* Minor updates to Asset, Building Block, Data Origin, Data Source, Data Provenance, Endpoint, Management Plane, Posture, Posture Attribute, SACM Component, SACM Component Discovery, Target Endpoint Discovery.

* Relabeled Function to SACM Function.


Changes from version 08 to version 09:

* Updated author list.

* Added Data Plane, Endpoint Characterization, Endpoint Classification, Guidance, Interaction Model, Software Component, Software Instance, Software Package, Statement, Target Endpoint Profile, SACM Task.

* Removed Building Block.

* Major updates to Control Plane, Endpoint Attribute, Expected Endpoint State, Information Model, Management Plane.

* Minor updates to Attribute, Capabilities, SACM Function, SACM Component, Collection Task.

* Moved Asset Characterization to The Attic.


Changes from version 09 to version 10:

* Added Configuration Drift, Data in Motion, Data at Rest, Endpoint Management Capability, Hardware Component, Hardware Inventory, Hardware Type, SACM Interface, Target Endpoint Characterization Record, Target Endpoint Characterization Task, Target Endpoint Classification Task, Target Endpoint Discovery Task, Vulnerability Description Information, Vulnerability Detection Data, Vulnerability Management Capability, Vulnerability Assessment

* Added references to i2nsf definitions in Capability, SACM Component, SACM Interface, SACM Role.

* Added i2nsf Terminology I-D Reference.

* Major Updates to Endpoint, SACM Task, Target Endpoint Identifier.

* Minor Updates to Guidance, SACM Component Discovery, Target Endpoint Label, Target Endpoint Profile.

* Relabeled SACM Task

* Removed Target Endpoint Discovery

Changes from version 10 to version 11:

* Added Content Element, Content Metadata, Endpoint Label, Information Element, Metadata, SACM Component Label, Workflow.

* Major Updates to Assessment, Capability, Collector, Endpoint Management Capabilities, Guidance, Vulnerability Assessment Capabilities, Vulnerability Detection Data, Vulnerability Assessment Capabilities.

* Minor updates to Collection Result, Control Plane, Data in Motion, Data at Rest, Data Origin, Network Interface, Statement, Target Endpoint Label.

* Relabeled Endpoint Management Capability, Vulnerability Management Capability, Vulnerability Assessment.

Changes from version 11 to version 12:

* Added Configuration, Endpoint Characteristic, Event, SACM Content, State, Subject.

* Major Updates to Assertion, Data in Motion, Data Provenance, Data Source, Interaction Model.

* Minor Updates to Attribute, Control Plane, Data Origin, Data Provenance, Expected Endpoint State, Guidance, Target Endpoint Classification Task, Vulnerability Detection Data.

Changes from version 12 to version 13:

* Added Virtual Component.

* Major Updates to Capability, Collection Task, Hardware Component, Hardware Type, Security Automation, Subject, Target Endpoint, Target Endpoint Profile.

* Minor Updates to Assertion, Data Plane, Endpoint Characteristics.

Changes from version 13 to version 14:

* Handled a plethora of issues listed in GitHub.

* Pruned commonly understood terms.

* Narrowing term labels per their definitions.

* Pruning superfluous/unnecessary definitions.

# Contributors


    David Waltermire
    National Institute of Standards and Technology
    100 Bureau Drive
    Gaithersburg, MD  20877
    USA

    Email: david.waltermire@nist.gov


    Adam W. Montville
    Center for Internet Security
    31 Tech Valley Drive
    East Greenbush, NY  12061
    USA

    Email: adam.w.montville@gmail.com


    David Harrington
    Effective Software
    50 Harding Rd
    Portsmouth, NH  03801
    USA

    Email: ietfdbh@comcast.net

    Brian Ford
    Lancope
    3650 Brookside Parkway, Suite 500
    Alpharetta, GA  30022
    USA

    Email: bford@lancope.com


    Merike Kaeo
    Double Shot Security
    3518 Fremont Avenue North, Suite 363
    Seattle, WA  98103
    USA

    Email: merike@doubleshotsecurity.com

--- back

# The Attic

The following terms are stashed for now and will be updated later:

Asset Characterization:

: Asset characterization is the process of defining attributes that describe properties of an identified asset.

Asset Targeting:

: Asset targeting is the use of asset identification and categorization information to drive human-directed, automated decision making for data collection and analysis in support of endpoint posture assessment.

Client:

: An architectural component receiving services from another architectural component.

Endpoint Identification (TBD per list; was "Endpoint Discovery"):

: The process by which an endpoint can be identified.
