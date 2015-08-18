---
title: Secure Automation and Continuous Monitoring (SACM) Terminology
abbrev: SACM Terminology
docname: draft-ietf-sacm-terminology-07
date: 2015-07-06
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

normative:

informative:
  RFC3444:
  RFC4949:
  RFC5209:





--- abstract 

This memo documents terminology used in the documents produced by SACM (Security Automation and Continuous Monitoring).

--- middle


# Introduction

Our goal with this document is to improve our agreement on the terminology used in documents produced by the IETF Working Group for Security Automation and Continuous Monitoring.  Agreeing on terminology should help reach consensus on which problems we're trying to solve, and propose solutions and decide which ones to use.

# Terms and Definitions

This section describes terms that have been defined by other RFC's and defines new ones.  The predefined terms will reference the RFC and where appropriate will be annotated with the specific context by which the term is used in SACM.

Assessment:

: Defined in {{RFC5209}} as "the process of collecting posture for a set of capabilities on the endpoint (e.g., host-based firewall) such that the appropriate validators may evaluate the posture against compliance policy."

: Within SACM the use of the term is expanded to support other uses of collected posture (e.g. reporting, network enforcement, vulnerability detection, license management).  The phrase "set of capabilities on the endpoint" includes: hardware and software installed on the endpoint."

Asset:

: Defined in {{RFC4949}} as "a system resource that is (a) required to be protected by an information system's security policy, (b) intended to be protected by a countermeasure, or (c) required for a system's mission.

Asset Characterization:

: Asset characterization is the process of defining attributes that describe properties of an identified asset.

Asset Management:

: The process by which assets are provisioned, updated, maintained and deprecated.

Attribute:

: Defined in {{RFC5209}} as "data element including any requisite meta-data describing an observed, expected, or the operational status of an endpoint feature (e.g., anti-virus software is currently in use)."

Authentication: 

: Defined in {{RFC4949}} as "the process of verifying a claim that a system entity or system resource has a certain attribute value."

Authorization:

: Defined in {{RFC4949}} as "an approval that is granted to a system entity to access a system resource."

Broker:

: A broker is a SACM role that is assigned to a SACM component that contains only control plane functions that provide and/or connect services on behalf of other SACM components via interfaces on the control plane. A broker may provide, for example, authorization services and find, upon request, SACM components providing requested services.

Building Block:

: For SACM, a building block is a unit of functionality that is used to compose SACM components. It contains SACM functions and may apply to one or more use cases. The functions of a building block can have interfaces on the data plane, the control plane, or on the management plane.

Capability:

: The extent of an SACM component's ability enabled by the functions (bundled into building blocks) it is composed of.  Capabilites are propagated by a SACM component and can be discovered by or negotiated with other SACM components. For example, the capability of a SACM Provider may be to only provide endpoint management data, or only a subset of that data.

Collection Task:

: The task by which endpoint attributes and/or corresponding attribute values are collected.

Consumer:

: A consumer is a SACM role that is assigned to a SACM component that contains functions to receive information from other SACM components.

Control Plane:

: An architectural component providing common functions to all SACM components, including authentication, authorization, capability discovery or negotiation.

Controller:

: A controller is a SACM role that is assigned to a SACM component containing control plane functions that manage and facilitate information sharing or execute on security functions. There are three types of SACM controllers: Broker, Proxy, and Repository. Depending on its type, a controller can also contain functions that have interfaces on the data plane.

Data Confidentiality:

: Defined in {{RFC4949}} as "the property that data is not disclosed to system entities unless they have been authorized to know the data."

Data Integrity:

: Defined in {{RFC4949}} as "the property that data has not been changed, destroyed, or lost in an unauthorized or accidental manner."

Data Source:

: One or more properties that enable a SACM component to identify an (target) endpoint that is claimed to be the original source of received data.

Data Origin:

: One or more properties that enable a SACM component to identify the SACM component that initially acquired or produced data about a (target) endpoint (e.g. via collection from a data source).

Data Provenance:

: A historical record of the sources, origins and evolution of data that is influenced by inputs, entities, functions and processes.

Endpoint:

: Defined in {{RFC5209}} as "any computing device that can be connected to a network.  Such devices normally are associated with a particular link layer address before joining the network and potentially an IP address once on the network.  This includes: laptops, desktops, servers, cell phones, or any device that may have an IP address."

: To further clarify the {{RFC5209}} definition, an endpoint is any physical or virtual device that may have a network address.  Note that, network infrastructure devices (e.g. switches, routers, firewalls), which fit the definition, are also considered to be endpoints within this document.

: Based on the previous definition of an asset, an endpoint is a type of asset.

Endpoint Attributes:

: [TODO] (Definition of content, structure, and relationship to Posture Attributes)

Evaluation Task:

: The task by which endpoint attributes are evaluated.

Evaluation Result:

: The resulting value from having evaluated a set of posture attributes.

Expected Endpoint State:

: The required state of an endpoint that is to be compared against.

SACM Function:

: A behavioral aspect or capacity of a particular building block that is part of a SACM component, which belies that SACM component's purpose.  For example, a SACM function with interfaces on the control plane can provide a brokering function to other SACM components. Via data plane interfaces, a function can act as a provider and/or as a consumer of information. SACM functions can be propagated as the capabilities of a SACM component and can be discovered by or negotiated with other SACM components.

Information Model:

: An information model is an abstract representation of data, their properties, relationships between data and the operations that can be performed on the data.  While there is some overlap with a data model, {{RFC3444}} distinguishes an information model as being protocol and implementation neutral whereas a data model would provide such details.

