# Introduction

Relying parties require evidence about the trustworthiness of remote system components [RFC4949] they interact with. Remote attestation (RATS) procedures enable relying parties to establish a level of confidence in the trustworthiness of remote system components by creating and processing attestation evidence. Based on the provided evidence, a relying party can decide whether to consider a remote system component trustworthy or not.

To improve the confidence in a system component's trustworthiness a relying party may require evidence about:

* system component identity,
* composition of system components, including nested components,
* roots of trust,
* assertion/claim origination or provenance,
* manufacturing origin,
* system component integrity,
* system component configuration, or
* operational state and measurements of steps which led to the operational state.

# Scope and Problem Statement

The RATS model assumes there are system components (e.g., a device, or a device's sub-components) that are relied upon by relying parties to operate in an intended way and/or have intended characteristics.

The problem addressed by the working group is that there is no common way to create and process attestation evidence in a meaningful and believable manner while also supporting relying parties of different manufactures and origin. The challenge is to create syntactic and semantic interoperability to foster a spectrum of attestation ecosystems with respect to:

* evidence about characteristics and behaviour,
* workflows that enable the assessment of trustworthiness, and
* system components that take on corresponding remote attestation procedure roles in these workflows.

If each ecosystem defines its own procedures and evidence definitions, remote attestation for each use-case is likely to be less well-designed, leading to less accumulation and pooling of security expertise. These procedures include:

* Explicit attestation wherein a set of verifiable assertion/claims is transported in the attestation, and
* Implicit attestation wherein a set of claims is implied by possession of a secret.

In the absence of such interoperable procedures and specifications, while domain-specific attestation mechanisms such as TCG TPM/TSS, FIDO Alliance attestation and Android Keystore attestation exist, there is no common way for a relying party to acquire evidence to make determinations about the system component.

# Goals

Establishing trust in the assertions originating from system components is a vital prerequisite for remote attestation procedures. In consequence, the first goal of this working group is to provide evidence of validity of these assertions via roots of trust [NIST SP 800-164 draft 2012] that support attestation-related operation primitives. The second goal is to create a model that enables remote attestation procedures via trusted third parties, such as repositories of trusted secrets, and full device attestation, such as the assessment of system health via remote integrity verification.

Both evidence and the cryptographic procedures used to establish trust require privacy analysis. This information will be included as appropriate in the deliverable specifications, and may imply extension of procedures defined in other deliverables in support of privacy goals.

The working group will cooperate with the TEEP Working Group, which may generate requirements for assertions/claims relevant to TEE.

# Program of Work

The working group will develop standards supporting interoperable remote attestation procedures for system components that incorporate roots of trust. The main deliverables are as follows.

1. Specify an architecture establishing a common terminology for remote attestation, identifying mechanisms how to form trust relationships between system components and the relying parties via trusted introduction, and enumerating use-cases for remote attestation.

2. Specify information model for assertions/claims which provide information about system components characteristics scoped by the specified use-cases. 

3. Specify data models that implement the defined information model in formats, such as:

* CBOR Web Token structures [RFC8392]
* JSON Web Token structures [RFC7519]

4. Specify interoperable mechanisms to protect assertions/claims which may need to be protected from unauthorised disclosure (e.g. via a root of trust for storage) for privacy and/or security reasons, and for authenticity and integrity.

5. Specify procedures and network protocols to convey assertions/claims.

6. Specify procedures and network protocols to appraise attestation evidence via reference values.
