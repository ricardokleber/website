# **Instalação do Debian 12 no VirtualBox**

Roteiro para instalação do Debian 12 "Bookworm" em uma máquina virtual no VirtualBox.

## **1\. Preparativos**

### **1.1. Baixar o VirtualBox**

**Vamos pular este passo porque no Laboratório o VirtualBox já está instalado em todas as máquinas**

Se você ainda não tem o VirtualBox instalado, faça o download da versão mais recente no site oficial:

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Siga as instruções de instalação para o seu sistema operacional.

### **1.2. Baixar a ISO do Debian 12**

Baixe a imagem ISO do Debian 12\. Para baixar e instalar em casa e/ou com uma Internet banda larga é mais recomendável a versão "netinst" para uma instalação mais compacta, que baixará pacotes adicionais durante a instalação.

* **Para arquitetura AMD64 (a mais comum):** [https://www.debian.org/CD/http-ftp/\#stable](https://www.debian.org/CD/http-ftp/#stable)

   Procure por `debian-12.x.x-amd64-netinst.iso` (onde `x.x` são as versões mais recentes).

**Como no Laboratório serão várias máquinas instalando ao mesmo tempo utilizaremos a ISO completa para utilizar menos a Internet durante a instalação.**

[**https://mvs.projetos.cn.ifrn.edu.br/isos/debian-12.10.0-amd64-DVD-1.iso**](https://mvs.projetos.cn.ifrn.edu.br/isos/debian-12.10.0-amd64-DVD-1.iso)

---

## **2\. Configuração da Máquina Virtual no VirtualBox**

### **2.1. Criar uma Nova Máquina Virtual**

1. Abra o **VirtualBox**.  
2. Clique em **"Novo"** (ou `Ctrl + N`).  
3. **Nome:** `Debian 12` (sugiro colocar SEU NOME na máquina do Laboratório)  
4. **Pasta da Máquina:** Mantenha o padrão ou escolha um local.  
5. **Imagem ISO:** Clique em **"Outro..."** e selecione a ISO do Debian 12 que você baixou.  
6. **Tipo:** `Linux`  
7. **Versão:** `Debian (64-bit)`  
8. Marque a opção **"Pular instalação desassistida"**.  
9. Clique em **"Próximo"**.

### **2.2. Configurar Hardware**

1. **Memória RAM:** Defina para `2048 MB` (2 GB).  
2. **Processadores:** Pode manter `1` ou aumentar se desejar (não é crítico para esta instalação).  
3. Clique em **"Próximo"**.

### **2.3. Configurar Disco Rígido Virtual**

1. **Criar um disco rígido virtual agora.**  
2. **Tamanho do Disco:** Digite `30 GB`.  
3. Clique em **"Próximo"**.

### **2.4. Resumo e Criação**

1. Verifique o resumo das configurações.  
2. Clique em **"Finalizar"**.

---

## **3\. Instalação do Debian 12**

### **3.1. Iniciar a Máquina Virtual**

1. Na lista de máquinas virtuais do VirtualBox, selecione `Debian 12`.  
2. Clique em **"Iniciar"** (ou `Ctrl + S`).

### **3.2. Tela Inicial da Instalação**

1. Na primeira tela, selecione **"Graphical install"** (Instalação Gráfica) e pressione `Enter`.

### **3.3. Configurações Iniciais**

1. **Select a language:** Selecione `Português (Brasil)`. Clique em **"Continuar"**.  
2. **Selecione sua localização:** Selecione `Brasil`. Clique em **"Continuar"**.  
3. **Configurar o teclado:** Selecione `Português (Brasil)`. Clique em **"Continuar"**.

### **3.4. Configuração de Rede**

1. O sistema tentará configurar a rede automaticamente. Aguarde.

### **3.5. Configurar Usuários e Senhas**

1. **Nome da máquina:** Sugiro `debian12` (ou outro nome de sua preferência). Clique em **"Continuar"**.  
2. **Nome de domínio:** Deixe em branco. Clique em **"Continuar"**.  
3. **Senha do root:** Deixe em branco. Isso fará com que a conta de root seja desativada e o primeiro usuário criado terá permissões de sudo. É uma prática comum e segura. Clique em **"Continuar"**.  
4. **Nome completo do novo usuário:** `internacional`. Clique em **"Continuar"**.  
5. **Nome de usuário para sua conta:** `internacional` (será preenchido automaticamente). Clique em **"Continuar"**.  
6. **Escolha uma senha para o novo usuário:** `internacional`.  
7. **Redigite a senha para verificar:** `internacional`. Clique em **"Continuar"**.

### **3.6. Particionamento do Disco**

Esta é a etapa mais importante para as configurações de disco.

1. **Método de particionamento:** Selecione **"Manual"**. Clique em **"Continuar"**.  
2. Você verá o disco virtual que criamos (`VBOX HARDDISK`, com 30 GB). Selecione-o e clique em **"Continuar"**.  
3. Ele perguntará se deseja criar uma nova tabela de partições vazia. Selecione **"Sim"**. Clique em **"Continuar"**.

Agora vamos criar as partições:

4. Selecione o **espaço livre** (30 GB). Clique em **"Continuar"**.  
5. Selecione **"Criar uma nova partição"**. Clique em **"Continuar"**.  
6. **Novo tamanho da partição:** Digite `2 GB`. Clique em **"Continuar"**.  
7. **Tipo para a nova partição:** Selecione **"Primária"**. Clique em **"Continuar"**.  
8. **Localização para a nova partição:** Selecione **"Início"**. Clique em **"Continuar"**.  
9. Na tela de detalhes da partição:  
   * **Utilizar como:** Selecione **"área de troca (swap)"**.  
   * Selecione **"Finalizar a configuração da partição"**. Clique em **"Continuar"**.

Agora, vamos criar a partição `/`:

10. Selecione o **espaço livre** restante (aproximadamente 28 GB). Clique em **"Continuar"**.

11. Selecione **"Criar uma nova partição"**. Clique em **"Continuar"**.

12. **Novo tamanho da partição:** Deixe o valor padrão (máximo restante). Clique em **"Continuar"**.

13. **Tipo para a nova partição:** Selecione **"Primária"**. Clique em **"Continuar"**.

14. **Localização para a nova partição:** Selecione **"Início"**. Clique em **"Continuar"**.

15. Na tela de detalhes da partição:

    * **Utilizar como:** Deixe `Sistema de arquivos journaling Ext4`.  
    * **Ponto de montagem:** Deixe `/`.  
    * Selecione **"Finalizar a configuração da partição"**. Clique em **"Continuar"**.  
16. Você verá as duas partições configuradas: uma swap de 2 GB e uma partição `/` (root) Ext4.

17. Selecione **"Finalizar o particionamento e escrever as mudanças no disco"**. Clique em **"Continuar"**.

18. Confirme para escrever as mudanças no disco. Selecione **"Sim"**. Clique em **"Continuar"**.

### **3.7. Instalação do Sistema Base**

1. Aguarde enquanto o sistema base do Debian é instalado. Isso pode levar alguns minutos.

### **3.8. Seleção de Software**

1. **Participar do levantamento de uso de pacotes?** Selecione **"Não"**. Clique em **"Continuar"**.  
2. **Seleção de software:**  
   * Desmarque **"GNOME"** (se não quiser ambiente gráfico).  
   * **Marque:**  
     * `Debian desktop environment` (se quiser um ambiente gráfico padrão, que inclui GNOME por padrão)  
     * `standard system utilities` (já vem marcado)  
   * Se você quiser apenas uma instalação mínima sem ambiente gráfico, desmarque "Debian desktop environment" e certifique-se de que "standard system utilities" esteja marcado.  
   * Clique em **"Continuar"**.  
3. Aguarde o download e a instalação dos pacotes selecionados.

### **3.9. Instalação do Carregador de Inicialização GRUB**

1. **Instalar o carregador de inicialização GRUB no registro mestre de inicialização?** Selecione **"Sim"**. Clique em **"Continuar"**.  
2. **Dispositivo para instalação do carregador de inicialização:** Selecione o disco principal do VirtualBox (geralmente `/dev/sda`). Clique em **"Continuar"**.

### **3.10. Finalizar a Instalação**

1. Aguarde a finalização da instalação.  
2. Uma mensagem indicará que a instalação foi concluída. Clique em **"Continuar"** para reiniciar.

---

## **4\. Primeiro Acesso**

### **4.1. Reiniciar a Máquina Virtual**

1. A máquina virtual será reiniciada automaticamente.  
2. Você verá o menu do GRUB. Deixe a primeira opção selecionada e pressione `Enter`.

### **4.2. Tela de Login**

1. Após o sistema inicializar, você verá a tela de login (se você instalou um ambiente gráfico) ou um prompt de login (se você instalou apenas o sistema base).  
2. **Usuário:** `internacional`  
3. **Senha:** `internacional`

---

Parabéns\! Você concluiu a instalação do Debian 12 no VirtualBox com as configurações especificadas. Agora você pode começar a explorar seu novo sistema Debian.

