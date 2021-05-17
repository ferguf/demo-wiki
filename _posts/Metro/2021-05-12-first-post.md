---
layout: post
title: Metro - TUN update -
---
{:toc}

{| class="wikitable" width="30%"
|-
||To:
|| 
||Network Engineering
|-
||From:
|| 
||Architecture
|-
||Date:
|| 
||April 2, 2021
|-
||Notification Type:
|| 
||Hardware Usage
|-
||Notification Target groups:
|| 
||Metro Engineering
|-
||Prepared by:
|| 
||James Bachtel
|}


<br />


{| border="2" width="75%" cellspacing="0" cellpadding="4"
|-
!|Notification Number
||TUN-Metro-2029
|-
!|Notification Name
||New 100GE QSFP28 Optics for Metro 3.0
|-
!|Status
||Active


|}


This '''''Technology Update Notification''''' (TUN) is being published to inform you of changes or additions to Lumen Technology's network architecture, hardware, software or device configuration. This TUN is a dated document and reflects changes to the architecture, hardware, software, or device configuration at this moment in time. As such, subsequent policy updates may be issued at a later date that could override this document.

<br />

==Purpose==
This '''''Technology Update Notification''''' advises the respective groups of the proposed changes to the currently approved configurations in '''Lumen's''' network. A '''TUN''' is accompanied by WIKI documents that have been updated with information about new deployment standards and general configuration templates. A '''TUN''' announces that the architecture design work has been completed, with new architectures documented and approved by the architecture team. This '''TUN''' can be used as a notification to other teams and a handoff for further development.

<br />

'''A TUN ''does not approve technologies or configuration changes, for use in the production network.'''''

