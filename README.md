# ASR2023

## Informações

Projeto da unidade curricular de Administração de Sistemas em Rede:
+ Ficheiros de simulação do Cisco Packet Tracer das redes de cada edifício;
+ PDF com a vista sumária dos três edifícios e pisos e das redes utilizadas em cada um (TO-DO);
+ Plantas dos edifícios.

Realizado por:
+ Jorge Pissarra, A39489
+ Sara Martins, A44488-E10973

---

## Configurações dos Equipamentos

### Edifício 1 - XPTOtec_Oriente

#### Piso 0

##### Configuração dos *Routers*

**`2811 IOS15`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.25`
  + Subnet Mask: `255.255.255.248`
  + CLI: `ip helper-address 192.168.1.98`
+ `Gigabit Ethernet 6/0`: ligação ao `Nascente` (*multiuser*)
+ `Gigabit Ethernet 7/0`: ligação ao `Leste` (*multiuser*)
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `Server Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.26`
  + Subnet Mask: `255.255.255.248`
  + CLI: `ip helper-address 192.168.1.98`
+ `Fast Ethernet 1/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.97`
  + Subnet Mask: `255.255.255.224`
  + CLI: `ip helper-address 192.168.1.98`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `IoT Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.27`
  + Subnet Mask: `255.255.255.248`
  + CLI: `ip helper-address 192.168.1.98`
+ `Fast Ethernet 0/1`: ligação ao `IoT Switch`
  + IPv4 Address: `192.168.2.1`
  + Subnet Mask: `255.255.255.0`
  + CLI: `ip helper-address 192.168.1.98`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `PC Network Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.28`
  + Subnet Mask: `255.255.255.248`
  + CLI: `ip helper-address 192.168.1.98`
+ `Fast Ethernet 1/0`: ligação ao `First Floor Switch`
  + IPv4 Address: `192.168.3.1`
  + Subnet Mask: `255.255.255.192`
  + CLI: `ip helper-address 192.168.1.98`
+ `Fast Ethernet 6/0`: ligação ao `Second Floor Switch`
  + IPv4 Address: `192.168.4.1`
  + Subnet Mask: `255.255.255.192`
  + CLI: `ip helper-address 192.168.1.98`
+ `Fast Ethernet 7/0`: ligação ao `Groundfloor Switch`
  + IPv4 Address: `192.168.5.1`
  + Subnet Mask: `255.255.255.192`
  + CLI: `ip helper-address 192.168.1.98`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI (após configurações): `copy running-config tftp` > `192.168.1.101`

##### Configuração dos *Switches*

**`2960-24TT`**: `Main Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Main Router`
+ `Gigabit Ethernet 0/2`: ligação ao `Server Router`
+ `Fast Ethernet 0/1`: ligação ao `IoT Router`
+ `Fast Ethernet 0/2`: ligação ao `PC Network Router`

**`2960-24TT`**: `Server Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Server Router`
+ `Gigabit Ethernet 0/2`: ligação ao `OrienteController`
+ `Fast Ethernet 0/1`: ligação ao `DHCP`
+ `Fast Ethernet 0/2`: ligação ao `DNS`
+ `Fast Ethernet 0/3`: ligação ao `Email`
+ `Fast Ethernet 0/4`: ligação ao `TFTP`
+ `Fast Ethernet 0/5`: ligação ao `HTTP`
+ `Fast Ethernet 0/6`: ligação ao `IoT Register`
+ `Fast Ethernet 0/7`: ligação ao `OrienteAdmin`

**`2960-24TT`**: `IoT Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `IoT Router`
+ `Fast Ethernet 0/1`: ligação a `Access Point IoT`

**`2960-24TT`**: `Ground Floor Switch`
+ `Fast Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/2`: ligação ao `PC1`
+ `Fast Ethernet 0/3`: ligação ao `PC0`
+ `Fast Ethernet 0/4`: ligação ao `PC2`
+ `Fast Ethernet 0/5`: ligação ao `PC3`

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.98`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.97`
  + DNS Server: `192.168.1.99`
