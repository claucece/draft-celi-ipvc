---
title: "Intimate Partner Violence Digital Considerations"
abbrev: "ipvc"
docname: draft-ietf-celi-ipvc-latest
category: info

ipr: trust200902
area: General
workgroup: None
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
  RFC7624:
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
  Freed:
    target: https://doi.org/10.1145/3134681
    title: "Technologies and Intimate Partner Violence: A Qualitative Analysis with Multiple Stakeholders"
    author:
      - name: Diana Freed
      - name: Jackeline Palmer
      - name: Diana Minchala
      - name: Karen Levy
      - name: Thomas Ristenpart
      - name: Nicola Dell
    date: 2017
  Citron:
    target: https://wwnorton.com/books/9780393882315
    title: "The Fight for Privacy: Protecting Dignity, Identity, and Love in the Digital Age"
    author:
      - name: Danielle Keats Citron
    date: 2023
  IPVTechBib:
    target: https://ipvtechbib.randhome.io/
    title: "Selected Research Papers on Technology used in Intimate Partner Violence"
    author:
      - name: Etienne Maynier
  CSP:
    target: https://www.ipvtechresearch.org
    title: "Computer Security and Privacy for Survivors of Intimate Partner Violence"
    author:
      - name: Clinic to End Tech Abuse
  CETAStrategies:
    target: https://www.ceta.tech.cornell.edu/resources
    title: "Resources from the Clinic to End Tech Abuse"
    author:
      - name: Clinic to End Tech Abuse
  TBMDGMMDR:
    target: https://arxiv.org/abs/2005.14341
    title: "The Tools and Tactics Used in Intimate Partner Surveillance: An Analysis of Online Infidelity Forums"
    author:
      - name: Emily Tseng
      - name: Rosanna Bellini
      - name: Nora McDonald
      - name: Matan Danos
      - name: Rachel Greenstadt
      - name: Damon McCoy
      - name: Nicola Dell
      - name: Thomas Ristenpart
  CDOHPFLDMR:
    target: https://ieeexplore.ieee.org/document/8418618
    title: "The Spyware Used in Intimate Partner Violence"
    author:
      - name: Rahul Chatterjee
      - name: Periwinkle Doerfler
      - name: Hadas Orgad
      - name: Sam Havron
      - name: Jackeline Palmer
      - name: Diana Freed
      - name: Karen Levy
      - name: Nicola Dell
      - name: Damon McCoy
      - name: Thomas Ristenpart
      - name: Emily Tseng
  APCFramework:
    target: https://www.apc.org/sites/default/files/gender-cybersecurity-policy-litreview.pdf
    title: "A framework for developing gender-reponsive cybersecurity policy"
    author:
      - Association for Progressive Communication
  Witness:
    target: https://journals.sagepub.com/doi/10.1177/14648849211060644
    title: "Deepfakes, misinformation and disinformation and authenticity infrastructure responses: Impacts on frontline witnessing, distant witnessing, and civic journalism"
    author:
      - Sam Gregory


--- abstract

This document aims to inform how Internet protocols and their implementations might better mitigate technical attacks at the user endpoint by describing technology-based practices to perpetrate intimate partner violence (IPV). IPV is a pervasive reality that is not limited to, but can be exacerbated with, the usage of technology. The IPV context enables the attacker to access one, some or all of: devices, local networks, authentication mechanisms, identity information, and accounts. These kinds of technical compromise exist in addition to on-path attacks, both active and passive {{RFC7624}}. In this document we describe the tactics the IPV attacker uses and what kind of counter-measures can be designed in IETF protocols.

--- middle

# Introduction

Intimate partner violence (IPV) refers to physical, emotional, verbal, sexual, or economic abuse of a person by a current or former intimate partner (henceforth, refered to as the attacker or abuser).{{WHO}} It is understood that in IPV cases there is an unequal power relationship that enables the abuser to cause harm in romantic or sexual relationships, as well as child or elder abuse, or abuse by any member of a household.

Digital technologies are central in modern lives and can be used as a way to enable and enhance IPV. Technology-based IPV has impact on the physical, psychological and emotional health of survivors, affecting them not only individually but their social environment [ref].

There is significant existing work in the field of online gender based violence {{IPVTechBib}}{{CSP}} and technology-based IPV {{Freed}} mainly focused on response and resiliency, including digital privacy and safety strategies. Nevertheless, IPV is not considered enough when designing digital technologies, networks, or Internet protocols against threats. Only in rare cases are protocol design or cybersecurity best practices/tactics available {{CETAStrategies}}.

