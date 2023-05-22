# Notas

## Equipamentos

### *Routers*

Cada edifício tem quatro *routers*:
* O *router* principal, que faz ligação com os outros edifícios (e a Internet, no caso do XPTOtec_Oriente);
* O *router* da subrede dos servidores;
* O *router* da subrede dos dispositivos de IoT;
* O *router* da subrede dos computadores pessoais.

Em todos os *routers* é necessário configurar o RIP.

### *Switches*

*Switches* permitem fazer *ping*.

## *Multiuser Connection*

URL: https://itexamanswers.net/10-3-1-3-packet-tracer-multiuser-tutorial-instruction-answers.html (tutorial)

## Cablagem

URL: https://www.cables-solutions.com/difference-between-straight-through-and-crossover-cable.html

**Cabo *Straight-Through*** -- cabo de pares cruzados em que os *pins* são correspondentes entre si (ambos os *pins* seguem o padrão T568A ou T568B). Primariamente utilizado para ligar dispositivos diferentes, por exemplo, *switch* para *router*, *switch* para computador/servidor, *hub* para computador/servidor.

**Cabo *Crossover*** -- cabo de pares cruzados em que os *pins* não correspondem entre si (um dos *pins* segue o padrão T568A, o outro segue o padrão T568B). Primariamente utilizado para ligar dispositivos iguais, por exemplo, *switch* para *switch*, *switch* para *hub*, *hub* para *hub*, *router* para *router*, *router Ethernet* para NIC de computador, computador para computador.

## Protocolos

### DNS (*Domain Name Service*)

O endereço `8.8.8.8` é o DNS da Google. É utilizado por conveniência quando o dispositivo não consegue encontrar o DNS através do DHCP (*Dynamic Host Configuration Protocol*). Numa situação real, não é recomendado utilizar o endereço `8.8.8.8`.

## Endereçamento IPv4

URL: https://www.cloudaccess.net/cloud-control-panel-ccp/157-dns-management/322-subnet-masks-reference-table.html
URL: https://www.calculator.net/ip-subnet-calculator.html?cclass=c&csubnet=27&cip=192.168.1.127&ctype=ipv4&printit=0&x=0&y=0

A rede `192.168.1.0` pertence à gama de endereços privados de classe C. Se a máscara de subrede é `255.255.255.224`, ou seja, com 27 bits de rede, possui um máximo de 30 *hosts*. Escolheu-se esta rede, com esta submáscara, para os endereços estáticos dos servidores, do computador do administrador de sistemas e do *network controller*. A rede do edifício XPTOtec_Oriente permite a inserção de mais um dispositivo; as redes dos edifícios XPTOtec_Nascente e XPTOtec_Leste permitem a inserção de mais dois dispositivos.

A rede `192.168.2.0` pertence à gama de endereços privados de classe C. Se a máscara de subrede é `255.255.255.0`, ou seja, com 24 bits de rede, possui um máximo de 254 *hosts*. Escolheu-se esta rede, com esta submáscara, para os endereços dinâmicos dos dispositivos de IoT.

As redes `192.168.3.0` e `192.168.4.0` pertencem à gama de endereços privados de classe C. Se a máscara de subrede é `255.255.192`, ou seja, com 26 bits de rede, possuem um máximo de 62 *hosts* cada. Escolheram-se estas redes, com estas submáscaras, para os endereços dinâmicos dos computadores pessoais dos colaboradores da empresa em cada piso.

A rede `192.168.10.0` pertence à gama de endereços privados de classe C. Se a máscara de subrede é `255.255.255.248`, ou seja, com 29 bits de rede, possui um máximo de 6 *hosts*. Escolheu-se esta rede, com esta submáscara, para os endereços estáticos da rede interna aos *routers*.