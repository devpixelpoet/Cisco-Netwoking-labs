# Cisco Real-Hardware DHCP Configuration Project

Ushbu loyihada o'quv markazidagi real Cisco router (fizik qurilma) ustida MobaXterm va konsol kabeli (COM3) orqali LAN tarmog'i uchun DHCP xizmati muvaffaqiyatli sozlangan. Shuningdek, loyihaning simulyatsiya varianti Cisco Packet Tracer dasturida ham ishlab chiqilgan.

## 🛠 Ishlatilgan texnologiyalar va uskunalar
- **Hardware:** Real Cisco Router & Switch
- **Software:** MobaXterm (Serial Console), Cisco Packet Tracer
- **Protocols:** DHCP, IPv4 Subnetting

## 🌐 Tarmoq arxitekturasi (Network Topology)
- **LAN Network:** 192.168.1.0/24
- **Gateway (Router IP):** 192.168.1.1
- **Excluded IPs (Band qilingan manzillar):** 192.168.1.1 (Gateway uchun chiqarib tashlangan)
- **DNS Server:** 1.1.1.1

## 💻 Konfiguratsiya buyruqlari (Cisco CLI)

```cisco
Router> enable
Router# configure terminal

! DHCP Pool yaratish
Router(config)# ip dhcp pool LAN-1
Router(dhcp-config)# network 192.168.1.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.1.1
Router(dhcp-config)# dns-server 1.1.1.1
Router(dhcp-config)# exit

! Gateway IP-ni tarqatishdan chiqarib tashlash
Router(config)# ip dhcp excluded-address 192.168.1.1

! Interfeysni sozlash va yoqish
Router(config)# interface fastEthernet 0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown

## 📸 Real laboratoriyadan foto
![Cisco Hardware DHCP]()