+ Serviços DHCP
  + Rede base
    + Pool Name: `serverpool`
    + Default Gateway: `192.168.1.97`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.1.106`
    + Subnet Mask: `255.255.255.224`
    + Maximum Number of Users: 10
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede dos dispositivos IoT
    + Pool Name: `iotoriente`
    + Default Gateway: `192.168.2.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.2.2`
    + Subnet Mask: `255.255.255.0`
    + Maximum Number of Users: 254
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso 1
    + Pool Name: `primeiropiso`
    + Default Gateway: `192.168.3.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.3.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso 2
    + Pool Name: `segundopiso`
    + Default Gateway: `192.168.4.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.4.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso térreo
    + Pool Name: `resdochao`
    + Default Gateway: `192.168.5.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.5.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`

###### Servidor DNS

**`Server-PT`**: `DNS` - servidor de DNS (*Domain Name Service*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.99`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.97`
  + DNS Server: `192.168.1.99`
+ Serviços DNS
  + *Network Controller*
    + Name: `adminmachine`
    + Type: `A Record`
    + Detail: `192.168.1.104`
  + DNS (endereço textual)
    + Name: `ns1.xpto.tec`
    + Type: `NS`
    + Detail: `ns1.xpto.tec`
  + Email
    + Name: `mail.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.1.100`
  + DNS (endereço IP)
    + Name: `ns1.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.1.99`
  + HTTP
    + Name: `home.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.1.102`
  + IoT
    + Name: `iot.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.1.103`
  + SOA (*Start of Authority*)
    + Name: `xpto.tec`
    + Type: `SOA`
    + Detail: 
      + Primary Server Name: `ns1.xpto.tec`
      + Mail Box: `mail.xpto.tec`
      + Minimum TTL: `12000`
      + Refresh Time: `86400`
      + Retry Time: `86400`
      + Expiry Time: `2592000`

###### Servidor de Email

**`Server-PT`**: `Email` - servidor de e-mail
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.100`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.97`
  + DNS Server: `192.168.1.99`
+ Serviços Email
  + Domain Name: `xpto.tec`
    + User: `password` | Password: `user`
    + User: `user` | Password: `password`
    + User: `admin` | Password: `password`
    + User: `ceo` | Password: `password`

###### Servidor TFTP

**`Server-PT`**: `TFTP` - servidor de TFTP (*Trivial File Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.101`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.97`
  + DNS Server: `192.168.1.99`

###### Servidor HTTP

**`Server-PT`**: `HTTP` - servidor de HTTP (*HyperText Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.102`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.97`
  + DNS Server: `192.168.1.99`

###### Servidor de Registo IoT

**`Server-PT`**: `IoT Register` - servidor de Registo IoT (*Internet of Things*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.103`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.97`
  + DNS Server: `192.168.1.99`

###### *Network Controller*

**`NetworkController`**: `OrienteControl` - controlador de rede
+ `Gigabit Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.104`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.97`
  + DNS Server: `192.168.1.99`

##### Configuração do Computador do Administrador de Sistemas

