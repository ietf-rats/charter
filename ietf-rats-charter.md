# Introduction

Remote attestation procedures (RATS) establish trust in the trustworthiness of devices and services. There is high demand for network protocols that not only provide strong authentication but also trusted assertions about the communication partner. To improve the confidence in a communication partner's trustworthiness a relying party requires trusted claims or specific evidence about:

* device identity,
* device composition, including sub-modules and roots of trust,
* claim origination/provenance,
* manufacturing origin,
* system integrity,
* configuration, or
* operational state and measurements of steps which led to the operational state.

In the absence of such procedures, while domain-specific attestation mechanisms such as TCG TPM/TSS, FIDO Alliance attestation and Android Keystore attestation exist, there is no common way for a relying party to tell if data originates from a trustworthy device (e.g. a Trusted System designed to support a specific set of operations/functionalities and to operate only as intended) or not.

# High Level Goals of the Working Group

Establishing trust in the assertions originating from devices and services or other trusted third parties is a vital prerequisite for remote attestation procedures. Establishing trust relationships suitable for RATS via roots of trust [NIST SP 800-164 draft 2012] or trust anchors [I-D.ietf-teep-architecture] provided by remote entities is a goal of the RATS WG. Correspondingly, the RATS WG will facilitate full device attestation, such as the assessment of system health via remote integrity verification, based on these trust relationships.

The Working Group will define:

1. Standardized and interoperable mechanisms to establish a sufficient level of confidence that data originates from trustworthy systems designed to support a specific set of operations/functionalities.

2. Standardized and interoperable mechanisms building on (1.) to allow relying parties to know the attestation provenance and characteristics with respect to systems from which it may request services, consume information or to which a relying party may provide information.

The Working Group will maintain close relationships with bodies undertaking complementary work streams in the area of remote attestation, such as GlobalPlatform, Trusted Computing Group, and FIDO Alliance.

The Working Group will cooperate with the TEEP Working Group, which may generate requirements for claims relevant to TEE.

# Program of Work

The Working Group will develop standards supporting the creation of interoperable remote attestation procedures for systems and entities which incorporate roots of trust. The main deliverables are as follows.

1. Specify an architecture establishing a common terminology for remote attestation, identifying mechanisms which will be supported for establishing trust relationships between a system and a remote party, and enumerating sample use-cases for remote attestation.

2. Specify interoperable cross-platform claims which provide information about systems and entities in support of the required use-cases, and extending the set of claims defined in RFC7519 and RFC8392. The specification will describe the syntax for each claim in at least the following formats:

* CBOR [RFC7049]
* JSON [RFC7159]

using modeling languages, such as:

* YANG [RFC6020]
* CDDL [I-D.ietf-cbor-cddl]

while retaining interoperability with existing formats based on ASN.1, where claim semantics are the same (or have sufficient semantic similarity that warrants semantic interoperability).

while retaining interoperability with existing formats based on ASN.1, if possible and feasible.

3. Specify interoperable mechanisms to protect claims which may need to be protected from unauthorised disclosure for privacy and/or security reasons (e.g. via a root of trust of storage).

4. Specify procedures, protocols, and corresponding claim semantics in support of verification services to validate or appraise claims via reference values within a remote attestation based on measured file execution procedures; supporting:

* Explicit attestation wherein a set of verifiable claims is transported in the attestation, and
* Implicit attestation wherein a set of claims is implied by possession of a secret.

5. Specify procedures and corresponding service graphs supporting the verification of claims encapsulated in:

* CBOR Web Token structures [RFC8392]
* JSON Web Token structures [RFC7519]

6. Perform privacy analysis of both claims and the cryptographic procedures used to establish trust. This information will be included as appropriate in the deliverable specifications, and may imply extension of procedures defined in other deliverables in support of privacy goals.
