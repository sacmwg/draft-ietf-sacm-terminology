---
title: Terminology for Security Assessment
abbrev: SACM-Terms
docname: draft-ietf-sacm-terminology-07
date: 2015-03-28
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
  -
    ins: D. Waltermire
    name: David Waltermire
    org: NIST
    email: david.waltermire@nist.gov
    street: 100 Bureau Drive
    city: Gaithersburg
    country: USA
    code: 20877

  -
    ins: A. Montville
    name: Adam W. Montville
    org: CIS
    email: adam.w.montville@gmail.com
    street: 31 Tech Valley Drive
    city: East greenbush
    code: 12061
    country: USA

  -
    ins: D. Harrington
    name: David Harrington
    org: Effective Software
    email: ietfdbh@comcast.net
    street: 50 Harding Rd.
    city: Portsmouth
    code: 03801
    country: USA

  -
    ins: N. Cam-Winget
    name: Nancy Cam-Winget
    org: Cisco Systems
    email: ncamwing@cisco.com
    street: 3550 Cisco Way
    city: San Jose
    code: 965134
    country: USA

  -
    ins: J. Lu
    name: Jarrett Lu
    org: Oracle Corporation
    email: jarrett.lu@oracle.com
    street: 4180 Network Circle
    city: Santa Clara
    code: 95054

  -
    ins: B. Ford
    name: Brian Ford
    org: Lancope
    email: bford@lancope.com
    street: 
    - 3650 Brookside Parkway
    - Suite 500
    city: Alpharetta
    code: 30022
    country: USA

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

: Within this document the use of the term is expanded to support other uses of collected posture (e.g. reporting, network enforcement, vulnerability detection, license management).  The phrase "set of capabilities on the endpoint" includes: hardware and software installed on the endpoint."

Asset:

: Defined in {{RFC4949}} as "a system resource that is (a) required to be protected by an information system's security policy, (b) intended to be protected by a countermeasure, or (c) required for a system's mission.

Asset characterization:

: Asset characterization is the process of defining attributes that describe properties of an identified asset.

Asset Management:

: The process by which assets are provisioned, updated, maintained and deprecated.

Asset Targeting:

: Asset targeting is the use of asset identification and categorization information to drive human-directed, automated decision making for data collection and analysis in support of endpoint posture assessment.

Attribute:

: Defined in {{RFC5209}} as "data element including any requisite meta-data describing an observed, expected, or the operational status of an endpoint feature (e.g., anti-virus software is currently in use)."

Broker:

: An entity providing and/or connecting services on the behalf of other architectural components.  Within the SACM Architecture, for example, a broker may provide authorization services and find, upon request, entities providing requested services.

Building Block:

: For SACM, a building block is a unit of functionality that may apply to more than one use case and can be supported by different components of an architectural model.

Capability:

: The extent of an architectural component's ability.  For example, a Posture Information Provider may only provide endpoint management data, and then only a subset of that data.

Client:

: An architectural component receiving services from another architectural component.

Collection Task:

: The process by which posture attributes or values are collected.

Consumer:

: An architectural component receiving information from another architectrual component.

Endpoint:

: Defined in {{RFC5209}} as "any computing device that can be connected to a network.  Such devices normally are associated with a particular link layer address before joining the network and potentially an IP address once on the network.  This includes: laptops, desktops, servers, cell phones, or any device that may have an IP address."

: To further clarify the {{RFC5209}} definition, an endpoint is any physical or virtual device that may have a network address.  Note that, network infrastructure devices (e.g. switches, routers, firewalls), which fit the definition, are also considered to be endpoints within this document.

: Based on the previous definition of an asset, an endpoint is a type of asset.

Evaluation Task:

: The process by which posture attributes are evaluated.

Endpoint Target:

: The endpoint of interest.

Endpoint Discovery:

: The process by which an endpoint can be identified.

Evaluation Result:

: The resulting value from having evaluated a set of posture attributes.

Expected Endpoint State:

: The required state of an endpoint that is to be compared against.

Function:

: A behavioral aspect of a particular architectural component, which belies that component's purpose.  For example, the Management Plane can provide a brokering function to other SACM architectrual components.

Information Model:

: An information model is an abstract representation of data, their properties, relationships between data and the operations that can be performed on the data.  While there is some overlap with a data model, {{RFC3444}} distinguished an information model as being protocol and implementation neutral whereas a data model would provide such details.

Management Plane (TBD per list; was "Control Plane"):

: Architectural component providing common functions to all SACM participants, including authentication, authorization, capabilities mappings, and the like.

Posture:

: Defined in {{RFC5209}} as "configuration and/or status of hardware or software on an endpoint as it pertains to an organization's security policy."

: This term is used within the scope of this document to represent the state information that is collected from an endpoint (e.g. software/hardware inventory, configuration settings).  The state information may constitute one to many Posture Attributes.

Posture Attributes:

: Defined in {{RFC5209}} as "attributes describing the configuration or status (posture) of a feature of the endpoint.  A Posture Attribute represents a single property of an observed state.  For example, a Posture Attribute might describe the version of the operating system installed on the system."

: Within this document this term represents a specific assertion about endpoint state (e.g. configuration setting, installed software, hardware).  The phrase "features of the endpoint" refers to installed software or software components.

Provider:

: An architectural component providing information to another architectrual component.

Proxy:

: An architectural component providing functions, information, or services on behalf of another component, which is not directly participating in the architecture.

Repository:

: An architectural component intended to store information of a particular kind.  A single repository may provide the functions of more than one repository type (i.e. configuration baseline repository, assessment results repository, etc.)

Role:

: A label representing a collection of functions provided by a particular architectural component.

Security Automation:

: The process of which security alerts can be automated through the use of different tools to monitor, evaluate and analyze endpoint and network traffic for the purposes of detecting misconfigurations, misbehaviors or threats.

Supplicant:

: The entity seeking to be authenticated by the Management Plane for the purpose of participating in the SACM architecture.

System Resource:

: Defined in {{RFC4949}} as "data contained in an information system; or a service provided by a system; or a system capacity, such as processing power or communication bandwidth; or an item of system equipment (i.e., hardware, firmware, software, or documentation); or a facility that houses system operations and equipment.



#  IANA Considerations

This memo includes no request to IANA.

#  Security Considerations

This memo documents terminology for security automation.  While it is about security, it does not affect security.

#  Acknowledgements

#  Change Log

##  ietf-sacm-terminology-01- to -02-

Added simple list of terms extracted from UC draft -05.  It is expected that comments will be received on this list of terms as to whether they should be kept in this document.  Those that are kept will be appropriately defined or cited.

##  ietf-sacm-terminology-01- to -02-

Added Vulnerability, Vulnerability Management, xposure, Misconfiguration, and Software flaw.

##  ietf-sacm-terminology-02- to -03-

Removed Section 2.1.  Cleaned up some editing nits; broke terms into 2 sections (predefined and newly defined terms).  Added some of the relevant terms per the proposed list discussed in the IETF 89 meeting.

##  ietf-sacm-terminology-03 to -04-

TODO

##  ietf-sacm-terminology-04 to -05-

TODO

##  ietf-sacm-terminology-05 to -06-

Updated author information.

Combined "Pre-defined Terms" with "New Terms and Definitions".

Removed "Requirements language".

Removed unused reference to use case draft; resulted in removal of normative references.

Removed introductory text from Section 1 indicating that this document is intended to be temporary.

Added placeholders for missing change log entries.





