Management Plane:

: An architectural component providing common functions to all SACM participants, including [TBD].

Posture:

: Defined in {{RFC5209}} as "configuration and/or status of hardware or software on an endpoint as it pertains to an organization's security policy."

: This term is used within the scope of SACM to represent the configuration and state information that is collected from an endpoint (e.g. software/hardware inventory, configuration settings, dynamically assigned addresses).  This information may constitute one to many Posture Attributes.

Posture Attributes:

: Defined in {{RFC5209}} as "attributes describing the configuration or status (posture) of a feature of the endpoint.  A Posture Attribute represents a single property of an observed state.  For example, a Posture Attribute might describe the version of the operating system installed on the system."

: Within this document this term represents a specific assertion about endpoint configuration or state (e.g. configuration setting, installed software, hardware).  The phrase "features of the endpoint" refers to installed software or software components.

Provider:

: A provider is a SACM role that is assigned to a SACM component that contains functions to provide information to other SACM components.

Proxy:

: A proxy is a SACM role that is assigned to a SACM component that provides data plane and control plane functions, information, or services on behalf of another component, which is not directly participating in the SACM architecture.

Repository:

: A repository is a SACM role that is assigned to SACM components that contain functions to store information of a particular kind.  A single repository may provide the functions of more than one repository type (i.e. configuration baseline repository, assessment results repository, etc.)

SACM Role:

: An Endpoint that contains a SACM component can take on the role(s) of provider, consumer, controller, and/or target endpoint. The role of an endpoint containing a SACM component is defined by the purpose of the functions and corresponding interfaces the SACM component is composed of. If a particular endpoint does not contain any SACM components it takes on the role of a target endpoint unless indicated otherwise.

SACM Component:

: A composition of building blocks that contain SACM functions (acting on control plane, data plane or management plane). SACM defines a set of standard components (e.g. a collector, a broker, or a data store). A SACM component contains at least a basic set of control plane building blocks and can contain data plane and management plane building blocks. A SACM component residing on an endpoint assigns one or more SACM roles to the corresponding endpoint due the SACM functions it is composed of. A SACM component "resides on" an endpoint and an endpoint "contains" a SACM component, correspondingly.

SACM Component Discovery:

: The function by which a SACM component (e.g. by role, functions, or data provided/consumed) can be discovered.

Security Automation:

: The process of which security alerts can be automated through the use of different tools to monitor, evaluate and analyze endpoint and network traffic for the purposes of detecting misconfigurations, misbehaviors or threats.

Supplicant:

: The entity seeking to be authenticated by the Management Plane for the purpose of participating in the SACM architecture.

System Resource:

: Defined in {{RFC4949}} as "data contained in an information system; or a service provided by a system; or a system capacity, such as processing power or communication bandwidth; or an item of system equipment (i.e., hardware, firmware, software, or documentation); or a facility that houses system operations and equipment.

Target Endpoint:

: A target endpoint is a specific SACM Role. An endpoint that takes on the target endpoint role either contains no SACM component or contains an internal SACM component. A target endpoint is an "endpoint under assessment" (even if it is not actively under assessment at all times). If an endpoint takes on both the role of target endpoint and _Not A Target Endpoint_ [TBD] it is not a Target Endpoint.

: A target endpoint is similar to a device that is a Target of Evaluation (TOE) as defined in Common Criteria.

Target Endpoint Discovery:

: The function by which target endpoints can be discovered. The output of target endpoint discovery typically includes identifying endpoint attributes.

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

* Relabled Role to SACM Role, Endpoint Target to Target Endpoint, Endpoint Discovery to Endpoint Identification.

* Moved Asset Targeting, Client, Endpoint Identification to The Attic.

* Endpoint Attributes added as a TODO.

* Changed the structure of the Change Log.

# Contributors

    David Waltermire
    National Institute of Standards and Technology
    100 Bureau Drive
    Gaithersburg, Maryland  20877
    USA

    Email: david.waltermire@nist.gov


    Adam W. Montville
    Center for Internet Security
    31 Tech Valley Drive
    East Greenbush, New York  12061
    USA

    Email: adam.w.montville@gmail.com


    David Harrington
    Effective Software
    50 Harding Rd
    Portsmouth, NH  03801
    USA

    Email: ietfdbh@comcast.net


    Nancy Cam-Winget
    Cisco Systems
    3550 Cisco Way
    San Jose, CA  95134
    US
    Jarrett Lu
    Oracle Corporation
    4180 Network Circle
    Santa Clara, California  95054

    Email: jarrett.lu@oracle.com

    Jarrett Lu
    Oracle Corporation
    4180 Network Circle
    Santa Clara, California  95054

    Email: jarrett.lu@oracle.com


    Brian Ford
    Lancope
    3650 Brookside Parkway, Suite 500
    Alpharetta, Georgia  30022

    Email: bford@lancope.com


    Merike Kaeo
    Double Shot Security
    3518 Fremont Avenue North, Suite 363
    Seattle, Washington  98103

    Email: merike@doubleshotsecurity.com

--- back

# The Attic

The following terms are stashed for now and will be updated later:

Asset Targeting:

: Asset targeting is the use of asset identification and categorization information to drive human-directed, automated decision making for data collection and analysis in support of endpoint posture assessment.

Client:

: An architectural component receiving services from another architectural component.

Endpoint Identification (TBD per list; was "Endpoint Discovery"):

: The process by which an endpoint can be identified.
