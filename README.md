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

-configure terminal
-interface gigabitEthernet (port number)
-switchport mode trunk
-switchport trunk allowed vlan (VLAN number)
-end

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
