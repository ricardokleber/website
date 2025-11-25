# IDS no Linux

Um Sistema de Detecção de Intrusão (IDS) é uma solução de segurança que monitora redes e/ou sistemas/hosts em busca de atividades maliciosas ou suspeitas. Sua atuação, dependendo de sua implementação, pode ser baseada na comparação do tráfego de rede e/ou eventos do sistema com um conjunto de regras ou padrões predefinidos, alertando os administradores quando uma atividade suspeita é detectada.

## **Principais Tipos de IDS**

Existem dois tipos principais de IDS  (ver slides para classificações mais detalhadas):

* **NIDS (Network Intrusion Detection System)**: Monitora o tráfego de rede em busca de atividades maliciosas de/para os componentes do sistema interno;
* **HIDS (Host Intrusion Detection System)**: Monitora hosts individualmente (servidores ou estações de trabalho) em busca de atividades suspeitas, como alterações em arquivos, sistema ou acesso não autorizado, etc.

<figure><img src="https://926166270-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F7A1yPw9vZimBv3uPIgNX%2Fuploads%2FZ2bjLK0J0JothPvcZ3gD%2F001.png?alt=media&#x26;token=7b415a86-20fe-45d4-872c-4d552f0f7689" alt=""><figcaption></figcaption></figure>

## **IDS no Linux**

O Linux oferece diversas opções de IDS, tanto de código aberto quanto comerciais. Apresentamos, a seguir, algumas das implementações de IDS em Linux mais populares:

* **Snort**: Um NIDS de código aberto amplamente utilizado, capaz de detectar uma variedade de ataques;
* **Suricata**: Outro NIDS de código aberto poderoso, conhecido por sua alta performance e capacidade de análise de tráfego;
* S**agan:** Solução que implementa sua estrutura e regras de forma semelhante aos IDS Suricata e Snort com o objetivo de permitir a correlação de eventos de log com seu sistema IDS/IPS;
* **OSSEC**: Um HIDS de código aberto que monitora arquivos de sistema, logs e atividades de usuários em busca de comportamento suspeito;
* **AIDE**: Um HIDS de código aberto que monitora a integridade de arquivos de sistema, alertando sobre alterações não autorizadas.

## **Implementando um IDS em Linux**

A implementação de um IDS em Linux envolve diversas etapas, incluindo:

1. **Escolha do IDS**: Selecione o IDS mais adequado para suas necessidades e ambiente;
2. **Instalação e configuração**: Instale o IDS e configure-o de acordo com suas preferências;
3. **Definição de regras**: Crie ou importe regras que definam as atividades maliciosas a serem detectadas;
4. **Monitoramento e alertas**: Monitore o IDS e configure alertas para receber notificações sobre eventos suspeitos;
5. **Análise de logs**: Analise os logs do IDS para identificar padrões e tendências de ataques.

## **Regras gerais para a manutenção de um IDS**

* **Mantenha o IDS atualizado**: Certifique-se de que o IDS esteja sempre atualizado com as últimas regras e patches de segurança;
* **Combine diferentes tipos de IDS**: Utilize tanto NIDS quanto HIDS para uma proteção mais completa;
* **Integre o IDS com outras ferramentas de segurança**: Combine o IDS com firewalls, antivírus e outras ferramentas para uma defesa em camadas;
* **Monitore o IDS regularmente**: Verifique os logs e alertas do IDS para identificar e responder a eventos suspeitos.

## **Interfaces Web para IDS Linux**

Praticamente todas as soluções de IDS para Linux apesar de robustas e de cumprirem efetivamente o seu papel se forem instaladas, configuradas e mantidas adequadamente, não é razoável (humanamente possível) monitorar os logs e alertas dos IDS em redes de médio e grande portes. Para auxiliar nessa tarefa é recomendável utilizar uma Interface Web integrada ao IDS escolhido.

Algumas interfaces web para IDS Linux bastante utilizadas e fáceis de instalar e geranciar, infelizmente foram descontinuadas (projetos baseados em software livre onde seus desenvolvedores deixaram de atualizar e não houve prosseguimento por parte dos usuários/colaboradores). Em nossa disciplina apresentaremos uma delas para fins didáticos, já instalada e configurada em uma máquina virtual para as práticas, o **ACIDBASE**.

