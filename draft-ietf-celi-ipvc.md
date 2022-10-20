---
title: "Intimate Partner Violence Digital Considerations"
abbrev: "ipvc"
docname: draft-ietf-celi-ipvc-latest
category: info

ipr: trust200902
area: General
workgroup: TODO Working Group
keyword: Internet-Draft

stand_alone: yes
smart_quotes: no
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: S. Celi
    name: Sofia Celi
    organization: Brave
    email: cherenkov@riseup.net

normative:

informative:
  NCAV:
    target: https://ncadv.org/learn-more/statistics
    title: "National Statistics Domestic Violence"
    author:
      - name: National Coalition Against Domestic Violence Abuse
    date: 2022-09-06


--- abstract

This document aims to describe how internet standards, protocols and
its implementations may not take into account an specific kind of attacker:
one that has complete access to devices or accounts. This kind of attacker
is a reality for many people in the real-world. Intimate partner violence (IPV) is
a pervasive problem that can increase with the usage of technology. On this
document, we aim to describe the types of strategies this attacker uses and
what kind of counter-measures we can design.

--- middle

# Introduction

Intimate partner violence (IPV) is a pervasive problem. On average, nearly 20
people per minute are physically abused by an intimate partner in the United States {{NCAV}}.
As digital technologies play a central role in everyday lives, it is used to enhance
and participate in IPV. Nevertheless, digitally enhanced IPV is rarely a consideration
when designing technology, protocols and networks. Inside attackers are rarely
discussed as well: attackers that have complete access to devices, networks
and can coerce users.

There are many ways in which technology is used to enhance Intimate Partner Violence (IPV):

* UI-bound attacks
* Ready-made apps available for stalking
* Dual-use applications: anti-theft, parental tracking,

# Definition of technology-based Intimate Partner Violence (IPV)

* Definition, mention that is not only about partners but also the case of geriatrics surveillance, for example.

# Definition of attacker

# Kind of attacks

* Digital tracking and stalking
* Compromise of account:
  * Deleting data
  * Access to contacts and data
  * Lock out
  * Impersonation
* Compromise of devices
  * Access to contacts and data
  * Impersonation
* Denial of access to device or networks, or destruction
* Exposing of private information or media
* Denial of access to contacts:
  * Device is the main mean of contact to family and friends

## Means of attacking

* Installation of spyware or spoofing:
  * Remote access
* Coercion and control:
  * Physically prevent access to devices and/or networks
  * Physical destruction of the device
  * Forcing to reveal password or account login mechanisms
  * Hacking into accounts
* Shared network plans between family/relationship members
* Monitoring:
  * Abuse of social media
  * Usage of dual-use applications: track my phone
* Exposure:
  * Posting harmful content to humiliate
  * Harass family or friends
  * Doxxing
  * Revenge porn or intimate media

# Specific abused technology

* Passwords
* PINs
* Other authentication methods: fingerprints, devices
* Media and private information
* Recovery of account mechanisms
* Lack of blocking mechanisms and abuse of anonymous mechanisms:
  * Contact through fake numbers
  * Contact through fake accounts
  * Open messages system of social media: anyone can send a DM, etc.
  * Abuse of read-recipes: 'I know you read the message'
  * Lack of proper UI for blocking
  * “Facebook is really a stalker’s paradise.”

Adversary is 'adversarially authenticated'.

# Recommendations

* Proper authentication systems
# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.



--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
