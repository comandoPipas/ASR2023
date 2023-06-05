# ASR2023

## Informações

Projeto da unidade curricular de Administração de Sistemas em Rede:
+ Ficheiros de simulação do Cisco Packet Tracer das redes de cada edifício;
+ PDF com a vista sumária dos três edifícios e pisos e das redes utilizadas em cada um;
+ Plantas dos edifícios.

Realizado por:
+ Jorge Pissarra, A39489
+ Sara Martins, A44488-E10973

---

## Configurações dos Equipamentos

### Exterior (Internet)

#### Configuração do *Router*

**`2811 IOS15`**: `THE INTERNET`
+ `Fast Ethernet 0/0`: ligação ao `Main Router`
  + IPv4 Address: `1.1.1.2`
  + Subnet Mask: `255.0.0.0`
  + CLI:
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `minhaubi.org`
  + IPv4 Address: `2.2.2.1`
  + Subnet Mask: `255.0.0.0`
  + CLI:
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/0`: ligação ao `google`
  + IPv4 Address: `3.3.3.1`
  + Subnet Mask: `255.0.0.0`
  + CLI:
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `1.0.0.0`: rede de ligação à Internet
  + `2.0.0.0`: rede do servidor `minhaubi.org`
  + `3.0.0.0`: rede do servidor da Internet (Google)
+ CLI
  + `ipv6 unicast-routing`

#### Configuração dos Servidores

**`Server-PT`**: `minhaubi.org`
+ `Fast Ethernet 0`: ligação ao `THE INTERNET`
  + IPv4 Address: `2.2.2.2`
  + Subnet Mask: `255.0.0.0`
  + Default Gateway: `2.2.2.1`
  + DNS Server: `3.3.3.2`

**`Server-PT`**: `google`
+ `Fast Ethernet 0`: ligação ao `THE INTERNET`
  + IPv4 Address: `3.3.3.2`
  + Subnet Mask: `255.0.0.0`
  + Default Gateway: `3.3.3.1`
  + DNS Server: `3.3.3.2`

### Edifício 1 - XPTOtec_Oriente

#### Piso 0

##### Configuração dos *Routers*

**`2811 IOS15`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.25`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.1.98`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `THE INTERNET`
  + IPv4 Address: `1.1.1.1`
  + Subnet Mask: `255.0.0.0`
  + CLI:
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/0`: ligação ao `Nascente` (*multiuser*)
  + IPv4 Address: `192.168.20.1`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/1`: ligação ao `Leste` (*multiuser*)
  + IPv4 Address: `192.168.21.1`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `1.0.0.0`: rede de ligação à Internet
  + `2.0.0.0`: rede do servidor `minhaubi.org`
  + `3.0.0.0`: rede do servidor da Internet (Google)
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `Server Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.26`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.1.98`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.97`
  + Subnet Mask: `255.255.255.224`
  + CLI:
    + `ip helper-address 192.168.1.98`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `IoT Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.27`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.1.98`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `IoT Switch`
  + IPv4 Address: `192.168.2.1`
  + Subnet Mask: `255.255.255.0`
  + CLI:
    + `ip helper-address 192.168.1.98`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `PC Network Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.28`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.1.98`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `First Floor Switch`
  + IPv4 Address: `192.168.3.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.1.98`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/0`: ligação ao `Second Floor Switch`
  + IPv4 Address: `192.168.4.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.1.98`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/1`: ligação ao `Groundfloor Switch`
  + IPv4 Address: `192.168.5.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.1.98`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.5.0`: rede dos PCs do piso térreo
  + `192.168.10.0`: rede entre os *routers*
+ CLI
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
+ `Gigabit Ethernet 0/2`: ligação ao `OrienteController`
+ `Fast Ethernet 0/1`: ligação ao `DHCP`
+ `Fast Ethernet 0/2`: ligação ao `DNS`
+ `Fast Ethernet 0/3`: ligação ao `Email`
+ `Fast Ethernet 0/4`: ligação ao `TFTP`
+ `Fast Ethernet 0/5`: ligação ao `HTTP`
+ `Fast Ethernet 0/7`: ligação ao `OrienteAdmin`