### **ACIDBASE (Analysis Console for Intrusion Databases)**

O ACIDBASE foi uma ferramenta popular para análise e gerenciamento de alertas gerados pelo sistema de detecção de intrusão (IDS) Snort (que infelizmente teve seu projeto descontinuado). A ferramenta surgiu como uma solução para facilitar a visualização e análise dos alertas do Snort, que, por padrão, são exibidos em formato de texto.

<figure><img src="https://926166270-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F7A1yPw9vZimBv3uPIgNX%2Fuploads%2FcxwTxWjCtJQA43xLkJKx%2F002.png?alt=media&#x26;token=136a3623-0b05-4c08-b012-4800329e2be8" alt=""><figcaption></figcaption></figure>

Com uma interface web intuitiva, o ACIDBASE permitia que os administradores de rede visualizassem os alertas de forma mais organizada, pesquisassem por tipos de ataque, endereços IP e outros critérios, além de gerar relatórios e estatísticas sobre as atividades maliciosas detectadas.

O **ACIDBASE** oferecia uma variedade de funcionalidades que o tornavam uma ferramenta útil para análise de alertas do Snort:

* **Visualização de alertas**: Exibição dos alertas em formato de tabela, com informações detalhadas sobre cada evento, como data, hora, tipo de ataque, endereços IP de origem e destino, portas e protocolos utilizados.
* **Filtragem e pesquisa**: Permitia filtrar os alertas por diversos critérios, como tipo de ataque, endereço IP, porta, protocolo, entre outros.
* **Agrupamento de alertas**: Agrupamento de alertas relacionados, facilitando a identificação de padrões e tendências de ataque.
* **Geração de relatórios**: Criação de relatórios personalizados com informações sobre os alertas, como os tipos de ataque mais frequentes, os endereços IP mais atacados, entre outros.
* **Integração com banco de dados**: Utilização de um banco de dados (MySQL) para armazenar os alertas, permitindo a análise histórica dos dados.

O **ACIDBASE** funcionava em conjunto com o Snort e um banco de dados (por padrão o MySQL). O Snort, ao detectar uma atividade suspeita, gerava um alerta que era armazenado no banco de dados. O ACIDBASE, por sua vez, acessava o banco de dados para exibir os alertas na interface web, permitindo que os administradores visualizassem e analisassem os dados.

Com o fim do projeto, novas ferramentas de análise de logs e alertas surgiram com funcionalidades mais avançadas e interfaces mais modernas, como o **Snorby** e o **Security Onion**.

### Snorby

O Snorby é uma interface web de código aberto para monitoramento de segurança de rede que se integra com sistemas de detecção de intrusão (IDS) populares, como Snort, Suricata e Sagan. Ele oferece uma maneira centralizada e amigável de visualizar, analisar e gerenciar alertas e eventos de segurança, facilitando a identificação e resposta a ameaças cibernéticas.

<figure><img src="https://926166270-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F7A1yPw9vZimBv3uPIgNX%2Fuploads%2Fb9EWxZy8cw1JR2HKC7wr%2F003.png?alt=media&#x26;token=021ae1f7-8460-4f3c-9112-8080b19abb78" alt=""><figcaption></figcaption></figure>

#### Funcionalidades Principais

O Snorby oferece uma ampla gama de funcionalidades para auxiliar na análise de segurança de rede:

* **Visualização de alertas**: Exibe alertas e eventos de segurança de forma organizada e intuitiva, com informações detalhadas sobre cada evento, como data, hora, tipo de ataque, endereços IP de origem e destino, portas e protocolos utilizados;
* **Filtragem e pesquisa**: Permite filtrar e pesquisar alertas por diversos critérios, como tipo de ataque, endereço IP, porta, protocolo, entre outros, facilitando a identificação de eventos específicos ou padrões de ataque;
* **Agrupamento de alertas**: Agrupa alertas relacionados, auxiliando na identificação de ataques complexos ou campanhas maliciosas;
* **Gráficos e estatísticas**: Gera gráficos e estatísticas sobre os alertas, permitindo visualizar tendências de ataque, os tipos de ataque mais frequentes e outros dados relevantes para a análise de segurança;
* **Integração com banco de dados**: Utiliza um banco de dados (MySQL) para armazenar os alertas e eventos, permitindo a análise histórica dos dados e a geração de relatórios;
* **Interface web amigável**: Oferece uma interface web intuitiva e fácil de usar, que facilita a navegação e a análise dos dados de segurança.

