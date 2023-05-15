# Notas

###### Outras anotações que possam vir a ser úteis para o projeto/defesa

## *Multiuser Connection*

URL: https://itexamanswers.net/10-3-1-3-packet-tracer-multiuser-tutorial-instruction-answers.html (tutorial)

## Cablagem

URL: https://www.cables-solutions.com/difference-between-straight-through-and-crossover-cable.html

**Cabo *Straight-Through*** -- cabo de pares cruzados em que os *pins* são correspondentes entre si (ambos os *pins* seguem o padrão T568A ou T568B). Primariamente utilizado para ligar dispositivos diferentes, por exemplo, *switch* para *router*, *switch* para computador/servidor, *hub* para computador/servidor.

**Cabo *Crossover*** -- cabo de pares cruzados em que os *pins* não correspondem entre si (um dos *pins* segue o padrão T568A, o outro segue o padrão T568B). Primariamente utilizado para ligar dispositivos iguais, por exemplo, *switch* para *switch*, *switch* para *hub*, *hub* para *hub*, *router* para *router*, *router Ethernet* para NIC de computador, computador para computador.

## Protocolos

### DNS (*Domain Name Service*)

O endereço `8.8.8.8` é o DNS da Google. É utilizado por conveniência quando o dispositivo não consegue encontrar o DNS através do DHCP (*Dynamic Host Configuration Protocol*). Numa situação real, não é recomendado utilizar o endereço `8.8.8.8`.

## Endereços IPv4

A rede `192.168.x.x` é uma gama de endereços privados de classe C, cuja máscara de subrede é `255.255.255.0/24`, com um máximo de 254 *hosts*.

A rede `172.16.x.x` é uma gama de endereços privados de classe B, cuja máscara de subrede é `255.255.0.0/16`, com um máximo de 65534 *hosts*.

A rede `10.0.x.x` é uma gama de endereços privados de classe A, cuja máscara de subrede é `255.0.0.0/8`, com um máximo de 16777214 *hosts*.

:::warning
Todas as subredes podem ser do tipo 255.255.255.0/24 (254 *hosts* no máximo). Ficam todas `/24` ou alteram-se (classe A e B) para poder ter mais anfitriões?
:::