The type of abuser that is close and familiar to the victim, "the attacker you know", is neither on- nor off-path, they have complete access to-- perhaps even share-- devices and local networks. They can even coerce their targets.

This document describes the tactics used in technology-based IPV. It provides recommendations for the design of protocols and implementations to mitigate those tactics. In what follows, we first describe IPV and related terminology, the kind of tactics attackers use, and we end with the recommendations.

Although the category of tech abuse includes practices such as Child Sexual Abuse Material (CSAM), or digital manipulation of images and videos (deepfakes) to exhibit and slander women {{Witness}}, those tactics are out of scope in this document, since the attacker is not part of the victim's social environment, i.e. they do not necessarily have access to the victim's local network.

# Definition of technology-based IPV

Technology enables and enhances IPV attacks with pervasive surveillance, overt monitoring, and coercive access. IPV refers to physical, emotional, verbal, sexual, or economic abuse of a person by a current or former intimate partner. By "partner" we mean anyone with a close relationship with the victim that can exercise abuse in a romantic or sexual relationship, as well as child or elder abuse, or abuse by any member of a household. In cases of IPV, there is an unequal power relationship that enables the attacker to cause harm. {{Dragiewicz2018}} calls this "digital coercive control" whereby Internet-enabled technology-- through access to local networks, devices and accounts-- becomes a mechanism to exert control, to conduct surveillance, or to aggravate and harass.

Note that while this kind of abuse of technology is excerted to any person (regarless of their gender or sexuality), there is an interesection with gender violence. As noted by {{APCFramework}}, "women and girls face specific cyber threats in the digital age that are considered forms of gender-based violence as they occur because of their gender, or because they disproportionately affect one gender. While this violence is mediated by digital technology, it is part of the same offline structural violence; but its technological dimension adds elements of search, persistence, replicability and scalability that facilitate the aggressors’ access to their targets and can exacerbate the harm."

## Terminology

In the rest of this draft, we will use this terminology:

* Attacker: By "attacker" we mean a person, an abuser in an IPV situation that is using
  digital tools to enable and enhance abuse. An attacker can also be referred to as "perpetrator".
* Victim: By "victim" we mean a person who is subject or target of an attack. Notice that we are using
  this term only in the temporary context of an attack scenario. We prefer the term "survivor", which recognizes the agency and resistance tactics of those facing IPV, but for the purposes of this document we focus on the fact of being subject of specific technology-based IPV attacks.

# Technology-based IPV attacks

In order to describe IPV attacks that are enabled or exacerbated by Internet technology, we first describe our assumptions about the attacker and common tactics that can be used. Then, the types of technology-enabled IPV attacks are described.

## The intimate attacker

The attacker we present in this document is one that either has forceful control of
accounts, devices, and/or authentication information for accessing systems, or uses
public information to exercise control.
This kind of attacker can be technologically savvy or not. We define this
attacker as one of the strongest ones as it can have unlimited access to
systems and devices, whithout investing a lot of financial or computational resources.

The attacker has some kind of physical access to the victim (or has had it in the past),
and often shares a common social network with them. In some cases, it can be
the legal owner of the devices/accounts a victim uses.

## Tech-based IPV tactics

There are many ways in which digital and networked technology can facilitate an attacker perpetrating IPV.
For an in-depth reading, see {{TBMDGMMDR}} and {{CDOHPFLDMR}}.
Here we informally list their main groups:

* Ready-made tools: Attackers can use applications or devices
  that are solely built to facilitate IPV. These apps are sometimes called "stalkerware" or "spouseware".
* Dual-use tools: Attackers can use applications, control settings or devices built for beneficial or innocuous
  purposes and repurpose them for harm. This is the case, for example, of anti-theft
  devices that can be repurposed for stalking.
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
* Perception of threat: The mere presence of a pervasive threat is a form of control. The perception that technology can be used to enhance IPV
  is a tactic of attackers to control victims, take away agency and abuse them. This can lead
  to lack of trust in technology, and further isolates the victim from seeking and receiving support.

## Kinds of tech-enabled IPV attacks

