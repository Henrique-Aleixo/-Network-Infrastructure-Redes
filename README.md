# Network Infrastructure Redes
___
## **Introduction**
The main objective of this project is the construction of a communication infrastructure for the company Redes e Ligações Lda. headquartered in Lisbon and branches in Porto, Portimão, Coimbra, and Beja.

## **Installation guide**

To run the network, you need to pull the repository.
Then, install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) and open the ProjetoFinal.pkt

## **Implemented Model**
![image](https://github.com/Henrique-Aleixo/-Network-Infrastructure-Redes/assets/95305819/86bfe429-3d93-45f3-b3cd-62ee7f7071ab)

## **PCs/Switches Creation and Configuration**
Based on the desired departments, a model with 3 floors was implemented for the Lisbon headquarters and 1 floor for each other headquarters, namely Porto, Coimbra, Portimão, and Beja.

Additionally, for each department in a branch, 2 computers were provided.

Therefore, the logical division of resources such as PCs and Switches was started, followed by configuring the corresponding VLANs on each Switch.

Commands:
- [x] enable
- [x] configure terminal
- [x] vlan (VLAN number)
- [x] name (Department name)
- [x] exit
- [x] end
- [x] wr

VLANs:
- Human Resources -> VLAN10
- Marketing -> VLAN20
- Finance -> VLAN30
- Logistics -> VLAN40
- Administration -> VLAN50
- Information Technology -> VLAN60

## **Creating Connections and Access Ports**
After configuring the switches, the PCs were connected to the respective switches using 'Copper Straight-Through' cables and connecting to FastEthernet ports on both the PC and the switch. Next, the access ports were configured.

- configure terminal
- interface fastEthernet (port number)
- switchport mode access
- switchport access vlan (VLAN number)
- exit
- end

The following are the results obtained for each branch:

### Lisbon Model
![image](https://github.com/Henrique-Aleixo/-Network-Infrastructure-Redes/assets/95305819/3337bffd-99ac-4015-a198-55bcf38592aa)

Departments in the Lisbon branch: Human Resources, Marketing, Finance, Administration, and Information Technology

### Porto Model
![image](https://github.com/Henrique-Aleixo/-Network-Infrastructure-Redes/assets/95305819/86466293-4263-48e7-8e7d-1035987a6278)

Departments in the Porto branch: Human Resources, Marketing, Finance, Administration, and Information Technology

### Portimão Model
![image](https://github.com/Henrique-Aleixo/-Network-Infrastructure-Redes/assets/95305819/b3c697c7-a1a2-4bf2-b38f-211c4dc8a444)

Departments in the Portimão branch: Marketing, Finance, Logistics, Administration, and Information Technology

### Coimbra Model
![image](https://github.com/Henrique-Aleixo/-Network-Infrastructure-Redes/assets/95305819/9e53c290-b73b-4ce3-9677-bc92af3c5772)

Departments in the Coimbra branch: Marketing, Finance, Logistics, and Administration

### Beja Model
![image](https://github.com/Henrique-Aleixo/-Network-Infrastructure-Redes/assets/95305819/49b37243-bd09-427a-a8d4-45d38d42f158)

Departments in the Beja branch: Finance, Logistics, and Administration

## **Core Creation and Configuration**
At this stage, 2 Core switches were created, one exclusively for the Lisbon branch with 3 floors and the other Core for the remaining branches and servers. For the configuration of each Core, we began by creating the VLANs on them.

- [x] enable
- [x] configure terminal
- [x] vlan (VLAN number)
- [x] name (Department name)
- [x] exit
- [x] end
- [x] wr

Next, Copper Cross-Over cables were used to connect the Switches to the Core, establishing GigabitEthernet connections. Additionally, Trunk ports were configured for each Core.

- configure terminal
- interface gigabitEthernet (port number)
- switchport mode trunk
- switchport trunk allowed vlan (VLAN number)
- end

Lisbon Branch Core

![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/66ba06fa-7b5c-4e62-9045-ca5f60aa2b39)

Remaining Branches Core

![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/791aacaa-25da-4534-a4bd-18b5c248eae5)

## **Gateway Creation**
At this stage, VLAN interfaces were created on the Core, using the base address 172.16.0.0 and adapting according to the type of department.

- [x] interface vlan (vlan number)
- [x] ip address (subnet IP) 255.255.255.0
- [x] no shutdown
- [x] end

VLAN Attribution
- Human Resources -> VLAN10 – 172.16.10.0
- Marketing -> VLAN20 – 172.16.20.0
- Finance -> VLAN30 – 172.16.30.0
- Logistics -> VLAN40 – 172.16.40.0
- Administration -> VLAN50 – 172.16.50.0
- Information Technology -> VLAN60 – 172.16.60.0

## **Wireless Connection**
For the wireless connection, a laptop was used, connected to Floor 2 of the Lisbon branch with the following configurations:

![image](https://github.com/Henrique-Aleixo/-Network-Infrastructure-Redes/assets/95305819/6f8098d7-124f-4e2b-8747-2d16f08df60c)

## **Server Configuration (DHCP, DNS, FTP, TFTP)**
![image](https://github.com/Henrique-Aleixo/-Network-Infrastructure-Redes/assets/95305819/51f16b45-9ad0-48c8-8ee3-a55073074a24)

To enable communication between servers and VLANs appropriately, the servers listed above were deployed. 
Additionally, a VLAN70 named "Server" was created on the switch connected to the various servers and correspondingly on the Core switches.

Here are the configurations for each type of server:

### **DHCP Server**
The DHCP (Dynamic Host Configuration Protocol) service automates the assignment of IPv4 addresses, subnet masks, gateways, and other network parameters. At this stage, the six services corresponding to the available departments were created, as the other PCs will be using a DHCP connection.

![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/12512a33-fb06-4f3e-9779-052a7bcb0fe4)

Right after the services were created, the IPv4 Gateway/DNS settings were changed to DHCP on each computer.

### **DNS Server**
It is a hierarchical and distributed system for managing names for computers, services, or any machine connected to the Internet or a private network. It associates various pieces of information with domain names and each participating entity.

![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/7ec5e158-b6b0-4cba-a5d9-e836fca5a87e)
![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/6da0c666-1b1f-4741-b519-39071989fcdc)

### **FTP Server**
It is a standard/generic and hardware-independent protocol that allows the transfer of files.

![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/89375bd1-072d-4284-9fd9-76ddb9039708)
![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/8d29a463-eacc-4bbd-920c-2924980573fb)

### **TFTP Server**
It is a very simple file transfer protocol, similar to FTP, through which it is also possible to save backup configuration files of devices.

![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/4a541c23-0591-4647-a87b-5aba5db868d8)
![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/4735ab7c-a293-450e-8509-51a363266553)

## **Default Routes and NAT Server**
A default route and VLAN80 were added to the core, as well as the configuration of NAT on the ISP (ISR4331). To make this process executable, a configuration was performed on the second ISR4331 named INTERNET, including a loopback interface. Finally, the routes were set on the ISP with the appropriate IPs.

![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/d1ca7fe6-baef-44a3-a852-9b57f97fc7c8)
![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/facd29ce-d39d-498b-bb9b-371757117143)
![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/f0fe485e-67f3-48ec-862a-1ff648bc63a2)

## **Connectivity Tests**
Connectivity tests were conducted through the command prompt of the PCs using the examples below, yielding the following results:

![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/055fef6d-14fa-484f-ba46-366064d77918)
![image](https://github.com/Henrique-Aleixo/Network-Infrastructure-Redes/assets/95305819/6b588dcc-85ed-4860-bf9a-1c12c782782f)

Other connectivity tests were also performed between PCs of the same department in the same branch or different branches, among others, and no problems were detected.
