
Authenticated Arbitrary local file read via path traversal
==========================================================

Overview
========

* Title : Authenticated Arbitrary local file read via path traversal
* Author: Kaustubh G. Padwad
* CVE-ID: CVE-2019-7387
* Vendor: Systrome Networks (http://systrome.com/about/)
* Products:  1.ISG-600C
	         2.ISG-600H
	         3.ISG-800W
	         4.
* Tested Version: : ISG-V1.1-R2.1_TRUNK-20181105.bin(Respetive for others)
* Severity: High--Critical

Advisory ID
===========
KSA-Dev-004

About the Product:
==================

Cumilon ISG-* cloud gateway is the security product developed by Systrome for the distributed access network for the cloud-computing era. It integrates the L2-L7security features of the next-generation firewall, is based on the user identification and application identification and provides the application-layer firewall, intrusion prevention, anti-virus, anti-APT, VPN, intelligent bandwidth management, multi-egress link load balancing, content filtering, URL filtering, and other security functions. It provides the cloud interface. The security cloud management platform based on the big data platform architecture can monitor the network topology and device status in real time, simplifying the online deployment of the professional device via the auto configuration delivery. The real-time monitoring of the mobile terminal reduces the maintenance cost and makes the security visible at any time and anywhere. Systrome cloud gateway is the best access security choice of the middle and small enterprises, branch interconnection, and chain enterprises.



Description
-----------
A local file inclusion vulnerability exists in the web interface of Systrome Cumilon ISG-600C, ISG-600H, and ISG-800W 1.1-R2.1_TRUNK-20180914.bin
devices. When the export function is called from system/maintenance/export.php, it accepts the path provided by the user, leading to path traversal
via the name parameter.


Additional_information
----------------------
The php file /system/maintenance/export.php does not properly validate the user input which leads to the path traversal vulberability below is the code sniped for vulnerable code 
if ('isp' == $type)
	$fname = $_GET['name'];


Vulnerability Type
------------------
Directory Traversal


Affected Product Code Base
--------------------------
ISG-600C - ISG-V1.1-R2.1_TRUNK-20181105.bin

Affected Component
------------------
/system/maintenance/export.php

Attack Type
-----------
Remote

Impact Escalation of Privileges
-------------------------------
true


Impact Information Disclosure
-----------------------------
true


Attack Vectors
--------------
Attacker have to send the crafted request while authenticated

Reference
---------
https://s3curityb3ast.github.io/KSA-Dev-004.txt


How to Reproduce: (POC):
------------------------

1. visit the url http://device_ip/system/maintenance/export.php?type=isp&name=../../../../../../etc/passwd.

Mitigation
----------

This issue is fixed in ISG-V1.1-R2.1_TRUNK-20181229.bin

Disclosure: 
-----------
10-Dec-2018 Discoverd the Vulnerability
10-DEC-2018 Reported to vendor 
04-JAN-2019 Recived the fixed from vendor
04-JAN-2019 Request for the CVE-ID
4-Feb-2019 CVE Assign.
8-Feb-2019 Advisiory Published

Discoverer /Credits
-------------------
* Kaustubh Padwad
* Information Security Researcher
* kingkaustubh@me.com
* https://twitter.com/s3curityb3ast
* http://breakthesec.com
* https://www.linkedin.com/in/kaustubhpadwad