**`2960-24TT`**: `IoT Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `IoT Router`
+ `Fast Ethernet 0/1`: ligação ao `First Floor IoT`
+ `Fast Ethernet 0/2`: ligação ao `Ground Floor IoT`
+ `Fast Ethernet 0/3`: ligação ao `Second Floor IoT`
+ `Fast Ethernet 0/4`: ligação ao `Water Shooter`
+ `Fast Ethernet 0/5`: ligação ao `Fire Detector`
+ `Fast Ethernet 0/6`: ligação ao `Card Reader`
+ `Fast Ethernet 0/7`: ligação ao `Blower`
+ `Fast Ethernet 0/8`: ligação ao `Laser`
+ `Fast Ethernet 0/24`: ligação ao `IoT Register`

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
    + Start IP Address: `192.168.2.3`
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
  + DNS (endereço IP)
    + Name: `ns1.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.1.99`
  + Email (Oriente)
    + Name: `mail.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.1.100`
  + Email (Nascente)
    + Name: `nascente.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.200.109`
  + Email (Leste)
    + Name: `leste.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.100.119`
  + HTTP (Oriente)
    + Name: `home.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.1.102`
  + HTTP (Nascente)
    + Name: `home-nascente.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.200.111`
  + HTTP (Leste)
    + Name: `home-leste.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.100.121`
  + IoT
    + Name: `iot.xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.1.103`
  + "Google"
    + Name: `ns1.org`
    + Type: `A Record`
    + Detail: `3.3.3.2`
  + "Google" (domínio `org`)
    + Name: `org`
    + Type: `NS`
    + Detail: `ns1.org`
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
+ `Fast Ethernet 0`: ligação ao `IoT Switch`
  + IPv4 Address: `192.168.2.2`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.2.1`
  + DNS Server: `192.168.1.99`
+ `Desktop` > `iot.xpto.tec`
  + Login:
    + Username: `admin`
    + Password: `admin`
  + Add Rule:
    + Name: `Fire Detected`
    + Condition: `Fire Detector` > `Fire Detected` > `true`
    + Then:
      + `Ground Floor Siren` >  `On` > `true`
      + `First Floor Siren` > `On` > `true`
      + `Second Floor Siren` > `On` > `true`
      + `Water Shooter` > `Status` > `true`
  + Add Rule:
    + Name: `Fire Over`
    + Condition: `Fire Detector` > `Fire Detected` > `false`
    + Then:
      + `Ground Floor Siren` >  `On` > `false`
      + `First Floor Siren` > `On` > `false`
      + `Second Floor Siren` > `On` > `false`
      + `Water Shooter` > `Status` > `false`
  + Add Rule:
    + Name: `Titanic`
    + Condition: `Water Level Jigamabob` > `Level` > `>` > `7`
    + Then: `Water Hole` > `Status` > `true`
  + Add Rule:
    + Name: `Sahara`
    + Condition: `Water Level Jigamabob` > `Level` > `=` > `0`
    + Then: `Water Hole` > `Status` > `false`
  + Add Rule:
    + Name: `Canary Stopped Singing`
    + Condition: `Smoke Detector` > `Level` > `>` > `50`
    + Then: `Smoke Window` > `On` > `true`
  + Add Rule: 
    + Name: `Canary Crispy`
    + Condition: `Smoke Detector` > `Level` > `>` > `65`
    + Then: `Blower` > `Status` > `High`
  + Add Rule:
    + Name: `Canary Sings Again`
    + Condition: `Smoke Detector` > `Level` > `<` > `30`
    + Then:
      + `Smoke Window` > `On` > `false`
      + `Blower` > `Status` > `Off`
  + Add Rule:
    + Name: `You Shall Pass`
    + Condition: `Card Reader` > `Card ID` > `=` > `1001`
    + Then: `Server Door` > `Lock` > `Unlock`
  + Add Rule:
    + Name: `You Shall Not Pass`
    + Condition: `Card Reader` > `Card ID` > `!=` > `1001`
    + Then: `Ground Floor Siren` > `On` > `true`
  + Add Rule:
    + Name: `Close Door`
    + Condition: `Door` > `Lock` > `Unlock`
    + Then: `Door` > `Lock` > `Lock`

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

##### Configuração da IoT

