# Chairs
TBD

# Area and Area Director(s)
Security

# Responsible Area Director:
Benjamin Kaduk

# Mailing List:
rats@ietf.org

# Description of working group

## (Introduction)

Traditional uses of asymmetric cryptography introduce proof-of-possession techniques that prove to the verifier that the authenticator possesses the private key. Authentication presumes some protection: e.g., that there is not an illicit copy of the private key available to anyone other than the intended subject. More generally, authentication of a system is not useful if it can readily be taken over by an attacker. Proof-of-possession techniques do not describe mechanisms for ascertaining the protection of the system and its integrity, and for conveying evidence about that (“proof-of-protection” henceforth). 

The details of these mechanisms vary between implementations, including what kinds of trust are being generated and what entities need to cooperate to create and verify this proof-of-protection. They, however, all need network protocols to interconnect the entities that need to work together.  The RATS effort strives to provide evidence about a system's health and trustworthiness via the Internet.  Instead of having a separate set of protocols for each set of mechanisms, the RATS effort will define a common set of protocols that can be used interoperably over the Internet.

## (Background)

Attestation provides a mechanism where an *Attester* supplies a trustworthy assertion of a system’s characteristics such as its hardware identity, boot time firmware identity, compliance status or run-time status to a Verifier.
This allows the *Verifier* (or other parties relying on the *Verifier*) to consider a system's trust properties and to better manage risk. Trust properties are defined by Reference Values that relate to a security policy, privacy policy, or other critical infrastructure interest.

In essence, a trusted system is one that operates as expected, according to its design and operational policies, doing what is required - and not doing other things.
Correspondingly, Remote Attestation Procedures enable dynamic periodic appraisals of a system to determine, convincingly, its trustworthiness status.

Attestation has two fundamental ways of operating, Remote Attestation and Local Attestation.
* *Remote Attestation* is where the Attester conveys Attestation Evidence to a Verifier that compares it with Reference Values (in order for it to be considered, for example, healthy)
A Relying Party (or the Verifier acting as a Relying Party) appraises the verification result to assess device trustworthiness and to manage security risk.
The Verifier is typically physically remote from the Attester and the conveyance method often involves a network protocol.
* *Local Attestation* is where trustworthiness is determined locally on the device. For example, access to application configuration files may be predicated on the correct operating system having been booted.
Local Attestation may not rely on an external conveyance method to determine trustworthiness.
Nevertheless, a remote Relying Party (or trusted third party) may be responsible for supplying attestation policies that are applied locally.

In scope are two types of attestation: Explicit Attestation and Implicit Attestation:
* *Explicit Attestation* is where the Attestation Claims/Evidence is conveyed authentically (e.g. signed) by the Attester to the Verifier where a root-of-trust enumerates the Attestation Claims/Evidence associated with an execution environment.
* *Implicit Attestation* is where the Attester conveys evidence of the availability of an authenticating credential that allows the Verifier to infer the Attestation Claims/Evidence associated with an execution environment.
The Verifier knows that the availability of the authenticating credential is bound to certain Attestation Claims/Evidence. Inferred knowledge may further be conveyed as Attestation Evidence by a Trusted Third Party via a credential certificate or other out-of-band method.

Remote Attestation Procedures have multiple facets, including but not limited to:
* A cryptographic identity that is bound to an execution environment consisting of some combination of hardware, firmware, OS, applications and other components.
* A conveyance method to present Attestation Evidence about an execution environment in a standard format.
* A method to protect Attestation Evidence during storage and conveyance, as well as to prove its integrity and freshness.

Attestation is scoped from small, resource-constrained devices to less constrained devices such as servers, rackscale systems, or services in a cloud.
Both types of attestation may be used by any system, though it is assumed likely that more constrained systems that are a relying party are less likely to also take on the role of a Verifier (and therefore are "off-loading the burden of appraisal").
Use of both Explicit and Implicit Attestation mechanisms together may also be done.

Generally speaking, attestation is applied before data is exchanged to avoid disclosure to insufficiently trusted environments.

## (Terminology for this charter)

The terminology used for Attestation in various industry groups and SDOs is not always consistent. So that this charter can have a well-defined meaning, it is necessary to supply some definitions.
(This set of terms will then be refined in the terminology document discussed below, with the expectation that the refined terms are consistent with the brief definitions here.)

* Assertion: Defined by the ITU in X.1252 as "a statement made by an entity without accompanying evidence of its validity".
* Attestation Claim: Information about some characteristics or attributes that affect device trustworthiness.
* Attestation Evidence: Proof for one or more Attestation Claims (characteristics, attributes, ...) that affect device trustworthiness, such as its hardware identity, firmware, software, configuration or composition, compliance status and runtime state.
Attestation Evidence may be consolidated through the use of cryptographic hash and key generation algorithms.
Attestation Evidence veracity may be augmented by Claimant signatures over portions of the Attestation Evidence.
Note that Claims are non-proven assertions as opposed to Attestation Evidence.
* Attester: An endpoint that has a root-of-trust for reporting (RTR) and implements a conveyance protocol, authenticates using an Attestation credential, collects Attestation Evidence about itself and presents it to a consumer of evidence (e.g. a Relying Party or a Verifier).
* Claimant: An entity that make an assertion to a certain property regarding the trustworthiness of an entity. This may be the binding of an Attester to an RTR or any other kind of property.
* Conveyance: The transfer of Attestation Evidence between Attester and Verifier, facilitated by network protocols that are reliable, secure and can prove the freshness of Evidence, if required.
* Reference Values: Information that can be matched with collected Attestation Evidence to determine if the device's operational state complies with an intended/expected operational state (e.g. Reference Integrity Measurements).
* Relying party: An entity that consumes and assesses Verifier results for the purpose of improved risk management, operational efficiency, security, privacy (natural or legal person) or safety. The Verifier and Relying Party functions may be tightly integrated.
* Remote Attestation: The procedure of supplying Attestation Evidence to a communication partner via an Attester using network protocols for Conveyance.
* Root of Trust: The base entity for a chain of trusts that builds up trust in an overall system.
* Verifier: An endpoint that has a root-of-trust for verification and implements a conveyance protocol, verifies Attestation credentials and may authenticate using Attestation Evidence or other credentials, appraises Attestation Evidence against Reference Values or policies and makes verification results available to Relying Parties.

