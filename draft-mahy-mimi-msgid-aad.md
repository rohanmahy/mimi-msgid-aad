---
title: "Conveying the More Instant Messaging Interoperability Message ID in Messaging Layer Security Additional Authenticated Data"
abbrev: "MIMI Message ID in AAD"
category: info

docname: draft-mahy-mimi-msgid-aad-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: ""
workgroup: "More Instant Messaging Interoperability"
keyword:
 - message ID
 - AAD
 - Additional Authenticated Data
 - message ID component
venue:
  group: "More Instant Messaging Interoperability"
  type: ""
  mail: "mimi@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/mimi/"
  github: "rohanmahy/mimi-msgid-aad"
  latest: "https://rohanmahy.github.io/mimi-msgid-aad/draft-mahy-mimi-msgid-aad.html"

author:
 -
    fullname: "Rohan Mahy"
    organization:
    email: "rohan.mahy@gmail.com"

normative:

informative:


--- abstract

The More Instant Messaging Interoperability (MIMI) content format defines a MIMI Message ID, communicated only to members of the Messaging Layer Security (MLS) group in which the message was sent.
This document defines a way to share a Message ID in the MLS Additional Authenticated Data (AAD) so it is visible to MIMI providers.

--- middle

# Introduction

Many messaging protocols and formats have a Message ID.
The MIMI content format defines how to calculate a MIMI Message ID (See {{Section 3.3 of !I-D.ietf-mimi-content}}) for an application/mimi-content application message.
A MIMI Message ID is currently only shared end-to-end encrypted with members of the MLS {{!RFC9420}} group in which the message was sent.
This document defines an optional mechanism to share a Message ID in the
MLS AAD, so it is visible to intermediary providers.
This greatly facilitates debugging and troubleshooting, but causes a modest reduction in privacy.


# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Mechanism

This document defines a new Safe AAD `message_id` component as described in {{Section 4.9 of !I-D.ietf-mls-extensions}}.

When the content of an MLS application message is a MIMI content message (media type `application/mimi-content`), if the `message_id` component is present inside `SafeAAD.aad_items`, it MUST contain the MIMI content Message ID calculated as described in {{Section 3.3 of !I-D.ietf-mimi-content}}.

>To the extent that other application formats or media types have a Message ID, the Message ID for an application message of that type or format MAY be conveyed in this extension, using a message ID appropriate to the media type of the content.


# Security Considerations

An attacker or provider with access to a fragment of message history, and the message logs of a MIMI provider in the path of a message could potentially learn more about the participants of a particular MIMI room or the room's corresponding MLS group if it can see message IDs.


# IANA Considerations

## message_id MLS Component Type

This document registers a new MLS Component Type in the Specification Required range with the following template:

- Value: TBD (new assignment by IANA)
- Name: message_id
- Where: AD
- Recommended: Y
- Reference: RFC XXXX


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
