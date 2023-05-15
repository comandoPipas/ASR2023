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

##### Configuração do *Router*

**`Router-PT`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `192.168.0.1`
  + Subnet Mask: `255.255.255.0`

##### Configuração dos *Switches*

**`2960-24TT`**: `Main Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Main Router`
+ `Gigabit Ethernet 0/2`: ligação ao `Peer 0`
+ `Fast Ethernet 0/1`: ligação ao `Server Switch`
+ `Fast Ethernet 0/2`: ligação ao `First floor Switch`

**`2960-24TT`**: `Server Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Server Switch`
+ `Fast Ethernet 0/1`: ligação ao `DHCP`
+ `Fast Ethernet 0/2`: ligação ao `HTTP`
+ `Fast Ethernet 0/3`: ligação ao `TFTP`
+ `Fast Ethernet 0/4`: ligação ao `Email`
+ `Fast Ethernet 0/5`: ligação ao `DNS`
+ `Fast Ethernet 0/6`: ligação ao `IoT Registrar`

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.0.2`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor DNS

**`Server-PT`**: `DNS` - servidor de DNS (*Domain Name Service*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.0.3`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor de Email

**`Server-PT`**: `Email` - servidor de e-mail
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.0.4`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor TFTP

**`Server-PT`**: `TFTP` - servidor de TFTP (*Trivial File Transfer Protocol*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.0.5`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor HTTP