**`AccessPoint-PT`**: `Ground Floor IoT` - *access point* para dispositivos de IoT no rés do chão
+ `Port 1`: ligação por *wireless*
  + SSID: `IoT Network`
  + 2.4GHz Channel: 1
  + Coverage Range: 50
  + Authentication: `WPA2-PSK`
    + PSK Pass Phrase: `password`

**`Door`**: `Server Door`
+ `Wireless0`: ligação ao `Ground Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Water Level Monitor`**: `Water Level Jigamabob`
+ `Wireless0`: ligação ao `Ground Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Window`**: `Smoke Window`
+ `Wireless0`: ligação ao `Ground Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Carbon Dioxide Detector`**: `Smoke Detector`
+ `Wireless0`: ligação ao `Ground Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Siren`**: `Ground Floor Siren`
+ `Wireless0`: ligação ao `Ground Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Water Drain`**: `Water Hole`
+ `Wireless0`: ligação ao `Ground Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Blower`**: `Blower`
+ `Wireless0`: ligação ao `IoT Switch`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Fire Sprinkler`**: `Water Shooter`
+ `Fast Ethernet 0`: ligação ao `IoT Switch`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Fire Monitor`**: `Fire Detector`
+ `Fast Ethernet 0`: ligação ao `IoT Switch`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Trip Sensor`**: `Laser`
+ `Wireless0`: ligação ao `IoT Switch`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`RFID Reader`**: `Card Reader`
+ `Fast Ethernet 0`: ligação ao `IoT Switch`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

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

##### Configuração de IoT

**`AccessPoint-PT`**: `First Floor IoT` - *access point* para dispositivos de IoT no primeiro piso
+ `Port 1`: ligação por *wireless*
  + SSID: `IoT Network`
  + 2.4GHz Channel: 1
  + Coverage Range: 50
  + Authentication: `WPA2-PSK`
    + PSK Pass Phrase: `password`

**`Siren`**: `First Floor Siren`
+ `Wireless0`: ligação ao `First Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Appliance`**: `Coffee Maker`
+ `Wireless0`: ligação ao `First Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

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

##### Configuração da IoT

**`AccessPoint-PT`**: `Second Floor IoT` - *access point* para dispositivos de IoT no segundo piso
+ `Port 1`: ligação por *wireless*
  + SSID: `IoT Network`
  + 2.4GHz Channel: 1
  + Coverage Range: 50
  + Authentication: `WPA2-PSK`
    + PSK Pass Phrase: `password`

**`Temperature Monitor`**: `Thermometer`
+ `Wireless0`: ligação ao `Second Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Siren`**: `Second Floor Siren`
+ `Wireless0`: ligação ao `Second Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Air Conditioner`**: `A/C`
+ `Wireless0`: ligação ao `Ground Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

**`Furnace`**: `Heater`
+ `Wireless0`: ligação ao `Ground Floor IoT`
  + Default Gateway: `DHCP: iotoriente`
  + DNS Server: `DHCP: iotoriente`
  + IPv4 Address: `DHCP: iotoriente`
  + Subnet Mask: `DHCP: resdochao`
  + IoT Server: Remote Server
    + Server Address: `192.168.2.2`
    + Username: `admin`
    + Password: `admin`

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
    + `ip helper-address 192.168.200.108`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `Oriente` (*multiuser*)
  + IPv4 Address: `192.168.20.2`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.200.108`
    + `ipv6 enable
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/0`: ligação ao `Leste` (*multiuser*)
  + IPv4 Address: `192.168.22.1`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.200.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.200.0`: rede dos servidores
  + `192.168.6.0`: rede dos dispositivos IoT
  + `192.168.7.0`: rede dos PCs do primeiro piso
  + `192.168.8.0`: rede dos PCs do segundo piso
  + `192.168.9.0`: rede dos PCs do piso térreo
  + `192.168.11.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `Server Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.11.26`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.200.108`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.200.107`
  + Subnet Mask: `255.255.255.224`
  + CLI:
    + `ip helper-address 192.168.200.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.200.0`: rede dos servidores
  + `192.168.6.0`: rede dos dispositivos IoT
  + `192.168.7.0`: rede dos PCs do primeiro piso
  + `192.168.8.0`: rede dos PCs do segundo piso
  + `192.168.9.0`: rede dos PCs do piso térreo
  + `192.168.11.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `IoT Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.11.27`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.200.108`
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
    + `ip helper-address 192.168.200.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.200.0`: rede dos servidores
  + `192.168.6.0`: rede dos dispositivos IoT
  + `192.168.7.0`: rede dos PCs do primeiro piso
  + `192.168.8.0`: rede dos PCs do segundo piso
  + `192.168.9.0`: rede dos PCs do piso térreo
  + `192.168.11.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `PC Network Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.11.28`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.200.108`
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
    + `ip helper-address 192.168.200.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/0`: ligação ao `Second Floor Switch`
  + IPv4 Address: `192.168.8.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.200.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/1`: ligação ao `Ground Floor Switch`
  + IPv4 Address: `192.168.9.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.200.108`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.200.0`: rede dos servidores
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
+ `Fast Ethernet 0/6`: ligação ao `NascenteAdmin`

**`2960-24TT`**: `IoT Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `IoT Router`
+ `Fast Ethernet 0/24`: ligação ao `Registo IoT`

