# KONFIGURASI VLAN

![alt text](https://github.com/akhbarss/JNAB-DAY2/blob/main/public/konfigurasi-vlan-image.jpg?raw=true)

# Ketentuan

#### VLAN 300
- Name : produksi
- Range Ethernet : FastEthernet0/1-8
- Network : 200.200.100.0/24

#### VLAN 400
- Name : marketing
- Range Ethernet : FastEthernet0/9-16
- Network : 200.200.200.0/24


# Emplementasi 
### 1. KONFIGURASI ROUTER
- enable
- conf t
- interface fa0/0.300
- encapsulation dot1Q 300
- ip address 200.200.100.1 255.255.255.0
- exit
---
- interface fa0/0.400
- encapsulation dot1Q 400
- ip address 200.200.200.1 255.255.255.0
- exit
---
- interface fa0/0
- no shutdown
- exit
- do wr

### 2. Konfigurasi Switch 1
Menambah vlan id pada switch pertama.

- enable
- conf t
- vlan 300
- name produksi
- vlan 400
- name marketing
- exit

Lalu konfigurasi access nya.
- masuk menu config ( conf t ) , jika belum
---
- interface range fa0/1-8
- switchport mode access
- switchport access vlan 300
- exit
---
- interface range fa0/9-16
- switchport mode access
- switchport access vlan 400
- exit
---
Lalu konfigurasi mode trunk nya.
- interface gigabitEthernet 0/1
- switchport mode trunk
- switchport trunk allowed vlan 300,400
- exit
- do wr

### 3. Konfigurasi Switch 2
Menambah vlan id pada switch kedua.

- enable
- conf t
- vlan 300
- name produksi
- vlan 400
- name marketing
- exit
---
Lalu konfigurasi access nya.
- interface range fa0/1-8
- switchport mode access
- switchport access vlan 300
- exit
---
- interface range fa0/9-16
- switchport mode access
- switchport access vlan 400
- exit
---
Lalu konfigurasi mode trunk nya.
- interface gigabitEthernet 0/1
- switchport mode trunk
- switchport trunk allowed vlan 300,400
- exit
- do wr