**`PC-PT`**: `OrienteAdmin` - computador do administrador de sistemas do edifício XPTOtec_Oriente
+ `Fast Ethernet 0`: ligação ao `First floor Switch`
  + IPv4 Address: `192.168.1.105`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.97`
  + DNS Server: `192.168.1.99`
+ Desktop > Web Browser > `adminmachine`
  + Login:
    + Username: `admin`
    + Password: `admin`
  + Menu > Provisioning > Credentials
    + \+ Credential
      + Username: `admin`
      + Password: `admin`
      + Enable Password: `admin`
      + Description: `admin`
  + Menu > Provisioning > Network Device
    + \+ Device
      + IP Address: `192.168.1.97`
      + CLI Credential: `admin - admin`
    + \+ Device
      + IP Address: `192.168.2.1`
      + CLI Credential: `admin - admin`
    + \+ Device
      + IP Address: `192.168.4.1`
      + CLI Credential: `admin - admin`
  + Menu > Assurance > Hosts
    + ??

##### Configuração da IoT

**`AccessPoint-PT`**: `IoT Access Point` - *access point* para dispositivos de IoT
+ `Port 1`: ligação por *wireless*
  + SSID: `IoT Network`
  + 2.4GHz Channel: 1
  + Coverage Range: 50
  + Authentication: `WPA2-PSK`
    + PSK Pass Phrase: `password`

###### Ar Condicionado

###### Detetor de Incêndio

###### Dispersores de Água

###### Ralos de Extração de Água

###### Detetores de CO2

###### RFID (*Radio Frequency Identification*)

##### Configuração dos Computadores-exemplo

**`PC-PT`**: `PC0`
+ `Fast Ethernet 0`: ligação ao `Ground Floor Switch`
  + Default Gateway: `DHCP: resdochao`
  + DNS Server: `DHCP: resdochao`
  + IPv4 Address: `DHCP: resdochao`
  + Subnet Mask: `DHCP: resdochao`

**`PC-PT`**: `PC1`
+ `Fast Ethernet 0`: ligação ao `Ground Floor Switch`
  + Default Gateway: `DHCP: resdochao`
  + DNS Server: `DHCP: resdochao`
  + IPv4 Address: `DHCP: resdochao`
  + Subnet Mask: `DHCP: resdochao`

**`PC-PT`**: `PC2`
+ `Fast Ethernet 0`: ligação ao `Ground Floor Switch`
  + Default Gateway: `DHCP: resdochao`
  + DNS Server: `DHCP: resdochao`
  + IPv4 Address: `DHCP: resdochao`
  + Subnet Mask: `DHCP: resdochao`

**`PC-PT`**: `PC3`
+ `Fast Ethernet 0`: ligação ao `Ground Floor Switch`
  + Default Gateway: `DHCP: resdochao`
  + DNS Server: `DHCP: resdochao`
  + IPv4 Address: `DHCP: resdochao`
  + Subnet Mask: `DHCP: resdochao`

#### Piso 1

##### Configuração do *Switch*

**`2960-24TT`**: `First Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/1`: ligação ao `PC4`
+ `Fast Ethernet 0/2`: ligação ao `PC5`
+ `Fast Ethernet 0/3`: ligação ao `PC6`
+ `Fast Ethernet 0/4`: ligação ao `PC7`

##### Configuração dos Computadores-exemplo

**`PC-PT`**: `PC4`
+ `Fast Ethernet 0`: ligação ao `First Floor Switch`
  + Default Gateway: `DHCP: primeiropiso`
  + DNS Server: `DHCP: primeiropiso`
  + IPv4 Address: `DHCP: primeiropiso`
  + Subnet Mask: `DHCP: primeiropiso`

**`PC-PT`**: `PC5`
+ `Fast Ethernet 0`: ligação ao `First Floor Switch`
  + Default Gateway: `DHCP: primeiropiso`
  + DNS Server: `DHCP: primeiropiso`
  + IPv4 Address: `DHCP: primeiropiso`
  + Subnet Mask: `DHCP: primeiropiso`

**`PC-PT`**: `PC6`
+ `Fast Ethernet 0`: ligação ao `First Floor Switch`
  + Default Gateway: `DHCP: primeiropiso`
  + DNS Server: `DHCP: primeiropiso`
  + IPv4 Address: `DHCP: primeiropiso`
  + Subnet Mask: `DHCP: primeiropiso`

**`PC-PT`**: `PC7`
+ `Fast Ethernet 0`: ligação ao `First Floor Switch`
  + Default Gateway: `DHCP: primeiropiso`
  + DNS Server: `DHCP: primeiropiso`
  + IPv4 Address: `DHCP: primeiropiso`
  + Subnet Mask: `DHCP: primeiropiso`

##### Configuração da IoT

###### *Appliances* (Cafeteira)

#### Piso 2

##### Configuração do *Switch*

**`2960-24TT`**: `Second Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/1`: ligação ao `Guest Access Point`
+ `Fast Ethernet 0/2`: ligação ao `Laptop1`

##### Configuração do *Access Point*

**`AccessPoint-PT`**: `Guest Access Point` - *access point* para dispositivos convidados
+ `Port 1`: ligação por *wireless*
  + SSID: `convidados`
  + 2.4GHz Channel: 6
  + Coverage Range: 100
  + Authentication: `WPA2-PSK`
    + PSK Pass Phrase: `guests@xpto`

##### Configuração dos Computadores-exemplo

**`Laptop-PT`**: `Laptop0`
+ `Bluetooth`: ligação *wireless* ao `Guest Access Point`
  + Default Gateway: `DHCP: segundopiso`
  + DNS Server: `DHCP: segundopiso`
  + IPv4 Address: `DHCP: segundopiso`
  + Subnet Mask: `DHCP: segundopiso`

**`Laptop-PT`**: `Laptop1`
+ `Fast Ethernet 0`: ligação ao `Second Floor Switch`
  + Default Gateway: `DHCP: segundopiso`
  + DNS Server: `DHCP: segundopiso`
  + IPv4 Address: `DHCP: segundopiso`
  + Subnet Mask: `DHCP: segundopiso`



### Edifício 2 - XPTOtec_Nascente

#### Piso 0

##### Configuração dos *Routers*

**`2811 IOS15`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.11.25`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.1.108`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `Oriente` (*multiuser*)
+ `Fast Ethernet 1/0`: ligação ao `Leste` (*multiuser*)
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.6.0`: rede dos dispositivos IoT
  + `192.168.7.0`: rede dos PCs do primeiro piso
  + `192.168.8.0`: rede dos PCs do segundo piso
  + `192.168.9.0`: rede dos PCs do piso térreo
  + `192.168.11.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `Server Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.11.26`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.1.108`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.107`
  + Subnet Mask: `255.255.255.224`
  + CLI:
    + `ip helper-address 192.168.1.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.6.0`: rede dos dispositivos IoT
  + `192.168.7.0`: rede dos PCs do primeiro piso
  + `192.168.8.0`: rede dos PCs do segundo piso
  + `192.168.9.0`: rede dos PCs do piso térreo
  + `192.168.11.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `IoT Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.11.27`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.1.108`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `IoT Switch`
  + IPv4 Address: `192.168.6.1`
  + Subnet Mask: `255.255.255.0`
  + CLI:
    + `ip helper-address 192.168.1.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.6.0`: rede dos dispositivos IoT
  + `192.168.7.0`: rede dos PCs do primeiro piso
  + `192.168.8.0`: rede dos PCs do segundo piso
  + `192.168.9.0`: rede dos PCs do piso térreo
  + `192.168.11.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `PC Network Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.11.28`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.1.108`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `First Floor Switch`
  + IPv4 Address: `192.168.7.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.1.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/0`: ligação ao `Second Floor Switch`
  + IPv4 Address: `192.168.8.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.1.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/1`: ligação ao `Ground Floor Switch`
  + IPv4 Address: `192.168.9.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.1.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.6.0`: rede dos dispositivos IoT
  + `192.168.7.0`: rede dos PCs do primeiro piso
  + `192.168.8.0`: rede dos PCs do segundo piso
  + `192.168.9.0`: rede dos PCs do piso térreo
  + `192.168.11.0`: rede entre os *routers*
+ CLI:
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

##### Configuração dos *Switches*

**`2960-24TT`**: `Main Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Main Router`
+ `Gigabit Ethernet 0/2`: ligação ao `Server Router`
+ `Fast Ethernet 0/1`: ligação ao `IoT Router`
+ `Fast Ethernet 0/2`: ligação ao `PC Network Router`

**`2960-24TT`**: `Server Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Server Router`
+ `Gigabit Ethernet 0/2`: ligação ao `NascenteController`
+ `Fast Ethernet 0/1`: ligação ao `DHCP`
+ `Fast Ethernet 0/2`: ligação ao `Email`
+ `Fast Ethernet 0/3`: ligação ao `FTP`
+ `Fast Ethernet 0/4`: ligação ao `HTTP`
+ `Fast Ethernet 0/5`: ligação ao `Registo IoT`
+ `Fast Ethernet 0/6`: ligação ao `NascenteAdmin`

**`2960-24TT`**: `IoT Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `IoT Router`

