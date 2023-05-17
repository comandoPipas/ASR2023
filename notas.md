# Notas

###### Outras anotações que possam vir a ser úteis para o projeto/defesa

## Equipamentos

### *Routers*

Cada edifício tem quatro *routers*:
* O *router* principal, que faz ligação com os outros edifícios (e a Internet, no caso do XPTOtec_Oriente);
* O *router* da subrede dos servidores;
* O *router* da subrede dos dispositivos de IoT;
* O *router* da subrede dos computadores pessoais.

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

A rede `192.168.1.x` é uma gama de endereços privados de classe C, cuja máscara de subrede é `255.255.255.224/27`, com um máximo de 30 *hosts*. Escolheu-se esta rede para os endereços estáticos dos servidores e do computador do administrador de sistemas. A rede do edifício XPTOtec_Oriente permite a inserção de mais um dispositivo; as redes dos edifícios XPTOtec_Nascente e XPTOtec_Leste permitem a inserção de mais dois dispositivos.