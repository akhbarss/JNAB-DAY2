# KONFIGURASI VLAN

## 1. Konfigurasi Switch

### bagian 1

- enable
- conf t
- vlan 100
- name marketing
- vlan 200
- name produksi
- vlan 300
- name keuangan
- exit

### Mode Access
- masuk menu config ( conf t )
---
- interface range fa0/1-8
- swicthport mode access
- swicthport access vlan 100
- exit

---

- interface range fa0/9-16
- swicthport mode access
- swicthport access vlan 200
- exit

---

- interface range fa0/17-24
- swicthport mode access
- swicthport access vlan 300
- exit

### Mode Trunk
- switchport  trunk allowed vlan 100,200,300

## 2. KONFIGURASI ROUTER
- interface fa0/0.100
- encapsulation dot1Q 100
- ip address 192.168.100.1 255.255.255.0
- exit
---
- interface fa0/0.200
- encapsulation dot1Q 200
- ip address 192.168.200.1 255.255.255.0
- exit
---
- interface ( fa0/0.300  / fa0/0.210 )
- encapsulation dot1Q 300
- ip address 192.168.210.1 255.255.255.0
- exit
