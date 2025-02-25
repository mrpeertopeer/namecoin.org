---
layout: post
title: "p11mod Now Supports Signatures"
author: Jeremy Rand
tags: [News]
---

In a [previous post]({{ "/2021/07/10/lab-leak-p11mod.html" | relative_url }}), I covered p11mod and how it improves the auditability of Namecoin's TLS interoperability with NSS and GnuTLS.  Recently, I've expanded the subset of the PKCS#11 implementation that p11mod covers; p11mod can now:

* Import certificates, public keys, and private keys.
* Delete certificates, public keys, and private keys.
* Sign messages with private keys.
* Verify signatures with public keys.

None of these operations are required by Namecoin, but they do make p11mod useful for a wider variety of use cases, which helps attract more users and developers.  This new functionality was made possible by integration tests from OpenDNSSEC.  Thanks to the OpenDNSSEC developers for that!

I also fixed a PKCS#11 specification compliance bug in p11mod (stupid off-by-one error in object handle validation), which was surfaced by a GnuTLS upgrade that enforces greater strictness.  Kudos to the GnuTLS developers for being strict and helping me fix a bug!

All of these improvements are now tested daily on Cirrus via p11proxy.
