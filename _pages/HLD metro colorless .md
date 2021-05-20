{| cellspacing="0" cellpadding = "10" style="border-style:solid; border-color:black; border-width:1px;" width="100%"
| align="right" | [[Image:Level 3 logo.jpg|none|319px]]
|-
|
|-
| align="center" | <font size = "6">'''NETWORK ARCHITECTURE'''</font>
|-
| align="center" | <font size = "6">'''FOR'''</font>
|-
| align="center" | <font size = "6">'''COLORLESS METRO ETHERNET'''</font>
|-
| align="center" | <font size = "6">'''Inter-connecting and Integrating the Metro 3.0 and ILEC Metro Ethernet Networks'''</font>
|-
| align="center" | <font size = "6">Revision 1.0</font>
|-
|
|-
| align = "center"|'''''CONFIDENTIAL AND PROPRIETARY<br>'''''COPYRIGHT LUMEN TECHNOLOGIES 2021'''
|}


'''Revision History:'''

{|border="2" cellspacing="0" cellpadding="4" width="70%"
|Version<br>
|'''Date Issued'''
|'''Status'''
|'''Editor'''
|'''Reason for Change'''
|-
|1.0
|3/31/2021
|Released
|James Bachtel
|Initial Release
|}

'''Contributors:'''
<br>Francis Ferguson
<br>James Bachtel
<br>

__TOC__


----


'''Intellectual Property Rights'''

This document contains valuable trade secrets and confidential information of Lumen Technologies and shall not be disclosed to any person, organization, or entity unless such disclosure is subject to the provisions of a written non-disclosure and proprietary rights agreement or intellectual property license agreement approved by Lumen Technologies. The distribution of this document does not grant any license in or rights, in whole or in part, to the content, the product(s), technology, or intellectual property described herein

----


=Colorless Metro Overview=
This HLD specifies the "Colorless Metro Ethernet" Architecture for Metro Access Networks, a.k.a. Metro 3.0, Legacy QC ILEC and Legacy EQ/CTL ILEC Networks.  The primary goal of this HLD is to establish the protocols and mechanisms which will be used to interconnect the Metro 3.0 and ILEC networks and to provision services end-to-end between the two networks. <br />

The High-Level Objectives of the Colorless Metro Integration effort include:
* Support our growth Services – including ILEC and consumer services
** 3356 DIA & HSIP
** Integrated IPVPN, Hyper-WAN and Fiber +
** E-Services Suite (E-Line , E-access , E-LAN)
** ILEC Wholesale Ethernet and Cell site backhaul
** Quantum Fiber / Consumer Broadband (HSI) <br />
* Stop parallel growth and duplicative capital investment in two separate networks, instead inter-connect the networks and focus growth into the Metro 3.0 network.<br />
* Elimination of dual stacked NIDs (ILEC NID + Metro 2.0 NID) at a customer site

Ultimately the BGP-LU ENNIs should replace FIN-E ENNIs between Metro 2.0 and ILEC Metro Networks. Existing Services would be migrated to the new ENNIs to improve service redundancy and availability.
<br />

<br />



==Colorless Metro Integration Strategy & Goals==
Grow Metro 3.0 as the strategic Metro/Access network and continue to support “all growth” service.  The Metro 3.0 Architecture will be adopted on a Global Basis in all markets. Which will in turn support a standardized product set Globally.<br />
* ILEC Metro Ethernet Networks will continue to support existing services and will be primarily focused on lower speed access circuits (1GE or Less)
** Since many of the ILEC assets are already deployed in the network, it is important that we continue to utilize the imbedded infrastructure for lower-speed service
* Grow new and higher speed service (10GE and above) on Metro 3.0
* Ensure the Metro 3.0 access architecture that support “all” service types
* Eliminate duplicity of network and hardware at customer sites (NIDs), eliminating duplicative truck rolls and streamline Access service delivery
* Leverage BGP-LU (which has already been proven elsewhere in LUMEN networks) for Metro 3.0 to ILEC Metro interconnects using Option C NNIs
** Leverage these Option-C ENNIs for bi-directional service delivery
* Support for all growth services & Products between Metro to networks:
** ILEC Cell-site backhaul, Wholesale Ethernet and MOE services
** AS3356 Internet, AS3549 Integrated VPN and E-Services and AS209 IQ Product sets
* Utilize a two-touch service provisioning process leveraging the benefits of MPLS transport and VPLS Service constructs
** VPLS Node A - ILEC MER /MGR
** VPLS Node B - Metro 3.0 M3/ECN
** Exchange of Route-Target and VPN-IDs are the only two variables required for Edge-to-Edge Service provisioning
* Reflect Metro 3.0 ME/ECN Nodes in ILEC Inventory systems as a barebones/black box
* Reflect ILEC Metro MER/MGR Nodes in Metro 3.0 Inventory systems as a barebones/black box
** Leverage Real time Reconciliation of port inventory between OSS/Inventory systems
** Leverage Real time Reconciliation Customer Facing Service (CFS) inventory between OSS/Inventory systems
<br />

:
:: <span color="blue" data-mce-style="color: blue;" style="color: blue;">'''NOTE :'''</span> New development within the ILEC network and associated IT Systems stacks should be limited whenever possible
:: <span color="blue" data-mce-style="color: blue;" style="color: blue;">'''NOTE :'''</span> BGP-LU ENNIs are already supported in the ILEC Metro Ethernet Networks on the MGR platforms
:: <span color="blue" data-mce-style="color: blue;" style="color: blue;">'''NOTE :'''</span> VPLS based service instantiation for both point-to-point and multi-point services are already used in both ILEC and Metro 3.0 Networks

=Colorless Metro Terms, Roles and Platforms=
This section provides on overview of the device naming convention, descriptions, roles, terms and the associated features and functionality on the Colorless Metro Ethernet Architecture.<br>
<br>

== Inter-AS Option 10C ENNIs ==

The Inter-connections between the Metro 3.0 and ILEC Metro Networks are the foundation for the Colorless Metro Architecture.  Use of BGP-LU for inter-connecting MPLS networks via Inter-AS option 10C ENNIs has been used elsewhere within Lumen Networks and provides a highly scalable Inter-AS MPLS VPN/VPLS solution.  While other methods are available for interconnection disparate networks, the use of BGP-LU and Inter-AS option 10C ENNIs, will greatly improve upon the scalability and redundancy of the Inter-AS option 10A (VLAN-based) ENNIs in use between the Metro Networks today.
<br>

==In Scope Metro 3.0 Roles & Platforms==

=== Metro Core (MC) ===
The '''Metro Core''' is an existing Metro 2.0/3.0 Platform.  This role has been well defined and utilizes the Cisco ASR9000 series hardware.  The Metro Core platforms will be used as an Intra-Metro "service aware" Platforms.  In Metro 2.0/3.0 Network the Metro Cores are the only Devices that support up-links to the PE Routers on the AS3549 and AS3356 Networks.<br>

It is important to note that existing ASR9000 MCs must participate in the Color-less Network design in order to achieve VPLS to VLAN inter-working.  <br>

The Metro Core role in the Metro 2.0/3.0 Network is very similar to the MGR role in the ILEC Metro Networks.  However, Metro 2.0/3.0 Cores are always deployed in a fully redundant pair allowing for increased service availability to the upstream PE routers on the AS3549 and AS3356 Networks. <br>

* '''MC - Metro Core Router''' - A Metro 2.0/3.0 Aggregation Platform Supporting SR-MPLS, VPLS, VLAN Based Trunk Interfaces, Multi-Chassis LAG and L2VPN/VPLS RR functions
** Deployed in fully redundant pairs
** No support for Customer facing Ports
** Terminates Metro 3.0 SR-MPLS Based Rings
** Inter-connects to Test Gear Infrastructure via Trunk Interfaces with Multi-Chassis LAG
** Supports up-links to PE routers via Trunk Interfaces with Multi-Chassis LAG
** Supports down-links to 2.0 Metro Hubs via MPLS and VPLS (Metro 2.0 is out of scope for intra-metro colorless services)
** Supports down-links to 1.0 Metro CO Aggregation (7609) and 1.0 Metro Hub Sites via Trunk Interfaces with Multi-Chassis LAG (Metro 1.0 is out of scope for intra-metro colorless services)

:<font color=red>'''REQ:'''</font> PEs in Metro 3.0 must connect to connect to both MCs via MC-LAG in the site (This is to protect against a single MC failure)

<br>

=== Metro Segment Router (MS) ===

The "Metro Segment Router" (MS) performs the LSR role (P-Router) role in the Metro 3.0.  Several models of the Cisco NCS-5500 Series Routers will initially be certified for deployment in the Metro 3.0 Architecture.  The Cisco NCS-5508 and NCS5504 have currently been certified for deployment in the MS role and support high-densities of 100GE Interfaces.  Other Vendor platforms may be qualified in the MS role in the future. Note, that the Cisco NCS based platforms or Metro Segment Routers (MS) '''will not''' perform Segment Routing to VLAN inter-working functions.  The MS role has also been referred to as an MLSR or "Metro Label Switching Router".
<br>

* '''MS - Metro Segment Router''' - A Metro 3.0 Aggregation Platform running Segment Routing.  <br>
** Deployed in fully redundant pairs
** No support for Customer facing Ports
** These platforms will not be service aware; they will be purely Segment Routing LSRs
** Terminates Metro 3.0 Segment Routing Based Rings (10G and/or 100G)
** '''Does Not''' Support direct inter-connects to Test Gear Infrastructure
** '''Does Not''' Support VLAN Based Trunk Interfaces for up-links to PEs or Down-Links to Metro 1.0/2.0
** Supports infrastructure links to 2.0 Metro Cores, Metro Hubs and other Metro Segment Routers via SR-MPLS (NO VPLS or VLAN Trunks)
** '''Will Support eBGP-LU based Inter-AS Option 10C ENNIs to the ILEC Metro Networks'''


<br>

=== Metro 3.0 Edge (M3) and ECN ===
The Metro 3.0 Edge (M3) Role is an existing role in the Metro 3.0 Architecture.  The M3 Role is essentially a SR-MPLS service aware (PE Router) ME Role in the Metro 3.0 Network. The M3 Role is defined as a platform supporting at least two 100G interfaces for connection to a 100G Metro 3.0 Access ring.  The M3 node must be capable of supporting 10G interfaces for customer connections and should also support 100G Interfaces for customer connections.  An M3 Node must also support Segment Routing with TI-LFA and SR-TE features, along with Customer Service configurations for COS Classification and Queuing.  The M3 node must be capable of supporting VLAN tag manipulation, TWAMP responder, Layer-2 Smart Loopback and Y.1564 Test Head.  <br>

The Ethernet Collector Node Role (ECN) is an M3 node to which sub-tended Metro NIDs (MNs) are connected.  The ECN role is very similar to the MER role in the ILEC Metro Networks. <br>

Both the Cisco NCS-5501-SE and NCS-540, are being certified in the customer facing Metro 3.0 Edge (M3) and ECN Roles in the Metro 3.0 Architecture.  Over time it is expected that other 100G/10G capable platforms which support segment routing, will be eligible for certification in the M3 role.
<br>

* '''M3 - Metro 3.0 Edge''' - A Metro 3.0 100G based Ring Node or Access Platform.
** These platforms terminate 1G/10G/100G customer connections
** Service Instances (or equivalent functionality) on Customer facing Interfaces
** 100G Ring interfaces based on OSPF and Segment Routing with TI-LFA for FRR, utilizing IP Un-numbered
** Cisco NCS-5501-SE will be deployed in 3.0 Ring in the Metro 3.0 Edge Role (M3), Primarily at Data-Center locations or other Larger MTU sites where both 10GE and 100GE UNIs are required
** Cisco NCS-540 may be deployed in 3.0 Ring in the Metro 3.0 Edge Role (M3), Primarily at smaller customer sites  where only 10GE UNIs are required
** Metro 3.0 Edge Devices may also be used to Aggregate off-net port-based circuits
** Metro 3.0 Edge Devices may also be used in an ECN role to Aggregate on-net fiber Laterals to NSB sites ([[HLD - Metro - Ethernet Collector Node|see ECN HLD for more details]])
** '''Lateral connections from M3 ECNs to NID Served Buildings (NSBs) will be permitted as part of the Colorless Metro'''

<br>

== Out-of-Scope Metro 2.0/3.0 Roles & Platforms ==

On the Metro 3.0 Network, only 100GE MS Routers (LSRs) are in scope for development.
On the Metro 3.0 Network, service-aware platforms which fall under two categories are in-scope for development:
* For ILEC-to-Metro3.0 services, only Metro 3.0 platforms capable of delivering 10GE UNIs are in-scope
* For Metro3.0-to-ILEC services, only Metro 2.0/3.0 Metro Cores are in-scope
<br/>


The following Metro 1.0/2.0/3.0 network elements are out-of-scope for development:
<br/>
* The '''Metro 3.0 Hub/MS''' is an existing Metro 3.0 Platform, utilizing NCS-5501-SE 100GE/10GE Hardware; Metro 3.0 Hub/MS Role is out of scope for Colorless Metro Development<br/>
* The '''Metro 3.0 ME''' is an existing Metro 3.0 Platform, utilizing ASR920 10GE/1GE Hardware; Metro 2.0 ME Nodes are out of scope for Colorless Metro Development<br/>
* The '''Metro 2.0 Hub''' is an existing Metro 2.0 Platform, utilizing ASR9K 10GE Hardware; Metro 2.0 Hubs are out of scope for Colorless Metro Development<br/>
* The '''Metro 2.0 ME''' are existing Metro 2.0 Platforms, utilizing ASR920 & ME3600CX 10GE/1GE Hardware; Metro 2.0 ME Nodes are out of scope for Colorless Metro Development<br/>
* The '''Metro 1.0 Aggregation''' are existing Metro 1.0 Platforms, utilizing 7609 & 4900M 10GE/1GE Hardware; Metro 1.0 in its entirety is out of scope for Colorless Metro Development<br/>
* The '''Metro 1.0 ME''' are existing Metro 1.0 Platforms, utilizing 4924, 3400 and 3550 10GE/1GE Hardware; Metro 1.0 in its entirety is out of scope for Colorless Metro Development<br/>
<br/>

==In Scope ILEC Metro Roles & Platforms==

=== Metro Gateway Router (MGR) ===
The '''Metro Gateway Router''' (MGR) is an existing ILEC Metro Platform.  The MGR role has been well defined in the ILEC Network in high-density service edge role (PE Router) and utilizes the Cisco ASR9000 series and Nokia 7750-SR series hardware. Supporting High density service counts supporting handoffs to BRAS, PE Routers on AS209, etc..

=== Metro Core Router (MCR) ===

The "Metro Core Router" (MCR) is an existing ILEC Metro Platform.  The MCR role has been well defined in the ILEC Network and performs the LSR role (P-Router) role and utilizes the Cisco ASR9000 series and Nokia 7750-SR series hardware.


<br>

=== Metro Edge Router (MER) ===
The '''Metro Edge Router''' (MER) is an existing ILEC Metro Platform.  The MER role has been well defined in the ILEC Network in lower-density service edge Role (PE Router) and utilizes the Cisco ASR9000 series and Nokia 7750-SR series hardware. MERs are Service aware PE Routers (LERs) to which Metro Ethernet NIDs are subtended From the MER routers also support satellite shelves for high density 1GE aggregation:

* Nokia 7750-SR7/12 support subtended 7210 satellites
* Cisco ASR9K support subtended ASR9000v satellites


<br>

For more details about the defined roles of platforms used in the ILEC network, see the TSDS Architecture Documentation:

[[HLD-ILEC-TSDS_Architecture#TSDS_MEN_Device_Roles|HLD ILEC TSDS Architecture TSDS MEN Device Roles]]
<br>

=Colorless Metro Ethernet Architecture=
The mechanisms and protocols used to interconnect the Metro 3.0 and ILEC Networks and establish end-to-end service connectivity will be described in this section.  The Colorless Metro Ethernet Architecture will make use of platforms and roles which are already well defined and available for use within the respective Metro Ethernet Networks.
<br>

::<u>'''NOTE:'''</u> Deployment of Metro 3.0 Architecture within a Metro Market is a pre-requisite for Colorless Metro Integration
<br>


'''The following diagram depicts Inter-AS Option 10C ENNIs between Metro 3.0 and ILEC Metro Networks'''

<br>
[[Image:Colorless_Infrastructrue_Large.png |900px]]<br />
<br />

<br>
:<font color=red>'''REQ:'''</font> The Inter-AS Option-10C ENNI will land on the MSs platforms on the Metro 3.0 Network, as this is the most efficient place to interconnect the two networks
:<font color=red>'''REQ:'''</font> The Inter-AS Option-10C ENNI will land on the MGRs platforms on the ILEC Metro Networks, as BGP-LU ENNIs are already supported on these platforms, thus requiring minimal development on the ILEC Network

==Colorless Metro Ethernet Protocols==
===BGP-LU===
BGP Labeled Unicast (BGP-LU) will be used to created end-to-end MPLS Label Switched Paths (LSPs) between MGR/MERs on the ILEC network and M3s/ECNs/MCs on the Metro 3.0 Network.  BGP-LU will be used to redistribute the /32 loopback addresses (and an associated MPLS Label) of the VPLS enabled platforms across the option-10C ENNIs.  BGP-LU provides reachability between the ILEC Metro Ethernet Network and Metro 3.0 network by advertising PE loopbacks and label bindings between the Boarder Routers via an eBGP session carrying Labeled Unicast routes (eBGP-LU).  These Labeled Unicast routes will in turn be re-distributed within the respective Metro Ethernet Networks using an iBGP session carrying Labeled Unicast routes (iBGP-LU).  This results in redistribution of all loopbacks and label bindings of all remote M3s/ECNs and MERs/MGR to one another.


'''The following diagram depicts the redistribution of Labeled /32 Routes via BGP-LU across the Inter-AS Option 10C ENNIs and within the respective Metro Ethernet Networks'''

<br>
[[Image:Colorless_BGP-LU_re-distribution.png |900px]]<br />
<br />

<br>

<br>

===mBGP===
mBGP Multi-Protocol BGP for VPLS Auto-Discovery (AD) will be utilized to provide end-to-end service coordination between VPLS enabled endpoints on the Metro 3.0 (M3/ECN/MC) and the ILEC Metro (MER/MGR) Networks.   BGP Address Family (SAFI) L2VPN/VPLS will advertises VPLS Route targets between the VPLS enabled service endpoints.  The only variables required for service establishment between the two endpoints are the Route-Target and VPN-ID of the services.


'''The following diagram depicts the use mBGP sessions support VPLS-AD across the option-10C ENNIs'''

<br>
[[Image:Colorless_mBGP_VPLS-AD_RR.png |900px]]<br />
<br />

<br>

===T-LDP===
While mBGP will perform the VPLS endpoint auto-discovery function.  A targeted LDP session between service endpoints will ultimately coordinate the VPLS Service Label (VC ID) used to establish the service level PW between the two endpoints.

<br>

===Class of Service===
Since the option-10C ENNI interfaces interconnecting the Metro 3.0 and ILEC Metro Networks, will not be serviced aware.  Class of service treatment on these interfaces should be treated the same as any other MPLS enabled Infrastructure Interface within the Metro Ethernet Networks.  MPLS EXP based classication details are called out in the "Updated Metro COS" HLD provided below:
<br>

[[HLD_-_Metro_-_Updated_Metro_COS#Cisco_ASR_9000|HLD_-_Metro_-_Updated_Metro_COS#Cisco_ASR_9000]]
<br>

<br>

= Colorless Metro End-to-End Data Forwarding =
Customer data will be forwarded end-to-end (from VPLS enabled MER/MGR to VPLS enabled M3/ECN/MC) via MPLS.  The MPLS forwarding paths will be determined by a combination of OSPF with SR-MPLS in the Metro 3.0 Network, RSVP-TE in the ILEC Metro Network and BGP-LU which will be used to interconnect and re-distribute routes between the two networks.  Forwarding of traffic from the ECN Nodes and MER nodes to subtended NIDs on these networks, will continue to utilize the VLAN based mechanisms which are already in place today.

'''The following diagram depicts forwarding of data from the Metro 3.0 network to the ILEC Metro network'''

<br>
[[Image:Colorless_Data_Forwarding_Metro3.0-to-ILEC.png |900px]]<br/>
<br />

<br>

'''The following diagram depicts forwarding of data from the ILEC Metro network to the Metro 3.0 network'''

<br>
[[Image:Colorless_Data_Forwarding_ILEC-to-Metro3.0.png |900px]]<br/>
<br />

<br>


<br/>


= Colorless Metro Supported Services =

The two Primary service delivery objectives of the colorless Metro Ethernet integration, around which our development efforts should focus are:
* 1 - Support of high-bandwidth (10GE or Larger UNIs with greater than 1Gbps BW) Wholesale ILEC Ethernet Services; specifically EVPL based Cell Site backhaul
* 2 - Support of Go-Forward National Enterprise product sets (Integrated VPN, E-Services, AS3356 Internet)
<br/>

ILEC Services to be supported on the Metro 3.0 network as part of the Colorless Metro Integration include:

For Legacy QC, the Metro Ethernet (ME) or Metro optical Ethernet (MOE) Products which include:
* Metro Ethernet EVPL
* Ethernet EPL
* Metro Ethernet ELAN
* 1G and 10G UNI
* Service bandwidth 1Mb, 3Mb, 5Mb, 7Mb, 10Mb - 100Mb (10Mb increments), 200Mb - 1Gb (100Mb increments) and 2G - 10G (1G increments)


For Legacy EQ/CTL Metro Ethernet EVPL Products which include:
* Metro Ethernet EVPL
* 1G and 10G UNI
* Service bandwidth 1Mb, 3Mb, 5Mb, 7Mb, 10Mb - 100Mb (10Mb increments), 200Mb - 1Gb (100Mb increments) and 2G - 10G (1G increments)



'''The following diagram depicts support of a High-Bandwidth Wholesale ILEC EVPL Service supporting Cell-Site Backhaul'''

<br>
[[Image:Colorless_Wholesale_EVPL_Service_Path.png |900px]]<br/>
<br />

<br>


'''The following diagram depict support of Metro-Direct Services utilizing ILEC Metro Ethernet for delivery of low-speed services'''

<br>
[[Image:Colorless_Metro-Direct_Service_Path.png |900px]]<br/>
<br />

<br>

= Colorless Metro Development Phases =
During the initial implementation of Colorless Metro (a.k.a Phase 1), specific service types will be prioritized for development. The following Development, Products and Services are in scope for Phase 1:


== Phase#1 Development ==
:<font color=red>'''REQ:'''</font> Build and design BGP-LU Interconnect between Metro 3.0 and ILEC Metro Networks
:<font color=red>'''REQ:'''</font> Services Support ILEC wholesale Ethernet Product for cell site backhaul
:<font color=red>'''REQ:'''</font> Support ECN with NID Served Building (NSB) & Metro NIDS (MN), leverage existing processes to deploy ECN
:<font color=red>'''REQ:'''</font> Develop processes to add ECN + NSB for new 10GE UNI & service builds of ILEC services
:<font color=red>'''REQ:'''</font> Continue to leverage existing ILEC MERs & NIDs for 1GE UNIs & Services; consumption rules will need to be developed for this
:<font color=red>'''REQ:'''</font> Add ECN and NSB ports into ASRI inventory as BAU and Reconcile ECN and NSB ports into ILEC inventory (TIRKS/ARM) in near real-time

:<font color=red>'''REQ:'''</font> Add MER and ILEC NID ports into ILEC inventory (TIRKS/ARM) as BAU and Reconcile ILEC MER and NID ports into ASRI Inventory in near real-time
:<font color=red>'''REQ:'''</font> Services Support for all product supported over Finished-E today (i.e. AS3356 DIA, AS3549 VPN, E-Services, etc)

== Out-of-Scope for Phase#1 Development ==
* Support of ILEC services on Metro 1.0/2.0 VLAN based Nodes/Infrastructure
** All ILEC services with 1GE UNIs and below will continue to leverage ILEC + 1G NID
* Consumer/Residential Internet Services
** GPON OLTs 10GE and 1G
** DSLAMs
** BRAS

= Colorless Metro Software Version Requirements =

Implementing the BGP-LU Option-10C ENNI interconnects and establishing end-to-end service provisioning, will not require any new code revisions in any of the Metro Ethernet Networks.  BGP-LU Option-10C ENNIs are already supported in ILEC Markets for interconnects to the AS209 national network on both Nokia 7750-SR MGR platforms and on Cisco ASR9K MGR platforms.  On the Metro 3.0 networks all required features are supported on ASR9K platforms prior to 6.4.2 software, which is currently required for Metro 3.0 deployment.  On the NCS platforms all features are supported prior to 6.5.3.
<br>

'''The following table details minimum software version requirements for the Metro 3.0 network'''

<br>
[[Image:Colorless_Metro 3.0_Code_Revisions.png |900px]]<br />
<br />

=References=

The following HLDs contain detailed information about the Metro 3.0 Network, ECN Architecture, ILEC TSDS Architecture and BGP-LU re-distribution for AS209-AS3549.

The HLD for the Metro 3.0 Network can be found here:

:[[HLD - Metro - 3.0|HLD - Metro - 3.0]]

The HLD for ECN can be found here:

:[[HLD - Metro - Ethernet Collector Node|HLD - Metro - Ethernet Collector Node]]

The HLD for the ILEC TSDS Architecture can be found here:

:[[HLD-ILEC-TSDS Architecture|HLD-ILEC-TSDS Architecture]]

The HLD for BGP-LU redistribution can be found here:

:[[HLD - BB4- BGP-LU Versus IGP Redistribution|HLD - BB4- BGP-LU Versus IGP Redistribution]]

=Impacted Systems=
The Inter-connection and Integration of the ILEC Metro Networks and the  Metro 3.0 Network will have impacts on Inventory, Service Provisioning and Network Monitoring Systems.  Ideally Network Engineering Standardization and NSD development will limit the amount of IT Systems Development that is required. With that being said, some amount of development in IT Systems is likely to occur.  The list of systems which are likely to be impacted are as follows:

* ASRI - ASRI currently inventories all Metro 3.0 equipment, the inventory for Metro 3.0 M3, ECN Nodes and Metro NIDs sub-tended from ECNs must be made visible in ILEC inventory tools (TIRKS/ARM)
* TIRKS/ARM ILEC Inventory - TIRKS & ARM currently inventory all ILEC Metro Ethernet equipment, the inventory of ILEC MGRs, MERs and NIDs subtended from MERs must be made visible in the ASRI inventory
* Scenario Manager & SWIFT - The availability of ILEC MGRs, MERs and NIDs subtended from MERs must be made visible in Scenario Manager & Swifter for Quoting and Order Entry
* ILEC order entry - The availability of Metro 3.0 M3, ECN Nodes and Metro NIDs sub-tended from ECNs must be made visible in ILEC order entry toolsets
* SAO/Rubicon - Service Provisioning of "Colorless" service configuration templates on Metro 3.0 and ILEC network elements
<br>

::<font color=blue>'''NOTE :'''</font> Other Impacted systems will be added to this list as they are identified
<br>

==Inventory Systems Requirements==

The Metro 3.0 ASRI Inventory will support:
* Metro 3.0 Edge Nodes (M3/ECN-MN) for both Orange (national) and Green (ILEC) UNI ports Simultaneously
* Metro 3.0 Edge Nodes (M3/ECN-MN) for both Orange (national) and Green (ILEC) Services and EVCs Simultaneously
* Ideally customer facing UNIs/Ports port on a M3 and MN Nodes can be designated as Orange or Green from an inventory perspective
** Alternatively Inventory can be maintained on a node-by-node basis, whereby all ports on an M3 or MN are green and all ports on a second M3 or MN Node are orange ports if that simplifies the IT development
* The green or Colorless NIDs (MNs) subtended from ECN Nodes will be inventoried in ASRI
* All NIDs (MNs) will be deployed/ZTP’ed with Metro 3.0 systems
* All Nodes will have Metro 3.0 TIDs
** If Inventory separation by node is required, the Green Node will have a name Alias that will be used to identify and inventory in TIRKS / ARM green Inventory
*All Nodes/Rings will be capacity managed as Metro 3.0 nodes
*All Nodes will be managed for fault and Alarming as Metro 3.0 nodes
*The Metro 3.0 Metro Cores and MSs (LSRs terminating the Option-C ENNIs) will Only be inventoried in ASRI


TIRKS and ARM inventory will support
* The M3 and MN port inventory will be reconciled from ASRI into TIRKS
* The M3 and MN EVC and service design will be reconciled from ASRI into ARM
* The Metro 3.0 ECN to MNs (NIDs) will use 10G Bidi a 20km consuming only a single fiber strand out of physical inventory
* The Lateral distance limits from ECN to MN will follow pre-established rules for ECN (10Km)
* M3 Nodes on the Metro 3.0 network will support all ILEC services, Wholesale Ethernet, Access Ports for GPON, etc...
* The Phase 1 development should focus on getting T-Mobile/Sprint/Dish Cell-site backhaul services delivered via a Metro 3.0 ECN and 10GE MNs (NIDs)


=Sequencing Diagrams for Metro 3.0 ECN Nodes and Multi-Tennant NIDs=

The following sequencing diagrams visually describe the lifecycle planning and workflow for deploying Metro Ethernet Platforms used as part of the Colorless Metro Ethernet Network.

==Sequencing Diagram for  deployment of M3/ME Nodes at Ethernet Collector Node Sites (ECN) ==

The planning and deployment workflow and systems Sequencing for
[https://sequencediagram.org/index.html#initialData=C4S2BsFMAIFEGEBy0AmkAO4D2BPAtpAHbDQjFbQCykwAThQMwB0ADAPQDqItkAxkcEi0AUMICGvYFlrQAMgFcChaAAVwYwoSEBiAPK0NAc0jjJ06IhoB3aQGtoAEUgBnEIa209BwsdEAzLGIxKxcsAmg-FgAWKOgAZQBBXWgvIxNhAKCQ5zDIAFYc8BAUCIBGSDELGgAjeRBwEtSfdMzgYNCCAqwikr9yyoS4gCUASRT9NOEUMTbqsWcYEcJeLHcwLCbfVvaczsLisuqADmgE+AAVTZNt7NyunsOTh0Gr0WnZ+Zh4QL83IYwNhNmqIJFIZFYxDwABZYeQLV4ZQJtW57boHPwANj8fjgSHG3l8ILMMnOLhIsB8r1B5gAYiBIA1oKTeFCEQJaDhnOgJGRDNAWEwAJzCQz0eToU4oFC86AaXHIRBYNDQXTKah0LDMFjCXg8GYwBRKVTqTRCHV6wRVYC1eooYSGojGjQeaAAWgAfFabYyAFxeuqMgIyLRWCxKkxoZwazn1ARyRSOtTOs26iqWwajUQZsYAHld-tt0D9SwAbgJpDhoFgcZUQ9BCOHoCs8JgaBGyfQY1BiKdhiNzWmYJZgDZaPYnK53Gbh6Pxy43C68wWGsXCGB9ah5+4BxvErphDO7I4ty6PfEkn6EMgAEIBkp0NzGESR6OubskQ9j4+Tjw7y1LFY1ikYQ9zdT0ANWNcpD9BJnB-aARhUaApHlKYO1wN84wgoCsD-GAznOECkjA04Lj9W9C2+QhfkMNCo07TCez3PDoComj-nQXCCJIti-gBP04jBL4fjcOjX1jHsCLEhiJJIXjDA43DUw3CFoVhBYDxqO8SNUyAYThSABKhEAJSvMM0GkjDZOgXT9I05TLTpBkSmZKFNOtbSzycxlXPIogWXlY8SxAfhoGgSyuzjYdvTtByYFJKM4B8YRvJcvgoRIhLyR8P0VCEIM8ECkAWygJQ2lAQIWOeOJhGqzKySSww-XkzdgtClir1qwYSKvP10B4CU0Dakw4tYkSFIBLq4h48bFL9ABxGgxuotw2AAVXQUUxGVRBdBql8ZPfZb2Mmuqz166BsG21qQuElbaIOqyjuqiLGPJJAUvpHz0ugJcssav1pS5GYArM8LHsint-opWjUqZH6lzh3yEMIKMxHAcAbtCsLXuspH0txo7oeS6kZF2+A2H+1zXlG8nKYa1yD10CmqYR-M6dZlk-XVegLGZ2VeH4dA2mWGBCai5n6cSxmIbe6B8ZZcWewVtzZes4mHvQyH3sQJWSGwqDcLVo75MUvXSMI42oq021zZeq2mKSc2HWUJNTWfLW5ZV83bPU9t6Ke62RyPCcFzNIg7WEIA M3/ME Nodes at ECN Sites]

==Sequencing Diagram for ASR920 Multi-Tennant NID (MN) at NID Served Buildings (NSB) ==

The planning and deployment workflow and systems Sequencing for
[https://sequencediagram.org/index.html#initialData=C4S2BsFMAIDkEkAi0AmkAO4D2BPAtpAHbDQjFbQCykwAThQMwB0ADAPQDqItkAxkcEi0AUMICGvYFlrQAMgFcChaAAVwYwoSEBiAPK0NAc0jjJ0uDQDu0gNbREkAM4hDW2noOFjpqTIBiIJDgKNAAol4eRiYAZljEYpZOWATQ0SwALOnQAMoAgrrQkV4xccAJSQQArI5Y4CAh0QCMkGIWwABG8iDBhfpRwrHxiTVVNXUNza252QBK8L2e3ihiZe1ijjDwhLxYrmBYRd6DZcPJkNW19amN7QAc0LkAwgAqhyVDFedjV0130ABazxUqno-EcjjeA1K5RGX0uDQAbNFolQaPQ4EgFv1lqt1jBHnFoi4ZhgDn1ij5zJYxDwABZYeQbSESXzQZ5OEjhQzMsz+QI9dm8WmQ0SGejydAPFAoMiGaAaaCNFgAcSo8nAoAAtIJCBoSAhkAAKaYzaAATgATCwAJTQKSouiMVhhR6waDCXg8FYwBRKVTqTRCD1ewRtTrdFDCX1Ef0aNzQTUAPjDXR6AC4UxHUuYtJYMYhhGhHI6cM4oMQ5IoY2o40HPS1QwEgiEucGGzATfBRE2elzoAAeTWZ9PDho5yB5g0Jl1u9DSEjrZyuJTAYQ9lteBPJzvQDNbABuAmkOGgWBRrVz+cLHPope6Amg67CXjb3py+WEeQKg4es3gGdgLBQGiE8v1PFFYAnK9X1DLYdj2KRP3yLdoDg3ZCH2DNcnBFxlHgYF7WoR183dIsSzLB80IQrAYI7F4kIKJMHheDMACFUxCKcCUIIlDFEes30g4BrFoOwHCXNxhCEkSxKcXChAHIchPDEdxNw+UcNcSA8ArWBKHmUJXSYg1RGk2x7DkrSZCYncMzU1w4H0mdjMxMhfzmUib1wCjdKscz7MksCf1suAgJAED3wKM8LEnfTRDI28fJITtaOgbjeJJOdhCeZ4UPS4lSQzbJfHxQkXGvYtEvvCscoq8jqpIfLDEymjUsBYEVFBJxHAYlD2pBLAwUcXcASBaA51oEh0B4dBesHId+s6wbupG-qJqmmboB2PBMBoSBIwS7yGuY546qq8sSC-VLqTpBkNikmgVJCJibsgelGUgIraRASUp3tZVvWpHA2EoGkbBoTzKqOi7Ro6rrwTO6GH2UjjEbvGHXve+7UqfQVaW7fkQjxlDcb4WkRuMEhgFpGAp1Soj0RM0mhRQhmKCnPdCGLMRwHAVBIH3EB+DRpLH0JtkybasalqG4RFvh4afzZkiM36tBBf4B5JBAfcVhAOJUqu+XlvBFCwNVsbcm13XQDiLbkl2wRUvZYtnz4l3OU3H9zdC4Chb1u3ov6lkdYD5RsnkXghrYPwxG6UQ5elhWzfyC3gRDm39eUAkdqgQQ2FgUIChlRwdkPWgTxF47jdl1KUYjB6Og4xSJddrkM0ebANjtDkNOcV2ykcOwhzoFxjBkAApJhKGgUvaB+kgq5hj23aXh8a+64Rlanb3U+gcljAddF1aFmBdEIdosBpGUX0O9GH23pBKRkWBdEeNgV7xyE79Fq6BNDV+79P6S3rj0Yyb8P69zxhmBmcA37yijhgMo2wYCDzsBHIa0A2CPjjuANevkm4N0AZA12xMfzEOAUKGBaJ2bwIkPwdAyDNY50dvtBOP9joUKgZLDhMNmb414Q+FerZBEViohhRCojGplWaqSfByV6JSNHPIyKKjozKBrIGEQSj+EqMxndEwSizKiQshJIMRBIwJyAA ASR920 MN at NSB Sites]

==NOC Metro 3.0 device On Boarding Process ==

The planning and deployment workflow and systems Sequencing for
[https://sequencediagram.org/index.html#initialData=C4S2BsFMAIFlOAJwPbQMwDoAM0ByB5AYWgBNIA3EAYxmQDsAjZAQ0RJDoHMAoXgM3rBmAd0gBnZAFsYfLABY50AMoBBfNADE+RMy6RuAukNETpAVgngQJaHwCMkZngQMAriHA2tOvQcEjxKUgLZCsbewYADjwAUXxvXU59Q2NA80trWwA2Pj5nYGFkRABraAARCmoYBN8UgNNgjPCHJyVYFQAlABUlTW1E5P8TIJCw2zsouAQUcpAxKmRySEQATz6fJO4SZiEGZjEYGK4SBnWBrZ3mPYPofAAHMROz323d-Zgy3F6azder9+gHQoyxun2+-Rel2uMA6uiomR++j8RnqIya40mACkMLAMNB5ogQHdgM9NtxIEZVmI7sx4VxoHYMAAmbicFCuO63DYweBIVAVSg0W6MFhsaC8KiIRzAGCqfDcSXSmC4OK8OUAWgAfCr8AAuMpzBZLRDQGJQaRGBVSnbKhCFErlSo0bg6rW4O1FUoCqq6gBqzDCNsdgv0ZDEfJWYg8FJJ7oKnuDVStSuU7W6ShdcS1bU6PT9AesQaUuFgAAVoKXQlYuGq1AAedU6-WGxbLU3mmPQBaSO5QGW1-Dqt1xXVbcQRqNQIzKNS8V3akcc14wea6OhtqViVzgYBiAA6dF4mfwDZz6d1AEke0USUoqGu20Ctzv94fj0PNWe82PwyhI9Hpy-DNkyDI5OBOECZVuB4ILDCcAJJe5HgYbg6GQKDWxNMCTl1KU+CgKhQHpKhXEQKVp3DG0ABpTWOU4qAACwGMRoA4dV8JATgGOAOc4gbbCGEva9EFve86HXE0n23XdeMHLUBNHOC-0nTsBIla0oN5GYDXmTCVmPaAGy0-kW2NFYhLuG9lDEiTAXEaSWIACiZOQGMQABKWSP2M2ZdLM0cf3gqdY1VSDbXjB1vWdON7S9J1ICM6YTL85ZzIAcQpZZqFIeLSFM1LoGc1yPLnD1Ivi7ykt8o1UoCpTkH-YL8lixNnR8nSatWLV2vy1ZdQAVTuZccpDaArHDMK7ONUEvm4HqUtWBsgWmj4vgsqyyFG8aSSKtzPLmqqOr0j9lpBValACybYToeESEmsFuFpYAijwIhESPU7EBmpQtTBXVCA0mFgS+87oClBY2EC5SEKms7ylm+rGs7B75s6lYlrhax1pEkaqjGuYdpczzEZU6dUb03hrturUqaxgGUz2KhinVDlbGjKGGtJklabuxUg2xXF8UlIkeL5qC4zcDxecB17CFK4BJc8BsBbxAkRd1StQlsF6AH49d4FWhcJYk3SIAahqDAhiBUKgaGJOEYC6ZBQh11D0NoY1oENtXiV1aBCH8QiveQBi6AwcOyCEDwWNcOhijQ4Q3wpO7eBJmGdQ5pHpxihMotDcdoaannM652GQfhjM06auUS5hh6q9Uuja6apDYILzmYaA5vOyt7uycO3r9Ib6dveF4k+9jFx3E8I8jyAA NOC Metro 3.0 device On boarding]