* Monitoring: One of the most prevalent methods to enhance IPV is the usage of
  active monitoring of any online account that the victim has or of any action that the
  victim does in the digital world. This includes a variety of behaviors that
  feel unwelcomed and intrusive, and can involve threats.
  The monitoring is "active" in that is a permanent action that the victim can be
  aware of or not, and that the abuser might want to make them aware or not. It can
  include:
  * Monitoring e-mail, chat-based or social media communications, or browsing information
    (history, cookies or more) either directly on the victim's device or through
    specialised applications.
  * Monitoring location and whereabouts by looking at the metadata of communication,
    by using location-help applications, or by using specialized applications.
  * Monitoring any data sent over the network by mounting DNS attacks or other specialised
    attacks.
  * Monitoring any information found on the UI by looking at devices screens while the
    victim is using them.
  * Using the Internet to seek public or private information to compile a
    victim's personal information for use in harassment.

  In this type of attack, we see these dimensions:

  * Monitoring of the content of communications either at the application layer
    or other layers.
  * Monitoring of the UI content of application tools.
  * Monitoring of location information.

* Compromise of accounts: An attacker may demand access to the victim's accounts to continuously monitor, control or restrict their online communications and activities. In contrast to the previous point, rather than using "publicly available" tools the perpetrator demands access to tools and contents in order to reduce the "life space" or "space for action" that the victim-survivor may have to perform activities that do not involve the attacker. Once an attacker has access to an online account, they can use that to:
  * Delete data, which can be communication data, documents and more (any information s
    stored in the device).
  * Have access to contacts such as friends, family or colleagues.
  * Have access to communications, audio-video content, and any associated metadata.
  * Lock out or change the authentication mechanisms that grant access to the account.
  * Impersonate by using the victim's online identity to send false/forged messages to
    others or to purchase goods and services.
  * Impersonate by using the victim's online identity to publicly post information
    that can be private or fake.
  * Impersonate by using the victim's online or legal identity to sign victims up for services.

* Compromise of devices: This attack is similar to the above, but the attacker
  demands access to the victim's devices. The goal is the same as the above but the
  result is more impactful as it restricts access to accounts that are accessed
  through the device. It can also prevent any connection to the Internet.
  Once an attacker has access to the device, they can use it to:
  * Phisically prevent the use of the device (the device can be used, for example,
    to call police services, which is restricted with this attack).
  * Access contacts and data (media or messages) stored in it.
  * Access to accounts and authentication mechanisms for other accounts (saved passwords or
    authenticator apps -2-factor authentication-, for example).
  * Perform impersonation.
  * Perform denial of access to the device, networks or the Internet in general.
  * Destroy the device itself and any information stored in it.
  * Impersonate by using the victim's online identity, as accessed through the device,
    to publicly post information that can be private or fake.

* Exposing of private information or media: This attack builds on top of other attacks.
  Once an attacker has access to an account or device, they can use this access to gather
  private information or private media stored in it. This can later be used for
  threatening, extortion, doxing (posting private information), and more.
  It can also be used to gather information regarding bank accounts, tax information and more.

* Denial of access: This attack can be built on top of other attacks. It can consist
  of denying access to a device, but also denying access to the Internet in general
  by destroying routers (or network devices), changing Wi-Fi passwords or network
  settings. The goal is to disallow access to services, or contact with family and friends.
  It can also take the form of disrupting digital communications by flooding a
  victim's communication tool with unwanted messages or by sending a virus program.

* Threats: This attack can be considered as a dimension of the previous attack as it can result
  on a denial of access attack. It consists on sending e-mail, chat-based messages
  or social media messages that threatens, insults, or harasses a victim.

* Harrassing: Harrassment can be anonymous, but a victim often knows from whom harrassment
   messages/actions come from; but, due to its anonymity, it is unable to hold
   atackers accountable. The systems we have in place often need that harrassment
   content is permanently available so that an investigation takes place. This
   enhances the abuse a victim is suffering. This type of attack appears in different dimensions:
  * On-going harassment with the goal of intimidation, humiliation and monitoring.
  * Harrassment that appears after a victim has [disconnected] to continue coercion. When the abuser no longer has any physical control over the victim they can start to stalk them.

## Means of attacking

The above attacks can be carried out in different ways. We list here the most
common ones:

* Installation of spyware or spoofing: This form of attack consists of installing
  unwanted tools into a device in order to gain access to accounts or for active
  monitoring. It can also take the form of remote access by remotely "hacking"
  security questions, passwords or any authentication mechanism. Most of the
  time, these tools are installed without the victim's knowledge.
* Coercion and control: This form of attack consists of using coercion and control
  (which can be physical, emotional or psychological) to gain access to devices,
  network devices, accounts or digital information. It often takes the form of
  forcing victims to reveal passwords or account/devices authentication mechanisms.
