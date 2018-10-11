# Introduction

Remote ATtestation ProcedureS (RATS) are included in network protocols to provide the basis for establishing trustworthy exchanges with a device.
A certain set of Information Elements (IE) - representing device characteristics - has to be conveyed appropriately in order to enable a reliable level of confidence that specific claims from the device may be trusted. Additionally, specific protocol/procedure work-flows have to ensure that the origin of data (Attestation Provenance) is actually the device it is supposed to be and that the information conveyed is unique, complete, and fresh (exposing tampering, replay, and/or relay attacks).
Hence, all RATS are based on secure and resilient methods to identify the device that is providing the IE to be appraised and verified (Attestation Evidence).

The most prominent representation of IE are Claims - a concept introduced in RFC 7519. Claims are per-determined types of IE that can be used to represent Attestation Evidence. Attested Authentication conveys signed claim sets that are intended to be trusted due to key availability (Proof-of-Possession). Establishment in the trustworthiness in a communication partner can be achieved by the exposition of restricted secrets that can only be accessed if certain device characteristics are met (Proof-of-Protection).

Measured file execution procedures (including the now deprecated term Secure Boot) provide the basis for conveying additional device characteristics that enable a Verifying Party to assess that a device is a Trusted System: one that operates as expected, does what is required, and does not do other things. Various Roots of Trust (e.g. for Measurement, for Reporting, or for Verification) provide the foundation to enable Implicit Attestation (the fact that a secret key is accessible implies specific meaning) and Explicit Attestation, which uses the output of Measured file execution as Attestation Evidence which along with event Log details can be used to can ratify that the device is actually a Trusted System.

In summary, RATS expose trusted claim sets to detailed Attestation Evidence that enables a Verifying Party to retrace every step that led to its current Operational State. A consequence of this retracing is that it is possible to appraise the  trustworthiness of a device. Application of RATS encompasses infrastructure supporting financial transactions, critical infrastructure, constrained-node environments, or the management of end-user devices.

# Problem Statement

(1) Establishing a sufficient level of confidence that a communication partner is a trustworthy endpoint. This is a fundamental challenge.
Currently, there are no agreed upon standards that define a minimal set of Reference Values and Attestation Evidence that distinguishes a trustworthy execution environment over one that isn't. There isn't agreement on how to convey it appropriately, how to appraise evidence and how to present the appraisal results in an interoperable fashion. In essence, there is increasing demand for an overall communication, trust and assurance model to establish trust in potentially lying endpoints that is not currently met by other standards.

(2) Today, there is no common, standard way for Relying Parties to know the provenance and characteristics of a device (e.g., an end-user device, platform or endpoint, servers, IoT devices, device subsystems and sub-modules) that may be requesting services. For example, there is no common, standard, secure way for Relying Parties to tell if a device is trying to mimic the identity of (or passes created by) another device or some of its characteristics. In the context of performing a financial transaction, different platforms may have specific, security relevant characteristics that help the Relying Party offset transaction risk. There are existing domain-specific ways to do this, such as TCG TPM Attestation, FIDO Alliance attestation and Android Keystore Attestation.

Risk engines collect large amounts of information from a device in order to determine whether it is allowed access to data, a financial transaction or to perform other risk-sensitive operations. Agreement over the syntax and semantics of provenance and characteristics is essential for interoperability. Attestation provenance and characteristics represented via IE require proper definitions as Assertions. Standardized assertions promote increased - possibly ubiquitous - interoperability. Assertions also must be believable, for example, via Evidence that proves Assertion veracity.

# Goals

In summary, the goals addressed by the RATS working group are:

1. Definition of inter-operable, cross-platform Assertions based on an unified terminology such that they can be asserted by Entities and substantiated with Attestation Evidence

2. Syntax for each Assertion in CBOR, JSON, YANG, and potentially others \[reintroduce terminology here? TARGET 2 @everyone, please chime in here}

3. A framework for the construction of Evidence (e.g. embedded asymmetric key pair), associating Evidence with Assertions (e.g. signing) and for conveying Evidence and Assertions to Relying Parties, Validators, or Verifiers
  * A definition of the Assertions independent of the means of Conveyance (e.g., independent of the transfer protocol)
  * A definition of Assertions independent of how Evidence is constructed. That is, it should be possible to use a variety of Evidence of an Assertion without affecting Assertion semantics

4. Creating generally applicable Assertions, Evidence and Conveyance mechanisms: inter-operable and neutral with respect to the type of attestation mechanisms embedded in a Device. (e.g., minimally tied to trusted keystore, TPM, Trusted Execution Environments, JavaCard, etc.)

5. Privacy and GDPR compliance with respect to Assertions: definition of ‘privacy by design’ principles for Assertions

# Deliverables

1. Attestation information flows, consolidated terminology and corresponding taxonomies (overview/architecture to be developed in parallel with solution documents; can be separate document or go into 2, 3, 4 below)

2. Privacy Analysis (similar to 1, separate and/or included in the solution documents)

3. Information elements for use in evidence-based attestation; serialization in CBOR and JSON; including YANG-based modules

4. CWT claim definitions for use in pass-based attestation tokens (EAT)

5. Time-based Unidirectional Attestation: interaction models, information elements, YANG modules.