#### Instalação e Configuração

A instalação e configuração do Snorby podem variar dependendo do ambiente e dos requisitos específicos. No entanto, geralmente envolvem as seguintes etapas:

1. **Instalação dos pré-requisitos**: Instalação do Ruby on Rails, MySQL e outras dependências;
2. **Download e instalação do Snorby**: Download do pacote do Snorby e instalação no servidor web;
3. **Configuração do banco de dados**: Criação do banco de dados e configuração das credenciais de acesso;
4. **Configuração do Snort (ou Suricata)**: Configuração do Snort (ou Suricata) para enviar os alertas para o banco de dados do Snorby;
5. **Configuração do Snorby**: Configuração do Snorby para acessar o banco de dados e exibir os alertas na interface web.

### **Security Onion**

O Security Onion é uma **distribuição Linux** focada em segurança que reúne diversas ferramentas de código aberto para monitoramento e análise de redes (**inclusive a mplementação de um IDS pronto para uso**). Ele é projetado para facilitar a detecção de intrusões, análise de logs e gerenciamento de eventos de segurança.

<figure><img src="https://926166270-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F7A1yPw9vZimBv3uPIgNX%2Fuploads%2FZfMgOdFAWvXbhF21z2NO%2F004.png?alt=media&#x26;token=eca9e86b-348a-4f7e-b19f-6c665e4c118e" alt=""><figcaption></figcaption></figure>

#### **Principais Componentes:**

* **Snort e Suricata:** Sistemas de detecção de intrusão (IDS) que monitoram o tráfego de rede em busca de atividades maliciosas;
* **Bro:** Plataforma de análise de rede que oferece recursos avançados para inspeção e análise de tráfego;
* **Snorby:** Interface web para visualizar e gerenciar alertas gerados pelo Snort/Suricata/Sagan;
* **Squid:** Proxy web utilizado para coletar logs de acesso e analisar o tráfego HTTP;
* **Wireshark:** Analisador de pacotes que permite inspecionar o tráfego de rede;
* **ELK stack:** Plataforma de análise de logs e eventos que inclui soluções bastante utilizadas atualmente, como o Elasticsearch, Logstash e o Kibana;
* **NetworkMiner:** Ferramenta para análise de tráfego de rede que permite extrair arquivos e credenciais de conexões.

#### **Funcionalidades:**

* **Detecção de intrusões:** Utiliza Snort, Suricata e Bro para identificar atividades maliciosas na rede;
* **Análise de logs:** Coleta e analisa logs de diversas fontes, como firewalls, servidores web e outros dispositivos de rede;
* **Monitoramento de segurança:** Permite monitorar o tráfego de rede e os eventos de segurança em tempo real;
* **Gerenciamento de alertas:** Facilita a visualização e o gerenciamento de alertas gerados pelas ferramentas de segurança;
* **Análise forense:** Oferece ferramentas para análise forense de incidentes de segurança.

## **Material Complementar:**

* **Documentação do Snort**: [https://www.snort.org](https://www.snort.org/)
* **Documentação do Suricata**: [https://suricata.io](https://suricata.io/)
* **Documentação do Sagan:** <https://github.com/quadrantsec/sagan>
* **Documentação do OSSEC**: [https://www.ossec.net](https://www.ossec.net/)
* **Documentação do AIDE**: [https://sourceforge.net/projects/aide](https://sourceforge.net/projects/aide/)
* **Documentação do Snorby:** <https://github.com/Snorby/snorby>
* **Documentação do Security Onion**: [https://securityonionsolutions.com](https://securityonionsolutions.com/)