## (Problem statement)

The problem statement addressed by the working group can be segregated into four inter-connected problems:

(1) Establishing a sufficient level of confidence that a communication partner is a trustworthy endpoint. This is a fundamental challenge.
Currently, there are no agreed upon standards that define a minimal set of Reference Values and Attestation Evidence that distinguishes a trustworthy execution environment over one that isn't. There isn't agreement on how to convey it appropriately, how to appraise evidence and how to present the appraisal results in an interoperable fashion.
In essence, there is increasing vendor demand for an overall communication, trust and assurance model to establish trust in potentially lying endpoints that is not currently met by other standards.

(2) Current and emerging protocols oftentimes do not contain interfaces for trust establishment in the communication endpoints.
Some protocols may contain extensibility features that could serve this purpose, but have not yet been defined.

(3) There is no central alignment process or place for resolving issues related to the application of remote attestation techniques to existing and emerging IETF protocols, e.g. Initial Implicit Attestation via TLS Token Binding, complementary Attestation in OSCORE, YANG modules for conveying Explicit Attestation Evidence about composite devices (e.g. I-D.birkholz-yang-basic-remote-attestation), the Attestation procedures for virtualized network security functions in I2NSF (I-D.pastor-i2nsf-nsf-remote-attestation), or Time-Based Uni-Directional Attestation procedures (e.g. I-D.birkholz-i2nsf-tuda).

(4) The lack of generic models and commonly understood terminology that would allow for semantic interoperability and a common understanding of trustworthiness inhibits the establishment of trust between endpoints of heterogeneous realms and limits application-specific protocols and solutions to specifically scoped domains.
This includes the lack of:
* a taxonomy of information elements that can be used as Attestation Evidence, e.g. EAT/CWT claims,
* a way to consolidate and agree upon what a claim is and means, as well as allocate tokens under the token name space in an orderly manner, and
* leveraging or incorporating existing semantics and namespaces, e.g. YANG identifiers.

## (Program of work)

This working group will consolidate the various methods for creating and conveying Attestation Evidence using network protocols created in the IETF, to enable semantic interoperability.
This group will also establish and maintain close relationships to the IETF I2NSF WG, Global Platform, the Trusted Computing Group, the Cloud Native Computing Foundation, the Open Connectivity Foundation, the Alliance for Telecommunications Industry Solutions, and the ETSI NFV Industry Specification Group.

The following is within this working group's scope:
* Architectural components, such as roles, relationships, work-flows and actions
* Data formats and protocols for Remote, Explicit, and Implicit Attestation
* Protocols and new bindings of protocols (e.g. CoAP) to supply Attestation Policies to a Verifier or Relying Party
* Terminology and the interconnected relationships of existing solutions (also as a basis for identifying gaps and new applications)
* Attestation procedures for authentication that are based on the operational state of the Attester

The following is outside this working group's scope:
* Local Attestation and corresponding "in-box" APIs.
* Attestation Policy Formats
* Authentication procedure extension that do not convey Attestation Evidence.

As Attestation has acquired many definitions, an early goal for this working group will be a document defining the terms used by attestation, coordinating terminology with the groups and organizations listed above.
This provides the various standards a consistent set of terms for their subjects, objects and their relationships.

# Goals

## Architectural Documents (informational):
* (1.1) Terminology & Architecture
* (1.2) Reference Interaction Models

##  Solution Documents (standards-track):
* (1.3) Claim Taxonomy for Semantic Interoperability
* (2.1) YANG Module for Explicit Attestation
* (2.2) Explicit Attestation Extension to the I2NSF Architecture using EAT
* (2.3) Time-Based Uni-Directional Attestation

# Milestones
* IETF 104+6weeks (2.1) mostly complete \[✔], WG consensus
* (2.1) submitted to IESG
* IETF 105+6weeks (1.1, 1.2) mostly complete, WG consensus
* (1.1, 1.2) submitted to IESG
* IETF 105+6weeks (2.2) mostly complete, WG consensus
* (2.2) submitted to IESG
* IETF 105+6weeks (2.3) mostly complete, WG consensus \[½✔]
* (2.3) submitted to IESG
* IETF 106+6weeks (1.3) mostly complete, WG consensus
* (1.3) submitted to IESG

<!--  LocalWords:  Attester Verifier runtime rackscale NFV verifier
 -->
<!--  LocalWords:  authenticator SDOs virtualized namespaces RTR TUDA
 -->
<!--  LocalWords:  OSCORE APIs interoperably
 -->
