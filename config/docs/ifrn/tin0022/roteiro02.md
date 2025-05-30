## **Roteiro:: Instalando e Testando Ambientes Desktop no Debian 12**

### **1\. Identificando o Ambiente Desktop Atual e Verificando a Instalação**

Vamos começar descobrindo qual ambiente desktop está ativo na sua instalação padrão do `Debian 12 com XFCE4` e como verificar as informações do sistema com o Neofetch.

**1.1. Verificando o DE Atual:**

  * Abra um terminal e execute os seguintes comandos para verificar as variáveis de ambiente que indicam o DE em uso:  

    ```
    echo $DESKTOP_SESSION  
    ```
    ```
    echo $XDG_CURRENT_DESKTOP
    ```

**1.2. Instalando e Verificando com Neofetch:**

  * **Neofetch** é uma ferramenta de linha de comando que exibe informações do sistema de forma elegante, incluindo o ambiente desktop.  
  * **Instalação:**  

    ```
    sudo apt update  
    ```
    ```
    sudo apt install neofetch -y
    ```
  
  * **Verificação:**  
    * Após a instalação, execute:  

        ```
        neofetch
        ```

---

### **2. Preparação do Ambiente e Atualização do Sistema**

**2.1. Atualização do Sistema:**  
Execute os comandos abaixo para garantir que todos os pacotes do sistema estejam atualizados. Isso evita conflitos e garante a disponibilidade das versões mais recentes dos softwares.  

```
sudo apt update  
```
```
sudo apt upgrade -y  
```
```
sudo apt autoremove -y
```

---

### **3. Instalação e Verificação de Novos Ambientes Desktop**

Agora vamos instalar e verificar alguns dos **Ambientes Desktop (DEs)** mais populares no Debian. Para cada ambiente, demonstre a instalação e o processo de verificação.

**Importante:** Após a instalação de cada ambiente, você precisará **reiniciar o sistema** (sudo reboot) e, na **tela de login (Display Manager)**, selecionar o DE recém-instalado antes de fazer login. Use o comando neofetch para confirmar a instalação.

**3.1. GNOME:**

**Instalação:**  

```
sudo apt install task-gnome-desktop -y
```
 
**Verificação:**  
    1. Reinicie o sistema: sudo reboot  
    2. Na tela de login, clique no ícone de engrenagem ou nas opções de sessão.  
    3. Selecione "**GNOME**" e faça login.  
    4. Abra um terminal e execute neofetch. Confirme que o GNOME é o ambiente listado.  
    5. Explore a interface, o menu de aplicativos ("Atividades"), e as configurações do sistema.  

**3.2. KDE Plasma:**

**Instalação:**  

```
sudo apt install task-kde-desktop -y
```
**Verificação:**  
    1. Reinicie o sistema: sudo reboot  
    2. Na tela de login, selecione "**Plasma**" (ou "KDE Plasma") e faça login.  
    3. Abra um terminal e execute neofetch. Confirme que o KDE Plasma é o ambiente listado.  
    4. Observe o painel (barra de tarefas), o menu "Kickoff Application Launcher" e as "System Settings" (Configurações do Sistema).  

**3.3. MATE:**

**Instalação:**  

```
sudo apt install task-mate-desktop -y
```
**Verificação:**  
    1. Reinicie o sistema: sudo reboot  
    2. Na tela de login, selecione "**MATE**" e faça login.  
    3. Abra um terminal e execute neofetch. Confirme que o MATE é o ambiente listado.  
    4. Note o painel clássico, o menu de aplicativos e o "Control Center" (Centro de Controle).  

**3.4. LXDE:**

**Instalação:**  

```
sudo apt install task-lxde-desktop -y
```

**Verificação:**  
    1. Reinicie o sistema: sudo reboot  
    2. Na tela de login, selecione "**LXDE**" e faça login.  
    3. Abra um terminal e execute neofetch. Confirme que o LXDE é o ambiente listado.  
    4. Observe a simplicidade da interface, o painel inferior e o menu de aplicativos.  

