Introduction
============

In network protocol exchanges, it is often the case that one entity (a relying
party) requires evidence about the remote peer (and system components [RFC4949]
thereof), in order to assess the trustworthiness of the peer.  Remote
attestation procedures (RATS) enable relying parties to establish a level of
confidence in the trustworthiness of remote system components through the
creation of attestation evidence by remote system components and a processing
chain towards the relying party.  A relying party can then decide whether to
consider a remote system component trustworthy or not.

To improve the confidence in a system component's trustworthiness, a relying
party may require evidence about:
* system component identity,
* composition of system components, including nested components,
* roots of trust,
* assertion/claim origination or provenance,
* manufacturing origin,
* system component integrity,
* system component configuration,
* operational state and measurements of steps which led to the operational state, or
* other factors that could influence trust decisions.

While domain-specific attestation mechanisms such as Trusted Computing Group
(TCG) Trusted Platform Module (TPM)/Trusted Software Stack (TSS), Fast Identity
Online (FIDO) Alliance attestation, and Android Keystore attestation exist,
there is no interoperable way to create and process attestation evidence to
make determinations about system components among relying parties of different
manufactures and origins. 

Goals
=====

This WG will standardize formats for describing assertions/claims about system
components and associated evidence; and procedures and protocols to convey
these assertions/claims to relying parties.  Given the security and privacy
sensitive nature of these assertions/claims, the WG will specify approaches to
protect this exchanged data.  While a relying party may use reference, known, or
expected values or thresholds to assess the assertions/claims, the procedures
for this activity are out of scope for this WG (without rechartering).

The working group will cooperate and coordinate with other IETF WGs such as
TEEP, SUIT, and SACM, and work with organizations in the community, such as the TCG
and the FIDO Alliance, as appropriate.  The WG will also evaluate prior work
such as NEA and proprietary attestation technologies like the Android Keystore.

Program of Work
===============

The working group will develop standards supporting interoperable remote
attestation procedures for system components. The main deliverables are as
follows:

1. Specify use cases for remote attestation (to document and achieve WG
consensus but not expected to be published as an RFC).

2. Specify terminology and architecture that enable attestation techniques.
The architecture may include a system security model for the signing key
material and involve at least the system component, system component provider,
and the relying authority.

3. Standardize an information model for assertions/claims which provide
information about system components characteristics scoped by the specified
use-cases.

4. Standardize data models that implement and secure the defined information
model (e.g., CBOR Web Token structures [RFC8392], JSON Web Token structures
[RFC7519]).

5. Standardize interoperable protocols to securely convey assertions/claims.