**`Server-PT`**: `HTTP` - servidor de HTTP (*HyperText Transfer Protocol*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.0.6`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor de Registo IoT

**`Server-PT`** - servidor de Registo IoT (*Internet of Things*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `192.168.0.7`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.0.1`
  + DNS Server:`8.8.8.8`

##### Configuração do Computador do Administrador de Sistemas

**`PC-PT`**: `OrienteAdmin` - computador do administrador de sistemas
+ `Fast Ethernet 0/0`: ligação ao `First floor Switch`
  + IPv4 Address: `192.168.0.6`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.0.1`
  + DNS Server:`8.8.8.8`

##### Configuração da IoT

###### Ar Condicionado

###### Detetor de Incêndio

###### Dispersores de Água

###### Ralos de Extração de Água

###### Detetores de CO2

###### RFID (*Radio Frequency Identification*)

#### Piso 1

##### Configuração do *Switch*

**`2960-24TT`**: `First floor Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Main Switch`
+ `Fast Ethernet 0/1`: ligação ao `OrienteAdmin`

##### Configuração do Computador-exemplo

##### Configuração da IoT

###### *Appliances* (Cafeteira)

#### Piso 2

##### Configuração do *Switch*

##### Configuração do Computador-exemplo



### Edifício 2 - XPTOtec_Nascente

#### Piso 0

##### Configuração do *Router*

**`Router-PT`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `172.16.0.1`
  + Subnet Mask: `255.255.0.0`

##### Configuração dos *Switches*

**`2960-24TT`**: `Main Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Main Router`
+ `Gigabit Ethernet 0/2`: ligação à rede *multiuser*

**`2960-24TT`**: `Server Switch`
+ `Fast Ethernet 0/0`: 

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `172.16.0.2`
  + Subnet Mask: `255.255.0.0`
  + Default Gateway: `172.16.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor de Email

**`Server-PT`**: `Email` - servidor de e-mail
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `172.16.0.3`
  + Subnet Mask: `255.255.0.0`
  + Default Gateway: `172.16.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor FTP

**`Server-PT`**: `FTP` - servidor de FTP (*File Transfer Protocol*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `172.16.0.4`
  + Subnet Mask: `255.255.0.0`
  + Default Gateway: `172.16.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor HTTP

**`Server-PT`**: `HTTP` - servidor de HTTP (*HyperText Transfer Protocol*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `172.16.0.5`
  + Subnet Mask: `255.255.0.0`
  + Default Gateway: `172.16.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor de Registo IoT

**`Server-PT`** - servidor de Registo IoT (*Internet of Things*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `172.16.0.6`
  + Subnet Mask: `255.255.0.0`
  + Default Gateway: `172.16.0.1`
  + DNS Server:`8.8.8.8`

##### Configuração do Computador do Administrador de Sistemas

##### Configuração do Computador-exemplo

#### Piso 1

##### Configuração do *Switch*

##### Configuração do Computador-exemplo

#### Piso 2

##### Configuração do *Switch*

##### Configuração do Computador-exemplo



### Edifício 3 - XPTOtec_Leste

#### Piso 0

#### Piso 1

##### Configuração do *Router*

**`Router-PT`**: `Main Router`
+ `Fast Ethernet 0/0`: ligação ao `Main Switch`
  + IPv4 Address: `10.0.0.1`
  + Subnet Mask: `255.0.0.0`

##### Configuração dos *Switches*

**`2960-24TT`**: `Main Switch`
+ `Gigabit Ethernet 0/1`: ligação ao `Main Router`
+ `Gigabit Ethernet 0/2`: ligação à rede *multiuser*

**`2960-24TT`**: `Server Switch`
+ `Fast Ethernet 0/0`: 

##### Configuração dos Servidores

###### Servidor DHCP

**`Server-PT`**: `DHCP` - servidor de DHCP (*Dynamic Host Configuration Protocol*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `10.0.0.2`
  + Subnet Mask: `255.0.0.0`
  + Default Gateway: `10.0.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor de Email

**`Server-PT`**: `Email` - servidor de e-mail
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `10.0.0.3`
  + Subnet Mask: `255.0.0.0`
  + Default Gateway: `10.0.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor FTP

**`Server-PT`**: `FTP` - servidor de FTP (*File Transfer Protocol*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `10.0.0.4`
  + Subnet Mask: `255.0.0.0`
  + Default Gateway: `10.0.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor HTTP

**`Server-PT`**: `HTTP` - servidor de HTTP (*HyperText Transfer Protocol*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `10.0.0.5`
  + Subnet Mask: `255.0.0.0`
  + Default Gateway: `10.0.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor de Registo IoT

**`Server-PT`** - servidor de Registo IoT (*Internet of Things*)
+ `Fast Ethernet 0/0`: ligação ao `Server Switch`
  + IPv4 Address: `10.0.0.6`
  + Subnet Mask: `255.0.0.0`
  + Default Gateway: `10.0.0.1`
  + DNS Server:`8.8.8.8`

###### Servidor de E-Mail

###### Servidor HTTP

###### Servidores DHCP

###### Servidor TFTP

###### Servidor de Registo IoT

##### Configuração do Computador do Administrador de Sistemas

##### Configuração do Computador-exemplo

#### Piso 2

##### Configuração do *Switch*

##### Configuração do Computador-exemplo

---

## Configurações de Segurança

ACLs.

<!--

ALERTA:
Como o 8.8.8.8 é o DNS da Google, numa situação real este endereço não é recomendado e teria de ser um endereço diferente.

## Configuração do Equipamento

Lado interno da empresa:

+ **`PC Admin`** - *PC* ligado ao `Switch0`;
  + IPv4 Address: `Set by DHCP SERVER`
  + Subnet Mask: `Set by DHCP SERVER`
  + Default Gateway: `192.168.8.1`
  + DNS Server:`192.168.8.8`
+ **`Linux 1`** - *PC* ligado ao `Switch0`;
  + IPv4 Address: `Set by DHCP SERVER`
  + Subnet Mask: `Set by DHCP SERVER`
  + Default Gateway: `192.168.8.1`
  + DNS Server:`192.168.8.8`
+ **`Linux 2`** - *PC* ligado ao `Switch0`;
  + IPv4 Address: `Set by DHCP SERVER`
  + Subnet Mask: `Set by DHCP SERVER`
  + Default Gateway: `192.168.8.1`
  + DNS Server:`192.168.8.8`
+ **`NTP Server`** - *Server* ligado ao `Switch0`;
  + IPv4 Address: `192.168.8.10`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.8.1`
  + DNS Server:`192.168.8.8`
+ **`NAS`** - *Server* ligado ao `Switch0`;
  + IPv4 Address: `192.168.8.11`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.8.1`
  + DNS Server:`192.168.8.8`
+ **`www.empresa`** - *Server* ligado ao `Switch0`;
  + IPv4 Address: `192.168.8.12`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.8.1`
  + DNS Server:`192.168.8.8`
+ **`DNS 192.168.8.8`** - *Server* ligado ao `Switch0`;
  + IPv4 Address: `192.168.8.8`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.8.1`
  + DNS Server:`192.168.8.8`
+ **`Switch0`** - *Switch* ligado ao `Router`.
+ Configuração do **`Router Principal`**:
  + `Ethernet 0/0/0`:
    + IPv4 Address: `192.168.8.1`
    + Subnet Mask: `255.0.0.0`
  + `Ethernet 0/0/1`:
    + IPv4 Address: `100.100.200.1`
    + Subnet Mask: `255.255.255.0`

Segundo Espaço da Empresa:

+ **`Linux5`** - *PC* ligado ao `Switch0`;
  + IPv4 Address: `Set by DHCP SERVER`
  + Subnet Mask: `Set by DHCP SERVER`
  + Default Gateway: `192.168.8.1`
  + DNS Server:`192.168.8.8`
+ **`Linux6`** - *PC* ligado ao `Switch0`;
  + IPv4 Address: `Set by DHCP SERVER`
  + Subnet Mask: `Set by DHCP SERVER`
  + Default Gateway: `192.168.8.1`
  + DNS Server:`192.168.8.8`
+ **`Switch0`** - *Switch* ligado ao `Router`.
+ Configuração do **`Router Secundario`**:
  + `Ethernet 0/0/0`:
    + IPv4 Address: `80.80.80.1`
    + Subnet Mask: `255.0.0.0`
  + `Ethernet 0/0/1`:
    + IPv4 Address: `192.168.6.1`
    + Subnet Mask: `255.255.255.0`

Lado externo da empresa:

+ **`DNS 8.8.8.8`** - Servidor normal ligado ao `Switch1`;
  + IPv4 Address: `8.8.8.8`
  + Subnet Mask: `255.0.0.0`
  + Default Gateway: `192.168.1.1`
  + DNS Server: `8.8.8.8`
+ **`www.sysadmintools.net`** - Servidor normal ligado ao `Switch1`;
  + IPv4 Address: `192.168.1.2`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.1.1`
  + DNS Server: `8.8.8.8`
+ **`Linux 3`** - *PC* ligado ao `Switch1`;
  + IPv4 Address: `192.168.1.3`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.1.1`
  + DNS Server: `8.8.8.8`
+ **`Linux 4`** - *PC* ligado ao `Switch1`;
  + IPv4 Address: `192.168.1.4`
  + Subnet Mask: `255.255.255.0`
  + Default Gateway: `192.168.1.1`
  + DNS Server: `8.8.8.8`
+ **`Switch1`** - *Switch* ligado ao `Router Externo`.
+ Configuração do **`Router Externo`**:
  + `Ethernet 0/0/0`:
    + IPv4 Address: `192.168.8.1`
    + Subnet Mask: `255.0.0.0`
  + `Ethernet 0/0/1`:
    + IPv4 Address: `100.100.200.1`
    + Subnet Mask: `255.255.255.0`

## 1) Configuração de servidor `www.empresa.com`

Passos para que o website empresa esteja disponível dentro da empresa:

1. Abrir a tab de **`Services`** do Servidor www.empresa;
2. Escolher a opção de **`HTTP`**;
3. Verificar que as opções HTTP e HTTPS estão **`ON`**;
4. Mudar para o Servidor DNS interno `192.168.8.8`;
5. Abrir a tab de **`Services`** do **`Servidor DNS 192.168.8.8`**;
6. Escolher a opção de **`DNS`**;
7. Adicionar entrada com os seguintes elementos:
   + Name: `www.empresa`
   + Type: `A Record`
   + Address: `192.168.8.12`
8. Adicionar entrada com os seguintes elementos:
   + Name: `www.empresa.com`
   + Type: `A Record`
   + Address: `192.168.8.12`
9. Dar *fast forward* ao tempo;
10. Aceder a um PC interno da rede;
11. Abrir um web browser;
12. Pesquisar por `www.empresa` e por `www.empresa.com`.

## 2) Configuração de servidor sysadmintools

1. Abrir a tab de **Services** do Servidor `www.sysadmintools.net`;
2. Escolher a opção de **`HTTP`**;
3. Verificar que as opções HTTP e HTTPS estão **`ON`**;
4. Mudar para o Servidor DNS interno `8.8.8.8`;
5. Abrir a tab de **`Services`** do **`Servidor DNS 8.8.8.8`**;
6. Escolher a opção de **`DNS`**;
7. Adicionar entrada com os seguintes elementos:
   + Name: `www.sysadmintools.net`
   + Type: `A Record`
   + Address: `8.8.8.2`
8. Dar *fast forward* ao tempo;
9. Aceder a um PC interno da rede;
10. Abrir um web browser;
11. Pesquisar por `www.sysadmintools.net`.

## 3) Configuração de DNS hierárquico

1. Abrir a tab de **Services** do **`Servidor DNS 8.8.8.8`**;
2. Escolher a opção de **`DNS`**;
3. Adicionar entrada com os seguintes elementos:
     + Name: `empresa.com`
     + Type: `NS`
     + Address: `root`
4. Adicionar entrada com os seguintes elementos:
     + Name: `root`
     + Type: `A Record`
     + Address: `192.168.8.8`
5. Abrir a tab de **Services** do **`Servidor DNS 192.168.8.8`**;
6. Escolher a opção de **`DNS`**;
7. Adicionar entrada com os seguintes elementos:
     + Name: `net`
     + Type: `NS`
     + Address: `root`
8. Adicionar entrada com os seguintes elementos:
     + Name: `root`
     + Type: `A Record`
     + Address: `8.8.8.8`
9. Dar *fast forward* ao tempo;
10. Aceder a um PC interno da rede;
11. Abrir um web browser;
12. Pesquisar por `www.sysadmintools.net`.
13. Aceder a um PC externo da rede;
14. Abrir um web browser;
15. Pesquisar por `www.empresa.com`.

## 4) Configuração da Firewall

### Versão 1

1. Abrir a tab **CLI** do Router Principal;
2. Utilizar o comando **configure terminal** para entrar em modo config;
3. Criar a firewall com um **access-list** no tipo extended e de nome "Firewall" usando o comando: **ip access-list extended Firewall**;
4. Negar todo o acesso com o comando: **deny ip any any**;
5. Adicionar uma excepção para permitir acesso HTTP ao servidor empresa.com: **permit tcp any host 192.168.8.12 eq www**;
6. Adicionar uma excepção para permitir acesso DNS: **permit udp any any eq domain**;
7. Adicionar uma excepção para permitir acesso através da VPN: **permit udp any any eq isakmp**;
8. Sair com **exit**;
9. Conectar à Ethernet desejada com: **Ethernet GigabitEthernet 0/0/1**; 
10. Activar a firewall para esta Ethernet para pacotes de entrada: **ip access-group Firewall in**.

### Versão 2

1. Abrir a tab **`Cli`** do Router Principal;
2. Utilizar o comando **`enable`**;
3. Utilizar o comando **`write erase`** para apagar as configurações;
4. Utilizar o comando **`reload`** para introduzir definições de fábrica;
5. Reconfigurar as Ethernets de acordo com a configuração base do equipamento, a VPN e o NAT;
6. 

## 5) Configuração do Servidor NTP

Passos para configurar o servidor NTP:

1. Abrir a tab de **Services** do Servidor NTP;
2. Escolher a opção de **NTP**;
3. Verificar que o serviço está no **ON**;
4. Sair do servidor;
5. Ir ao **Router**;
6. Abrir o **CLI**;
7. Verificar que o Router está **Enable**;
8. Utilizar comando **show ntp status**;
9. Entrar no modo de configuração ao executar o comando **conf t**;
10. Definir o servidor NTP a ser utilizado com o comando **ntp server 192.168.8.10**;
11. Dar *fast forward* ao tempo;
12. Voltar a executar o comando **show ntp status**.

(*tip*: caso o relógio no equipamento continuar a indicar não estar configurado e todos os passos tenham sido seguidos então continuar a dar *fast forward* ao tempo até o assunto estar resolvido)

## 6) Configuração de um Servidor NAS e das permissões de partilha de ficheiros

Passos para configurar o servidor NAS:

1. Abrir a tab de **Services** do Servidor NTP;
2. Escolher a opção de **FTP**;
3. Verificar que o serviço está no **ON**;
4. Verificar que as seguintes credênciais existem (criar caso não existam):
    + Admin:
       + Username: admin
       + Password: admin
       + Permission: RWDNL
    + Linux 1:
       + Username: linux1
       + Password: linux1
       + Permission: RWL
    + Linux 1:
       + Username: linux2
       + Password: linux2
       + Permission: RWL
5. Aceder a um PC e abrir a `Command Prompt`;
6. Escrever `ftp nas` ou `ftp 192.168.8.11`;
7. Utilizar qualquer par de credênciais;
8. Escrever `help` caso seja necessário.

## 7) Configuração do Crontab para arquivamento de ficheiros

Como o Cisco Packet Tracer não possui sistemas linux então não é possível utilizar o Crontab por isso foram criados dois *scripts* em python para tratar do armazenamento de ficheiros.

No servidor www.empresa/www.empresa.com existe um programa em Python que segue a seguinte lógica:
1. Ligar ao servidor NAS por uma socket TCP;
2. Iniciar um *loop* que verifica a hora real a cada segundo
3. Caso esta hora seja a hora definida para que o *backup* seja feito então o programa vai:
   1. Ler o ficheiro index.txt para uma variável;
   2. Enviar o conteúdo desta variável para o servidor NAS;
4. Continuar o *loop* até que a hora volte a ser a correta.

No servidor NAS existe um programa em Python que segue a seguinte lógica:
1. Ligar ao servidor www.empresa/www.empresa.com (Empresa) por uma socket TCP;
2. Aguardar que o servidor Empresa envie uma mensagem TCP;
3. Guardar a mensagem num ficheiro escolhido conforme o dia da semana relativo ao primeiro *backup*;
4. Incrementar o contador do dia para que no próximo *backup*, este seja guardado no ficheiro correspondente (no caso de ser o sétimo dia então o contador volta ao início).

## 8) Configuração de NAT-PT no router

1. Abrir o **`Router Principal`**;
2. Aceder ao **`CLI`**;
3. Escrever **`enable`**;
4. Escrever **`configure terminal`**;
5. Escrever **`ip nat inside source static 192.168.8.1 192.168.1.1`**;
6. Abrir a Ethernet **`Gigabit0/0/0`**:
  + Escrever **`ip nat inside`**;
7. Abrir a Ethernet **`Gigabit0/0/1`**;
  + Escrever **`ip nat outside`**.

## 9) Configuração de um tunel VPN

1. Abrir o **`Router Principal`**;
2. Aceder ao **`CLI`**;
3. Escrever **`Enable`**;
4. Escrever **`Configure Terminal`**;
5. Escrever **`license boot level securityk9`**;
6. Escrever **`write`**;
7. Escrever **`copy run start`**;
8. Escrever **`reload`**;
9. Escrever **`show version`** e verificar que o securityk9 existe;
10. Voltar ao **`Configure Terminal`**;
11. Escrever **`access-list 100 permit ip 192.168.8.0 0.0.0.255 192.168.6.0 0.0.0.255`**;
12. Repetir passos 2. a 10. no **`Router Secundario`**;
13. Escrever **`access-list 100 permit ip 192.168.6.0 0.0.0.255 192.168.8.0 0.0.0.255`**;
14. Voltar ao **`Router Principal`**;
    1.  Escrever **`crypto isakmp policy 10`**;
    2.  Escrever **`encryption aes 256`**;
    3.  Escrever **`authentication pre-share`**;
    4.  Escrever **`group 5`**;
15. Escrever **`crypto isakmp key Secret-2020 address 80.80.80.1`**;
16. Repetir passos 14.1. a 14.4. no **`Router Secundario`**;
17. Escrever **`crypto isakmp key Secret-2020 address 100.100.200.1`**;
18. Voltar ao **`Router Principal`**;
19. Escrever **`crypto ipsec transform-set MainRouter-SecundaryRouter esp-aes 256 esp-sha-hmac`**;
20. Voltar ao **`Router Secundario`**;
21. Escrever **`crypto ipsec transform-set SecundaryRouter-MainRouter esp-aes 256 esp-sha-hmac`**;
22. Voltar ao **`Router Principal`**;
23. Escrever **`crypto map IPSEC-CRYPTOMAP 100 ipsec-isakmp`** no **`config t`**;
    1. Escrever **`set peer 80.80.80.1`**;
    2. Escrever **`set pfs group5`**;
    3. Escrever **`set security-association lifetime seconds 86400`**;
    4. Escrever **`set transform-set MainRouter-SecundaryRouter`**;
    5. Escrever **`match address 100`**;
24. Voltar ao **`Router Secundario`**;
25. Escrever **`crypto map IPSEC-CRYPTOMAP 100 ipsec-isakmp`** no **`config t`**;
    1. Escrever **`set peer 100.100.200.1`**;
    2. Escrever **`set pfs group5`**;
    3. Escrever **`set security-association lifetime seconds 86400`**;
    4. Escrever **`set transform-set MainRouter-SecundaryRouter`**;
    5. Escrever **`match address 100`**;
26. Voltar ao **`Router Principal`**;
    1.  Aceder à Ethernet Externa;
    2.  Escrever **`crypto map IPSEC-CRYPTOMAP`**;
27. Voltar ao **`Router Secundario`**;
    1.  Aceder à Ethernet Externa;
    2.  Escrever **`crypto map IPSEC-CRYPTOMAP`**;
28. Testar em um dos routers com o comando **`show crypto ipsec sa`**.




## Extras

### 10) Configuração do DHCP para Computadores Pessoais

Os computadores internos da Empresa recebem a atribuição dos seus IPs a partir de um servidor DHCP com uma pool de IPs permitidos de forma a facilitar a adição de novos equipamentos pessoais à rede.

-->