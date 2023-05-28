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

URL: https://www.cloudflare.com/learning/dns/dns-records/dns-soa-record/

O endereço `8.8.8.8` é o DNS da Google. É utilizado por conveniência quando o dispositivo não consegue encontrar o DNS através do DHCP (*Dynamic Host Configuration Protocol*). Numa situação real, não é recomendado utilizar o endereço `8.8.8.8`.

O registo SOA (*Start of Authority*) armazena informação importante sobre um domínio ou zona (conjunto de domínios ou subdomínios), como o endereço de e-mail do administrador, a última atualização do domínio e o tempo de espera entre atualizações do servidor. Todas as zonas DNS requerem um registo SOA para se conformarem aos padrões IETF.

## Endereçamento IPv4

URL: https://www.cloudaccess.net/cloud-control-panel-ccp/157-dns-management/322-subnet-masks-reference-table.html
URL: https://www.calculator.net/ip-subnet-calculator.html?cclass=c&csubnet=27&cip=192.168.1.127&ctype=ipv4&printit=0&x=0&y=0

As redes `192.168.1.0`, `192.168.100.0` e `192.168.200.0` pertencem à gama de endereços privados de classe C. Se a máscara de subrede é `255.255.255.224`, ou seja, com 27 bits de rede, possuem um máximo de 30 *hosts*. Escolheram-se estas redes, com esta submáscara, para os endereços estáticos dos servidores, do computador do administrador de sistemas e do *network controller*.

As redes `192.168.2.0`, `192.168.6.0` e `192.168.13.0` pertencem à gama de endereços privados de classe C. Se a máscara de subrede é `255.255.255.0`, ou seja, com 24 bits de rede, possuem um máximo de 254 *hosts*. Escolheram-se estas redes, com esta submáscara, para os endereços dinâmicos dos dispositivos de IoT.

As redes `192.168.3.0`, `192.168.4.0`, `192.168.5.0`, `192.168.7.0`, `192.168.8.0`, `192.168.9.0`, `192.168.14.0`, `192.168.15.0`, `192.168.16.0` pertencem à gama de endereços privados de classe C. Se a máscara de subrede é `255.255.192`, ou seja, com 26 bits de rede, possuem um máximo de 62 *hosts* cada. Escolheram-se estas redes, com estas submáscaras, para os endereços dinâmicos dos computadores pessoais dos colaboradores da empresa em cada piso. O DHCP está configurado para atribuir dinamicamente 30 *hosts*, pelo que permite a inserção de mais 32 dispositivos para cada subrede.

As redes `192.168.10.0`, `192.168.11.0`, `192.168.12.0`, `192.168.20.0`, `192.168.21.0` e `192.168.22.0` pertencem à gama de endereços privados de classe C. Se a máscara de subrede é `255.255.255.248`, ou seja, com 29 bits de rede, possuem um máximo de 6 *hosts*. Escolheram-se estas redes, com esta submáscara, para os endereços estáticos da rede interna aos *routers*.

As redes `1.0.0.0`, `2.0.0.0` e `3.0.0.0` pertencem à gama de endereços públicos, pelo que são usados para simular a Internet.

## Listas de Controlo de Acesso (ACLs)

Utilizadas para filtrar tráfego de rede em *routers* Cisco, controlam se os pacotes devem ser encaminhados ou bloqueados na entrada ou saída da interface.

Em ACLs padrão o tráfego é filtrado com base no endereço IP de origem dos pacotes IP. Devem ser implementadas perto do destino de modo a evitar bloquear tráfego legítimo da fonte.

Em ACLs estendidas o tráfego é filtrado com base numa combinação de critérios múltiplos: endereço IP de origem, endereço IP de destino, porta TCP ou UDP, protocolo, entre outros. Devem ser colocadas perto da origem devido a permitirem controlo mais granular dos recursos acedidos sem haver desperdício de largura de banda pelo tráfego de pacotes que serão potencialmente bloqueados.