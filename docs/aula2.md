# Criando Usuário Cliente e hospendando-o em um servidor

## 1. Criação de servidor

> Acessar máquina linux.
> Atualizar os pacotes utilizando comandos `sudo su` `apt update` `apt upgrade`
>
> Instalar dependências necessárias: `apt install samba smbclient krb5-user dnsutils winbind`
>
> Dar reboot para ativar serviços `reboot`
>
> Verificar status dos serviços instalados `testparm`
>
> Fazer backup do arquivo do serviço samba `cp /etc/samba/smb.conf /etc/samba/smb.conf.old`
>
> Remover arquivo antigo do serviço samba `rm /etc/samba/smb.conf`
>
> Promover um membro de domínio existente `samba-tool domain provision`
>
> Colocar IP da máquina Linux no comando `samba-tool domain provision`
>
> Alterar o "Net Bios Name" para remover duplicidade que gerava erro
>
> Reboot na máquina para salvar alterações `reboot`
>
> Fazer backup do arquivo `cp /var/lib/samba/private/krb5.conf /etc/`
>
> Parar serviços para realizar ajustes `systemctl stop smbd nmbd winbind systemd-resolved`
>
> Desabilitar serviços para realizar ajustes `systemctl disable smbd nmbd winbind systemd-resolved`
>
> Remover arquivos para realizar ajustes `systemctl unmask samba-ad-dc`
>
> Criar link lógico `ll /etc/resolv.conf`
>
> Remover a referência ao link simbólico contida no `/etc/resolv` usando `rm /etc/resolv.conf`
>
> Editar arquivo `/etc/resolv.conf` incluindo `domain local.[user]` e `nameserver 127.0.0.1`
>
> Editar arquivo /usr/share/samba/setup incluindo `defaultRealm: [user].local`
>
> Reiniciando arquivos anteriormente parados `systemctl start samba-ad-dc`
>
> Ativar arquivos anteriormente parados `systemctl enable samba-ad-dc`
>
> Criando backup do arquivo krb5.conf `cp /usr/share/samba/setup/krb5.conf /etc/`
>
> Verificar status do usuário administrador `kinit Administrator`
>
> Verificar status do domínio `samba-tool domain level show`

## 2. Iniciar alocação do cliente

> Iniciar máquina virtual windows
>
>Certficar-se de que as configurações de rede são iguais em ambas as máquinas
>
> Verificar conexão entre maquinas utilizando `ping ip linux` na máquina windows e `ping ip windows` na máquina linux
>
> Verificar conexão de internet acessando página web
>
> Alterar configurações de rede passando ip da máquina linux como DNS e gateway `central de rede e compartilhamento>alterar as configurações do adaptador>conexão local>protocolo tcp/ip versão 4> propriedades>DNS>Adicionar` e `Configurações IP>Adicionar Gateway`
>
> Alterar configurações para acessar domínio criado `painel de controle>sistema e segurança>sistema>alterar configurações>alterar>domínio`
>
> Reinicia windows
>
> Criar usuário na máquina linux `samba-tool user create [nome usuário]`
>
> Definir senha
>
> Logar no Windows com novo usuário que foi criado
>
> Caso internet não esteja funcionando, desativar e ativar o adaptador em `Central de rede e compartilhamento`