**`2960-24TT`**: `Ground Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Gigabit Ethernet 0/2`: ligação ao `Guest Access Point`

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.108`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.107`
  + DNS Server: `192.168.1.99`
+ Serviços DHCP
  + Rede base
    + Pool Name: `serverpool`
    + Default Gateway: `192.168.1.97`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.1.106`
    + Subnet Mask: `255.255.255.224`
    + Maximum Number of Users: 10
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede dos dispositivos IoT
    + Pool Name: `iotnascente`
    + Default Gateway: `192.168.6.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.6.2`
    + Subnet Mask: `255.255.255.0`
    + Maximum Number of Users: 254
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso 1
    + Pool Name: `primeiropiso`
    + Default Gateway: `192.168.7.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.7.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso 2
    + Pool Name: `segundopiso`
    + Default Gateway: `192.168.8.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.8.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso térreo
    + Pool Name: `resdochao`
    + Default Gateway: `192.168.9.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.9.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number os Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`

###### Servidor de Email

**`Server-PT`**: `Email` - servidor de e-mail
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.109`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.107`
  + DNS Server: `192.168.1.99`
+ Serviços Email
  + Domain Name: `nascente.xpto.tec`
    + User: `admin` | Password: `admin`
    + User: `user1` | Password: `password`
    + User: `user2` | Password: `password`

###### Servidor FTP

**`Server-PT`**: `FTP` - servidor de FTP (*File Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.110`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.107`
  + DNS Server: `192.168.1.99`

###### Servidor HTTP

**`Server-PT`**: `HTTP` - servidor de HTTP (*HyperText Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.111`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.107`
  + DNS Server: `192.168.1.99`

###### Servidor de Registo IoT

**`Server-PT`** - servidor de Registo IoT (*Internet of Things*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.112`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.107`
  + DNS Server: `192.168.1.99`

###### *Network Controller*

**`NetworkController`**: `NascenteController` - controlador de rede
+ `Gigabit Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.113`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.107`
  + DNS Server: `192.168.1.99`

