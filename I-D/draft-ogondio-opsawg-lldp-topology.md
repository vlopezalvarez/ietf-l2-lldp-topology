---
coding: utf-8

title: A YANG Data Model for Link Layer Discovery Protocol (LLDP) topology

abbrev: LLDP Topology YANG
docname: draft-ogondio-opsawg-lldp-topology-00
workgroup: OPSAWG Working Group
category: std
ipr: trust200902

stand_alone: yes
pi: [toc, sortrefs, symrefs, comments]

author:
  -
    name: Oscar González de Dios
    org: Telefonica
    email: oscar.gonzalezdedios@telefonica.com
  -
    name: Samier Barguil Giraldo
    org: Telefonica
    email: samier.barguilgiraldo.ext@telefonica.com

  -
    name: Victor Lopez
    org: Nokia
    email: victor.lopez@nokia.com

#contributor:
#  -


--- abstract

This document defines a YANG data model for representing an abstract view of the provider network topology that contains Link Layer Discovery Protocol (LLDP)  information. This document augments the 'ietf-network' data model by adding LLDP concepts. 

The YANG data model defined in this document conforms to the Network Management Datastore Architecture (NMDA).


--- middle

# Introduction

Topology collection is a critical use case for the network operators because the network topology is an abstract representation of the physical nodes, links and network interconnections. 

Exchanging LLDP information between a service orchestration layer and a SDN controller to create services is desirable. The deployment of L2 services with the Layer 2 VPN Network Model (L2NM) {{!draft-ietf-opsawg-l2nm}} is more accurate if the SDN controller can export LLDP topological information, so the customer uses the information of the controller instead of getting it from inventory information. 

The main idea of this model is to represent most relevant of the LLDP topology attributes.

This document defines a YANG data model for representing, managing and controlling the LLDP topology. The data model augments ietf-network module {{!RFC8345}} by adding the LLDP information.

This document explains the scope and purpose of the LLDP topology model and how the topology and service models fit together.

The YANG data model defined in this document conforms to the Network Management Datastore Architecture {{!RFC8342}}.

## Terminology and Notations 

This document assumes that the reader is familiar with the contents of {{!RFC8345}}, . The document uses terms from those documents.

The terminology for describing YANG data models is found in {{!RFC7950}}, {{!RFC8795}} and {{!RFC8346}}.

Following terms are used for the representation of this data model.

TBD

## Requirements Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in  {{!RFC2119}}, {{!RFC8174}} when, and only when, they appear in all capitals, as shown here.

## Tree Diagram

Authors include a simplified graphical representation of the data model is used in {{ietf-l2-lldp-topology-tree}} of this document.
The meaning of the symbols in these diagrams is defined in {{!RFC8340}}.

## Prefix in Data Node Names

  In this document, names of data nodes and other data model objects are prefixed using the standard prefix associated with the corresponding YANG imported modules, as shown in the following table.

| Prefix | Yang Module            | Reference    |
| ------ | ---------------------- | ------------ |
| lldpnt | ietf-l2-lldp-topology  | RFCXXX       |
| yang   | ietf-yang-types        | {{!RFC6991}} |
{: #tab-prefixes title="Prefixes and corresponding YANG modules"}

RFC Editor Note:
Please replace XXXX with the RFC number assigned to this document.
Please remove this note.

# YANG Data Model for LLDP Topology

## YANG Model Overview

The abstract (base) network data model is defined in the "ietf-network" module of {{!RFC8345}}. The LLDP-topology builds on the network data model defined in the "ietf-network" module {{!RFC8345}}, augmenting the nodes with LLDP information, which anchor the links and are contained in nodes).

The set of parameters and augmentations are included just at the termination point level. Each parameter is listed as follows:

* LLDP state on/off
+ Neighbor Mac Address
+ Age since discovery
+ Time-to-live (TTL)
- LLDP TLVs state. This item contains the following items:
  * System Name
  + System Description
  + Port ID
  - Port Description

{: #ietf-l2-lldp-topology-tree}

# LLDP Topology Tree Diagram

{{fig-ietf-l2-lldp-topology-tree}} below shows the tree diagram of the YANG data model defined in module ietf-l2-lldp-topology.yang ({{ietf-l2-lldp-topology-yang}}). 

~~~~
{::include ../Yang/ietf-l2-lldp-topology.tree}
~~~~
{: #fig-ietf-l2-lldp-topology-tree title="LLDP Topology tree diagram"}

{: #ietf-l2-lldp-topology-yang}

# YANG Model for LLDP topology

This module imports types from {{!RFC8343}} and {{!RFC8345}}.

~~~~
<CODE BEGINS> file "ietf-l2-lldp-topology@2022-03-07.yang"
{::include ../Yang/ietf-l2-lldp-topology.yang}<CODE ENDS>
~~~~
{: #fig-ietf-lldp-topolopy-yang title="LLDP Topology YANG module"}

# Security Considerations

    The YANG module specified in this document defines a schema for
    data that is designed to be accessed via network management
    protocols such as NETCONF {{!RFC6241}} or RESTCONF 
    {{!RFC8040}}.  The lowest NETCONF layer is the secure transport
    layer, and the mandatory-to-implement secure transport is Secure
    Shell (SSH) {{!RFC6242}}. The lowest RESTCONF layer is HTTPS, and
    the mandatory-to-implement secure transport is TLS {{!RFC5246}}.

   The NETCONF access control model {{!RFC6536}} provides the means to restrict access for particular NETCONF or RESTCONF users to a    preconfigured subset of all available NETCONF or RESTCONF protocol operations and content.

   There are a number of data nodes defined in this YANG module that are writable/creatable/deletable (i.e., config true, which is the default).  These data nodes may be considered sensitive or vulnerable   in some network environments.  Write operations (e.g., edit-config) to these data nodes without proper protection can have a negative effect on network operations.

# IANA Considerations

  This document registers the following namespace URIs in the IETF XML registry {{!RFC3688}}:

    --------------------------------------------------------------------
    URI: urn:ietf:params:xml:ns:yang:ietf-l2-lldp-topology
    Registrant Contact: The IESG.
    XML: N/A, the requested URI is an XML namespace.
    --------------------------------------------------------------------

   This document registers the following YANG module in the YANG Module Names registry {{!RFC6020}}:

    --------------------------------------------------------------------
    name:         ietf-l2-lldp-topology
    namespace:    urn:ietf:params:xml:ns:yang:ietf-l2-lldp-topology
    maintained by IANA: N
    prefix:       ietf-l2-lldp-topology
    reference:    RFC XXXX
    --------------------------------------------------------------------

# Implementation Status

This section will be used to track the status of the implementations of the model. It is aimed at being removed if the document becomes RFC.

--- back

{: numbered="false"}

# Acknowledgments

The authors of this document would like to thank XXX.

This document was prepared using kramdown.
