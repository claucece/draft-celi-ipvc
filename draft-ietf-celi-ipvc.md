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
  Dragiewicz2018:
    target: https://www.tandfonline.com/doi/abs/10.1080/14680777.2018.1447341
    title: "Technology facilitated coercive control: domestic violence and the competing roles of digital media platforms"
    author:
      - name: Molly Dragiewicz
      - name: Jean Burgess
      - name: Ariadna Matamoros-Fernández
      - name: Michael Salter
      - name: Nicolas P. Suzor
      - name: Delanie Woodlock
      - name: Bridget Harris
    date: 2022-09-06


--- abstract

This document aims to describe how internet standards, protocols and
its implementations may not take into account an specific kind of attacker:
one that has complete access to devices or accounts. This kind of attacker
is a reality for many people in the real-world. Intimate partner violence (IPV) is
a pervasive problem that can increase with the usage of technology, that exhibits the
kind of attacker just described. On this document, we aim to describe the types
of strategies this attacker uses and what kind of counter-measures we can design.

--- middle

# Introduction

Intimate partner violence (IPV) is a pervasive problem. On average, nearly 20
people per minute are physically abused by an intimate partner in the United States {{NCAV}}.
As digital technologies play a central role in everyday lives, it is used to enhance
and participate in IPV. Nevertheless, digitally enhanced IPV is rarely a consideration
when designing technology, protocols and networks. Inside attackers are rarely
discussed as well: attackers that have complete access to devices, networks
and/or can coerce users.

This document aims to describe the types of strategies attackers of IPV use. It
also aims to provide recommendations that protocols, standards and implementations
can use in order to prevent it.

In what follows, we first describe what is IPV, the kind of strategies attackers
use, and we end with the recommendations.

# Definition of technology-based Intimate Partner Violence (IPV)

IPV refers to physical, emotional, verbal, sexual, or economic abuse of a person
by a current or former intimate partner. By partner here we mean anyone with a
close relationship with the victim, which relationship can be romantic, sexual,
of care, family, and more. Technology plays a role in IPV by the means of pervasive
surveillance and coercive access. Dragiewicz et al. {{Dragiewicz2018}} calls this
"digital coercive control". In this case, technology becomes a mechanism by which
attackers enhance abuse often by controlling devices and/or accounts to increase
surveillance and harassment. IPV however should not be only defined as a
phenomenon of romantic/sexual relationships. It can also be present on family
relationships, geriatric surveillance and more.

There are many ways in which technology is used to enhance IPV. Here we informally
list their main groups:

* UI-bound attacks: Attackers can abuse technology to enhance IPV by abusing the
  UI. In this case, attackers become authenticated but adversarial users of a
  system. They cannot, however, escalate to root privileges or access other
  functionalities of the system. They are bounded to whatever system they managed
  to authenticate to. We will explore later the ways attackers use forcibly gain
  authentication to a system.
* Ready-made applications/devices: Attackers can use tools
  that are solely built to enhance IPV. The biggest example of this tool is spyware.
* Dual-use applications/devices: Attackers can use tools built for beneficial or innocuous
  purposes and repurpose them for harm. This is the case, for example, of anti-theft
  devices that can be repurposed for tracking.
* Social media and forums: Attackers can learn and share information on how to use
  technology to enhance IPV through the usage of this applications. They can also
  receive narrative justification to condone their behaviour. They can also
  perform cyberstalking, cyberbullying, doxxing with the usage of these tools.
* Perception of threat: the mere perception of using technology to enhance IPV
  can be used by attackers to control victims and enhance abuse. This can lead
  to lack of trust in technology and isolation from support from the victims
  side.

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
