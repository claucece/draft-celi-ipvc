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

This document aims to inform how Internet protocols and their implementations might better mitigate technical attacks at the user endpoint, by describing technology-based practices to perpetrate intimate partner violence (IPV). IPV is a pervasive reality for people. It is not limited to, but can be exacerbated with the usage of technology because the attacker has access to one, some or all of: devices, local networks, authentication mechanisms, identity information, and accounts. This kind of technical compromise is distinct from active or passive on-path attacks [Cite RFC7624 or another one?]. In this document we describe the tactics this attacker uses and what kind of counter-measures can be designed in IETF protocols.

--- middle

# Introduction

Intimate partner violence (IPV) refers to physical, emotional, verbal, sexual, or economic abuse of a person by a current or former intimate partner. It is understood that in IPV cases there is an unequal power relationship that allows the abuser to cause harm in romantic or sexual relationships, as well as child or elder abuse, or abuse by any member of a household.

Digital technologies are central in modern lives and can be used as a way to enhance IPV. At the same time, IPV is rarely considered when designing digital technologies, networks, or Internet protocols. This lack of consideration has put pressure on health professionals and social workers to be the ones solving it. In turn, survivors and targets have to develop on their own ad-hoc strategies for digital privacy and safety. It adds even more preasure as this type of abuser, "the attacker you know", is neither on- nor off-path, they have complete access to-- perhaps even share-- devices and local networks. They can even coerce their targets.

This document describes the tactics used in technology-based IPV. It provides recommendations for the design of protocols and implementations to mitigate those tactics.

In what follows, we first describe IPV and related terminology, the kind of tactics attackers
use, and we end with the recommendations.

# Definition of technology-based Intimate Partner Violence (IPV)

IPV refers to physical, emotional, verbal, sexual, or economic abuse of a person
by a current or former intimate partner. By "partner" we mean anyone with a
close relationship with the victim that can exercise abuse in a romantic or sexual relationship, as well as child or elder abuse, or abuse by any member of a household. It is understood in these cases that there is an unequal power relationship that allows the attacker to cause harm. Technology plays a role in IPV by the means of pervasive surveillance and coercive access. {{Dragiewicz2018}} calls this
"digital coercive control" whereby technology becomes a mechanism of control-- through access to devices or accounts-- or to conduct
surveillance or subject the target to harassment.

# Terminology used

Attacker/perpetrator/abuser, victim/survivor

# Types of technology-based Intimate Partner Violence (IPV)

There are many ways in which digital and networked technology can facilitate an attacker perpetrating IPV. Here we informally
list their main groups:

* Ready-made tools: Attackers can use applications or devices
  that are solely built to facilitate IPV. These apps are sometimes called "stalkerware" or "spouseware".
* Dual-use tools: Attackers can use applications, control settings or devices built for beneficial or innocuous
  purposes and repurpose them for harm. This is the case, for example, of anti-theft
  devices that can be repurposed for monitoring.
* Impersonation attacks: Knowing personal information coupled with access to authentication mechanisms gives an attacker the ability to fully authenticate to services and accounts of the victim, effectively impersonating them. This can be executed to the degree that the victim can no longer successfully authenticate themselves.
* UI-bound impersonation attacks: Attackers can abuse technology to enhance IPV by abusing the
  UI of a specific tool. In this case, attackers become authenticated but adversarial users of a
  system. They cannot, however, escalate to root privileges or access other underlying
  functionalities of the system. They are bound to whatever system they managed
  to authenticate to. We will explore later the ways attackers use to forcibly gain
  authentication to a system.
* Social media and forums: Attackers can learn and share information on how to use
  technology to enhance IPV through the usage of these tools. They can also
  receive narrative justification to condone their behaviour. They can also
  perform cyberstalking, cyberbullying, doxxing with the usage of these tools.
* Perception of threat: the mere perception of using technology to enhance IPV
  can be used by attackers to control victims and enhance abuse. This can lead
  to lack of trust in technology and isolation from support from the victim's
  side.

# Definition of the Attacker

The attacker we present in this document is one that either has forceful control of
accounts, devices, and/or authentication information for accessing systems, or uses
public information to exercise control.
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

* Compromise of accounts: Research suggests that in IPV, an attacker may demand
  access to a victim's accounts for continuous monitoring
  and/or restricting their communication with others. This is different from the
  previous point in that the perpetrator demands access (or uses invasive tools) to tools and contents, rather
  than using "publicly available" tools or by monitoring without coercion. This type of attack is mounted in order
  to reduce the "life space" or "space for action" that the victim-survivor may
  have to perform activities that do not involve their attacker. Once an attacker
  has access to an online account, they can use that to:
  * Delete data, which can be communication data, documents and more.
  * Have access to friends, family and contacts.
  * Have access to communication, audio-video content, and any associated metadata.
  * Lock out or change the authentication mechanisms that grant access to the account.
  * Impersonate by using the victim's online identity to send false/forged messages to
    others or to purchase goods and services.
  * Impersonate by using the victim's online identity to post public information
    that can be private or fake.

* Compromise of devices: This attack is similar to the above, but the attacker
  demands access to victim's devices. The goal is the same as the above but the
  result is more impactful as it restricts acess to accounts that are accessed
  through the device. It can also prevent any connection to the Internet.
  Once an attacker has access to the device, they can use that to:
  * Phisicall prevention of usage of the device (to call police services, for example)
  * Access contacts and data (media or messages) stored in it
  * Access to accounts and authentication mechanisms to accounts (saved passwords or
    authenticator apps -2-factor authentication-)
  * Impersonation
  * Denial of access to device, networks or the Internet in general
  * Destruction to the device itself and any information on it
  * Impersonate by using the victim's online identity to post public information
    that can be private or fake.

* Exposing of private information or media: This attack builds on top of other attacks.
  Once an attacker has access to an account or device, they can use the access to get
  private information or private media stored in it. This can later be used for
  threatening, extortion, doxing (posting private information), and more.
  It can also be used to gather information regarding bank accounts, tax information and more.

* Denial of access: This attack can be built on top of other attacks. It can consist
  of denying access to a device, but also denying access to the Internet in general
  by destroying routers (or network devices), changing Wi-Fi passwords or network
  settings. The goal is to disallow access to services or contact with family and friends.
  It can also take the form of sisrupting digital communications by flooding a
  victim's communication's tool with unwanted messages or by sending a virus program.

* Threats: This attack can be a dimension of the previous attack as it can result
  on a denial of access attack. It consists on sending e-mail, chat-based messages
  or social media messages that threatens, insults, or harasses a victim.

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
   messages/actions come from; but, due to its anonymity, it is unable to hold
   atackers accountable. The systems we have in place often need that harrassment
   content is permanently available so that an investigation takes place. This
   enhances the abuse a victim is suffering.

## Means of attacking

* Installation of spyware or spoofing: This form of attack consists on installing
  unwanted tools into a device in order to gain access to accounts or for active
  monitoring. It can also take the form of remote access by remotely "hacking"
  security questions or passwords.
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
