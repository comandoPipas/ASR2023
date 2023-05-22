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

**`Router-PT`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.25`
  + Subnet Mask: `255.255.255.248`
+ `Gigabit Ethernet 6/0`: ligação ao `Nascente` (*multiuser*)
+ `Gigabit Ethernet 7/0`: ligação ao `Leste` (*multiuser*)
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.10.0`: rede entre os *routers*

**`Router-PT`**: `Server Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.26`
  + Subnet Mask: `255.255.255.248`
+ `Fast Ethernet 1/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.97`
  + Subnet Mask: `255.255.255.224`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.10.0`: rede entre os *routers*

**`Router-PT`**: `IoT Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.27`
  + Subnet Mask: `255.255.255.248`
+ `Fast Ethernet 0/1`: ligação ao `IoT Switch`
  + IPv4 Address: `192.168.2.1`
  + Subnet Mask: `255.255.255.0`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.10.0`: rede entre os *routers*

**`Router-PT`**: `PC Network Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.10.28`
  + Subnet Mask: `255.255.255.248`
+ `Fast Ethernet 1/0`: ligação ao `First Floor Switch`
  + IPv4 Address: `192.168.3.1`
  + Subnet Mask: `255.255.255.192`
+ `Fast Ethernet 6/0`: ligação ao `Second Floor Switch`
  + IPv4 Address: `192.168.4.1`
  + Subnet Mask: `255.255.255.192`
+ `Routing RIP`
  + `192.168.1.0`: rede dos servidores
  + `192.168.2.0`: rede dos dispositivos IoT
  + `192.168.3.0`: rede dos PCs do primeiro piso
  + `192.168.4.0`: rede dos PCs do segundo piso
  + `192.168.10.0`: rede entre os *routers*

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

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.98`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.97`
  + DNS Server: `192.168.1.99`
+ Serviços DHCP
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
    + Name: `dns.tec`
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
    + Name: `xpto.tec`
    + Type: `A Record`
    + Detail: `192.168.1.102`

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

**`AccessPoint-PT`**: `Access Point IoT` - *access point* para dispositivos de IoT
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

#### Piso 1

##### Configuração do *Switch*

**`2960-24TT`**: `First Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`

##### Configuração do Computador-exemplo

##### Configuração da IoT

###### *Appliances* (Cafeteira)

#### Piso 2

##### Configuração do *Switch*

**`2960-24TT`**: `Second Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`

##### Configuração do *Access Point*

**`AccessPoint-PT`**: `nome` - *access point* para dispositivos convidados
+ `Port 1`: ligação por *wireless*
  + SSID: `convidados`
  + 2.4GHz Channel: 6
  + Coverage Range: 50
  + Authentication: `WPA2-PSK`
    + PSK Pass Phrase: `guests@xpto`

##### Configuração do Computador-exemplo



### Edifício 2 - XPTOtec_Nascente

#### Piso 0

##### Configuração do *Router*

**`Router-PT`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`
+ `Gigabit Ethernet 6/0`: ligação ao `Oriente` (*multiuser*)
+ `Gigabit Ethernet 7/0`: ligação ao `Leste` (*multiuser*)

**`Router-PT`**: `Server Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`
+ `Fast Ethernet 1/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.107`
  + Subnet Mask: `255.255.255.224`

**`Router-PT`**: `IoT Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`
+ `Fast Ethernet 1/0`: ligação ao `IoT Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`

**`Router-PT`**: `PC Network Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`
+ `Fast Ethernet 1/0`: ligação ao `First Floor Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`
+ `Fast Ethernet 6/0`: ligação ao `Second Floor Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`

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

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.108`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.107`
  + DNS Server: `192.168.1.99`

###### Servidor de Email

**`Server-PT`**: `Email` - servidor de e-mail
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.109`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.107`
  + DNS Server: `192.168.1.99`

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

##### Configuração do Computador-exemplo

#### Piso 2

##### Configuração do *Switch*

**`2960-24TT`**: `Second Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`

##### Configuração do Computador-exemplo



### Edifício 3 - XPTOtec_Leste

#### Piso 0

#### Piso 1

##### Configuração do *Router*

**`Router-PT`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`
+ `Gigabit Ethernet 6/0`: ligação ao `Nascente` (*multiuser*)
+ `Gigabit Ethernet 7/0`: ligação ao `Oriente` (*multiuser*)

**`Router-PT`**: `Server Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`
+ `Fast Ethernet 1/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.117`
  + Subnet Mask: `255.255.255.224`

**`Router-PT`**: `IoT Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`
+ `Fast Ethernet 0/1`: ligação ao `IoT Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`

**`Router-PT`**: `PC Network Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`
+ `Fast Ethernet 1/0`: ligação ao `Second Floor Switch`
  + IPv4 Address: `x.x.x.x`
  + Subnet Mask: `x.x.x.x`

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

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.118`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.117`
  + DNS Server: `192.168.1.99`

###### Servidor de Email

**`Server-PT`**: `Email` - servidor de e-mail
+ `Fast Ethernet 0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.1.119`
  + Subnet Mask: `255.255.255.224`
  + Default Gateway: `192.168.1.117`
  + DNS Server: `192.168.1.99`

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

**`Server-PT`** - servidor de Registo IoT (*Internet of Things*)
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

##### Configuração do Computador-exemplo

#### Piso 2

##### Configuração do *Switch*

**`2960-24TT`**: `Second Floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `PC Network Router`

##### Configuração do Computador-exemplo

---

## Configurações de Segurança

ACLs.