##### Configuração do *Access Point*

**`AccessPoint-PT`**: `Guest Access Point` - *access point* para dispositivos convidados
+ `Port 1`: ligação por *wireless*
  + SSID: `convidados`
  + 2.4GHz Channel: 6
  + Coverage Range: 100
  + Authentication: `WPA2-PSK`
    + PSK Pass Phrase: `guests@xpto`

##### Configuração do Computador do Administrador de Sistemas

**`PC-PT`**: `NascenteAdmin` - computador do administrador de sistemas do edifício XPTOtec_Nascente
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.114`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.107`
  + DNS Server: `192.168.1.99`

##### Configuração do Computador-exemplo

#### Piso 1

##### Configuração do *Switch*

**`2960-24TT`**: `First Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/1`: ligação ao `PC0`
+ `Fast Ethernet 0/2`: ligação ao `PC1`

##### Configuração dos Computadores-exemplo

**`PC-PT`**: `PC0`
+ `Fast Ethernet 0`: ligação ao `First Floor Switch`
  + Default Gateway: `DHCP: primeiropiso`
  + DNS Server: `DHCP: primeiropiso`
  + IPv4 Address: `DHCP: primeiropiso`
  + Subnet Mask: `DHCP: primeiropiso`

**`PC-PT`**: `PC1`
+ `Fast Ethernet 0`: ligação ao `First Floor Switch`
  + Default Gateway: `DHCP: primeiropiso`
  + DNS Server: `DHCP: primeiropiso`
  + IPv4 Address: `DHCP: primeiropiso`
  + Subnet Mask: `DHCP: primeiropiso`

#### Piso 2

##### Configuração do *Switch*

**`2960-24TT`**: `Second Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/1`: ligação ao `PC2`
+ `Fast Ethernet 0/2`: ligação ao `PC3`

##### Configuração dos Computadores-exemplo

