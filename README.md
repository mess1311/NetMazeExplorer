# NetMazeExplorer

NetMazeExplorer project is designed to implement and manage virtual networking in Azure. In this project we will create a hybrid networking environment where on-premises networks connect securely to Azure resources using Azure's networking capabilities, ensuring secure data transition and effective resource access controls.


**Azure Services Used:**

 - Azure Virtual Networks
 - Azure VPN Gateway
 - Network Security Groups (NSGs)
 - Azure Bastion
 - Azure Private Link
 - Azure DNS
 - Azure Load Balancer

**Steps:**

**1. Azure Virtual Network Setup:**

Provision an Azure Virtual Network (VNet) named NetMazeVNET in France Central region. Create 4 subnets within this VNet to segregate resources effectively (WebAppSubnet, DatabaseSubnet, AdminSubnet, GatewaySubnet).

**2. On-Premises Network Simulation:**

To simulate your on-premises environment, deploy another VNet named OnPremVNET in Spain Central region.

**3. Secure Connectivity:**

Implemented Azure VPN Gateway to create a site-to-site VPN connection between the OnPremVNet and NetMazeVNet by creating:

 - NetMazeVPNGateway for NetMazeVNET
 - OnPremVPNGateway for OnPremVNET
 - Local network gateways to represent each environment in the opposite network
 - Site-to-site VPN connections: NetMazeToOnPrem and OnPremToNetMaze.

**4. Resource Deployment**

Deploy VMs in each subnet:
 - WebAppVM in WebAppSubnet (Windows Server with IIS installed)
 - DatabaseVM in DatabaseSubnet (Ubuntu Server with MySQL installed)
 - AdminVM in AdminSubnet (Windows Server with administrative tools)

**5. Network Access Control:**

Use Network Security Groups (NSGs) to define inbound and outbound access rules for each subnet, ensuring that only valid traffic is allowed:
 - WebAppNSG: Allows HTTP/HTTPS traffic to WebAppVM
 - DatabaseNSG: Allows MySQL and SSH traffic to DatabaseVM
 - AdminNSG: Allows RDP and SSH traffic to AdminVM

**6. Secure Administrative Access:**

Implement Azure Bastion for secure and seamless RDP and SSH access to your virtual machines, ensuring you don't expose your VMs to the public internet.

**7. Private Access to Azure PaaS Services:**

Use Azure Private Link to access Azure PaaS services (Azure SQL Database named NetMazeSQLDB) over a private endpoint within NetMazeVNET, ensuring data doesn't traverse over the public internet.

**8. DNS and Load Balancing:**

Configure Azure DNS with private DNS zone named netmaze.local to have custom domain names for your resources. Implement Azure Load Balancer named NetMazeLoadBalancer  to distribute traffic across your VMs in WebAppSubnet.

**9. Performance and Security Testing:**

Simulate various network scenarios to test performance, such as data transition between on-premises and Azure. Attempt to access resources from outside the permitted paths to validate the security configurations in place.

**10. Monitoring and Auditing:**

Enable monitoring and diagnostics on your VPN Gateway, NSGs, and other network resources to gain insights into network operations. Review logs and set up alerts for any suspicious activities.
