---
title: "An EAT Profile for Device Attestation"
abbrev: "EAT DA"
category: info

docname: draft-poirier-rats-eat-da-latest
submissiontype: independent
number:
date:
consensus: false
v: 3
area: AREA
workgroup: WG Working Group
keyword:
 - attestation
 - device assignment
 - EAT
venue:
  group: WG
  type: Working Group
  mail: WG@example.com
  arch: https://example.com/WG
  github: USER/REPO
  latest: https://example.com/LATEST

author:
 -
    fullname: Mathieu Poirier
    organization: Linaro
    email: mathieu.poirier@linaro.org
 -
    fullname: Thomas Fossati
    organization: Linaro
    email: thomas.fossati@linaro.org

normative:
  RFC9711: rats-eat

informative:

--- abstract

In confidential computing, device assignment (DA) is the method by which a device (e.g., network adapter, GPU), whether on-chip or behind a PCIe Root Port, is assigned to a Trusted Virtual Machine (TVM).
For the TVM to trust the device, the device must provide the TVM with attestation Evidence confirming its identity and the state of its firmware and configuration.

This document defines an attestation Evidence format for DA as an EAT (Entity Attestation Token) profile.

--- middle

# Introduction

In confidential computing, device assignment (DA) is the method by which a device (e.g., network adapter, GPU), whether on-chip or behind a PCIe Root Port, is assigned to a Trusted Virtual Machine (TVM).
Most confidential computing platforms (e.g., Arm CCA, AMD SEV-SNP, Intel TDX) provide DA capabilities.
Such capabilities prevent agents which are untrusted by the TVM (including other TVMs and the host hypervisor) from accessing or controlling a device that has been assigned to the TVM.
This includes, for example, protection of device MMIO interfaces and device caches.
From a trust perspective, DA allows a device to be included in the TVM's Trusted Computing Base (TCB).
For the TVM to trust the device, the device must provide the TVM with attestation Evidence confirming its identity and the state of its firmware and configuration.

This document defines an attestation Evidence format for DA as an EAT {{-rats-eat}} profile.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Device Attestation Claims

~~~ cddl
{::include-fold cddl/da-token.cddl}
~~~

## SPDM Claims

~~~ cddl
{::include-fold cddl/spdm-claims.cddl}
~~~

### Measurement Claims

~~~ cddl
{::include-fold cddl/spdm-measurement.cddl}
~~~

### Certificate Claims

~~~ cddl
{::include-fold cddl/spdm-certificates.cddl}
~~~

# Collated CDDL

~~~ cddl
{::include-fold cddl/da-token-autogen.cddl}
~~~

# Security Considerations

TODO Security

# IANA Considerations

## New CWT Claims Registrations

TODO IANA CWT allocations

## New CBOR Tags Registrations

TODO IANA CBOR Tag allocations

--- back

# Examples

~~~ cbor-diag
{::include-fold cddl/examples/1.diag}
~~~

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