**3.5. LXQt:**

**Instalação:**  

```
sudo apt install task-lxqt-desktop -y
```

**Verificação:**  
    1. Reinicie o sistema: sudo reboot  
    2. Na tela de login, selecione "**LXQt Desktop**" e faça login.  
    3. Abra um terminal e execute neofetch. Confirme que o LXQt é o ambiente listado.  
    4. Explore a interface moderna, o painel e as opções de configuração.

---

### **4. Entendendo e Trocando Gerenciadores de Sessão (Display Managers)**

O **Gerenciador de Sessão (Display Manager)** é a interface gráfica que você vê antes de fazer login no sistema. Ele permite que você selecione o usuário e o ambiente desktop antes de iniciar a sessão.

**4.1. Conceito de Gerenciador de Sessão:**

  * O Display Manager é responsável por apresentar a tela de login, gerenciar as sessões de usuário e permitir a escolha do ambiente desktop. Cada ambiente desktop geralmente vem com um gerenciador de sessão padrão (por exemplo, GDM3 para GNOME, SDDM para KDE Plasma).  

**4.2. Trocando o Gerenciador de Sessão Padrão:**

  * O Debian permite que você altere o gerenciador de sessão padrão usando o comando dpkg-reconfigure. Você pode ter vários instalados e escolher qual será o padrão na inicialização do sistema.

**GDM3 (GNOME Display Manager 3):**

**Instalação (se ainda não estiver instalado com o GNOME):**

```
 sudo apt install gdm3 -y  
```

**Para torná-lo padrão:**  

```
sudo dpkg-reconfigure gdm3
```

* Na tela que aparecer, selecione gdm3 e pressione Enter.  

**LightDM:**

    * Frequentemente usado com ambientes como XFCE e MATE.  

**Instalação:**  

```
sudo apt install lightdm -y
```

**Para torná-lo padrão:**  

```
sudo dpkg-reconfigure lightdm
```

  * Na tela que aparecer, selecione lightdm e pressione Enter.  

**SDDM (Simple Desktop Display Manager):**

    * **Padrão para KDE Plasma.  

**Instalação (se ainda não estiver instalado com o KDE Plasma):**

```
 sudo apt install sddm -y  
```

**Para torná-lo padrão:**  

```
sudo dpkg-reconfigure sddm
```
 
  * Na tela que aparecer, selecione sddm e pressione Enter.  

**LXDM (LXDE Display Manager):**

    * Gerenciador de sessão padrão para LXDE.  

**Instalação (se ainda não estiver instalado com o LXDE):**

```
sudo apt install lxdm -y  
```

**Para torná-lo padrão:**  

```
sudo dpkg-reconfigure lxdm
```

  * Na tela que aparecer, selecione lxdm e pressione Enter.  

**XDM (X Display Manager):**

    * Um dos mais antigos e simples gerenciadores de sessão, faz parte do X Window System.  

**Instalação:**  

```
sudo apt install xdm -y
```

**Para torná-lo padrão:**  

```
sudo dpkg-reconfigure xdm
```

  * Na tela que aparecer, selecione xdm e pressione Enter.  

  * **Após alterar o gerenciador de sessão, reinicie o sistema para que as mudanças tenham efeito:**

```
sudo reboot
```

---

### **5. Limpeza e Considerações Finais**

* **5.1. Desinstalando Ambientes Desktop (Limpeza):**

  * **Importante:** Certifique-se de **não estar logado** no ambiente que você deseja desinstalar. Faça login em outro ambiente (por exemplo, GNOME ou XFCE) antes de executar os comandos.  
  * **Exemplo (desinstalando KDE Plasma):**  

```
sudo apt purge task-kde-desktop -y  
```
```
sudo apt autoremove --purge -y  
```