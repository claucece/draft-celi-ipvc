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
 -
    ins: J. Guerra
    name: Juliana Guerra
    organization: Derechos Digitales
    email: juliana@derechosdigitales.org
 -
    ins: M. Knodel
    name: Mallory Knodel
    organization: CDT
    email: mknodel@cdt.org


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
  WHO:
    target: https://apps.who.int/iris/bitstream/handle/10665/77432/WHO_RHR_12.36_eng.pdf
    title: "Understanding and Addressing Violence Against Women: Intimate Partner Violence"
    author:
      - name: World Health Organization
    date: 2012

--- abstract

This document aims to inform how internet protocols and their implementations might better mitigate technical attacks at the user endpoint, by describing technology-based practices to perpetrate intimate partner violence (IPV). IPV is a pervasive reality for people. It is not limited to, but can be exacerbated with the usage of technology because the attacker has access to one, some or all of: devices, local networks, authentication mechanisms, identity information, and accounts. This kind of technical compromise is distinct from active or passive on-path attacks [Cite RFC7624 or another one?]. In this document we describe the tactics this attacker uses and what kind of counter-measures can be designed in IETF protocols.

--- middle

# Introduction

Intimate partner violence (IPV) refers to physical, emotional, verbal, sexual, or economic abuse of a person by a current or former intimate partner. It is understood that in IPV cases there is an unequal power relationship that allows the abuser to cause harm, including romantic or sexual relationships, as well as child or elder abuse, or abuse by any member of a household. 

Digital technologies are central in modern lives and can be used against targets of IPV. At the same time IPV is rarely considered when designing digital technologies, networks, nor internet protocols. This lack of consideration has put pressure on professionals and, in turn, survivors and targets, to develop ad-hoc strategies for digital privacy and safety. It adds even more preasure as this type of abuser, "the attacker you know", is neither on- nor off-path, they have complete access to-- perhaps even share-- devices and local networks. They can coerce their targets.

This document describes the tactics used in technology-based IPV. It provides recommendations for the design of protocols and implementations to mitigate those tactics.

In what follows, we first describe IPV and related terminology, the kind of tactics attackers
use, and we end with the recommendations.

# Definition of technology-based Intimate Partner Violence (IPV)

IPV refers to physical, emotional, verbal, sexual, or economic abuse of a person
by a current or former intimate partner. By "partner" we mean anyone with a
close relationship with the victim that can exercise abuse in a romantic or sexual relationship, as well as child or elder abuse, or abuse by any member of a household. It is understood in these cases that there is an unequal power relationship that allows the attacker to cause harm. Technology plays a role in IPV by the means of pervasive surveillance and coercive access. {{Dragiewicz2018}} calls this
"digital coercive control" whereby technology becomes a mechanism of control-- through access to devices or accounts-- or to conduct
surveillance or subject the target to harassment.

There are many ways in which digital and networked technology can facilitate an attacker perpetrating IPV. Here we informally
list their main groups:

* Ready-made tools: Attackers can use applications or devices
  that are solely built to facilitate IPV. These apps are sometimes called "stalkerware" or "spouseware".
* Dual-use tools: Attackers can use applications, control settings or devices built for beneficial or innocuous
  purposes and repurpose them for harm. This is the case, for example, of anti-theft
  devices that can be repurposed for tracking.
* Impersonation attacks: Knowing personal information coupled with acccess to devices gives an attacker the ability to fully authenticate to services and accounts of the victim, effectively impersonating them, sometimes to the degree that the victim can no longer successfully authenticate themselves.
* UI-bound impersonation attacks: Attackers can abuse technology to enhance IPV by abusing the
  UI. In this case, attackers become authenticated but adversarial users of a
  system. They cannot, however, escalate to root privileges or access other
  functionalities of the system. They are bounded to whatever system they managed
  to authenticate to. We will explore later the ways attackers use forcibly gain
  authentication to a system.
* Social media and forums: Attackers can learn and share information on how to use
  technology to enhance IPV through the usage of these applications. They can also
  receive narrative justification to condone their behaviour. They can also
  perform cyberstalking, cyberbullying, doxxing with the usage of these tools.
