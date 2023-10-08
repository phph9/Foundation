# Azure

- Personal global network
- VNET - network, we can devide it into subnets
- Network interfaces - create separately
- Connect network interface to network and subnets
- Enable IP forwarding separtly
- Network securiyt group - firewall - attach to subnet or interface - best practise is subnet
- If attach to sybnet - traffic between hosts in subnet is filtered as well
- Application security group - add vm to it and use in NSG rules
- VPN gateway - only one for one vnet
- Route based VPN gateway - BGP - Virtual Network Interface
- Policy based VPN
- VPN gateway can connect 2 Vnets, or it can connect vnet with on premise site
- Peering is recomended for connection of 2 Vnets - 2 vnets like in one switch
- vnet1-vnet2-vnet3: peering is not transitive, vnet1 cannot ping vnet3
- But we can add a router to vnet2 - and it will work
- vnet1 can use remote gateway in vnet2
- Gateway subnet at least /27 for VPN
- VPN connection requires public IP
- First we need to create a resource group - we specify region - devices with one lifecycle in one resource group
- Then we create VNEts - specify resource group + address space + subnets
- Network watcher resource group - created by default - monitors everytthing and builds topology
- Topology is very nice - it shows vnet, subnetwork, public IP, VM and NSG group
- Then create a Network Security Group + assosiate it with subnet
- Add rules to NSG
- Service tags can be used in rules to allow access to internal Azure services: storage for example
- We also configure priority for rules - the lower - the higher
- Then we create VM
- For VM we configure resource group, region, Vnet, subnet, public IP, Application Security group
- IP flow verify tool does exist to validate NSG rules
- Nexthop tool - shows next hop for particular traffic flow
- We can see all routes in VM from Azure interface
- We can run PowerShell on VM from Azure, for example install IIS server
- Then we add peering for VNET with another VNET - Azure will add routes to VM automatically
- For VPN we create a gateway subnet - /27 min - subnet gateway on every vnet which we want to connect
- Then we create virtual network gateway - region, policy or route base, Public IP, BGP - gateway for every VNET
- In virtual network gateway we create connection: Site-to-site, or Vnet-to-Vnet, or express route
- Then we configure IKE, bgp, shared key
- 2 types of routes: system and user defined
- Routing and switching is automatic in VNET
- You cannot change System routes
- You can overright them with User Defined Routes
- Next hop types: Virtual Network, VNET peering, Virtual Network Gateway, Internet, None - Drop
- User Defined Routes: Static or BGP
- We create a route table and attach it to subnet
- Then we add routes to the table
- Route choosing priority: UDR, BGP, System
- U can use UDR to send traffic between 2 subnets via Virtual Appliance - FW
- Azure Route Server - via it exchange of routes between VNETS and Virtaul Appliances
- Load balancers:
	- APP Gateway - Layer 7, cookie affinity, SSL termination + WAF
	- Load balancer - basic - Layer 4 - Intrnal and external - 5 tuple hash based, session persistance
	- Traffic manager - DNS based - global load balancer - between public facing apps routing methods: priority, weight, performance, geographic, multipule endpoints in DNS reply, subnet traffic routing method - based on client subnet
	- Front Door and CDN providers - has everything from app gateway + global + waf + static content cashing
- Service Endpoints: SQL, Storage - public services come with firewall - uses public IP of service
- Private Endpoint - connection between VNET and service - no public IPs, only private - you create it for subnet
- Azure private link service
- Express route 
- Virtual WAN