**`PC-PT`**: `PC2`
+ `Fast Ethernet 0`: ligação *wireless* ao `Guest Access Point`
  + Default Gateway: `DHCP: segundopiso`
  + DNS Server: `DHCP: segundopiso`
  + IPv4 Address: `DHCP: segundopiso`
  + Subnet Mask: `DHCP: segundopiso`

**`PC-PT`**: `PC3`
+ `Fast Ethernet 0`: ligação ao `Second Floor Switch`
  + Default Gateway: `DHCP: segundopiso`
  + DNS Server: `DHCP: segundopiso`
  + IPv4 Address: `DHCP: segundopiso`
  + Subnet Mask: `DHCP: segundopiso`



### Edifício 3 - XPTOtec_Leste

#### Piso 0

##### Configuração do *Switch*

**`Switch-PT`**: `Ground Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Gigabit Ethernet 0/2`: ligação ao `Guest Access Point`

##### Configuração do *Access Point*

**`AccessPoint-PT`**: `Guest Access Point` - *access point* para dispositivos convidados
+ `Port 1`: ligação por *wireless*
  + SSID: `convidados`
  + 2.4GHz Channel: 6
  + Coverage Range: 100
  + Authentication: `WPA2-PSK`
    + PSK Pass Phrase: `guests@xpto`

#### Piso 1

##### Configuração dos *Routers*

**`2811 IOS15`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.25`
  + Subnet Mask: `255.255.255.248`
  + CLI: `ip helper-address 192.168.1.118`
+ `Gigabit Ethernet 6/0`: ligação ao `Nascente` (*multiuser*)
+ `Gigabit Ethernet 7/0`: ligação ao `Oriente` (*multiuser*)
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `Server Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.26`
  + Subnet Mask: `255.255.255.248`
  + CLI: `ip helper-address 192.168.1.118`
+ `Fast Ethernet 1/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.117`
  + Subnet Mask: `255.255.255.224`
  + CLI: `ip helper-address 192.168.1.118`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `IoT Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.27`
  + Subnet Mask: `255.255.255.248`
  + CLI: `ip helper-address 192.168.1.118`
+ `Fast Ethernet 0/1`: ligação ao `IoT Switch`
  + IPv4 Address: `192.168.2.1`
  + Subnet Mask: `255.255.255.0`
  + CLI: `ip helper-address 192.168.1.118`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `PC Network Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.28`
  + Subnet Mask: `255.255.255.248`
  + CLI: `ip helper-address 192.168.1.118`
+ `Fast Ethernet 1/0`: ligação ao `First Floor Switch`
  + IPv4 Address: `192.168.3.1`
  + Subnet Mask: `255.255.255.192`
  + CLI: `ip helper-address 192.168.1.118`
+ `Fast Ethernet 6/0`: ligação ao `Second Floor Switch`
  + IPv4 Address: `192.168.4.1`
  + Subnet Mask: `255.255.255.192`
  + CLI: `ip helper-address 192.168.1.118`
+ `Fast Ethernet 7/0`: ligação ao `Ground Floor Switch`
  + IPv4 Address: `192.168.5.1`
  + Subnet Mask: `255.255.255.192`
  + CLI: `ip helper-address 192.168.1.118`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI (após configurações): `copy running-config tftp` > `192.168.1.101`

##### Configuração dos *Switches*

**`2960-24TT`**: `Main Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Main Router`
+ `Gigabit Ethernet 0/2`: ligação ao `Server Router`
+ `Fast Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/2`: ligação ao `IoT Router`

**`2960-24TT`**: `Server Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Server Router`
+ `Gigabit Ethernet 0/2`: ligação ao `LesteController`
+ `Fast Ethernet 0/1`: ligação ao `DHCP`
+ `Fast Ethernet 0/2`: ligação ao `Email`
+ `Fast Ethernet 0/3`: ligação ao `FTP`
+ `Fast Ethernet 0/4`: ligação ao `HTTP`
+ `Fast Ethernet 0/5`: ligação ao `Registo IoT`
+ `Fast Ethernet 0/6`: ligação ao `LesteAdmin`

**`2960-24TT`**: `IoT Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `IoT Router`