* Perception of threat: the mere perception of using technology to enhance IPV
  can be used by attackers to control victims and enhance abuse. This can lead
  to lack of trust in technology and isolation from support from the victims
  side.

# Definition of the Attacker

The attacker we present in this document is one that has forceful control of
accounts, devices, and/or authentication information for accessing systems.
The kind of attacker can be technologically savvy or not. We define this
attacker as one of the strongest ones as it can have unlimited access to
systems and devices.

The attacker has some kind of physical access to the victim (or has had it in the past),
and often shares a common social network with them. In some cases, it can be
the legal owner of the devices/accounts a victim uses.

# Kind of attacks

* Monitoring: One of the most prevelant methods to enhance IPV is the usage of
  active monitoring of any online account that the victim has or of any action that the
  victim does in the digital world. This includes a variety of behaviors that
  feel unwelcomed and intrusive, and can involve threats.
  The monitoring is "active" in that is a permanent action that the victim can be
  aware of or not, and that the abuser might want to make them aware or not. It can
  include:
  * Monitoring e-mail, chat-based or social media communication, or browsing history
    either directly on the victim’s computer or through specialised applications.
  * Monitoring location and wherabouts by looking at the metadata of communication,
    by using location-help applications, or by using specialized applications.
  * Monitoring any data sent over the network by mounting DNS attacks or other specialised
    attacks.
  * Monitoring any information found over the UI by looking at laptops, or other
    devices while the victim is using them.
  * Using the Internet to seek public or private information to compile a
    victim's personal information for use in harassment

  On this type of attack, we see these dimensions:
  * Monitoring of the content of communications either at the application layer
    or other layers.
  * Monitoring of the UI content of digital tools.
  * Monitoring of location information.

* Compromise of accounts: Research suggests that IPV, a perpetrator may demand
  access to a victim-survivor's devices and accounts for continuous monitoring
  and/or restricting their communication with others. This is different from the
  previous point in that the perpetrator demands access (or uses invasive tools) to tools and contents, rather
  than using "publicly available" tools. This type of attack is mounted in order
  to reduce the "life space" or "space for action" that the victim-survivor may
  have to perform activities that do not involve their abuser. Once an attacker
  has access to an online account, they can use that to:
  * Delete data, which can be communication, documents and more.
  * Have access to friends, family and contacts.
  * Have access to communication, audio-video content, and any associated metadata.
  * Lock out ot change the authentication mechanisms that grant access to the account.
  * Impersonate by using the victim's online identity to send false messages to
    others or to purchase goods and services.

* Compromise of devices
  * Access to contacts and data
  * Access to accounts
  * Impersonation
  * Denial of access to device or networks, or destruction
* Exposing of private information or media
* Denial of access:
  * Device is the main mean of contact to family and friends
  * Disrupting digital communications by flooding a victim's communication's tool
    with unwanted messages or by sending a virus program.
* Threats
  * Sending e-mail, chat-based messages or social media messages that threatens,
    insults, or harasses.
* Harrassing: This type of attacks seems to appear in different dimensions:
  * On-going harrassment with the goal of intimidation, humiliation and monitoring.
  * Harrassment that appears after a victim has "disconnected" to continue coercion:
    "[Disconnecting] often makes it worse. Clients are much more at risk when they actually separate
    from their abusers because he suddenly no longer has any control over that victim.
    So often the only thing left is through the phone, so he’s going to start
    harassing you, calling, texting. If you change your number, now he’s most
    likely going to go crazy. So that’s when he’s going to start stalking you
    any way he can."
   Harrassment can be anonymous, but a victim often knows from whom harrassment
   messages/actions come from but, due to its anonymity, it is unable to hold
   abusers accountable. The systems we have in place often need that harrassment
   content is permanently available so that an investigation takes place. This
   enhances the abuse a victim is suffering.

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
  * Non-consensual sharing of intimate images

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

# Recommendations

* Proper authentication systems
* Proper blocking systems
* Considering local attackers when designing sensitive apps
* Plausible deniability for sensitive apps

# Recommendations that do not work

* Disconnecting or ceasing the use of technology

# Effects on society

# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.



--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
