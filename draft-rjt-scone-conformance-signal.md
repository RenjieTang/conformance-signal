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

This document proposes conformance signals to be sent by CAPs when they are able to adapt to bitrate indicated by the SCONE signal so that CSPs stop policing.


--- middle

# Introduction

The primary objective of SCONE is to facilitate communication between CSPs and CAPs regarding throughput advice. One of the main motivations is the recognition that traffic shapers are expensive and inaccurate, and they should be disabled if possible. A [paper](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45411.pdf) was pubished on the prevalance and harmfulness of packet policers specifically. However, the ability for CSPs to unidirectionally send signals to the client does not provide CSPs with assurance to disable them.

In addition to determining the format and delivery method for throughput advice, the working group should also establish the conditions under which CSPs SHOULD deactivate their traffic shapers and transition into trust-and-verify mode. This helps CSPs by reducing the costs of traffic shapers and CAPs by reducing the workload of congestion controllers.


# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Proposals

The following proposals assume the throughput advice is transmitted from CSPs to CAPs in the format of a QUIC packet.

1. The CSP default marks the 4-tuple flow as conformant when its SCONE packet is received by the QUIC client. The CSP SHOULD not disable traffic shapers until it confirms the QUIC client has acked the SCONE signal. Because the CSP lacks visibility into packets containing ACK frames, it MAY only deduce the QUIC client's receipt of the signal by observing the cessation of SCONE packet retransmissions by the QUIC server. If the CSP gives an unrealistically low throughput advice and the QUIC client decides to not follow, the client SHOULD not ack the SCONE packet. The SCONE protocol SHOULD also specify a limit on the number of SCONE packet retransmissions. On retransmission timeout, the QUIC server MUST not retransmit more SCONE packets, and the CSP SHOULD consider the current flow ineligible for SCONE.
2. The QUIC client signals conformance by echoing back the SCONE packet. Upon accepting the throughput advice, the QUIC client MAY send back the SCONE packet along with its ack packet to the QUIC server. Upon receiving the SCONE packet, the CSP SHOULD drop it and disable traffic shapers. The QUIC client MAY refuse the throughput advice by not sending the SCONE packet back.


# Security Considerations

The transmission of the conformance signal MUST employ the same security protection mechanism utilized for the original SCONE packets.


# IANA Considerations

This document has no IANA actions.


--- back