**`2960-24TT`**: `First Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/1`: ligação ao `PC0`
+ `Fast Ethernet 0/2`: ligação ao `PC1`

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.118`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.117`
  + DNS Server: `192.168.1.99`
+ Serviços DHCP
  + Rede base
    + Pool Name: `serverpool`
    + Default Gateway: `192.168.1.97`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.1.106`
    + Subnet Mask: `255.255.255.224`
    + Maximum Number of Users: 10
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede dos dispositivos IoT
    + Pool Name: `iotleste`
    + Default Gateway: `192.168.2.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.2.2`
    + Subnet Mask: `255.255.255.0`
    + Maximum Number of Users: 254
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso 1
    + Pool Name: `primeiropiso`
    + Default Gateway: `192.168.3.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.3.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso 2
    + Pool Name: `segundopiso`
    + Default Gateway: `192.168.4.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.4.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso térreo
    + Pool Name: `resdochao`
    + Default Gateway: `192.168.5.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.5.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`

###### Servidor de Email

**`Server-PT`**: `Email` - servidor de e-mail
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.119`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.117`
  + DNS Server: `192.168.1.99`
+ Serviços Email
  + Domain Name: `leste.xpto.tec`
    + User: `admin` | Password: `admin`
    + User: `user1` | Password: `password`
    + User: `user2` | Password: `password`

###### Servidor FTP

**`Server-PT`**: `FTP` - servidor de FTP (*File Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.120`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.117`
  + DNS Server: `192.168.1.99`

###### Servidor HTTP

**`Server-PT`**: `HTTP` - servidor de HTTP (*HyperText Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.121`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.117`
  + DNS Server: `192.168.1.99`

###### Servidor de Registo IoT

**`Server-PT`**: `Registo IoT` - servidor de Registo IoT (*Internet of Things*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.122`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.117`
  + DNS Server: `192.168.1.99`

###### *Network Controller*

**`NetworkController`**: `LesteController` - controlador de rede
+ `Gigabit Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.123`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.117`
  + DNS Server: `192.168.1.99`

##### Configuração do Computador do Administrador de Sistemas

**`PC-PT`**: `LesteAdmin` - computador do administrador de sistemas do edifício XPTOtec_Leste
+ `Fast Ethernet 0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.1.124`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.117`
  + DNS Server: `192.168.1.99`

##### Configuração dos Computadores-exemplo

**`PC-PT`**: `PC0`
+ `Fast Ethernet 0`: ligação ao `First Floor Switch`
  + Default Gateway: `DHCP: primeiropiso`
  + DNS Server: `DHCP: primeiropiso`
  + IPv4 Address: `DHCP: primeiropiso`
  + Subnet Mask: `DHCP: primeiropiso`

**`PC-PT`**: `PC1`
+ `Fast Ethernet 0`: ligação ao `First Floor Switch`
  + Default Gateway: `DHCP: primeiropiso`
  + DNS Server: `DHCP: primeiropiso`
  + IPv4 Address: `DHCP: primeiropiso`
  + Subnet Mask: `DHCP: primeiropiso`

#### Piso 2

##### Configuração do *Switch*

**`2960-24TT`**: `Second Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/1`: ligação ao `PC2`
+ `Fast Ethernet 0/2`: ligação ao `PC3`

##### Configuração dos Computadores-exemplo

**`PC-PT`**: `PC2`
+ `Fast Ethernet 0`: ligação ao `Second Floor Switch`
  + Default Gateway: `DHCP: segundopiso`
  + DNS Server: `DHCP: segundopiso`
  + IPv4 Address: `DHCP: segundopiso`
  + Subnet Mask: `DHCP: segundopiso`

**`PC-PT`**: `PC3`
+ `Fast Ethernet 0`: ligação ao `Second Floor Switch`
  + Default Gateway: `DHCP: segundopiso`
  + DNS Server: `DHCP: segundopiso`
  + IPv4 Address: `DHCP: segundopiso`
  + Subnet Mask: `DHCP: segundopiso`

---

## Configurações de Segurança

ACLs.