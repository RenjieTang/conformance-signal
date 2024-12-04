---
title: "CAP Conformance Signal For SCONE"
category: info

docname: draft-rjt-scone-conformance-signal-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Web and Internet Transport"
workgroup: "Standard Communication with Network Elements"
keyword:
 - next generation
 - unicorn
 - sparkling distributed ledger
venue:
  group: "Standard Communication with Network Elements"
  type: "Working Group"
  mail: "scone@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/scone"
  github: "RenjieTang/conformance-signal"
  latest: "https://RenjieTang.github.io/conformance-signal/draft-rjt-scone-conformance-signal.html"

author:
 -
    fullname: "Renjie Tang"
    organization: Google
    email: "renjietang27@gmail.com"

normative:

informative:


--- abstract

# Abstract

This document proposes conformance signals to be sent by CAPs when they are able to adapt to bitrate indicated by the SCONE signal so that CSPs stop policing.


--- middle

# Introduction

The primary objective of SCONE is to facilitate communication between CSPs and CAPs regarding throughput advice. One of the main motivations is the recognition that traffic shapers are expensive and inaccurate, and they should be disabled if possible. A [paper](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45411.pdf) was pubished on the prevalance and harmfulness of packet policers specifically. However, the ability for CSPs to unidirectionally send signals to the client does not provide CSPs with assurance to disable them.

In addition to determining the format and delivery method for throughput advice, the working group should also establish the conditions under which CSPs SHOULD deactivate their traffic shapers and transition into trust-and-verify mode. This helps CSPs by reducing the costs of traffic shapers and CAPs by reducing the workload of congestion controllers.



# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

The transmission of the conformance signal MUST employ the same security protection mechanism utilized for the original SCONE packets.


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
