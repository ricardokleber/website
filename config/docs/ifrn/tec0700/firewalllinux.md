# Firewalls no Linux

O iptables é o atual software de implementação de firewalls em sistemas Linux e está disponível por padrão na maioria das distribuições modernas do Linux.

Para implementar a ferramenta iptables é necessário um kernel que possua a infraestrutura netfilter implementada (disponível por ladrão a partir do kernel 2.3.15).

Caso não esteja instalado, em sistemas Debian, pode-se instalar utilizando o apt (**`apt-get install iptables`**).

### Tabelas (tables) do Iptables

Para utilizar o iptables é necessário especificar, inicialmente, uma das 'tables':

* FILTER;
* NAT;
* MANGLE; ou
* &#x20;RAW

Para indicar a table utiliza-se o parâmetro **`-t`** (**`iptables -t <table>`**), Porém, se esse parâmetro for omitido, subentende-se que se está utilizando a table filter (Firewall como **Filtro de Pacotes**) que é a principal funcionalidade do Firewall.&#x20;

**Abordaremos nesta disciplina prioritariamente a table 'FILTER' para filtragem de pacotes e a table 'NAT' para fazer mascaramento (NAT 1:N).**

### Table Filter: Chains padrões

Por padrão o Iptables tem 3 (três) chains padrões:

* **`INPUT:`** Chain com regras para pacotes 'entrando' (input) no Firewall
* **`OUPUT:`** Chain com regras para pacotes 'saindo' (output) do Firewall
* **`FORWARD:`** Chain com regras para pacotes 'cruzando' (forward) o Firewall

<img src="../images/iptables01.png">

## Facilitando a utilização do Firewall com o uso de scripts

O firewall não é um serviço (pois insere as regras diretamente no kernel) e, portanto, o Iptables não funciona como os serviços do Linux com 'start' para iniciar e 'stop' para parar ou 'restart' para reiniciar.

Em função disso, optamos por criar um script shell (**`fw.sh`**) e executá-lo sempre que a máquina reiniciar ou que as regras do firewall forem alteradas.

### Script Shell fw\.sh :: Estrutura padrão

A seguir um script sugerido como sendo um 'padrão' com linhas de comentário para facilitar o entendimento (defina o seu nome como **`fw.sh`** por exemplo):

<details>

<summary>Script Sugerido (Padrão)</summary>

```
#!/bin/bash

# Habilitando o roteamento (forward) entre as interfaces da máquina
echo 1 > /proc/sys/net/ipv4/ip_forward

# Limpando todas as regras de todas as chains da tabela filter
iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD

# Configurando as políticas default de entrada e saída do Firewall como ACCEPT
# Isso permitirá que o Firewall continue acessando a Internet normalmente
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT

# Configurando a política default de repasse de pacotes (FORWARD) como DROP
# A partir dessa configuração o firewall bloqueará todos os repasses e só
# liberará para o tráfego explicitamente liberado nas regras de filtragem
iptables -P FORWARD DROP

# Regras de Filtragem de Pacotes a partir daqui...
```
</details>


Esse script deve ter permissão de execução:

```
chmod +x fw.sh
```

A execução do script da forma como está bloqueará todos os repasses de pacote (FORWARD) e manterá liberadas as saídas e entradas de pacotes de/para a própria máquina do firewall (INPUT e OUTPUT).

```
./fw.sh
```

## Comandos básicos de manipulação de regras Iptables

### Listar as regras de uma ou de todas as tables de uma chain

```
iptables [-t <tabela>] -L [-n] <chain>
```

A execução da linha de comandos a seguir exibirá todas as regras e políticas das tables da chain filter.


```sh
# Listando todas as regras de todas as chains da table filter
iptables -L
```

### Opções mais utilizadas para especificar detalhes de filtragem nas regras Iptables:

* **`-s`** : Origem (source) = Pode ser uma rede (Endereço IP com máscara) ou um host (Endereço IP)
* **`-d`** : Destino (destination) = Pode ser uma rede (Endereço IP com máscara) ou um host (Endereço IP)
* **`-p`** : Protocolo (protocol)
* **`--dport`** : Porta de Destino (destination port)
* **`--sport`** : Porta de Origem (source port)
* **`-j`** : Ação (jump to) = Pode ser ACCEPT, DROP ou LOG (ações padrão)
* **`!`** : Inverte uma regra = (match NOT equal to)

<details>

<summary>Exemplos</summary>

```sh
# Bloquear o repasse (FORWARD) de todos os pacotes destinados à porta 22/TCP
# em qualquer uma das redes às quais o firewall está ligado
iptables -A FORWARD -p tcp --dport 22 -j DROP

# Bloquear o repasse (FORWARD) de todos os pacotes destinados à porta 23/TCP
# em um host específico (192.168.1.100)
iptables -A FORWARD -d 192.168.1.100 -p tcp --dport 23 -j DROP

# Liberar o repasse de pacotes de uma rede específica (10.0.0.0/8) destinadas
# a um host específico (172.16.20.1) na porta 80/TCP e fazer o 'caminho de
# volta", ou seja, liberar pacotes vindos da porta 80/TCP do host específico
# para a rede específica
iptables -A FORWARD -s 10/8 -d 172.16.20.1 -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -s 172.16.20.1 -d 10/8 -p tcp --sport 80 -j ACCEPT
```

</details>