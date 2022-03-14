# azure_paas_services_inspection
This document describes how to inspect traffic to PaaS services (f.e. Azure SQL) by using FortiGate and Private Endpoint.
In this scenario FortiGate operates as a DNS Forwarder.
A DNS Forwarder is a Virtual Machine running on the Virtual Network linked to the Private DNS Zone that can proxy DNS queries coming from other Virtual Network or from on-premises. The main reason of using this scenario was to provide the access from on-premise network connected to Fortigate via IPSEC VPN (client-to-site or site-to-site) to the Private Endpoint and the resource (f.e. Azure SQL or Storage Account) linked to that Private Endpoint. The second scenario was to forward and filter all the DNS queries by using Fortigate Virtual Appliance.