<br />
==Introduction==
The [http://wiki.level3.com/wiki/Network_Architecture_and_Design_-_Third_Party_Optics Third Party Optics] wiki describes the approved certification and use of Champion One optics in the various IP/Data Routing, Switching and NID platforms deployed within the affiliate CenturyLink Networks. To date Champion One Optics have been Tested and Certified for use in the Metro 2.0/ 3.0, AS209, ILEC Metro, AS3549 (MPLS) and AS 3356 (Internet ) networks.

This TUN requests that a new set of Champion One 100GE QSFP28 optics be officially certified for use in the Metro 3.0 Network. <br />


<br />
==Business Driver and Timing==

{| border="2" width="75%" cellspacing="0" cellpadding="4"
|-
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Business Driver'''</span>
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Timing'''</span>
|-
||Test and Certify new set of Champion One 100GE QSFP28 optics
||Q2 2021
|}
<br />
==Network Impact==
===Impacted Architecture===

{| border="2" width="75%" cellspacing="0" cellpadding="4"
|-
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Severity:'''</span>
! scope="col" width="40%"|Minor
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Architectures Impacted:'''</span>
! scope="col" width="40%"|Metro 3.0
|-
| bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Availability Date:'''</span>
||Q2 2021
| bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Operational Impact:'''</span>
||Test and Certify new set of Champion One 100GE QSFP28 optics and update associated documentation
|}


<br />

===Impacted Platform===

{| border="2" width="75%" cellspacing="0" cellpadding="4"
|-
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Platform'''</span>
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Role'''</span>
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''OS version'''</span>
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Description'''</span>
|-
||
* Multiple
||See Tables Below
||See Tables Below
||See Tables Below
|}


<br />

===Impacted Product===


{| border="2" width="75%" cellspacing="0" cellpadding="4"
|-
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Product'''</span>


! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Impact'''</span>


! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Description'''</span><br /><br />


|-
||None
||None
||N/A
|}


<br />

===Impacted Systems===

{| border="2" width="75%" cellspacing="0" cellpadding="4"
|-
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Systems'''</span>
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Development'''</span>
! bgcolor="#cccccc"|<span style="color: #2f6682;" data-mce-style="color: #2f6682;">'''Description'''</span><br /><br />
|-
||ASRI
||Required
||Inventory of new optic types
|-
||SAP
||Required
||SAP Material codes to be created at completion of certification testing
|}


<br />


=== New 100G QSFP28 Optics to be certified ===

{| border="2" cellspacing="0" cellpadding="4" width="100%"
| align = "center"  width="5%" bgcolor="#FFCCCC"|'''SAP Mat Code #'''
| align = "center"  width="8%" bgcolor="#FFCCCC"|'''C1 Part Number'''
| align = "center"  width="13%" bgcolor="#FFCCCC"|'''C1 Short Description'''
| align = "center"  width="5%" bgcolor="#FFCCCC"|'''Form Factor'''
| align = "center"  width="5%" bgcolor="#CCCCCC"|'''Vendor'''
| align = "center"  width="10%" bgcolor="#CCCCCC"|'''Platform'''
| align = "center"  width="14%" bgcolor="#CCCCCC"|'''Software'''
| align = "center"  width="19%" bgcolor="#CCCCCC"|'''Line Card'''
|-
|rowspan="2"|'''TBD'''
|rowspan="2"|'''100GQSFP28E-ER4'''
|rowspan="2"|100G QSFP28 ER4
|rowspan="2"|QSFP28
<!-- Vendor  1 -->| Cisco
<!-- Platform1 -->| NCS540/NCS5501-SE
<!-- Software1 -->| 6.5.3 and newer
<!-- LineCard1 -->| built-in ports
|-
<!-- Vendor  3 -->| Cisco
<!-- Software3 -->| NCS5504/NCS5508
<!-- Software3 -->| 6.5.3 and newer
<!-- LineCard3 -->| NC55-36X100G-BA: NCS 5500 36x100G Base Line Card
|-
|rowspan="2"|'''TBD'''
|rowspan="2"|'''100GQSFP28E-ZR4'''
|rowspan="2"|100G QSFP28 ZR4

|rowspan="2"|QSFP28
<!-- Vendor  1 -->| Cisco
<!-- Platform1 -->| NCS540/NCS5501-SE
<!-- Software1 -->| 6.5.3 and newer
<!-- LineCard1 -->| built-in ports
|-
<!-- Vendor  3 -->| Cisco
<!-- Software3 -->| NCS5504/NCS5508
<!-- Software3 -->| 6.5.3 and newer
<!-- LineCard3 -->| NC55-36X100G-BA: NCS 5500 36x100G Base Line Card
|-
|rowspan="2"|'''TBD'''
|rowspan="2"|'''100GQSFP28ERBL20'''
|rowspan="2"|100G QSFP28 BIDI 4WDM20
|rowspan="2"|QSFP28
<!-- Vendor  1 -->| Cisco
<!-- Platform1 -->| NCS540/NCS5501-SE
<!-- Software1 -->| 6.5.3 and newer
<!-- LineCard1 -->| built-in ports
|-
<!-- Vendor  3 -->| Cisco
<!-- Software3 -->| NCS5504/NCS5508
<!-- Software3 -->| 6.5.3 and newer
<!-- LineCard3 -->| NC55-36X100G-BA: NCS 5500 36x100G Base Line Card
|-
|rowspan="2"|'''TBD'''
|rowspan="2"|'''100GQSFP28EBBL20'''
|rowspan="2"|100G QSFP28 BIDI 4WDM20
|rowspan="2"|QSFP28
<!-- Vendor  1 -->| Cisco
<!-- Platform1 -->| NCS540/NCS5501-SE
<!-- Software1 -->| 6.5.3 and newer
<!-- LineCard1 -->| built-in ports
|-
<!-- Vendor  3 -->| Cisco
<!-- Software3 -->| NCS5504/NCS5508
<!-- Software3 -->| 6.5.3 and newer
<!-- LineCard3 -->| NC55-36X100G-BA: NCS 5500 36x100G Base Line Card
|-
|rowspan="2"|'''TBD'''
|rowspan="2"|'''100GQSFP28E-FR1'''
|rowspan="2"|100G QSFP28 FR
|rowspan="2"|QSFP28
<!-- Vendor  1 -->| Cisco
<!-- Platform1 -->| NCS540/NCS5501-SE
<!-- Software1 -->| 6.5.3 and newer
<!-- LineCard1 -->| built-in ports
|-
<!-- Vendor  3 -->| Cisco
<!-- Software3 -->| NCS5504/NCS5508
<!-- Software3 -->| 6.5.3 and newer
<!-- LineCard3 -->| NC55-36X100G-BA: NCS 5500 36x100G Base Line Card
|-
|rowspan="2"|'''TBD'''
|rowspan="2"|'''100GQSFP28E-LR1'''
|rowspan="2"|100G QSFP28 LR

|rowspan="2"|QSFP28
<!-- Vendor  1 -->| Cisco
<!-- Platform1 -->| NCS540/NCS5501-SE
<!-- Software1 -->| 6.5.3 and newer
<!-- LineCard1 -->| built-in ports
|-
<!-- Vendor  3 -->| Cisco
<!-- Software3 -->| NCS5504/NCS5508
<!-- Software3 -->| 6.5.3 and newer
<!-- LineCard3 -->| NC55-36X100G-BA: NCS 5500 36x100G Base Line Card
|-
|}

===New 100G QSFP28 Optics Information===

{| border="2" width="100%" cellspacing="0" cellpadding="4"
|-
||'''Short Description'''
||'''C1 PN'''
||'''Long Description'''
||'''Specification Source'''
||'''Fiber Type'''
||'''Rated Distance'''
||'''Purpose'''
|-
||100G QSFP28 ER4
||100GQSFP28E-ER4
||100G QSFP28 LAN WDM 40-km, SMF, LC connector, C-Temp
||QSFP+ MSA 100G MSA
||SMF
||40km
||Extended reach over Dark-Fiber for Metro 3.0 Rings & Infrastructure
|-
||100G QSFP28 ZR4
||100GQSFP28E-ZR4
||100G QSFP28 LAN WDM 80-km, SMF, LC connector, C-Temp
||QSFP+ MSA 100G MSA
||SMF
||80km
||Extra Long reach over Dark-Fiber for Metro 3.0 Rings & Infrastructure
|-
||100G QSFP28 BIDI 4WDM20
||100GQSFP28ERBL20
||100G BIDI QSFP28 4WDM 20km, e-temp, single fiber LC connector, red side
||QSFP28 MSA 4WDM MSA
||SMF
||20km w/FEC
||Intermediate reach BiDi over Dark-Fiber for Metro 3.0 Rings & Infrastructure
|-
||100G QSFP28 BIDI 4WDM20
||100GQSFP28EBBL20
||100G BIDI QSFP28 4WDM 20km, e-temp, single fiber LC connector, blue side
||QSFP28 MSA 4WDM MSA
||SMF
||20km w/FEC
||Intermediate reach BiDi over Dark-Fiber for Metro 3.0 Rings & Infrastructure
|-
||100G QSFP28 FR
||100GQSFP28E-FR1
||100G QSFP28 FR1, 1 x 106.25Gb/S PAM4, 1310nm SMF LC connector, C-Temp, 2km, single Lambda
||100G Lambda MSA
||SMF
||2Km over SMF with FEC
||Short Reach interoperation with 400G QSFP56DD FR4 to FR1 via 4 x 100GE breakout
|-
||100G QSFP28 LR
||100GQSFP28E-LR1
||100G QSFP28 LR1, 1 x 106.25Gb/S PAM4, 1310nm SMF LC connector, C-Temp, 10km, single Lambda
||100G Lambda MSA
||SMF
||10Km over SMF with FEC
||Long Reach interoperation with 400G QSFP56DD FR4 to FR1 via 4 x 100GE breakout
|}


==Additional Documentation & References==
http://wiki.level3.com/wiki/Network_Architecture_and_Design_-_Third_Party_Optics <br />

<br />