**`2960-24TT`**: `Ground Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Gigabit Ethernet 0/2`: ligação ao `Guest Access Point`

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.200.108`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.200.107`
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
    + Start IP Address: `192.168.6.3`
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
  + IPv4 Address: `192.168.200.109`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.200.107`
  + DNS Server: `192.168.1.99`
+ Serviços Email
  + Domain Name: `nascente.xpto.tec`
    + User: `admin` | Password: `admin`
    + User: `user1` | Password: `password`
    + User: `user2` | Password: `password`

###### Servidor FTP

**`Server-PT`**: `FTP` - servidor de FTP (*File Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.200.110`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.200.107`
  + DNS Server: `192.168.1.99`

###### Servidor HTTP

**`Server-PT`**: `HTTP` - servidor de HTTP (*HyperText Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.200.111`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.200.107`
  + DNS Server: `192.168.1.99`

###### Servidor de Registo IoT

**`Server-PT`** - servidor de Registo IoT (*Internet of Things*)
+ `Fast Ethernet 0`: ligação ao `IoT Switch`
  + IPv4 Address: `192.168.6.3`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.6.1`
  + DNS Server: `192.168.1.99`

###### *Network Controller*

**`NetworkController`**: `NascenteController` - controlador de rede
+ `Gigabit Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.200.113`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.200.107`
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
  + IPv4 Address: `192.168.200.114`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.200.107`
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
  + IPv4 Address: `192.168.12.25`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.100.118`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `Oriente` (*multiuser*)
  + IPv4 Address: `192.168.21.2`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/0`: ligação ao `Nascente` (*multiuser*)
  + IPv4 Address: `192.168.22.2`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.100.0`: rede dos servidores
  + `192.168.13.0`: rede dos dispositivos IoT
  + `192.168.14.0`: rede dos PCs do primeiro piso
  + `192.168.15.0`: rede dos PCs do segundo piso
  + `192.168.16.0`: rede dos PCs do piso térreo
  + `192.168.12.0`: rede entre os *routers*
  + `192.168.20.0`: rede entre
  + `192.168.21.0`: rede entre
  + `192.168.22.0`: 
+ CLI
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `Server Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.12.26`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.100.118`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.100.117`
  + Subnet Mask: `255.255.255.224`
  + CLI:
    + `ip helper-address 192.168.100.118`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.100.0`: rede dos servidores
  + `192.168.13.0`: rede dos dispositivos IoT
  + `192.168.14.0`: rede dos PCs do primeiro piso
  + `192.168.15.0`: rede dos PCs do segundo piso
  + `192.168.16.0`: rede dos PCs do piso térreo
  + `192.168.12.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `IoT Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.12.27`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.100.118`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `IoT Switch`
  + IPv4 Address: `192.168.13.1`
  + Subnet Mask: `255.255.255.0`
  + CLI:
    + `ip helper-address 192.168.100.118`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.100.0`: rede dos servidores
  + `192.168.13.0`: rede dos dispositivos IoT
  + `192.168.14.0`: rede dos PCs do primeiro piso
  + `192.168.15.0`: rede dos PCs do segundo piso
  + `192.168.16.0`: rede dos PCs do piso térreo
  + `192.168.12.0`: rede entre os *routers*
+ CLI
  + `ipv6 unicast-routing`
  + `enable password admin`
  + `line vty 0 15`
    + `password admin`
    + `login`
  + (após configurações): `copy running-config tftp` > `192.168.1.101`

**`2811 IOS15`**: `PC Network Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.12.28`
  + Subnet Mask: `255.255.255.248`
  + CLI:
    + `ip helper-address 192.168.100.118`
    + `ipv6 enable`
    + `ipv6 address 2001:AAAA:BBBB:CCCC::/64 eui-64` (*eui-64 global unicast address*)
    + `ipv6 address 2001:AAAA:BBBB:CCCC:1234:1234:1234:1234/64` (*manual global unicast address*)
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 0/1`: ligação ao `First Floor Switch`
  + IPv4 Address: `192.168.14.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.100.118`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/0`: ligação ao `Second Floor Switch`
  + IPv4 Address: `192.168.15.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.100.118`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Fast Ethernet 1/1`: ligação ao `Ground Floor Switch`
  + IPv4 Address: `192.168.16.1`
  + Subnet Mask: `255.255.255.192`
  + CLI:
    + `ip helper-address 192.168.100.118`
    + `ipv6 enable`
    + `ipv6 address FE80::AAAA:BBBB:CCCC:DDDD link-local` (*link local address*)
    + `ipv6 address autoconfig`
    + `ipv6 address dhcp`
