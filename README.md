# FortiGate - inspecting common PaaS services f.e Azure SQL, Storage Account
This document describes how to inspect traffic to PaaS services (f.e. Azure SQL) by using FortiGate and Private Endpoint.
In this scenario FortiGate operates as a DNS Forwarder.
A DNS Forwarder is a Virtual Machine running on the Virtual Network linked to the Private DNS Zone that can proxy DNS queries coming from other Virtual Network or from on-premises. The main reason of using this scenario was to provide the access from on-premise network connected to Fortigate via IPSEC VPN (client-to-site or site-to-site) to the Private Endpoint and the resource (f.e. Azure SQL or Storage Account) linked to that Private Endpoint. The second scenario was to forward and filter all the DNS queries by using Fortigate Virtual Appliance.
## Requirements
-	Fortigate in Azure with at least 2 internal subnets
-	On-premise network connected to Fortigate (in my scenario it was C2S IPSEC VPN)
-	Private endpoint and resource connected to it (in my scenario it was Azure Storage Account)
-	Private DNS Zone ( privatelink.blob.core.windows.net )
## Design
The following diagram illustrates my testing environment. My main task is to make sure that IPSEC VPN clients and virtual machines from ProtectedB network will be able to connect to my storage account through the Fortigate. Since my storage account is available through the PrivateEndpoint my clients has to be able to resolve pcstorage.privatelink.blob.core.windows.net to the ip address of my Private Endpoints interface (172.16.137.6). To do this my Fortigate need to be configured as a DNS Proxy.
