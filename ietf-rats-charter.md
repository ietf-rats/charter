Introduction
============

In network protocol exchanges, it is often the case that one entity (a Relying
Party) requires evidence about the remote peer (and system components [RFC4949]
thereof), in order to assess the trustworthiness of the peer.  Remote
attestation procedures (RATS) determine whether relying parties can establish a level of
confidence in the trustworthiness of remote peers, called Attesters. 
The objective is achieved by a two-stage appraisal procedure facilitated by a trusted third
party, called Verifier, with trusted links to the supply chain.

The procedures for the two stages are:

* Evidence Appraisal: a Verifier applies policy and supply chain input, such as
Endorsements and References Values, to create Attestation Results from Evidence.
* Attestation Results Appraisal: a Relying Party applies policy to Attestation
Results associated with an Attester's Evidence that originates from a trusted Verifier.
The results are trust decisions regarding the Attester.

To improve the confidence in a system component's trustworthiness, a relying
party may require evidence about:
* system component identity,
* composition of system components, including nested components,
* roots of trust,
* an assertion/claim origination or provenance,
* manufacturing origin,
* system component integrity,
* system component configuration,
* operational state and measurements of steps which led to the operational state, or
* other factors that could influence trust decisions.

While domain-specific attestation mechanisms such as Trusted Computing Group
(TCG) Trusted Platform Module (TPM)/TPM Software Stack (TSS), Fast Identity
Online (FIDO) Alliance attestation, and Android Keystore attestation exist,
there is no interoperable way to create and process attestation evidence to
make determinations about system components among relying parties of different
manufactures and origins. 

Goals
=====

The WG has defined an architecture (draft-ietf-rats-architecture) for remote attestation.
The WG will standardize formats for describing evidence and attestation results
and the associated procedures and protocols to convey evidence for appraisal
to a verifier and attestation results to a relying party.
Additionally, the WG will standardize formats for endorsements and reference values,
and may apply and/or profile existing protocols (e.g., DTLS, CoAP, or MUD) to convey them
to the verifier. Formats and protocols for appraisal policy for evidence and appraisal
policy for attestation results are out of scope.

The WG will continue to cooperate and coordinate with other IETF WGs such as
TEEP and SUIT, and work with organizations in the community, such as the TCG,
Global Platform, and the FIDO Alliance, as appropriate.

Program of Work
===============

The working group will develop standards supporting interoperable remote
attestation procedures for system components. The main deliverables are as
follows:

1. Specify use cases for remote attestation (to document and achieve WG
consensus but not expected to be published as an RFC).

2. Specify terminology and architecture that enable attestation techniques.

3. Standardize an information model for evidence and attestations results scoped by the
specified use-cases.

4. Standardize data models that implement and secure the defined information
model (e.g., CBOR Web Token structures [RFC8392], JSON Web Token structures
[RFC7519]).

5. Standardize interoperable protocols to securely convey evidence and attestation results 
with a strong preference to use existing protocols.

6. Standardize interoperable data formats to securely declare and convey endorsements
and reference values.
