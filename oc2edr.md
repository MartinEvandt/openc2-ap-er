
![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v3.0.png)

-------

# OpenC2 Actuator Profile for Endpoint Response Version 1.0

## Committee Specification Draft 01

## 02 December 2020

&nbsp;

<!-- URI list start (commented out except during publication by OASIS TC Admin)

#### This version:
https://docs.oasis-open.org/openc2/ap-er/v1.0/csd01/ap-er-v1.0-csd01.md (Authoritative) \
https://docs.oasis-open.org/openc2/ap-er/v1.0/csd01/ap-er-v1.0-csd01.html \
https://docs.oasis-open.org/openc2/ap-er/v1.0/csd01/ap-er-v1.0-csd01.pdf

#### Previous version:
N/A

#### Latest version:
https://docs.oasis-open.org/openc2/ap-er/v1.0/ap-er-v1.0.md (Authoritative) \
https://docs.oasis-open.org/openc2/ap-er/v1.0/ap-er-v1.0.html \
https://docs.oasis-open.org/openc2/ap-er/v1.0/ap-er-v1.0.pdf

URI list end (commented out except during publication by OASIS TC Admin) -->

#### Technical Committee:
[OASIS Open Command and Control (OpenC2) TC](https://www.oasis-open.org/committees/openc2/)

#### Chairs:
Duncan Sparrell (duncan@sfractal.com), [sFractal Consulting LLC](http://www.sfractal.com/) \
Michael Rosa (mjrosa@cyber.nsa.gov), [National Security Agency](https://www.nsa.gov/)

#### Editors:
Vasileios Mavroeidis (vasileim@ifi.uio.no), [University of Oslo](https://www.uio.no/english/) \
Martin Evandt (martifev@ifi.uio.no), [University of Oslo](https://www.uio.no/english/)

#### Related work:
This specification is related to:
* _Open Command and Control (OpenC2) Language Specification Version 1.0_. Edited by Jason Romano and Duncan Sparrell. Latest stage: https://docs.oasis-open.org/openc2/oc2ls/v1.0/oc2ls-v1.0.html.

#### Abstract:
An 'Endpoint Detection and Response' (EDR) system is a security mechanism which identifies malicious behaviors by recording system activities and comparing them to sets of signatures or heuristics. EDR systems facilitate in digital forensics and incident response by storing and indexing said events, and provide functionality to respond to security incidents as they pertain to actively exploited, infected or vulnerable endpoints.

This actuator profile defines the OpenC2 Actions, Targets, Arguments, and Specifiers along with conformance clauses to enable the operation of OpenC2 Producers and Consumers in the context of the response functionalities found in EDR technologies. It covers the ability to respond to incidents by facilitating the containment of devices and files, stopping and restarting devices, denying devices from communicating with or storing files, IPv4-, IPv6- and domain name addresses using atomic indicators, the manipulation of files, registry entries, services and user accounts, and the initialization of anti-malware scans.

Open Command and Control (OpenC2) is an effort to rigorously standardize command and control of vital cyber defense systems. OpenC2 is a concise and extensible language to enable the command and control of cyber defense components, subsystems and/or systems in a manner that is agnostic of the underlying products, technologies, transport mechanisms or other aspects of the implementation.

#### Status:
This document was last revised or approved by the OASIS Open Command and Control (OpenC2) TC on the above date. The level of approval is also listed above. Check the "Latest stage" location noted above for possible later revisions of this document. Any other numbered Versions and other technical work produced by the Technical Committee (TC) are listed at https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=openc2#technical.

TC members should send comments on this specification to the TC's email list. Others should send comments to the TC's public comment list, after subscribing to it by following the instructions at the "[Send A Comment](https://www.oasis-open.org/committees/comments/index.php?wg_abbrev=)" button on the TC's web page at https://www.oasis-open.org/committees/openc2/.

This specification is provided under the [Non-Assertion](https://www.oasis-open.org/policies-guidelines/ipr/#Non-Assertion-Mode) Mode of the OASIS IPR Policy, the mode chosen when the Technical Committee was established. For information on whether any patents have been disclosed that may be essential to implementing this specification, and any offers of patent licensing terms, please refer to the Intellectual Property Rights section of the TC's web page (https://www.oasis-open.org/committees/openc2/ipr.php).

Note that any machine-readable content ([Computer Language Definitions](https://www.oasis-open.org/policies-guidelines/tc-process-2017-05-26/#wpComponentsCompLang)) declared Normative for this Work Product is provided in separate plain text files. In the event of a discrepancy between any such plain text file and display content in the Work Product's prose narrative document(s), the content in the separate plain text file prevails.

#### Key words:
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [[RFC2119](#rfc2119)] and [[RFC8174](#rfc8174)] when, and only when, they appear in all capitals, as shown here.

#### Citation format:
When referencing this specification the following citation format should be used:

**[AP-ER-v1.0]**

_OpenC2 Actuator Profile for Endpoint Response Version 1.0_. Edited by Vasileios Mavroeidis and Martin Evandt. 02 December 2020. OASIS Committee Specification Draft 01. https://docs.oasis-open.org/openc2/ap-er/v1.0/csd01/ap-er-v1.0-csd01.html. Latest stage: https://docs.oasis-open.org/openc2/ap-er/v1.0/ap-er-v1.0.html.

#### Notices
Copyright © OASIS Open 2022. All Rights Reserved.

Distributed under the terms of the OASIS [IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr/).

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the owner and developer of this specification, and should be used only to refer to the organization and its official outputs.

For complete copyright information please see the full Notices section in an Appendix below.

-------

# Table of Contents
- [1 Introduction](#1-introduction)
  - [1.1 Changes from earlier versions](#11-changes-from-earlier-versions)
  - [1.2 Glossary](#12-glossary)
    - [1.2.1 Definitions of terms](#121-definitions-of-terms)
    - [1.2.2 Acronyms and abbreviations](#122-acronyms-and-abbreviations)
    - [1.2.3 Document Conventions](#123-document-conventions)
      - [1.2.3.1 Naming Conventions](#1231-naming-conventions)
      - [1.2.3.2 Font Colors and Style](#1232-font-colors-and-style)
- [2 OpenC2 Language Binding for Endpoint Response](#2-openc2-language-binding-for-endpoint-response)
  - [2.1 OpenC2 Command Components](#21-openc2-command-components)
    - [2.1.1 Actions](#211-actions)
    - [2.1.2 Targets](#212-targets)
      - [2.1.2.1 Common Targets](#2121-common-targets)
      - [2.1.2.2 ER Targets](#2122-er-targets)
    - [2.1.3 Type Definitions](#213-type-definitions)
      - [2.1.3.1 Target Types](#2131-target-types)
    - [2.1.4 Command Arguments](#214-command-arguments)
    - [2.1.5 Actuator Specifiers](#215-actuator-specifiers)
  - [2.2 OpenC2 Response Components](#22-openc2-response-components)
    - [2.2.1 Response Status Codes](#221-response-status-codes)
  - [2.3 OpenC2 Commands](#23-openc2-commands)
    - [2.3.1 Scan](#231-scan)
      - [2.3.1.1 Scan device](#2311-scan-device)
    - [2.3.2 Query](#232-query)
      - [2.3.2.1 Query features](#2321-query-features)
    - [2.3.3 Deny](#233-deny)
      - [2.3.2.1 Deny domain_name](#2321-deny-domain_name)
      - [2.3.2.2 Deny file](#2322-deny-file)
      - [2.3.2.3 Deny ipv4_net](#2323-deny-ipv4_net)
      - [2.3.2.4 Deny ipv6_net](#2324-deny-ipv6_net)
    - [2.3.4 Contain](#234-contain)
      - [2.3.4.1 Contain device](#2341-contain-device)
      - [2.3.4.2 Contain file](#2342-contain-file)
    - [2.3.5 Allow](#235-allow)
      - [2.3.5.1 Allow domain_name](#2351-allow-domain_name)
      - [2.3.5.2 Allow device](#2352-allow-device)
      - [2.3.5.3 Allow file](#2353-allow-file)
      - [2.3.5.4 Allow ipv4_net](#2354-allow-ipv4_net)
      - [2.3.5.5 Allow ipv6_net](#2355-allow-ipv6_net)
    - [2.3.6 Start](#236-start)
      - [2.3.6.1 Start file](#2361-start-file)
    - [2.3.7 Stop](#237-stop)
      - [2.3.7.1 Stop device](#2371-stop-device)
      - [2.3.7.2 Stop process](#2372-stop-process)
      - [2.3.7.3 Stop er:service](#2373-stop-erservice)
    - [2.3.8 Restart](#238-restart)
      - [2.3.8.1 Restart device](#2381-restart-device)
    - [2.3.9 Set](#239-set)
      - [2.3.9.1 Set ipv4_net](#2391-set-ipv4_net)
      - [2.3.9.2 Set ipv6_net](#2392-set-ipv6_net)
      - [2.3.9.3 Set er:registry_entry](#2393-set-erregistry_entry)
      - [2.3.9.4 Set er:account](#2394-set-eraccount)
    - [2.3.10 Update](#2310-update)
      - [2.3.10.1 Update file](#23101-update-file)
    - [2.3.11 Create](#2311-create)
      - [2.3.11.1 Create er:registry_entry](#23111-create-erregistry_entry)
    - [2.3.12 Delete](#2312-delete)
      - [2.3.12.1 Delete file](#23121-delete-file)
      - [2.3.12.2 Delete er:registry_entry](#23122-delete-erregistry_entry)
      - [2.3.12.3 Delete er:service](#23123-delete-erservice)
- [3 Conformance](#3-conformance)
  - [3.1 Clauses Pertaining to the OpenC2 Producer Conformance Target](#31-clauses-pertaining-to-the-openc2-producer-conformance-target)
    - [3.1.1 Conformance Clause 1: Baseline OpenC2 Producer](#311-conformance-clause-1-baseline-openc2-producer)
    - [3.1.2 Conformance Clause 2: Downstream Device Producer](#312-conformance-clause-2-downstream-device-producer)
    - [3.1.3 Conformance Clause 3: Domain Name Producer](#313-conformance-clause-3-domain-name-producer)
    - [3.1.4 Conformance Clause 4: Scan Device Producer](#314-conformance-clause-4-scan-device-producer)
    - [3.1.5 Conformance Clause 5: Scan Depth Producer](#315-conformance-clause-5-scan-depth-producer)
    - [3.1.6 Conformance Clause 6: Periodic Scan Producer](#316-conformance-clause-6-periodic-scan-producer)
    - [3.1.7 Conformance Clause 7: Contain Device Producer](#317-conformance-clause-7-contain-device-producer)
    - [3.1.8 Conformance Clause 8: Permitted Addresses Producer](#318-conformance-clause-8-permitted-addresses-producer)
    - [3.1.9 Conformance Clause 9: Allow Device Producer](#319-conformance-clause-9-allow-device-producer)
    - [3.1.10 Conformance Clause 10: Stop Device Producer](#3110-conformance-clause-10-stop-device-producer)
    - [3.1.11 Conformance Clause 11: Restart Device Producer](#3111-conformance-clause-11-restart-device-producer)
    - [3.1.12 Conformance Clause 12: Deny File Producer](#3112-conformance-clause-12-deny-file-producer)
    - [3.1.13 Conformance Clause 13: Contain File Producer](#3113-conformance-clause-13-contain-file-producer)
    - [3.1.14 Conformance Clause 14: Allow File Producer](#3114-conformance-clause-14-allow-file-producer)
    - [3.1.15 Conformance Clause 15: Start File Producer](#3115-conformance-clause-15-start-file-producer)
    - [3.1.16 Conformance Clause 16: Deny IPv4 Net Producer](#3116-conformance-clause-16-deny-ipv4-net-producer)
    - [3.1.17 Conformance Clause 17: Allow IPv4 Net Producer](#3117-conformance-clause-17-allow-ipv4-net-producer)
    - [3.1.18 Conformance Clause 18: Set IPv4 Net Producer](#3118-conformance-clause-18-set-ipv4-net-producer)
    - [3.1.19 Conformance Clause 19: Deny IPv6 Net Producer](#3119-conformance-clause-19-deny-ipv6-net-producer)
    - [3.1.20 Conformance Clause 20: Allow IPv6 Net Producer](#3120-conformance-clause-20-allow-ipv6-net-producer)
    - [3.1.21 Conformance Clause 21: Set IPv6 Net Producer](#3121-conformance-clause-21-set-ipv6-net-producer)
    - [3.1.22 Conformance Clause 22: Stop Process Producer](#3122-conformance-clause-22-stop-process-producer)
    - [3.1.23 Conformance Clause 23: Set Registry Entry Producer](#3123-conformance-clause-23-set-registry-entry-producer)
    - [3.1.24 Conformance Clause 24: Create Registry Entry Producer](#3124-conformance-clause-24-create-registry-entry-producer)
    - [3.1.25 Conformance Clause 25: Delete Registry Entry Producer](#3125-conformance-clause-25-delete-registry-entry-producer)
    - [3.1.26 Conformance Clause 26: Set Account Producer](#3126-conformance-clause-26-set-account-producer)
    - [3.1.27 Conformance Clause 27: Account Status Producers](#3127-conformance-clause-27-account-status-producers)
    - [3.1.28 Conformance Clause 28: Stop Service Producer](#3128-conformance-clause-28-stop-service-producer)
    - [3.1.29 Conformance Clause 29: Delete Service Producer](#3129-conformance-clause-29-delete-service-producer)
  - [3.2 Clauses Pertaining to the OpenC2 Consumer Conformance Target](#32-clauses-pertaining-to-the-openc2-consumer-conformance-target)
    - [3.2.1 Conformance Clause 30: Baseline OpenC2 Consumer](#321-conformance-clause-30-baseline-openc2-consumer)
    - [3.2.2 Conformance Clause 31: Downstream Device Consumer](#322-conformance-clause-31-downstream-device-consumer)
    - [3.2.3 Conformance Clause 32: Domain Name Consumer](#323-conformance-clause-32-domain-name-consumer)
    - [3.2.4 Conformance Clause 33: Scan Device Consumer](#324-conformance-clause-33-scan-device-consumer)
    - [3.2.5 Conformance Clause 34: Scan Depth Consumer](#325-conformance-clause-34-scan-depth-consumer)
    - [3.2.6 Conformance Clause 35: Periodic Scan Consumer](#326-conformance-clause-35-periodic-scan-consumer)
    - [3.2.7 Conformance Clause 36: Contain Device Consumer](#327-conformance-clause-36-contain-device-consumer)
    - [3.2.8 Conformance Clause 37: Permitted Addresses Consumer](#328-conformance-clause-37-permitted-addresses-consumer)
    - [3.2.9 Conformance Clause 38: Allow Device Consumer](#329-conformance-clause-38-allow-device-consumer)
    - [3.2.10 Conformance Clause 39: Stop Device Consumer](#3210-conformance-clause-39-stop-device-consumer)
    - [3.2.11 Conformance Clause 40: Restart Device Consumer](#3211-conformance-clause-40-restart-device-consumer)
    - [3.2.12 Conformance Clause 41: Deny File Consumer](#3212-conformance-clause-41-deny-file-consumer)
    - [3.2.13 Conformance Clause 42: Contain File Consumer](#3213-conformance-clause-42-contain-file-consumer)
    - [3.2.14 Conformance Clause 43: Allow File Consumer](#3214-conformance-clause-43-allow-file-consumer)
    - [3.2.15 Conformance Clause 44: Start File Consumer](#3215-conformance-clause-44-start-file-consumer)
    - [3.2.16 Conformance Clause 45: Deny IPv4 Net Consumer](#3216-conformance-clause-45-deny-ipv4-net-consumer)
    - [3.2.17 Conformance Clause 46: Allow IPv4 Net Consumer](#3217-conformance-clause-46-allow-ipv4-net-consumer)
    - [3.2.18 Conformance Clause 47: Set IPv4 Net Consumer](#3218-conformance-clause-47-set-ipv4-net-consumer)
    - [3.2.19 Conformance Clause 48: Deny IPv6 Net Consumer](#3219-conformance-clause-48-deny-ipv6-net-consumer)
    - [3.2.20 Conformance Clause 49: Allow IPv6 Net Consumer](#3220-conformance-clause-49-allow-ipv6-net-consumer)
    - [3.2.21 Conformance Clause 50: Set IPv6 Net Consumer](#3221-conformance-clause-50-set-ipv6-net-consumer)
    - [3.2.22 Conformance Clause 51: Stop Process Consumer](#3222-conformance-clause-51-stop-process-consumer)
    - [3.2.23 Conformance Clause 52: Set Registry Entry Consumer](#3223-conformance-clause-52-set-registry-entry-consumer)
    - [3.2.24 Conformance Clause 53: Create Registry Entry Consumer](#3224-conformance-clause-53-create-registry-entry-consumer)
    - [3.2.25 Conformance Clause 54: Delete Registry Entry Consumer](#3225-conformance-clause-54-delete-registry-entry-consumer)
    - [3.2.26 Conformance Clause 55: Set Account Consumer](#3226-conformance-clause-55-set-account-consumer)
    - [3.2.27 Conformance Clause 56: Account Status Consumers](#3227-conformance-clause-56-account-status-consumers)
    - [3.2.28 Conformance Clause 57: Stop Service Consumer](#3228-conformance-clause-57-stop-service-consumer)
    - [3.2.29 Conformance Clause 58: Delete Service Consumer](#3229-conformance-clause-58-delete-service-consumer)
- [Appendix A. References](#appendix-a-references)
  - [A.1 Normative References](#a1-normative-references)
  - [A.2 Informative References](#a2-informative-references)
- [Appendix B. Acknowledgments](#appendix-b-acknowledgments)
  - [B.1 Participants](#b1-participants)
- [Appendix C. Revision History](#appendix-c-revision-history)
- [Appendix D: Sample Commands](#appendix-d-sample-commands)
  - [A.1 deny, contain and allow](#a1-deny-contain-and-allow)
    - [A.1.1 Ban a binary by hash on every endpoint](#a11-ban-a-binary-by-hash-on-every-endpoint)
    - [A.1.2 Network isolate a specific endpoint](#a12-network-isolate-a-specific-endpoint)
    - [A.1.X Network isolate an endpoint, but allow communication with selected IP and domain name addresses](#a1x-network-isolate-an-endpoint-but-allow-communication-with-selected-ip-and-domain-name-addresses)
    - [A.1.3 Allow unrestricted app execution on a group of endpoints](#a13-allow-unrestricted-app-execution-on-a-group-of-endpoints)
  - [A.2 Set](#a2-set)
    - [A.2.1 Set an account on a specific endpoint to be enabled](#a21-set-an-account-on-a-specific-endpoint-to-be-enabled)
    - [A.2.1 Set accounts on a group of endpoints to be disabled](#a21-set-accounts-on-a-group-of-endpoints-to-be-disabled)
- [Appendix D. Notices](#appendix-d-notices)

-------

# 1 Introduction

_The content in this section is non-normative, except where it is marked normative._

**Note:** This Actuator profile is consistent with Version 1.0 of the OpenC2 Language Specification [\[OpenC2-Lang-v1.0\]](#openc2-lang-v1.0).

OpenC2 is a suite of specifications that enables command and control of cyber defense systems and components. OpenC2 typically uses a request-response paradigm where a Command is encoded by a Producer (managing application) and transferred to a Consumer (managed device or virtualized function) using a secure transfer protocol, and the Consumer acts on the request and responds with status and any other requested information.

This Actuator profile specifies the set of Actions, Targets, Specifiers, and Command Arguments that integrates the response functionalities of EDR systems with the Open Command and Control (OpenC2) Command set. Through this Command set, cyber security orchestrators may gain visibility into and provide control over the ER functionality in a manner that is independent of the instance of the EDR solution.

All components, devices and systems that provide ER functionality MUST implement the OpenC2 Actions, Targets, Specifiers and Arguments identified as required in this document.

Though cyber defense components, devices, systems and/or instances may implement multiple Actuator profiles, a particular OpenC2 Message may reference at most a single Actuator profile. The scope of this document is limited to ER.

The purpose of this document is to:

* Identify the required and optional OpenC2 Actions for Actuators with ER functionality
* Identify the required and optional Target types for each Action in the ER class of Actuators
* Identify Actuator-Specifiers and Arguments for each Action/Target pair that are applicable and/or unique to the ER class of Actuators
* Annotate each Action/Target pair with a justification and example, and provide sample OpenC2 Commands to a ER with corresponding Responses

This ER profile:

* Does not define or implement Actions beyond those defined in Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10)
* Is consistent with Version 1.0 of the OpenC2 Language Specification

Cyber defense systems that are utilizing OpenC2 may require the following components to implement the ER profile:

* OpenC2 Producers: Devices that send Commands, receive Responses, and manage the execution of Commands involving one or more ER or other Actuators with ER capability. The OpenC2 Producer needs _a prior_ knowledge of which Commands the Actuator can process and execute, therefore must understand the profiles for any device that it intends to command
* OpenC2 Consumers: Devices or instances that provide endpoint detection and response functions. Typically these are Actuators that execute the cyber defense function, but could be orchestrators (i.e., a device or instance that forwards Commands to the Actuator)

## 1.1 Changes from earlier versions
This is the initial version of this specifciation.

## 1.2 Glossary

### 1.2.1 Definitions of terms
_This section is normative._

- **Action**: The task or activity to be performed (e.g., 'deny').

- **Actuator**: The function performed by the Consumer that executes the Command (e.g., 'Endpoint Response').

- **Argument**: A property of a Command that provides additional information on how to perform the Command, such as date/time, periodicity, duration, etc.

- **Command**: A Message defined by an Action-Target pair that is sent from a Producer and received by a Consumer.

- **Consumer**: A managed device / application that receives Commands. Note that a single device / application can have both Consumer and Producer capabilities.

- **Message**: A content- and transport-independent set of elements conveyed between Consumers and Producers.

- **Producer**: A manager application that sends Commands.

- **Response**: A Message from a Consumer to a Producer acknowledging a Command or returning the requested resources or status to a previously received Command.

- **Specifier**: A property or field that identifies a Target or Actuator to some level of precision.

- **Target**: The object of the Action, i.e., the Action is performed on the Target (e.g., device).

- **Agent**: A utility or suite of utilities with the capability to carry out EDR response functionalities on devices where the Agent is present and operational.

- **Endpoint**: A computing device capable of executing code and communicating with networks (e.g., desktop or laptop computers, servers, mobile devices). Use of this term within this Actuator Profile implies that the Endpoint has an Agent present and operational on it.

### 1.2.2 Acronyms and abbreviations
_This section is non-normative_

| Term | Expansion                       |
|:---  |:---                             |
| EDR  | Endpoint Detection and Response |
| ER   | Endpoint Response               |
| RFC  | Request For Comment             |


### 1.2.3 Document Conventions
#### 1.2.3.1 Naming Conventions
- [[RFC2119]](#rfc2119)/[[RFC8174]](#rfc8174) key words are in all uppercase.

- All property names and literals are in lowercase, except when referencing canonical names defined in another standard (e.g., literal values from an IANA registry).

- Words in property names are separated with an underscore (_), while words in string enumerations and type names are separated with a hyphen (-).

- The term "hyphen" used here refers to the ASCII hyphen or minus character, which in Unicode is "hyphen-minus", U+002D.

#### 1.2.3.2 Font Colors and Style
The following color, font and font style conventions are used in this document:

* A fixed width font is used for all type names, property names, and literals.
* Property names are in bold style – **'created_at'**.
* All examples in this document are expressed in JSON. They are in fixed width font, with straight quotes, black text and a light shaded background, and 4-space indentation. JSON examples in this document are representations of JSON Objects. They should not be interpreted as string literals. The ordering of object keys is insignificant. Whitespace before or after JSON structural characters in the examples are insignificant [[RFC8259]](#rfc8259).
* Parts of the example may be omitted for conciseness and clarity. These omitted parts are denoted with ellipses (...).

Example:

```json
{
    "action": "deny",
    "target": {
        "file": {
            "hashes": {
                "sha256": "22fe72a34f006ea67d26bb7004e2b6941b5c3953d43ae7ec24d41b1a928a6973"
            }
        }
    }
}
```

-------

# 2 OpenC2 Language Binding for Endpoint Response

_This section is normative_

This section defines the set of Actions, Targets, Specifiers, and Arguments that are meaningful in the context of Endpoint Response (ER). This section also describes the appropriate format for the status and properties of a Response frame. This section is organized into three major subsections; Command Components, Response Components and Commands.

Extensions to the Language Specification are defined in accordance with [[OpenC2-Lang-v1.0]](#openc2-lang-v10), Section 3.1.5, where:

1. The unique name of the ER schema is `oasis-open.org/openc2/v1.0/ap-er`
2. The namespace identifier (nsid) referring to the ER schema is:  `er`
3. The definitions and conformance requirements for these types are contained in this document

## 2.1 OpenC2 Command Components
The components of an OpenC2 Command include Actions, Targets, Actuators and associated Arguments and Specifiers. Appropriate aggregation of the components will define a Command-body that is meaningful in the context of an ER.

This specification identifies the applicable components of an OpenC2 Command. The components of an OpenC2 Command include:

* Action:  A subset of the Actions defined in the OpenC2 Language Specification that are meaningful in the context of an ER.
    * This profile SHALL NOT define Actions that are external to Version 1.0 of the [OpenC2 Language Specification](#openc2-lang-v10)
    * This profile MAY augment the definition of the Actions in the context of an ER
    * This profile SHALL NOT define Actions in a manner that is inconsistent with version 1.0 of the OpenC2 Language Specification
* Target:  A subset of the Targets and Target-Specifiers defined in Version 1.0 of the OpenC2 Language Specification that are meaningful in the context of ER and three Targets (and their associated Specifiers) that are defined in this specification
* Arguments:  A subset of the Arguments defined in the Language Specification and a set of Arguments defined in this specification
* Actuator:  A set of specifiers defined in this specification that are meaningful in the context of ER

### 2.1.1 Actions
Table 2.1.1-1 presents the OpenC2 Actions defined in Version 1.0 of the Language Specification which are meaningful in the context of an ER Actuator. The combinations of Action/Target pairs that are valid for Endpoint Response purposes are presented in [Section 2.3](#23-openc2-commands).

**Table 2.1.1-1. Actions Applicable to ER**

**Type: Action (Enumerated)**

| ID | Item        | Description                                                                                                                               |
|----|-------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | **scan**    | Initiate a scan for binaries classified as malicious.                                                                                     |
| 3  | **query**   | Query the ER actuator for a list of available features.                                                                                   |
| 6  | **deny**    | Deny a process or service from being executed on the Endpoint.                                                                            |
| 7  | **contain** | Isolate a device from communicating with other devices on a network, quarantine a file.                                                   |
| 8  | **allow**   | Un-isolate a previously isolated device.                                                                                                  |
| 9  | **start**   | Initiate a process, application, system, or activity.                                                                                     |
| 10 | **stop**    | Halt a system or end an activity.                                                                                                         |
| 11 | **restart** | Restart a device, system, or process.                                                                                                     |
| 15 | **set**     | Change a value, configuration, or state of a managed entity (e.g., registry value, account).                                              |
| 16 | **update**  | Instructs the Actuator to retrieve, install, process, and operate in accordance with a software update, reconfiguration, or other update. |
| 19 | **create**  | Add a new entity of a known type (e.g., registry entry, file).                                                                            |
| 20 | **delete**  | Remove an entity (e.g., registry entry, file).                                                                                            |


### 2.1.2 Targets
Table 2.1.2-1 summarizes the Targets defined in Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10) as they relate to ER functionality. Table 2.1.2-2 summarizes the Targets that are defined in this specification.

#### 2.1.2.1 Common Targets
Table 2.1.2-1 lists the Targets defined in the OpenC2 Language Specification that are applicable to ER . The particular Action/Target pairs that are required or are optional are presented in [Section 2.3](#23-openc2-commands).

**Table 2.1.2-1. Language Specification Targets Applicable to ER**

**Type: Target (Choice)**

| ID   | Name            | Type           | \# | Description                                                                                                                                                                                  |
|------|-----------------|----------------|----|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 3    | **device**      | ls:Device      | 1  | The properties of a device.                                                                                                                                                                  |
| 7    | **domain_name** | ls:Domain-Name | 1  | A network domain name.                                                                                                                                                                 |
| 9    | **features**    | ls:Features    | 1  | A set of items such as Action/Target pairs, profiles versions, options that are supported by the Actuator. The Target is used with the query Action to determine an Actuator's capabilities. |
| 10   | **file**        | ls:File        | 1  | The properties of a file.                                                                                                                                                                    |
| 13   | **ipv4_net**    | ls:IPv4-Net    | 1  | An IPv4 address range including CIDR prefix length.                                                                                                                                          |
| 14   | **ipv6_net**    | ls:IPv6-Net    | 1  | An IPv6 address range including prefix length.                                                                                                                                               |
| 18   | **process**     | ls:Process     | 1  | Common properties of an instance of a computer program as executed on an operating system.                                                                                                   |
| 1027 | **er/**         | er:AP-Target   | 1  | Targets defined in the Endpoint Response actuator profile                                                                                                                                    |

#### 2.1.2.2 ER Targets
The list of common Targets is extended to include the additional Targets defined in this section and referenced with the `er` namespace.

**Table 2.1.2-2. Targets Unique to ER**


**Type: AP-Target (Choice)**

| ID | Name               | Type           | \# | Description                                                                                                                     |
|----|--------------------|----------------|----|---------------------------------------------------------------------------------------------------------------------------------|
| 1  | **registry_entry** | Registry-Entry | 1  | A registry entry applicable to Windows Operating Systems.                                                                       |
| 2  | **account**        | Account        | 1  | A user account on an Endpoint.                                                                                                  |
| 3  | **service**        | Service        | 1  | A program which is managed and executed by a service host process, where several services may be sharing the same service host. |

### 2.1.3 Type Definitions

#### 2.1.3.1 Target Types

**Table 2.1.3-1. Registry Entry**

**Type: Registry-Entry (Record)**

| ID | Name      | Type   | \#   | Description                                                                                                         |
|----|-----------|--------|------|---------------------------------------------------------------------------------------------------------------------|
| 1  | **key**   | String | 0..1 | Specifies the full registry key including the hive.                                                                 |
| 2  | **type**  | String | 1    | The registry value type as defined in the [[Winnt.h header]](#winnth-registry-types).                               |
| 3  | **value** | String | 0..1 | The value of the registry key. The Actuator is responsible to format the value in accordance with the defined type. |

**Table 2.1.3-2. Account**

**Type: Account (Map{1..\*})**

| ID | Name             | Type   | \#   | Description                               |
|----|------------------|--------|------|-------------------------------------------|
| 1  | **uid**          | String | 0..1 | The unique identifier of the account.     |
| 2  | **account_name** | String | 0..1 | The chosen display name of the account.   |
| 3  | **directory**    | String | 0..1 | The path to the account's home directory. |


**Table 2.1.3-3. Service**

**Type: Service (Map{1..\*})**

| ID | Name             | Type   | \#   | Description                      |
|----|------------------|--------|------|----------------------------------|
| 1  | **name**         | String | 0..1 | The unique name of the service.  |
| 2  | **display_name** | String | 0..1 | The display name of the service. |

### 2.1.4 Command Arguments
Arguments provide additional precision to a Command by including information such as how, when, or where a Command is to be executed. Table 2.1.3-1 summarizes the Command Arguments defined in Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10) as they relate to ER functionality.

**Table 2.1.4-1. Command Arguments applicable to ER**

**Type: Args (Map{1..\*})**

| ID   | Name                   | Type             | \#   | Description                                                                        |
|------|------------------------|------------------|------|------------------------------------------------------------------------------------|
| 1    | **start_time**         | ls:Date-Time     | 0..1 | The specific date/time to initiate the Command                                     |
| 2    | **stop_time**          | ls:Date-Time     | 0..1 | The specific date/time to terminate the Command                                    |
| 3    | **duration**           | ls:Duration      | 0..1 | The length of time for an Command to be in effect                                  |
| 4    | **response_requested** | ls:Response-Type | 0..1 | The type of Response required for the Command: `none`, `ack`, `status`, `complete` |
| 1027 | **er/**                | er:AP-Args       | 0..1 | Command Arguments for Endpoint Response                                            |

**Table 2.1.4-2. Command Arguments Unique to ER**

**Type: AP-Args (Map{1..\*})**

| ID | Name                    | Type                | \#   | Description                                                                                                                                                                                                                                                                              |
|----|-------------------------|---------------------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | **account_status**      | Account-Status      | 0..1 | Specifies whether an account shall be enabled or disabled.                                                                                                                                                                                                                               |
| 2  | **device_containment**  | Device-Containment  | 0..1 | Specifies which type of isolation an Endpoint shall be subjected to (e.g., port isolation, application restriction).                                                                                                                                                                     |
| 3  | **permitted_addresses** | Permitted-Addresses | 0..1 | Specifies which IP or domain name addresses shall remain accessible when a device is contained with the 'device_containment' Argument set to 'network_isolation'.                                                                                                                        |
| 4  | **scan_depth**          | Scan-Depth          | 0..1 | Specifies which type of scan to perform on a device.                                                                                                                                                                                                                                     |
| 5  | **periodic_scan**       | Periodic-Scan       | 0..1 | Specifies whether periodic scans shall be enabled or disabled.                                                                                                                                                                                                                           |
| 6  | **downstream_device**   | Downstream-Device   | 0..* | Specifies a single Endpoint or group of Endpoints on which a Command is to be performed. MUST be included for Commands where the Target field is populated by types other than 'device' and the Command is meant to be performed on a single Endpoint or limited selection of Endpoints. |

**Type: Account-Status (Enumerated)**

| ID | Item         | Description                                                    |
|----|--------------|----------------------------------------------------------------|
| 1  | **enabled**  | Enable the account and render it available on the Endpoint.    |
| 2  | **disabled** | Disable the account and render it unavailable on the Endpoint. |

**Type: Device-Containment (Enumerated)**

| ID | Item                  | Description                                                                                                                                                                                                                                                                  |
|----|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | **network_isolation** | Isolate the Endpoint from communicating with other networked entities, typically through relegation to a private VLAN segment and/or port isolation. MAY be combined with the 'permitted_addresses' Argument to allow communication with select IP or domain name addresses. |
| 2  | **app_restriction**   | Restrict the execution of applications to only those that are signed by a trusted party (e.g., Microsoft only).                                                                                                                                                              |
| 3  | **disable_nic**       | Disable the Network Interface Controller(s) on the Endpoint.                                                                                                                                                                                                                 |

**Type: Permitted-Addresses (Map{1..\*})**

| ID | Name            | Type                    | \#   | Description                                                                          |
|----|-----------------|-------------------------|------|--------------------------------------------------------------------------------------|
| 1  | **domain_name** | ArrayOf(ls:Domain-Name) | 0..1 | The domain name address(es) the contained device(s) can still communicate with.      |
| 2  | **ipv4_net**    | ArrayOf(ls:IPv4-Net)    | 0..1 | The IPv4 address(es) or range(s) the contained device(s) can still communicate with. |
| 3  | **ipv6_net**    | ArrayOf(ls:IPv6-Net)    | 0..1 | The IPv6 address(es) or range(s) the contained device(s) can still communicate with. |

**Type: Scan-Depth (Enumerated)**

| ID | Item                  | Description                            |
|----|-----------------------|----------------------------------------|
| 1  | **shallow**           | Initiate a shallow (A.K.A quick) scan. |
| 2  | **deep**              | Initiate a deep (A.K.A full) scan.     |

**Type: Periodic-Scan (Enumerated)**

| ID | Item         | Description             |
|----|--------------|-------------------------|
| 1  | **enabled**  | Enable periodic scans   |
| 2  | **disabled** | Disable periodic scans. |

**Type: Downstream-Device (Map{1..\*})**

| ID | Name              | Type               | \#   | Description                                                                                               |
|----|-------------------|--------------------|------|-----------------------------------------------------------------------------------------------------------|
| 1  | **devices**       | ArrayOf(ls:Device) | 0..1 | One or more Endpoint on which the associated Command is to be performed.                                  |
| 2  | **device_groups** | ArrayOf(ls:String) | 0..1 | One or more defined groups of Endpoints on which the associated Command is to be performed.               |
| 3  | **tenant_id**     | ls:String          | 0..1 | Specifies a particular instance of an ER OpenC2 Message Consumer which is hosted in a multi-tenant cloud. |

Usage Requirements:
  * Entities that receive a Downstream-Device argument AND `tenant_id` is populated:
      * MUST process the `tenant_id` field before `device` or `device_groups`

### 2.1.5 Actuator Specifiers
An Actuator is the entity that provides the functionality and performs the Action. The Actuator executes the Action on the Target. In the context of this profile, the Actuator is the ER and the presence of one or more Specifiers further refine which Actuator(s) shall execute the Action.

**Type: Actuator (Choice)**

| ID   | Name    | Type             | \# | Description                                            |
|------|---------|------------------|----|--------------------------------------------------------|
| 1027 | **er/** | er:AP-Specifiers | 1  | Actuator function and specifiers for Endpoint Response |

The Actuator Specifiers defined in this document are referenced under the `er` namespace.

## 2.2 OpenC2 Response Components
Response messages originate from the Actuator as a result of a Command.

Responses associated with required Actions MUST be implemented. Implementations that include optional Actions MUST implement the RESPONSE associated with the implemented Action. Additional details regarding the Commands and associated Responses are captured in [Section 2.3](#23-openc2-commands). Examples are provided in [Annex A](#annex-a-sample-commands).

### 2.2.1 Response Status Codes
Table 2.2.1-1 lists the Response Status Codes defined in the OpenC2 Language Specification that are applicable to ER.

**Table 2.2.1-1. Response Status Codes**

**_Type: Status-Code (Enumerated.ID)_**

| Value | Description |
| :--- | :--- |
| 102 | Processing. The Command was received but the action is not necessarily completed. |
| 200 | OK. The Command was received and the action was performed. |
| 400 | Bad Request. Unable to process Command, parsing error. |
| 500 | Internal Error. |
| 501 | Not Implemented. For "response_requested" value "complete", one of the following MAY apply:<br> * Target not supported<br> * Option not supported<br> * Command not supported |

**Table 2.2.2-1. Results applicable to ER**

**Type: Results (Map{1..\*})**

| ID | Name           | Type              | \#    | Description                                                         |
|----|----------------|-------------------|-------|---------------------------------------------------------------------|
| 1  | **versions**   | ls:Version unique | 0..\* | List of OpenC2 language versions supported by this Consumer         |
| 2  | **profiles**   | ls:Nsid unique    | 0..\* | List of profiles supported by this Consumer                         |
| 3  | **pairs**      | Action-Targets    | 0..1  | List of targets applicable to each supported Action                 |
| 4  | **rate_limit** | Number{0.0..\*}   | 0..1  | Maximum number of requests per minute supported by design or policy |

## 2.3 OpenC2 Commands

An OpenC2 Command consists of an Action/Target pair and associated Specifiers and Arguments. This section enumerates the allowed Commands and presents the associated Responses.

Table 2.3-2 defines the Commands that are valid in the context of the ER profile. An Action (the top row in Table 2.3-2) paired with a Target (the first column in Table 2.3-2) defines a valid Command. The subsequent subsections provide the property tables applicable to each OpenC2 Command.

**Table 2.3-1. Command Matrix**

|                    |scan |query|deny |contain|allow|start|stop |restart|set  |update|create|delete|
|:---                |:---:|:---:|:---:|:---:  |:---:|:---:|:---:| :---: |:---:|:---: |:---: |:---: |
| **domain_name**		 |     |     |valid|       |valid|     |     |       |     |      |      |      |
| **device** 		     |valid|     |     | valid |valid|     |valid| valid |     |      |      |      |
| **features** 	  	 |     |valid|     |       |     |     |     |       |     |      |      |      |
| **file** 			     |     |     |valid| valid |valid|valid|     |       |     |valid |      |valid |
| **ipv4_net**		   |     |     |valid|       |valid|     |     |       |valid|      |      |      |
| **ipv6_net**		   |     |     |valid|       |valid|     |     |       |valid|      |      |      |
| **process** 		   |     |     |     |       |     |     |valid|       |     |      |      |      |
| **registry_entry** |     |     |     |       |     |     |     |       |valid|      |valid |valid |
| **account** 		   |     |     |     |       |     |     |     |       |valid|      |      |      |
| **service** 		   |     |     |     |       |     |     |valid|       |     |      |      |valid |

Table 2.3-2 defines the Command Arguments that are allowed for a particular Command by the ER profile. A Command (the top row in Table 2.3-2) paired with an Argument (the first column in Table 2.3-2) defines an allowable combination. The subsection identified at the intersection of the Command/Argument provides details applicable to each Command as influenced by the Argument.

A Command where the Target portion of the Action/Target pair is not specified (written as _target_), denotes that the Argument can be combined with all Commands covered by the Action.

**Table 2.3-2. Command Arguments Matrix**

|                         |**scan device**             |**deny _target_** |**contain device**             |**contain _target_** |**allow _target_** |**start _target_** |**stop _target_** |**restart _target_** |**set er:account**            |**set _target_** |**update _target_**  |**create _target_**   |**delete _target_**   |
|:---                     |:---:                       |:---:             |:---:                          |:---:                |:---:              |:---:              |:---:             |:---:                |:---:                         |:---:            |:---:                |:---:                 |:---:                 |
| **response_requested**  |[2.3.1.1](#2311-scan-device)|[2.3.3](#233-deny)|[2.3.4.1](#2341-contain-device)|[2.3.4](#234-contain)|[2.3.5](#235-allow)|[2.3.6](#236-start)|[2.3.7](#237-stop)|[2.3.8](#238-restart)|[2.3.9.4](#2394-set-eraccount)|[2.3.9](#238-set)|[2.3.10](#239-update)|[2.3.11](#2310-create)|[2.3.12](#2311-delete)|
| **device_containment**  |                            |                  |[2.3.4.1](#2341-contain-device)|                     |                   |                   |                  |                     |                              |                 |                     |                      |                      |
| **account_status**      |                            |                  |                               |                     |                   |                   |                  |                     |[2.3.9.4](#2394-set-eraccount)|                 |                     |                      |                      |
| **permitted_addresses** |                            |                  |[2.3.4.1](#2341-contain-device)|                     |                   |                   |                  |                     |                              |                 |                     |                      |                      |
| **scan_depth**          |[2.3.1.1](#2311-scan-device)|                  |                               |                     |                   |                   |                  |                     |                              |                 |                     |                      |                      |
| **periodic_scan**       |[2.3.1.1](#2311-scan-device)|                  |                               |                     |                   |                   |                  |                     |                              |                 |                     |                      |                      |
| **downstream_device**   |[2.3.1.1](#2311-scan-device)|[2.3.3](#233-deny)|[2.3.4.1](#2341-contain-device)|[2.3.4](#234-contain)|[2.3.5](#235-allow)|[2.3.6](#236-start)|[2.3.7](#237-stop)|[2.3.8](#238-restart)|[2.3.9.4](#2394-set-eraccount)|[2.3.9](#238-set)|[2.3.10](#239-update)|[2.3.11](#2310-create)|[2.3.12](#2311-delete)|


### 2.3.1 Scan

OpenC2 Consumers that receive a 'scan' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'scan' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Command not supported" in the status text
    * MAY respond with status code 500

#### 2.3.1.1 Scan device
Scan a device for binaries classified as malicious.


OpenC2 Producers that send 'scan device' Commands:

* MAY populate the Command Arguments field with a 'scan_depth' argument
* MAY populate the Command Arguments field with a 'periodic_scan' argument

OpenC2 Consumers that receive 'scan device' Commands:

* but do not support the 'scan_depth' argument
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Argument not supported" in the status Text
    * MAY respond with status code 500
* but do not support the 'periodic_scan' argument
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Argument not supported" in the status Text
    * MAY respond with status code 500

### 2.3.2 Query
The valid Target type, associated Specifiers, and Options are summarized in [Section 2.3.3.1](#2331-query-features).

#### 2.3.2.1 Query features
The 'query features' Command MUST be implemented in accordance with Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10).

### 2.3.3 Deny

OpenC2 Consumers that receive a 'deny' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'deny' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Command not supported" in the status text
    * MAY respond with status code 500

#### 2.3.2.1 Deny domain_name
Prevents an Endpoint from connecting to a Domain Name address.

OpenC2 Consumers that receive a 'deny domain_name' Command:

* but do not implement the 'deny domain_name' Command:
    * MUST NOT respond with a OK/200
    * SHOULD respond with the 501 Response code
    * SHOULD respond with 'Target type not supported' in the status text
    * MAY respond with the 500 status code

#### 2.3.2.2 Deny file
Prevents the execution of a file.

OpenC2 Consumers that receive a 'deny file' Command:

* but cannot access the file specified in the file Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access file" in the status text

#### 2.3.2.3 Deny ipv4_net
Prevents an Endpoint from connecting to an IPv4 address.

OpenC2 Consumers that receive a 'deny ipv4_net' Command:

* but do not implement the 'deny ipv4_net' Command:
    * MUST NOT respond with a OK/200
    * SHOULD respond with the 501 Response code
    * SHOULD respond with 'Target type not supported' in the status text
    * MAY respond with the 500 status code

#### 2.3.2.4 Deny ipv6_net
Prevents an Endpoint from connecting to an IPv6 address.

OpenC2 Consumers that receive a 'deny ipv6_net' Command:

* but do not implement the 'deny ipv6_net' Command:
    * MUST NOT respond with a OK/200
    * SHOULD respond with the 501 Response code
    * SHOULD respond with 'Target type not supported' in the status text
    * MAY respond with the 500 status code

### 2.3.4 Contain
OpenC2 Consumers that receive a 'contain' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'contain' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Command not supported" in the status text
    * MAY respond with status code 500

#### 2.3.4.1 Contain device
Limits the functionalities of an Endpoint in relation to application execution and/or network communications. The Producer and Consumer of the command MUST support the er:device_containment Command Argument as defined in [Section 2.1.4](#214-command-arguments)

OpenC2 Producers that send 'contain device' Commands:

* MUST populate the Command Arguments field with a 'device_containment' argument
* MAY populate the Command Arguments field with a 'permitted_addresses' argument

OpenC2 Consumers that receive a 'contain device' Command:

* but the Command Arguments field is not populated with a 'device_containment' argument
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with "Containment type argument not populated" in the status text
* but cannot access the device specified in the device Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access device" in the status text

#### 2.3.4.2 Contain file
Puts a file into quarantine, rendering it inaccessible to the user of the machine and unable to execute on the Endpoint.

OpenC2 Producers that send 'contain file' Commands:

* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive a 'contain file' Command:

* but cannot access the file specified in the file Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access file" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text

### 2.3.5 Allow
'Allow' can be treated as the mathematical complement to all 'deny' Actions as well as all 'contain' Actions defined in this document. Sections [2.3.3](#233-deny) and [2.3.4](#234-contain) lists all Commands constructed using 'deny' and 'contain', respectively.

OpenC2 Consumers that receive a 'allow' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'allow' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Command not supported" in the status text
    * MAY respond with status code 500

#### 2.3.5.1 Allow domain_name
Allows an Endpoint to connect to a Domain Name address. Can be treated as the mathematical complement to the 'deny domain_name' Command.

OpenC2 Consumers that receive a 'allow domain_name' Command:

* but do not implement the 'allow domain_name' Command:
    * MUST NOT respond with a OK/200
    * SHOULD respond with the 501 Response code
    * SHOULD respond with 'Target type not supported' in the status text
    * MAY respond with the 500 status code

#### 2.3.5.2 Allow device
Removes a device from containment.

OpenC2 Consumers that receive a 'allow device' Command. Can be treated as the mathematical complement to the 'contain device' Command.
* but cannot access the device specified in the device Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access device" in the status text


#### 2.3.5.3 Allow file
Either allows a file matching a certain hash to be written to an Endpoint, or takes a file out of quarantine, depending on which field of the file Target is populated.

OpenC2 Producers that send 'contain file' Commands:
* MUST only populate a single property of the file Target.

OpenC2 Consumers that receive a 'allow file' Command:

* and the 'path' property of the file Target is populated
    * SHOULD treat the Command as the mathematical complement to the 'contain file' Command.
* and the 'hashes' property of the file Target is populated
    * SHOULD treat the Command as the mathematical complement to the 'deny file' Command.
* and the 'name' property of the file Target is populated
    * SHOULD treat the Command as the mathematical complement to the 'deny file' Command.
* but more than one property is populated at a time
    * MUST respond with status code 400
    * SHOULD respond with "path and hashes cannot be populated at the same time" in the status text

#### 2.3.5.4 Allow ipv4_net
Allows an Endpoint to connect to an IPv4 address. Can be treated as the mathematical complement to the 'deny ipv4_net' Command.

OpenC2 Consumers that receive a 'allow ipv4_net' Command:

* but do not implement the 'allow ipv4_net' Command:
    * MUST NOT respond with a OK/200
    * SHOULD respond with the 501 Response code
    * SHOULD respond with 'Target type not supported' in the status text
    * MAY respond with the 500 status code

#### 2.3.5.5 Allow ipv6_net
Allows an Endpoint to connect to an IPv6 address. Can be treated as the mathematical complement to the 'deny ipv6_net' Command.

OpenC2 Consumers that receive a 'allow ipv6_net' Command:

* but do not implement the 'allow ipv6_net' Command:
    * MUST NOT respond with a OK/200
    * SHOULD respond with the 501 Response code
    * SHOULD respond with 'Target type not supported' in the status text
    * MAY respond with the 500 status code

### 2.3.6 Start
OpenC2 Consumers that receive a 'start' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'start' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Command not supported" in the status text
    * MAY respond with status code 500

#### 2.3.6.1 Start file
Instructs the Actuator to execute a file.

OpenC2 Producers that send 'start file' Commands:

* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive a 'start file' Commands:
* but cannot access the file specified in the file Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access file" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text

### 2.3.7 Stop
OpenC2 Consumers that receive a 'stop' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'stop <target>' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Command not supported" in the status text
    * MAY respond with status code 500

#### 2.3.7.1 Stop device
Shuts down an Endpoint.

OpenC2 Consumers that receive a 'stop device' Command:

* but cannot access the device specified in the device Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access device" in the status text

#### 2.3.7.2 Stop process
Stops an active process. A 'process' Target MUST contain at least one property.

OpenC2 Producers that send 'stop process' commands
* MUST populate at least one property of the Command Target
* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive 'stop process' commands
* but the Command Target does not contain at least one property
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with "Process Target does not have any properties populated" in the status text
* but cannot access the process specified by the populated propertie(s)
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access process" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text

#### 2.3.7.3 Stop er:service
Stops a running service and removes it from its service host process.

OpenC2 Producers that send 'stop er:service' commands
* MUST populate at least one property of the Command Target
* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive 'stop er:service' commands
* but the Command Target does not contain at least one property
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with 'Service Target does not have any properties populated' in the status text
* but cannot stop the service specified by the populated propertie(s)
    * MUST respond with status code 500
    * MAY respond with 'Cannot stop service' in the status text
    * SHOULD respond with a status text detailing why the service could not be deleted
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text

### 2.3.8 Restart
OpenC2 Consumers that receive a 'restart' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'restart' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Command not supported" in the status text
    * MAY respond with status code 500

#### 2.3.8.1 Restart device
Restarts an Endpoint.

OpenC2 Consumers that receive a 'restart device' Command:

* but cannot access the device specified in the device Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access device" in the status text

### 2.3.9 Set
OpenC2 Consumers that receive a 'set' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'set' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Command not supported" in the status text
    * MAY respond with status code 500

#### 2.3.9.1 Set ipv4_net
Sets the IPv4 address of the Endpoint to the specified Target value.

OpenC2 Producers that send 'set ipv4_net' Commands:
* MUST include an IPv4 address without the CIDR prefix-length, or have it set to 32
* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive 'set ipv4_net' Commands
* but the CIDR prefix-length is set to a value other than 32
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with "IPv4 address not set to a single address" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text

#### 2.3.9.2 Set ipv6_net
Sets the IPv6 address of the Endpoint to the specified Target value.

OpenC2 Producers that send 'set ipv4_net' Commands:
* MUST include an IPv4 address without the prefix-length, or have it set to 128
* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive a 'set ipv4_net' Command:
* but the CIDR prefix-length is set to a value other than 128
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with "IPv6 address not set to a single address" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text

#### 2.3.9.3 Set er:registry_entry
Sets the 'value' property of a Registry Entry. The 'type' property MUST be populated and MUST conform to the registry entry types as defined in [Winnt.h header](#winnth-registry-types).

OpenC2 Producers that send 'set er:registry_entry' Commands:
* MUST populate the 'type' property
* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive a'set er:registry_entry' Command:
* but the 'type' property is not populated
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with "Registry entry type not specified" in the status text
* but cannot access the registry entry specified in the registry entry Target
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with "Cannot access registry entry" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text


#### 2.3.9.4 Set er:account
Sets the status of the account to be either enabled or disabled. The producer and consumer of the command MUST support the er:account_status Command Argument as defined in [Section 2.1.4](#214-command-arguments)

OpenC2 Producers that send 'set er:account' Commands:
* MUST populate the Command Arguments field with a Account-Status argument
* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive a 'set er:account' Command:
* but the Command Arguments field is not populated with a Account-Status argument
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with "Account-status type argument not populated" in the status text
* but cannot access the account specified in the er:account Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access account" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text

### 2.3.10 Update
#### 2.3.10.1 Update file
The 'update file' Command is used to replace or update files such as configuration files, rule sets, etc. Implementation of the update file Command is OPTIONAL. OpenC2 Consumers that choose to implement the 'update file' Command MUST include all steps that are required for the update file procedure such as retrieving the file(s), install the file(s), restart/ reboot the device etc. The end state shall be that the ER actuator operates with the new file at the conclusion of the 'update file' Command. The atomic steps that take place are implementation specific.

### 2.3.11 Create
#### 2.3.11.1 Create er:registry_entry
Creates a registry entry in the specified path. The 'type' property MUST be populated and MUST conform to the registry entry types as defined in [Winnt.h header](#winnth-registry-types).

OpenC2 Producers that send 'create er:registry_entry' Commands:
* MUST include the 'path' property of the er:registry entry Target
* MUST refer to the registry key
    * SHOULD refer to the registry key using the 'key' property
    * MAY refer to the registry key by including the key in the 'path' property
* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive a 'create er:registry_entry' Command:
* but cannot access the registry entry specified in the registry entry Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access registry entry" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text

### 2.3.12 Delete
OpenC2 Consumers that receive a 'delete' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'delete <target>' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with "Command not supported" in the status text
    * MAY respond with status code 500

#### 2.3.12.1 Delete file
Deletes the specified file from an Endpoint.

OpenC2 Producers that send 'delete file' Commands:

* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive a 'delete file' Command:
* but cannot access the file specified in the file Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access file" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text

#### 2.3.12.2 Delete er:registry_entry
Deletes a registry entry. The 'type' property MUST be populated and MUST conform to the registry entry types as defined in [Winnt.h header](#winnth-registry-types).

OpenC2 Producers that send 'create er:registry_entry' Commands:
* MUST include the 'path' property of the er:registry entry Target
* MUST refer to the registry key
    * SHOULD refer to the registry key using the 'key' property
    * MAY refer to the registry key by including the key in the 'path' property
* MUST populate the Command Arguments field with a 'er:downstream_device' argument


OpenC2 Consumers that receive a 'create er:registry_entry' Command:
* but cannot access the registry entry specified in the registry entry Target
    * MUST respond with status code 500
    * SHOULD respond with "Cannot access registry entry" in the status text
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text


#### 2.3.12.3 Delete er:service
Deletes a service from the Endpoint.

OpenC2 Producers that send 'delete er:service' commands
* MUST populate at least one property of the Command Target
* MUST populate the Command Arguments field with a 'er:downstream_device' argument

OpenC2 Consumers that receive 'delete er:service' commands
* but the Command Target does not contain at least one property
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with 'Service Target does not have any properties populated' in the status text
* but cannot delete the service specified by the populated propertie(s)
    * MUST respond with status code 500
    * MAY respond with 'Cannot delete service' in the status text
    * SHOULD respond with a status text detailing why the service could not be deleted
* but the Command Arguments field is not populated with a 'er:downstream_device' argument
  * MUST NOT respond with status code OK/200
  * SHOULD respond with status code 400
  * MAY respond with status code 500
  * SHOULD respond with "Downstream device argument not populated" in the status text


# 3 Conformance
_This section is normative_
This section identifies the requirements for fifty eight conformance profiles as they pertain to two conformance targets. The two conformance targets are OpenC2 Producers and OpenC2 Consumers (as defined in [Section 1.8](#18-purpose-and-scope) of this specification).

## 3.1 Clauses Pertaining to the OpenC2 Producer Conformance Target
All OpenC2 Producers that are conformant to this specification MUST satisfy Conformance Clause 1 and MAY satisfy one or more of Conformance Clauses 2 through 11.

### 3.1.1 Conformance Clause 1: Baseline OpenC2 Producer
An OpenC2 Producer satisfies Baseline OpenC2 Producer conformance if:
* 3.1.1.1 **MUST** support JSON serialization of OpenC2 Commands that are syntactically valid in accordance with the property tables presented in [Section 2.1](#21-openc2-command-components)
* 3.1.1.2 All serializations **MUST** be implemented in a manner such that the serialization validates against and provides a one-to-one mapping to the property tables in [Section 2.1](#21-openc2-command-components) of this specification
* 3.1.1.3 **MUST** support the use of a Transfer Specification that is capable of delivering authenticated, ordered, lossless and uniquely identified OpenC2 messages
* 3.1.1.4 **SHOULD** support the use of one or more published OpenC2 Transfer Specifications which identify underlying transport protocols such that an authenticated, ordered, lossless, delivery of uniquely identified OpenC2 messages is provided as referenced in [Section 1](#1-introduction) of this specification
* 3.1.1.5 **MUST** be conformant with Version 1.0 of the OpenC2 Language Specification
* 3.1.1.6 **MUST** implement the 'query features' Command in accordance with the normative text provided in Version 1.0 of the OpenC2 Language Specification
* 3.1.1.7 **MUST** implement the 'response_requested' Command Argument as a valid option for any Command
* 3.1.1.8 **MAY** implement the 'er:downstream_device' Command Argument as a valid option for any Command not included in section [Section 3.1.2](#312-conformance-clause-2downstream-device-consumers)
* 3.1.1.9 **MUST** conform to at least one of the following conformance clauses in this specification:
   * Conformance Clause 7
   * Conformance Clause 9

### 3.1.2 Conformance Clause 2: Downstream Device Producer
An OpenC2 Producer satisfies 'Device-Containment Producer' conformance if:
* 3.1.2.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* And if the Producer implements the 'start file' command:
  * 3.1.2.2 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'start file' Command in accordance with [Section 2.3.6.1](#2361-start-file) of this specification
* And if the Producer implements the 'contain file' command:
  * 3.1.2.3 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'contain file' Command in accordance with [Section 2.3.4.2](#2342-contain-file) of this specification
* And if the Producer implements the 'set ipv4_net' command:
  * 3.1.2.4 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'set ipv4_net' Command in accordance with [Section 2.3.9.1](#2391-set-ipv4-net) of this specification
* And if the Producer implements the 'set ipv6_net' command:
  * 3.1.2.5 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'set ipv6_net' Command in accordance with [Section 2.3.9.2](#2392-set-ipv6-net) of this specification
* And if the Producer implements the 'stop process' command:
  * 3.1.2.6 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'stop process' Command in accordance with [Section 2.3.7.2](#2372-stop-process) of this specification
* And if the Producer implements the 'set er:registry_entry' command:
  * 3.1.2.7 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'set er:registry_entry' Command in accordance with [Section 2.3.9.3](#2393-set-erregistry-entry)) of this specification
* And if the Producer implements the 'create er:registry_entry' command:
  * 3.1.2.8 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'create er:registry_entry' Command in accordance with [Section 2.3.11.1](#23111-create-erregistry-entry) of this specification
* And if the Producer implements the 'delete er:registry_entry' command:
  * 3.1.2.9 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'delete er:registry_entry' Command in accordance with [Section 2.3.12.2](#23122-delete-erregistry-entry) of this specification
* And if the Producer implements the 'set er:account' command:
  * 3.1.2.10 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'set er:account' Command in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification
* And if the Producer implements the 'stop er:service' command:
  * 3.1.2.11 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'stop er:service' Command in accordance with [Section 2.3.7.3](#2373-stop-erservice) of this specification
* And if the Producer implements the 'delete er:service' command:
  * 3.1.2.12 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'delete er:service' Command in accordance with [Section 2.3.12.3](#23123-delete-erservice) of this specification

### 3.1.3 Conformance Clause 3: Domain Name Producer
An OpenC2 Producer satisfies 'Deny Domain Name Producer' conformance if:
* 3.1.3.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.3.2 **MUST** implement the 'deny domain_name' Command in accordance with [Section 2.3.3.1](#2331-deny-domain-name) of this specification
* 3.1.3.3 **MUST** implement the 'allow domain_name' Command in accordance with [Section 2.3.5.1](#2351-allow-domain-name) of this specification

### 3.1.4 Conformance Clause 4: Scan Device Producer
An OpenC2 Producer satisfies 'Scan Device Producer' conformance if:
* 3.1.4.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.4.2 **MUST** implement the 'scan device' Command in accordance with [Section 2.3.1.1](#2311-scan-device) of this specification

### 3.1.5 Conformance Clause 5: Scan Depth Producer
An OpenC2 Producer satisfies 'Scan Depth Producer' conformance if:
* 3.1.5.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.5.2 **MUST** implement the 'er:scan_depth' Command Argument as a valid option for the 'scan device' Command in accordance with [Section 2.3.1.1](#2311-scan-device) of this specification

### 3.1.6 Conformance Clause 6: Periodic Scan Producer
An OpenC2 Producer satisfies 'Periodic Scan Producer' conformance if:
* 3.1.6.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.6.2 **MUST** implement the 'er:periodic_scan' Command Argument as a valid option for the 'scan device' Command in accordance with [Section 2.3.1.1](#2311-scan-device) of this specification

### 3.1.7 Conformance Clause 7: Contain Device Producer
An OpenC2 Producer satisfies 'Contain Device Producer' conformance if:
* 3.1.7.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.7.2 **MUST** implement the 'contain device' Command in accordance with [Section 2.3.4.1](#2341-contain-device) of this specification
* 3.1.7.3 **MUST** implement the 'er:device_containment' Command Argument in accordance with [Section 2.3.4.1](#2341-contain-device) of this specification
* 3.1.7.4 **MUST** implement the 'er:device_containment' Command Argument as a valid option for the 'contain device' Command in accordance with [Section 2.3.4.1](#2341-contain-device) of this specification

### 3.1.8 Conformance Clause 8: Permitted Addresses Producer
An OpenC2 Producer satisfies 'Permitted Addresses Producer' conformance if:
* 3.1.8.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.8.2 **MUST** implement the 'er:permitted_addresses' Command Argument as a valid option for the 'contain device' Command in accordance with [Section 2.3.4.1](#2341-contain-device) of this specification

### 3.1.9 Conformance Clause 9: Allow Device Producer
An OpenC2 Producer satisfies 'Contain Device Producer' conformance if:
* 3.1.9.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.9.2 **MUST** implement the 'allow device' Command in accordance with [Section 2.3.5.1](#2351-allow-device) of this specification

### 3.1.10 Conformance Clause 10: Stop Device Producer
An OpenC2 Producer satisfies 'Stop Device Producer' conformance if:
* 3.1.10.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.10.2 **MUST** implement the 'stop device' Command in accordance with [Section 2.3.7.1](#2371-stop-device) of this specification

### 3.1.11 Conformance Clause 11: Restart Device Producer
An OpenC2 Producer satisfies 'Restart Device Producer' conformance if:
* 3.1.11.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.11.2 **MUST** implement the 'restart device' Command in accordance with [Section 2.3.8.1](#2381-restart-device) of this specification

### 3.1.12 Conformance Clause 12: Deny File Producer
An OpenC2 Producer satisfies 'Deny File Producer' conformance if:
* 3.1.12.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.12.2 **MUST** implement the 'deny file' Command in accordance with [Section 2.3.3.2](#2332-deny-file) of this specification

### 3.1.13 Conformance Clause 13: Contain File Producer
An OpenC2 Producer satisfies 'Contain File Producer' conformance if:
* 3.1.13.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.13.2 **MUST** implement the 'contain file' Command in accordance with [Section 2.3.4.2](#2342-contain-file) of this specification
* 3.1.13.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.4.2](#2342-contain-file) of this specification

### 3.1.14 Conformance Clause 14: Allow File Producer
An OpenC2 Producer satisfies 'Allow File Producer' conformance if:
* 3.1.14.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.14.2 **MUST** implement the 'allow file' Command in accordance with [Section 2.3.5.3](#2353-allow-file) of this specification
* 3.1.14.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.4.2](#2342-contain-file) of this specification

### 3.1.15 Conformance Clause 15: Start File Producer
An OpenC2 Producer satisfies 'Start File Producer' conformance if:
* 3.1.15.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.15.2 **MUST** implement the 'start file' Command in accordance with [Section 2.3.6.1](#2361-start-file) of this specification
* 3.1.15.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.6.1](#2361-start-file) of this specification

### 3.1.16 Conformance Clause 16: Deny IPv4 Net Producer
An OpenC2 Producer satisfies 'Deny IPv4 Net Producer' conformance if:
* 3.1.16.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification

### 3.1.17 Conformance Clause 17: Allow IPv4 Net Producer
An OpenC2 Producer satisfies 'Allow IPv4 Net Producer' conformance if:
* 3.1.17.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification

### 3.1.18 Conformance Clause 18: Set IPv4 Net Producer
An OpenC2 Producer satisfies 'Set IPv4 Net Producer' conformance if:
* 3.1.18.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.18.2 **MUST** implement the 'set ipv4_net' Command in accordance with [Section 2.3.9.1](#2391-set-ipv4-net) of this specification
* 3.1.18.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.9.1](#2391-set-ipv4-net) of this specification

### 3.1.19 Conformance Clause 19: Deny IPv6 Net Producer
An OpenC2 Producer satisfies 'Deny IPv6 Net Producer' conformance if:
* **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification

### 3.1.20 Conformance Clause 20: Allow IPv6 Net Producer
An OpenC2 Producer satisfies 'Allow IPv6 Net Producer' conformance if:
* **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification

### 3.1.21 Conformance Clause 21: Set IPv6 Net Producer
An OpenC2 Producer satisfies 'Set IPv6 Net Producer' conformance if:
* 3.1.21.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.21.2 **MUST** implement the 'set ipv6_net' Command in accordance with [Section 2.3.9.2](#2392-set-ipv6-net) of this specification
* 3.1.21.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.9.2](#2392-set-ipv6-net) of this specification

### 3.1.22 Conformance Clause 22: Stop Process Producer
An OpenC2 Producer satisfies 'Process Producer' conformance if:
* 3.1.22.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.22.2 **MUST** implement the 'stop process' Command in accordance with [Section 2.3.7.2](#2372-stop-process) of this specification
* 3.1.22.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.7.2](#2372-stop-process) of this specification

### 3.1.23 Conformance Clause 23: Set Registry Entry Producer
An OpenC2 Producer satisfies 'Registry Entry Producer' conformance if:
* 3.1.23.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.23.2 **MUST** implement the 'set registry_entry' Command in accordance with [Section 2.3.9.3](#2393-set-erregistry-entry) of this specification
* 3.1.23.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections

### 3.1.24 Conformance Clause 24: Create Registry Entry Producer
An OpenC2 Producer satisfies 'Registry Entry Producer' conformance if:
* 3.1.24.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.24.2 **MUST** implement the 'create er:registry_entry' Command in accordance with [Section 2.3.11.1](#23111-create-erregistry-entry) of this specification
* 3.1.24.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections

### 3.1.25 Conformance Clause 25: Delete Registry Entry Producer
An OpenC2 Producer satisfies 'Registry Entry Producer' conformance if:
* 3.1.25.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.25.2 **MUST** implement the 'delete rer:egistry_entry' Command in accordance with [Section 2.3.12.2](#23122-delete-erregistry-entry) of this specification
* 3.1.25.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections

### 3.1.26 Conformance Clause 26: Set Account Producer
An OpenC2 Producer satisfies 'Account Producer' conformance if:
* 3.1.26.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.26.2 **MUST** implement the 'set er:account' Command in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification
* 3.1.26.3 **MUST** implement the 'er:account_status' Command Argument in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification
* 3.1.26.4 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification

### 3.1.27 Conformance Clause 27: Account Status Producers
An OpenC2 Producer satisfies 'Account-Status Producers' conformance if:
* 3.1.27.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.27.2 **MUST** implement the 'er:account_status' Command Argument as a valid option for the 'set account' Command in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification

### 3.1.28 Conformance Clause 28: Stop Service Producer
An OpenC2 Producer satisfies 'Stop Service Producer' conformance if:
* 3.1.28.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.28.2 **MUST** implement the 'stop er:service' Command in accordance with [Section 2.3.7.3](#2373-stop-erservice) of this specification
* 3.1.28.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections

### 3.1.29 Conformance Clause 29: Delete Service Producer
An OpenC2 Producer satisfies 'Delete Service Producer' conformance if:
* 3.1.29.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.29.2 **MUST** implement the 'delete er:service' Command in accordance with [Section 2.3.12.3](#23123-delete-erservice) of this specification
* 3.1.29.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections

## 3.2 Clauses Pertaining to the OpenC2 Consumer Conformance Target
All OpenC2 Consumers that are conformant to this specification MUST satisfy Conformance Clause 12 and MAY satisfy one or more of Conformance Clauses 13 through 22.

### 3.2.1 Conformance Clause 30: Baseline OpenC2 Consumer
An OpenC2 Consumer satisfies Baseline OpenC2 Consumer conformance if:
* 3.2.1.1 **MUST** support JSON serialization of OpenC2 Commands that are syntactically valid in accordance with the property tables presented in [Section 2.1](#21-openc2-command-components)
* 3.2.1.2 All serializations **MUST** be implemented in a manner such that the serialization validates against and provides a one-to-one mapping to the property tables in [Section 2.1](#21-openc2-command-components) of this specification
* 3.2.1.3 **MUST** support the use of a Transfer Specification that is capable of delivering authenticated, ordered, lossless and uniquely identified OpenC2 messages
* 3.2.1.4 **SHOULD** support the use of one or more published OpenC2 Transfer Specifications which identify underlying transport protocols such that an authenticated, ordered, lossless, delivery of uniquely identified OpenC2 messages is provided as referenced in [Section 1](#1-introduction) of this specification
* 3.2.1.5 **MUST** be conformant with Version 1.0 of the OpenC2 Language Specification
* 3.2.1.6 **MUST** implement the 'query features' Command in accordance with the normative text provided in version 1.0 of the OpenC2 Language Specification
* 3.2.1.7 **MUST** implement the 'response_requested' Command Argument as a valid option for any Command
    * 3.2.1.7.1 All Commands received with a 'response_requested' argument set to 'none' **MUST** process the Command and **MUST NOT** send a Response. This criteria supersedes all other normative text as it pertains to Responses
    * 3.2.1.7.2 All Commands received without the 'response_requested' argument **MUST** process the Command and Response in a manner that is consistent with "response_requested":"complete"
* 3.2.1.8 **MAY** implement the 'er:downstream_device' Command Argument as a valid option for any Command not included in section [Section 3.1.2](#312-conformance-clause-2downstream-device-consumers)
* 3.2.1.8 **MUST** conform to at least one of the following conformance clauses in this specification:
    * Conformance Clause 36
    * Conformance Clause 38

### 3.2.2 Conformance Clause 31: Downstream Device Consumer
An OpenC2 Consumer satisfies 'Device-Containment Consumer' conformance if:
* 3.2.2.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* And if the Consumer implements the 'start file' command:
  * 3.2.2.2 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'start file' Command in accordance with [Section 2.3.6.1](#2361-start-file) of this specification
* And if the Consumer implements the 'contain file' command:
  * 3.2.2.3 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'contain file' Command in accordance with [Section 2.3.4.2](#2342-contain-file) of this specification
* And if the Consumer implements the 'set ipv4_net' command:
  * 3.2.2.4 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'set ipv4_net' Command in accordance with [Section 2.3.9.1](#2391-set-ipv4-net) of this specification
* And if the Consumer implements the 'set ipv6_net' command:
  * 3.2.2.5 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'set ipv6_net' Command in accordance with [Section 2.3.9.2](#2392-set-ipv6-net) of this specification
* And if the Consumer implements the 'stop process' command:
  * 3.2.2.6 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'stop process' Command in accordance with [Section 2.3.7.2](#2372-stop-process) of this specification
* And if the Consumer implements the 'set er:registry_entry' command:
  * 3.2.2.7 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'set er:registry_entry' Command in accordance with [Section 2.3.9.3](#2393-set-erregistry-entry)) of this specification
* And if the Consumer implements the 'create er:registry_entry' command:
  * 3.2.2.8 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'create er:registry_entry' Command in accordance with [Section 2.3.11.1](#23111-create-erregistry-entry) of this specification
* And if the Consumer implements the 'delete er:registry_entry' command:
  * 3.2.2.9 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'delete er:registry_entry' Command in accordance with [Section 2.3.12.2](#23122-delete-erregistry-entry) of this specification
* And if the Consumer implements the 'set er:account' command:
  * 3.2.2.10 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'set er:account' Command in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification
* And if the Consumer implements the 'stop er:service' command:
  * 3.2.2.11 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'stop er:service' Command in accordance with [Section 2.3.7.3](#2373-stop-erservice) of this specification
* And if the Consumer implements the 'delete er:service' command:
  * 3.2.2.12 **MUST** implement the 'er:downstream_device' Command Argument as a valid option for the 'delete er:service' Command in accordance with [Section 2.3.12.3](#23123-delete-erservice) of this specification

### 3.2.3 Conformance Clause 32: Domain Name Consumer
An OpenC2 Consumer satisfies 'Deny Domain Name Consumer' conformance if:
* 3.2.3.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.3.2 **MUST** implement the 'deny domain_name' Command in accordance with [Section 2.3.3.1](#2331-deny-domain-name) of this specification
* 3.2.3.3 **MUST** implement the 'allow domain_name' Command in accordance with [Section 2.3.5.1](#2351-allow-domain-name) of this specification

### 3.2.4 Conformance Clause 33: Scan Device Consumer
An OpenC2 Consumer satisfies 'Scan Device Consumer' conformance if:
* 3.2.4.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.4.2 **MUST** implement the 'scan device' Command in accordance with [Section 2.3.1.1](#2311-scan-device) of this specification

### 3.2.5 Conformance Clause 34: Scan Depth Consumer
An OpenC2 Consumer satisfies 'Scan Depth Consumer' conformance if:
* 3.2.5.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.5.2 **MUST** implement the 'er:scan_depth' Command Argument as a valid option for the 'scan device' Command in accordance with [Section 2.3.1.1](#2311-scan-device) of this specification

### 3.2.6 Conformance Clause 35: Periodic Scan Consumer
An OpenC2 Consumer satisfies 'Periodic Scan Consumer' conformance if:
* 3.2.6.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.6.2 **MUST** implement the 'er:periodic_scan' Command Argument as a valid option for the 'scan device' Command in accordance with [Section 2.3.1.1](#2311-scan-device) of this specification

### 3.2.7 Conformance Clause 36: Contain Device Consumer
An OpenC2 Consumer satisfies 'Contain Device Consumer' conformance if:
* 3.2.7.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.7.2 **MUST** implement the 'contain device' Command in accordance with [Section 2.3.4.1](#2341-contain-device) of this specification
* 3.2.7.3 **MUST** implement the 'er:device_containment' Command Argument in accordance with [Section 2.3.4.1](#2341-contain-device) of this specification
* 3.2.7.4 **MUST** implement the 'er:device_containment' Command Argument as a valid option for the 'contain device' Command in accordance with [Section 2.3.4.1](#2341-contain-device) of this specification

### 3.2.8 Conformance Clause 37: Permitted Addresses Consumer
An OpenC2 Consumer satisfies 'Permitted Addresses Consumer' conformance if:
* 3.2.8.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.8.2 **MUST** implement the 'er:permitted_addresses' Command Argument as a valid option for the 'contain device' Command in accordance with [Section 2.3.4.1](#2341-contain-device) of this specification

### 3.2.9 Conformance Clause 38: Allow Device Consumer
An OpenC2 Consumer satisfies 'Contain Device Consumer' conformance if:
* 3.2.9.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.9.2 **MUST** implement the 'allow device' Command in accordance with [Section 2.3.5.1](#2351-allow-device) of this specification

### 3.2.10 Conformance Clause 39: Stop Device Consumer
An OpenC2 Consumer satisfies 'Stop Device Consumer' conformance if:
* 3.2.10.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.10.2 **MUST** implement the 'stop device' Command in accordance with [Section 2.3.7.1](#2371-stop-device) of this specification

### 3.2.11 Conformance Clause 40: Restart Device Consumer
An OpenC2 Consumer satisfies 'Restart Device Consumer' conformance if:
* 3.2.11.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.11.2 **MUST** implement the 'restart device' Command in accordance with [Section 2.3.8.1](#2381-restart-device) of this specification

### 3.2.12 Conformance Clause 41: Deny File Consumer
An OpenC2 Consumer satisfies 'Deny File Consumer' conformance if:
* 3.2.12.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.12.2 **MUST** implement the 'deny file' Command in accordance with [Section 2.3.3.2](#2332-deny-file) of this specification

### 3.2.13 Conformance Clause 42: Contain File Consumer
An OpenC2 Consumer satisfies 'Contain File Consumer' conformance if:
* 3.2.13.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.13.2 **MUST** implement the 'contain file' Command in accordance with [Section 2.3.4.2](#2342-contain-file) of this specification
* 3.2.13.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.4.2](#2342-contain-file) of this specification

### 3.2.14 Conformance Clause 43: Allow File Consumer
An OpenC2 Consumer satisfies 'Allow File Consumer' conformance if:
* 3.2.14.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.14.2 **MUST** implement the 'allow file' Command in accordance with [Section 2.3.5.3](#2353-allow-file) of this specification
* 3.2.14.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.4.2](#2342-contain-file) of this specification

### 3.2.15 Conformance Clause 44: Start File Consumer
An OpenC2 Consumer satisfies 'Start File Consumer' conformance if:
* 3.2.15.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.15.2 **MUST** implement the 'start file' Command in accordance with [Section 2.3.6.1](#2361-start-file) of this specification
* 3.2.15.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.6.1](#2361-start-file) of this specification

### 3.2.16 Conformance Clause 45: Deny IPv4 Net Consumer
An OpenC2 Consumer satisfies 'Deny IPv4 Net Consumer' conformance if:
* 3.2.16.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification

### 3.2.17 Conformance Clause 46: Allow IPv4 Net Consumer
An OpenC2 Consumer satisfies 'Allow IPv4 Net Consumer' conformance if:
* 3.2.17.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification

### 3.2.18 Conformance Clause 47: Set IPv4 Net Consumer
An OpenC2 Consumer satisfies 'Set IPv4 Net Consumer' conformance if:
* 3.2.18.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.18.2 **MUST** implement the 'set ipv4_net' Command in accordance with [Section 2.3.9.1](#2391-set-ipv4-net) of this specification
* 3.2.18.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.9.1](#2391-set-ipv4-net) of this specification

### 3.2.19 Conformance Clause 48: Deny IPv6 Net Consumer
An OpenC2 Consumer satisfies 'Deny IPv6 Net Consumer' conformance if:
* **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification

### 3.2.20 Conformance Clause 49: Allow IPv6 Net Consumer
An OpenC2 Consumer satisfies 'Allow IPv6 Net Consumer' conformance if:
* **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification

### 3.2.21 Conformance Clause 50: Set IPv6 Net Consumer
An OpenC2 Consumer satisfies 'Set IPv6 Net Consumer' conformance if:
* 3.2.21.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.21.2 **MUST** implement the 'set ipv6_net' Command in accordance with [Section 2.3.9.2](#2392-set-ipv6-net) of this specification
* 3.2.21.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.9.2](#2392-set-ipv6-net) of this specification

### 3.2.22 Conformance Clause 51: Stop Process Consumer
An OpenC2 Consumer satisfies 'Process Consumer' conformance if:
* 3.2.22.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.22.2 **MUST** implement the 'stop process' Command in accordance with [Section 2.3.7.2](#2372-stop-process) of this specification
* 3.2.22.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.7.2](#2372-stop-process) of this specification

### 3.2.23 Conformance Clause 52: Set Registry Entry Consumer
An OpenC2 Consumer satisfies 'Registry Entry Consumer' conformance if:
* 3.2.23.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.23.2 **MUST** implement the 'set registry_entry' Command in accordance with [Section 2.3.9.3](#2393-set-erregistry-entry) of this specification
* 3.2.23.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections

### 3.2.24 Conformance Clause 53: Create Registry Entry Consumer
An OpenC2 Consumer satisfies 'Registry Entry Consumer' conformance if:
* 3.2.24.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.24.2 **MUST** implement the 'create er:registry_entry' Command in accordance with [Section 2.3.11.1](#23111-create-erregistry-entry) of this specification
* 3.2.24.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections

### 3.2.25 Conformance Clause 54: Delete Registry Entry Consumer
An OpenC2 Consumer satisfies 'Registry Entry Consumer' conformance if:
* 3.2.25.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.25.2 **MUST** implement the 'delete rer:egistry_entry' Command in accordance with [Section 2.3.12.2](#23122-delete-erregistry-entry) of this specification
* 3.2.25.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections

### 3.2.26 Conformance Clause 55: Set Account Consumer
An OpenC2 Consumer satisfies 'Account Consumer' conformance if:
* 3.2.26.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.26.2 **MUST** implement the 'set er:account' Command in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification
* 3.2.26.3 **MUST** implement the 'er:account_status' Command Argument in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification
* 3.2.26.4 **MUST** implement the 'er:downstream_device' Command Argument in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification

### 3.2.27 Conformance Clause 56: Account Status Consumers
An OpenC2 Consumer satisfies 'Account-Status Consumers' conformance if:
* 3.2.27.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.27.2 **MUST** implement the 'er:account_status' Command Argument as a valid option for the 'set account' Command in accordance with [Section 2.3.9.4](#2394-set-eraccount) of this specification

### 3.2.28 Conformance Clause 57: Stop Service Consumer
An OpenC2 Consumer satisfies 'Stop Service Consumer' conformance if:
* 3.2.28.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.28.2 **MUST** implement the 'stop er:service' Command in accordance with [Section 2.3.7.3](#2373-stop-erservice) of this specification
* 3.2.28.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections

### 3.2.29 Conformance Clause 58: Delete Service Consumer
An OpenC2 Consumer satisfies 'Delete Service Consumer' conformance if:
* 3.2.29.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.29.2 **MUST** implement the 'delete er:service' Command in accordance with [Section 2.3.12.3](#23123-delete-erservice) of this specification
* 3.2.29.3 **MUST** implement the 'er:downstream_device' Command Argument in accordance with the above sections


-------

# Appendix A. References

This appendix contains the normative and informative references that are used in this document. Normative references are specific (identified by date of publication and/or edition number or version number) and Informative references are either specific or non-specific.

While any hyperlinks included in this appendix were valid at the time of publication, OASIS cannot guarantee their long-term validity.

## A.1 Normative References

The following documents are referenced in such a way that some or all of their content constitutes requirements of this document.

###### [RFC1123]
Braden, R., Ed., "Requirements for Internet Hosts - Application and Support", STD 3, RFC 1123, DOI 10.17487/RFC1123, October 1989, <https://www.rfc-editor.org/info/rfc1123>.

###### [RFC2119]
Bradner, S., "Key words for use in RFCs to Indicate Requirement Levels", BCP 14, RFC 2119, DOI 10.17487/RFC2119, March 1997, <https://www.rfc-editor.org/info/rfc2119>.

###### [RFC8174]
Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174, May 2017, <https://www.rfc-editor.org/info/rfc8174>.

###### [OpenC2-Lang-v1.0]
_Open Command and Control (OpenC2) Language Specification Version 1.0_. Edited by Jason Romano and Duncan Sparrell. November 2018, <http://docs.oasis-open.org/openc2/oc2ls/v1.0/oc2ls-v1.0.html>.

###### [OpenC2-HTTPS-v1.0]
_Specification for Transfer of OpenC2 Messages via HTTPS Version 1.0_. Edited by David Lemire. Latest version: http://docs.oasis-open.org/openc2/open-impl-https/v1.0/open-impl-https-v1.0.html

###### [Winnt.h-registry-types]
_Registry Value Types_. Microsoft Windows documentation, <https://docs.microsoft.com/en-us/windows/win32/sysinfo/registry-value-types>

<!--
## A.2 Informative References

###### [RFC3552]
Rescorla, E. and B. Korver, "Guidelines for Writing RFC Text on Security Considerations", BCP 72, RFC 3552, DOI 10.17487/RFC3552, July 2003, https://www.rfc-editor.org/info/rfc3552.
-->

---
# Appendix B. Acknowledgments

Note: A Work Product approved by the TC must include a list of people who participated in the development of the Work Product. This is generally done by collecting the list of names in this appendix. This list shall be initially compiled by the Chair, and any Member of the TC may add or remove their names from the list by request. Remove this note before submitting for publication.

## B.1 Participants

<!-- A TC can determine who they list here, however, TC Observers must not be listed. It is common practice for TCs to list everyone that was part of the TC during the creation of the document, but this is ultimately a TC decision on who they want to list and not list. -->

The following individuals have participated in the creation of this specification and are gratefully acknowledged:

**OpenC2 TC Members:**

| First Name | Last Name  | Company                                     |
|:-----------|:-----------|:--------------------------------------------|
| Joe        | Brule      | National Security Agency                    |
| Alex       | Everett    | University of North Carolina at Chapel Hill |
| Martin     | Evandt     | University of Oslo                          |
| David      | Kemp       | National Security Agency                    |
| David      | Lemire     | G2                                          |
| Vasileios  | Mavroeidis | University of Oslo                          |
| Michael    | Rosa       | National Security Agency                    |
| Duncan     | Sparrell   | sFractal Consulting LLC                     |
| Russel     | Warren     | IBM                                         |

-------

# Appendix C. Revision History
| Revision | Date | Editor | Changes Made |
| :--- | :--- | :--- | :--- |
| er-ap-v1.0-wd01 | yyyy-mm-dd | Vasileios Mavroeidis, Martin Evandt | Initial working draft |

-------

# Appendix D: Sample Commands

_This section is non-normative_

This section will summarize and provide examples of OpenC2 Commands as they pertain to er systems. The sample Commands will be encoded in verbose JSON.

## A.1 deny, contain and allow

### A.1.1 Ban a binary by hash on every Endpoint

**Command:**

```json
{
  "action": "deny",
  "target": {
    "file": {
      "hashes": {
        "sha256": "0a73291ab5607aef7db23863cf8e72f55bcb3c273bb47f00edf011515aeb5894"
      }
    }
  },
  "actuator": {
    "er": {}
  }
}
```
**Responses:**

Case One: the Actuator successfully issued the deny.

```json
{
  "status": 200
}
```

Case Two: the Command failed due to a syntax error in the Command. Optional status text is ignored by the Producer, but may be added to provide error details for debugging or logging.

```json
{
  "status": 400,
  "status_text": "Validation Error: Target: flie"
}
```

Case Three: the Command failed because an Argument was not supported.

```json
{
  "status": 501
}
```

### A.1.2 Network isolate a specific Endpoint

**Command:**

```json
{
  "action": "contain",
  "target": {
    "device": {
      "hostname": "DESKTOP-123ABC"
    }
  },
  "args": {
    "er": {
      "device_containment":"network_isolation"
    }
   },
  "actuator": {
    "er": {}
  }
}

```

### A.1.X Network isolate an Endpoint, but allow communication with selected IP and domain name addresses

**Command:**

```json
{
  "action": "contain",
  "target": {
    "device": {
      "hostname": "DESKTOP-123ABC"
    }
  },
  "args": {
    "er": {
      "device_containment":"network_isolation",
      "permitted_addresses": {
        "ipv_net": ["192.168.0.255"],
        "domain_name": ["support.organization.tld", "wiki.organization.tld"]
      }
    }
   },
  "actuator": {
    "er": {}
  }
}
```

### A.1.3 Allow unrestricted app execution on a group of Endpoints

**Command:**

```json
{
  "action": "allow",
  "target": {
    "device": {
      "hostname": "DESKTOP-123ABC"
    }
  },
  "args": {
    "er": {
      "device_containment":"app_restriction"
    }
   },
  "actuator": {
    "er": {}
  }
}
```

## A.2 Set

### A.2.1 Set an account on a specific Endpoint to be enabled

**Command:**

```json
{
  "action": "set",
  "target": {
    "er": {
      "account": {
         "uid":"S-1-5-21-7375663-6890924511-1272660413-2944159"
      }
    }
  },
  "args": {
    "er": {
      "account_status":"enabled"
    }
   },
  "actuator": {
    "er": {
       "hostname": "edr-oslo"
    }
  }
}
```

### A.2.1 Set accounts on a group of Endpoints to be disabled

**Command:**

```json
{
  "action": "set",
  "target": {
    "er": {
      "account": {
        "account_name":"sql_admin"
      }
    }
  },
  "args": {
    "er": {
      "account_status":"disabled"
    }
   },
  "actuator": {
    "er": {}
  }
}
```

-------

# Appendix D. Notices

<!-- Required section. Do not modify. -->

Copyright © OASIS Open 2022. All Rights Reserved.

All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full [Policy](https://www.oasis-open.org/policies-guidelines/ipr/) may be found at the OASIS website.

This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restriction of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Technical Committee (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English.

The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns.

This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE.

As stated in the OASIS IPR Policy, the following three paragraphs in brackets apply to OASIS Standards Final Deliverable documents (Committee Specification, Candidate OASIS Standard, OASIS Standard, or Approved Errata).

\[OASIS requests that any OASIS Party or any other party that believes it has patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable, to notify OASIS TC Administrator and provide an indication of its willingness to grant patent licenses to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this deliverable.\]

\[OASIS invites any party to contact the OASIS TC Administrator if it is aware of a claim of ownership of any patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable by a patent holder that is not willing to provide a license to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this OASIS Standards Final Deliverable. OASIS may include such claims on its website, but disclaims any obligation to do so.\]

\[OASIS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this OASIS Standards Final Deliverable or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on OASIS' procedures with respect to rights in any document or deliverable produced by an OASIS Technical Committee can be found on the OASIS website. Copies of claims of rights made available for publication and any assurances of licenses to be made available, or the result of an attempt made to obtain a general license or permission for the use of such proprietary rights by implementers or users of this OASIS Standards Final Deliverable, can be obtained from the OASIS TC Administrator. OASIS makes no representation that any information or list of intellectual property rights will at any time be complete, or that any claims in such list are, in fact, Essential Claims.\]

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the owner and developer of this specification, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation and use of, specifications, while reserving the right to enforce its marks against misleading uses. Please see https://www.oasis-open.org/policies-guidelines/trademark/ for above guidance.
