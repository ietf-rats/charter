# Introduction

Remote ATtestation ProcedureS (RATS) are included in network protocols to provide the basis for establishing trustworthy exchanges with a device.
RATS expose device characteristics in the form of trusted claim sets (based on Proof-of-Possession) to detailed Attestation Evidence (Proof-of-Protection) that enable a Verifying Parties to retrace every step that led to its current Operational State. A consequence of this retracing is that it is possible to appraise the trustworthiness of a device.
RATS provide evidence that a device supports a certain set of operations and functions nd/or that it is actually the exact device it is supposed to be (Attestation Provenance) via identity documents or passes.
RATS ensure that the information conveyed is unique, complete, and fresh (exposing tampering, replay, and/or relay attacks).
Application of RATS encompasses infrastructure supporting financial transactions, critical infrastructure, constrained-node environments, or the management of end-user devices.

Measured file execution procedures provide the basis for conveying additional device characteristics that enable a Verifying Party to assess that a device is a Trusted System: one that operates as expected, does what is required, and does not do other things.
Various Roots of Trust (e.g. for Measurement, for Reporting, or for Verification) provide the foundation to enable Implicit Remote Attestation (the fact that a secret key is accessible implies specific meaning and specific assertions are optional) and Explicit Remote Attestation, which uses the output of measured file execution as Attestation Evidence which can be used (along with event log details) to ratify that the device is actually a Trusted System.

RATS also incorporate Verifying Parties that are capable of explicit appraisal of the Attestation Evidence conveyed - in contrast to the implicit validation of device characteristics enabled by Relying Parties.
In order to do so, Reference Values - typically provided by Trusted Third Parties - are required.
If an Operational State is the result of an indeterministic file execution procedure, secure audit logs (e.g. a canonical event logs) of recent or past events have to be conveyed securely alongside Attestation Evidence to enable an appropriate appraisal.
Appraisal of Attestation Evidence also requires semantic context about explicit verification rules (local or remote) in order to establish a sufficient level of confidence in the trustworthiness of an attesting device (Attester).

# Problem Statement

(1) In 2018, there exists no standardized way to establish a sufficient level of confidence that some data originates from a trustworthy device (e.g., platforms, servers, user endpoints, IoT devices, device subsystems or subcomponents) designed to support a specific set of operations/functionalities a communication partner is a trustworthy endpoint. This is a fundamental challenge.

(1a) In 2018, there were no agreed upon standards that define a minimal set of Reference Values and Attestation Evidence that distinguishes a trustworthy computing context (e.g. execution environments or a specific set of operations/functions supported) over one that is not.

(1b) There is no general agreement on how to convey these appropriately, how to appraise the evidence and how to present the appraisal results in an interoperable fashion. In essence, there is increasing demand for an overall communication, trust and assurance model to establish trust in potentially lying endpoints that is not currently met by other standards.

(2) In 2018, there are no common, standard ways for Relying Parties to know the provenance and characteristics of a device (e.g., an end-user device, platform or endpoint, servers, IoT devices, device subsystems and sub-modules) that may be requesting services.

As a result, in 2018, a Relying Party would be unable to tell if an unknown device is trying to mimic the identity of another device or some of its characteristics.

In 2018, there are existing domain-specific ways to do this, such as TCG TPM Attestation, FIDO Alliance attestation and Android Keystore Attestation.

(3) Risk engines collect large amounts of information from a device in order to determine whether it is allowed access to data, a network, a financial transaction or to perform other risk-sensitive operations.  Such systems can require observations and
data collection over a period of time in order to form a profile of the device, which leads to a "cold start"
problem.  Therefore even risk engines would benefit from an interoperable explicit attestation solution.

Agreement over the syntax and semantics of provenance and characteristics is essential for interoperability.
Attestation provenance and characteristics represented via trusted claim sets or Attestation Evidence require proper definitions as Assertions. Standardized assertions promote increased - possibly ubiquitous - interoperability. Assertions also must be believable, for example, via Evidence that proves assertion veracity.

# Goals

In summary, the goals addressed by the RATS working group are:

1. Definition of inter-operable, cross-platform Assertions based on an unified terminology such that they can be asserted by Entities and substantiated with Attestation Evidence

2. Syntax for each Assertion in CBOR, JSON, YANG, and potentially others. 

3. A framework for the construction of Evidence (e.g. embedded asymmetric key pair), associating Evidence with Assertions (e.g. signing) and for conveying Evidence and Assertions to Relying Parties, Validators, or Verifiers
  * A definition of the Assertions independent of the means of Conveyance (e.g., independent of the transfer protocol)
  * A definition of Assertions independent of how Evidence is constructed. That is, it should be possible to use a variety of Evidence of an Assertion without affecting Assertion semantics

4. Creating generally applicable Assertions, Evidence and Conveyance mechanisms: inter-operable and neutral with respect to the type of attestation mechanisms embedded in a Device along with the comminications protocols supported by the device and
Relying Party. (e.g., minimally tied to trusted keystore, TPM, Trusted Execution Environments, JavaCard, etc.)

5. Privacy and regulatory compliance with respect to Assertions: definition of ‘privacy by design’ principles for Assertions

# Deliverables

1. RATS consolidated terminology and corresponding taxonomies (to be developed in parallel with solution documents; can be separate document or merged with 2 below, intended to be published last)

2. RATS information flow templates and corresponding architecture (to be developed in parallel with solution documents; can be separate document or merged with 1 above, intended to be published last)

3. Privacy Analysis (similar to 1, separate and/or included in the solution documents below)

4. Information elements for use in evidence-based attestation; serialization in CBOR and JSON; including YANG-based modules

5. CWT claim definitions for use in pass-based attestation tokens (e.g. EAT) to enable Attester and Verifier duties.

6. JWT claim definitions that correspond with the CWT claim definitions, for use in frameworks such as OAuth.

7. Time-based Unidirectional Attestation: interaction models, information elements, YANG modules.
