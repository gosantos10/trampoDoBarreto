
# File Sharing usando Samba

## 1. Download dos ISO do Windows e Linux

> 1. Faça o download e instale o [Virtual Box para Ubuntu versão 18.04](https://www.virtualbox.com);
>
> 2. faça o download do Ubuntu 18.04 [Server ou Desktop](https://releases.ubuntu.com/18.04.4/);
>
> 3. Faça o download do [Windows 7 Professional](https://www.mediafire.com/file/6qlsra8hun0f8ks/Win7_Pro_SP1_BrazilianPortuguese_x64_-_PHDowns.iso.torrent/file?fbclid=IwAR30flNmma_F6D-3VhedeRrhegOm_TU4-KNVOLfB7S3w8MQ2px8IejOIX68)

## 2. Configurando sua VM - Ubuntu Desktop/Ubuntu Server/Windows 7 Pro

> 1. Abra o Virtual Box e clique em Novo.
> 2. Dê um nome para sua Máquina Virtual.
> 3. Selecione a quantidade de RAM que a máquina virtual poderá consumir (***recomendado: 2048 MB***).
> 4. Selecione "Criar um novo disco rígido virtual agora".
> 5. Marque a opção "VDI - VirtualBox Disk Image".
> 6. Marque a opção "Dinamicamente Alocado".
> 7. Selecione o tamanho do seu Disco Virtual (o tamanho do HD da máquina). ***Recomendado: valor maior que 20GB***
> 8. Clique em "Criar".
> 9. Selecione a sua Máquina virtual e Clique em Configurações.
> 10. Clique em Rede.
>     * Se estiver usando WIFI, selecione a Opção "habilitar placa de rede" e selecione a opção "placa em modo bridge".
>     * Caso contrário, selecione a opção "rede interna".
> 11. Clique em "Armazenamento", clique em "vazio" e em "drive óptico" Selecione a .ISO que você baixou do **Ubuntu Desktop 18.04** ou **Ubuntu Server 18.04**  ou **Windows 7 Pro**.
> 12. Clique em Okay e clique em Iniciar.

## 3. Instalando o Ubuntu Desktop

> 1. Após clicar em Iniciar no VirtualBox, selecione sua linguagem (português do Brasil) clique em *"Instalar Ubuntu"*.
>
> 2. Selecione o padrão de seu teclado. Para Português do Brasil, selecione *Português (Brasil)
>
> 3. Na pŕoxima tela:
>     * Se quiser uma instalação que venha editor de texto, calculadora e afins, selecione "Instalação completa".
>     * Para fazer o compartilhamento de arquivos, não precisamos de arquivos a mais, por isso *recomendamos selecionar a opção "Instalação minima"*.
>     * Deixe marcado a opção baixar atualizações enquanto instala o Ubuntu
> 4. Selecione a opção "Apagar Disco e Reinstalar o Ubuntu".
>
> 5. Selecione seu fuso horário. Em São Paulo, o fuso horário é -3GMT.
>
> 6. Na próxima tela:
>     * Digite seu nome;
>     * Digite o nome do host que o seu computador terá. **Tente NÃO usar o nome de outro computador conectado à mesma rede.
>     * Escolha um nome de usuário (este será o usuário administrador;
>     * Escolha uma senha para esse usuário. **Não a esqueça*;
>     * No nosso caso, selecione a opção "Solicitar minha senha para entrar", pois assim, o usuário administrador ficará mais protegido;
>
> 7. Clique em continuar. **A instalação será iniciada. O tempo de duração depende do hardware escolhido pela máquina virtual. Para as configurações recomendadas, o tempo médio é de *20 a 30 minutos***.

## 3.1 Instalando o Ubuntu Server

> 1. Após clicar em Iniciar no virtualBox, Selecione a linguagem. Como não há em Português, selecione *English* e aperte a tecla Enter.
>
> 2. Selecione *continue without updating*.
>
> 3. Selecione o padrão de seu teclado, no caso, selecione *Portuguese (Brazil)* usando a seta para cima e mova o cursor para Done. Em seguida, aperte Enter. 
>
> 4. Este é um passo **Muito Importante**. O Ubuntu vai tentar gerar um Ipv4 para você.
>       * O formato do IPv4 é 192.168.x.xxx. Certifique-se de entar nesse formato;
>       * Lembre-se de ter configurado corretamente o item **2.10**. 
>
> 5. Não utilizaremos Proxy, logo deixe-o em branco e aperte a tecla enter em Done.
>
> 6. Aperte a tecla enter novamente na tela "mirror address", pois não precisaremos configurar isso.
>
> 7. Selecione a opção "Use an Entire Disk" para formatar o Disco Virtual sem criar partições.
>
> 8. Confirme o disco selecionado apertando enter e depois em "continue" para confirmar a formatação do disco.
>
> 9. Vide item 2.6.
>
> 10. Na próxima tela, selecione com enter a opção "Open SSHServer" e confirme.
>
> 11. Na próxima tela, não precisamos de nenhum software adicional, logo não marque nenhum e confirme.
>
> 12. Aguarde a instação finalizar.
>
> 13. logue no Ubuntu Server usando as credenciais inseridas no item 3.1.9.

## 3.2 Instalando o Windows 7 professional

> 1. Após clicar em Iniciar, será aberta a instalação do Windows 7 Pro. Selecione o padrão de seu teclado utilizando o mouse. 
>
> 2. Clique em **Instalar Agora** e clique em aceitar os Termos da Licença.
>
> 3. Selecione a **Instalação Personalizada** para instalar o Windows.
>
> 4. Clique em **Opções de Unidade**, clique em **Novo** e clique em **Aplicar**. Confirme.
>
> 5. Selecione o disco do tipo **Primário** e clique em avançar. Será nesse disco que será instalado o Windows.
>
> 6. Aguarde a instalação do Windows. **Isso pode demorar** dependendo das configurações da máquina virtual selecionadas.
>
> 7. Escolha um nome de usuário e digite uma senha + uma dica de senha.
>
> 8. Após isso, o windows estará **pronto para uso**.

Desative o firewall do Windows 7 pesquisando no menu Iniciar "Firewall do Windows". Clique em "firewall do Windows", clique em "ativar ou desativar o Firewall do Windows" e desative-o. Após isso clique em "Aplicar".

## 4. Configurando o Ubuntu Server

**Vamos utilizar o Ubuntu Server a partir de agora**.

Precisamos atualizamos os packages do sistema. Para isso, após o item 3.1.13, execute os seguintes comandos.

>     $ sudo su        #para entrar em modo root.
>     $ apt update     #para atualizar a lista de pacotes disponíveis.
>     $ apt upgrade    #realiza a instaçação dessa nova lista de pacotes.

## 5. Instalando e Configurando o Samba 

Agora, precisamos instalar o Samba. Para isso, execute o seguinte comando:

>     $ apt install samba

Vamos configurar o Samba. Para isso, crie uma cópia do arquivo de configuração do Samba:

>     $ mv /etc/samba/smb.conf /etc/samba/smb.conf.old     #isso criará uma espécie de backup

Edite o arquivo de configuração do Samba:

>     $ nano /etc/samba/smb.conf

Insira o seguinte código dentro de smb.conf:

    [global]

        # Nome do grupo em que as máquinas estarão inseridas
        workgroup = nome_do_seu_grupo

        # Indetificador desta máquina ao ser acessada pelas outras na mesma rede
        netbios name = seu_identificador

        # Descrição do servidor
        server string = %h Server

        # Permite fornecer suporte a Windows
        wins support = yes

        # Não permite conexão por proxy
        dns proxy = no

        # Local onde ficarão os arquivos de log
        log file = /var/log/samba/log%m

        # Tamanho máximo de um arquivo de log (em KB)
        max log size = 1000

        # Impede que usuário root (adm) seja usado para login nas outras máquinas, por questões de segurança
        invalid users = root

        # Diz que o servidor foi configurado como um membro normal do grupo de trabalho
        server role = standalone server

        # Permita a criptografia de senhas
        encrypt passwords = yes

    # Configuração de uma Pasta pública. Insira nos colchetes o nome da pasta
    [nome_pasta]

        # Mostre onde essa pasta está localizada.
        path = /home/caminho_da_sua_pasta

        # permite edição do arquivo
        writable = yes

        # torna o arquivo disponível
        available = yes

após isso, salve usando `ctrl+O` e saia do editor usando `ctrl+x`. **NÃO ESQUEÇA de criar a pasta no mesmo caminho declarado em* `path`.

Para testar se o que você digitou está com a sintaxe correta, execute o comando:

>     $ testparm

Se nenhum erro foi acusado, podemos prosseguir para o próximo passo.

## 6. Testando a conectividade entre o Windows e o Linux Server

Instale o pacote net-tools no Ubuntu e execute o comando `ifconfig`:

>     $ apt install net-tools
>     $ ifconfig

Será mostrada as configurações de IP.

    enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
    inet 192.168.0.115  netmask 255.255.255.0  broadcast 192.168.0.255
    inet6 fe80::7682:b41c:b8ff:546  prefixlen 64  scopeid 0x20<link>
    ether 08:00:27:d6:54:26  txqueuelen 1000  (Ethernet)
    RX packets 778805  bytes 868576217 (868.5 MB)
    RX errors 0  dropped 0  overruns 0  frame 0
    TX packets 194332  bytes 25740557 (25.7 MB)
    TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

aqui verificamos que o IPv4 da máquina Linux é **192.168.0.115**.

Agora, vamos ver qual o IPv4 da máquina Windows. Para isso, aperte `windows+R` e digite **cmd**. Após isso, digite o seguinte comando:

>     $ ipconfig

Será mostrada as conigurações de IP da máquina Windows.

>     $ Endereco de IPv4...............: 192.168.0.111

Aqui, verificamos que o IPv4 da máquina Windows é **192.169.0.111**.

Para testarmos a conectividade entre Linux e Windows, digitamos na máquina Linux o seguinte comando:

>     $ ping IPv4_máquina_windows

E para testarmos a conectividade entre Windows e Linux, digitamos na máquina Windows o seguinte comando:

>     $ ping IPv4_máquina_linux

Se não houver nenhuma perda de dados, ambas as máquinas estão se **comunicando**.

## 7. File Sharing entre ambas as Máquinas

Na máquina Windows:

* clique em meu computador.
* Botão direito -> propriedades.
* Clique em alterar configurações.
* Na aba Nome do Computador, clique em Alterar...
* Altere o nome do Grupo de Trabalho para o nome do workgroup que você escolheu no arquivo de configuração do samba.
* Clique em Salvar.
* Clique em Rede. Selecione a máquina Linux. Ela pode ser identificada pelo netbios name que você escolheu no arquivo de configuração do Samba.
* Abrirá uma caixa de autenticação.

Por segurança, colocamos no arquivos de configuração do Samba dizendo que os usuários inválidos (invalid users) são o root (adm). Logo, precisamos criar um usuário que não é administrador para realizarmos a autenticação e podermos fazer o compartilhamento de arquivos.

Na máquina Linux, digite o comando:

>     $ adduser nome_usuario

Após isso, torne esse usuário passível de autenticação do Samba.

>     $ smbpasswd -a nome_usuario

Após, reinicie ambas as máquinas usando o comando:

>     $ reboot

Na Máquina Windows, em Rede, realize a autenticação requerida. Após isso, irá aparecer a pasta que vocẽ criou para compartilhamento disponível para visualização.

## 8. Não consegue ver a Pasta?

Talvez o problema seja permissão.

Execute o seguinte comando na pasta a ser compartilhada.

>     $ chmod 770 -R ../pasta_a_ser_compartilhada