+ `Routing RIP`
  + `192.168.100.0`: rede dos servidores
  + `192.168.13.0`: rede dos dispositivos IoT
  + `192.168.14.0`: rede dos PCs do primeiro piso
  + `192.168.15.0`: rede dos PCs do segundo piso
  + `192.168.16.0`: rede dos PCs do piso térreo
  + `192.168.12.0`: rede entre os *routers*
+ CLI
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
+ `Fast Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/2`: ligação ao `IoT Router`

**`2960-24TT`**: `Server Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Server Router`
+ `Gigabit Ethernet 0/2`: ligação ao `LesteController`
+ `Fast Ethernet 0/1`: ligação ao `DHCP`
+ `Fast Ethernet 0/2`: ligação ao `Email`
+ `Fast Ethernet 0/3`: ligação ao `FTP`
+ `Fast Ethernet 0/4`: ligação ao `HTTP`
+ `Fast Ethernet 0/6`: ligação ao `LesteAdmin`

**`2960-24TT`**: `IoT Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `IoT Router`
+ `Fast Ethernet 0/24`: ligação ao `Registo IoT`

**`2960-24TT`**: `First Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`
+ `Fast Ethernet 0/1`: ligação ao `PC0`
+ `Fast Ethernet 0/2`: ligação ao `PC1`

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.100.118`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.100.117`
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
    + Default Gateway: `192.168.13.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.13.3`
    + Subnet Mask: `255.255.255.0`
    + Maximum Number of Users: 254
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso 1
    + Pool Name: `primeiropiso`
    + Default Gateway: `192.168.14.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.14.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso 2
    + Pool Name: `segundopiso`
    + Default Gateway: `192.168.15.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.15.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`
  + Rede de PCs do piso térreo
    + Pool Name: `resdochao`
    + Default Gateway: `192.168.16.1`
    + DNS Server: `192.168.1.99`
    + Start IP Address: `192.168.16.2`
    + Subnet Mask: `255.255.255.192`
    + Maximum Number of Users: 30
    + TFTP Server: `192.168.1.101`
    + WLC Address: `0.0.0.0`

###### Servidor de Email

**`Server-PT`**: `Email` - servidor de e-mail
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.100.119`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.100.117`
  + DNS Server: `192.168.1.99`
+ Serviços Email
  + Domain Name: `leste.xpto.tec`
    + User: `admin` | Password: `admin`
    + User: `user1` | Password: `password`
    + User: `user2` | Password: `password`

###### Servidor FTP