* Shared network plans between family/relationship members: Often times, an
  attacker is the legal "owner" of a device (owning children's devices, for example)
  or accounts (a bank account, for example),
  or they have access to accounts/devices as they are part of a shared family
  plan. This enables an attacker to carry out the previously mentioned attacks
  without the knowledge of the victim and without the need for installation of
  tools.
* Monitoring: This means of attack consists of the abuse of social media and any public
  information found on digital tools from the victim that has been shared through them. It also involves installing
  tools for active monitoring on devices or using "benign" applications in
  a dual-use manner (applications, such as the "track my phone" one).
* Exposure: This means of attack consists of the abuse of social media to enhance
  harassment. It consists of using social media to post harmful content to humiliate,
  to harass family or friends, for doxxing or to non-consensually share
  intimate/private media.

# Specific abused technology

In the research of the ways attackers use technology to enhance IPV, we see this
specific technology being abused:

* Passwords and authentication mechanisms: all authentication mechanisms can be
  used to enhance IPV as they are the single point of failure used by attackers
  to get access to the account and/or devices (and, once they have access to those, they
  can get further access to other accounts or devices). Attackers can use
  specialised tools (to be installed in devices) to record authentication
  mechanisms, they can coerce victims in order to get access to devices, and more.
  They can also mount these attacks against fingerprints and biometric authentication
  mechanisms, 2-factor authentication devices/applications and more.
* Media and private information: attackers can use the access to accounts/devices
  to gain access to media and private information. This media can later be
  used to bribe a victim, to humiliate them (by publicly posting it), to
  enhance harassment and more.
* Recovery of account mechanisms: as with authentication mechanisms, attackers
  can use 2-factor authentication devices, accounts and/or applications to get access to other
  accounts or profiles
* Lack of blocking mechanisms and abuse of anonymous mechanisms: Often times
  attackers carry out abuse by:
  * Contacting through fake numbers
  * Contacting through fake accounts
  * Sending messages to applications that have a "open" chanel for receiving any
    message.
  * Abusing of read-recipes to enhance control.
  * Abusing the lack of blocking mechanisms.

# Recommendations

We list here some recommendations to protocol designers to mitigate technology-enabled IPV:

* Build proper authentication systems: authentication mechanisms should provide:
  * A non-deletable and non-modifiable list of who has access to accounts/devices:
    a list of recognised devices and a list of active sessions.
  * A way to recover access to an account and to change authentication
    mechanisms.
  * Provide mechanisms to revoke access.
  * Send clear notifications for:
    * when new devices are used to access an account,
    * when there is attempt to access an account,
    * when any change has been made to an account.
  * Provide mechanisms to approve access attempts to accounts (when, for example,
    a new device is trying to access an account).
* Storage and sharing of media: media should be stored/posted in such a way that:
  * It can be taken down at the request of a victim if it consists of
    private media posted without consent.
  * Provide good and private mechanisms for reporting the posting of
    non-consented media.
  * Provide a way to destroy media once a device is in the hands of an attacker.
* Social media: social media can be a way for attackers to enhance monitoring.
  They should:
  * Provide proper blocking systems that are not limited to an individual account.
  * Provide mechanisms by which only "accepted" people are able to send messages
    to an account.
* Browser history or searching information/metadata should be deleted by default.
* End-to-end encryption must be the default for any messaging in order to prevent network monitoring.
* Consider local attackers when designing sensitive applications.
* Engineer plausible deniability for sensitive applications.
* Build detection tools and improve logging and analytics for user agents and devices with IPV in mind.

It is important to note that IPV should not be mistaken to be a privacy issue alone. Furthermore any tech-based solutions and interventions that only address privacy can be used by attackers, helping them to cloak their attacks from the victim and other means of detection. Power is imbalanced in IPV and technology entrenches power.{{Citron}}

# Resources

* Cornell Tech's Clinic to End Tech Abuse https://www.ceta.tech.cornell.edu/
* List of domestic violence hotlines around the world https://en.wikipedia.org/wiki/List_of_domestic_violence_hotlines
* Procedures and tools for clinical computer security https://www.usenix.org/conference/usenixsecurity19/presentation/havron

# Security Considerations

# IANA Considerations

This document has no actions for IANA.

--- back

# Acknowledgments
{:numbered="false"}

Thanks to:

* Lana Ramjit and Thomas Ristenpart for their insipiring work on this area,
  and guidance for this draft.
* Shivan Kaul and Pete Snyder for discussions, guidance and support.