**`Server-PT`**: `FTP` - servidor de FTP (*File Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.100.120`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.100.117`
  + DNS Server: `192.168.1.99`

###### Servidor HTTP

**`Server-PT`**: `HTTP` - servidor de HTTP (*HyperText Transfer Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.100.121`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.100.117`
  + DNS Server: `192.168.1.99`

###### Servidor de Registo IoT

**`Server-PT`**: `Registo IoT` - servidor de Registo IoT (*Internet of Things*)
+ `Fast Ethernet 0`: ligação ao `IoT Switch`
  + IPv4 Address: `192.168.13.2`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.13.1`
  + DNS Server: `192.168.1.99`

###### *Network Controller*

**`NetworkController`**: `LesteController` - controlador de rede
+ `Gigabit Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.100.123`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.100.117`
  + DNS Server: `192.168.1.99`

##### Configuração do Computador do Administrador de Sistemas

**`PC-PT`**: `LesteAdmin` - computador do administrador de sistemas do edifício XPTOtec_Leste
+ `Fast Ethernet 0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.100.124`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.100.117`
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

### Configurações Gerais

+ Definir a lista de controlo de acesso: `ip access-list extended <numero>`
  + Recusar ligação por TELNET aos *routers* a todos os utilizadores, exceto os três computadores do administrador de sistemas:
    + `permit tcp 192.168.1.105 224.255.255.255 any eq telnet`
    + `permit tcp 192.168.200.114 224.255.255.255 any eq telnet`
    + `permit tcp 192.168.100.124 224.255.255.255 any eq telnet`
    + `deny tcp any <ip-interface-externa> 0.0.0.0 eq telnet`
+ Adicionar a lista de controlo de acesso (a uma interface): `ip access-group <numero> in`

### Configurações Específicas

+ Main Router:
  + Negar acesso ao `minhaubi.org` (XPTOtec_Oriente):
    + `deny ip any 2.2.2.2 0.0.0.255`
  + Bloquear TFTP e FTP a partir da Internet (XPTOtec_Oriente):
    + `deny tcp any any eq ftp`
    + `deny udp any any eq tftp`
  + Permitir apenas acesso ICMP e HTTP à Internet (XPTOtec_Oriente):
    + `permit tcp any any eq 80`(80 é a porta TCP para o protocolo HTTP)
    + `permit icmp any any`
  + Permitir tráfego entre redes:
    + `permit ip any any`
+ PC Network Router:
  + Permitir tráfego entre redes:
    + `permit ip any any`
+ Server Router:
  + Permitir apenas ligação à Internet ou ao email da empresa:
    + `permit tcp any <ip-servidor-http> 0.0.0.0 eq www`
    + `deny tcp any <ip-servidor-http> 0.0.0.0`
    + `permit tcp any <ip-servidor-email> 0.0.0.0 eq smtp`
    + `deny tcp any <ip-servidor-email> 0.0.0.0`
  + Permitir ligação aos protocolos EIGRP, OSPF, RIP, BGP, DNS:
    + `permit eigrp any any`
    + `permit ospf any any`
    + `permit udp any any eq 520` (520 é a porta UDP para o protocolo RIP)
    + `permit tcp any any eq 179` (179 é a porta TCP para o protocolo BGP)
    + `permit udp any any eq domain`
  + Permitir ligação à rede de servidores do edifício XPTOtec_Oriente para TFTP:
    + `permit udp 192.168.1.101 0.0.0.0 <ip-interface-externa> 0.0.0.0`
+ IoT Router:
  + Permitir ligação aos protocolos DHCP, EIGRP, OSPF, RIP, BGP, NSS:
    + `permit udp any any eq 67` (67 e 68 são as portas UDP para o protocolo DHCP)
    + `permit udp any any eq 68` (no `show access-lists` aparecem como `bootps` e `bootpc`)
    + `permit eigrp any any`
    + `permit ospf any any`
    + `permit udp any any eq 520` (520 é a porta UDP para o protocolo RIP)
    + `permit tcp any any eq 179` (179 é a porta TCP para o protocolo BGP)
    + `permit tcp any any eq 170` (170 é a porta TCP para o protocolo NSS)
  + Permitir ligação à rede de servidores do edifício XPTOtec_Oriente para TFTP:
    + `permit udp 192.168.1.101 0.0.0.0 <ip-interface-externa> 0.0.0.0`