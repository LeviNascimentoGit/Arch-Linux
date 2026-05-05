
# Manual de instalação UEFI do arch-linux + Gnome puro + systemd-boot [PT_BR]  
Testei diversas distros Linux, especialmente as mais populares (Arch, Mint, Fedora, Ubuntu e Debian), e cheguei à conclusão que essa combinação foi a melhor para o meu uso cotidiano com melhor suporte ativo da comunidade, boa compatibilidade com pacotes de aplicativos e com maior liberdade de personalização, basicamente tudo que serve pra outras distros, serve aqui também e algumas vezes até mais fácil ainda de ser feito. E acima de tudo, que contenha apenas o obrigatório para o sistema funcionar, mas sempre deixando a possibilidade de instalar qualquer coisa que eu precisar futuramente.  
<details>  

### Por quê o Arch-Linux?  
Ele é baseado no Debian que é uma das primeiras distros baseadas em Linux, a qual eu percebi que tem uma variedade de pacotes e de suporte muito grande comparado com outras distros. E possui uma comunidade ativa que te ensina a fazer qualquer tipo de coisa nele, além da [ArchWiki](https://wiki.archlinux.org/) que parece uma Bíblia de tão completa e sempre atualizada, e te explica em detalhes tudo sobre o Arch, até os arquivos de sistema e como cada comando funciona.  

- Por quê não instalar o Debian então?  

Diferente do Debian, o Arch tem um ambiente puro, sem GUI (interface) integrada na instalação. Além de não possuir aplicativos nativos, algo que testei no Fedora e gostei muito! Você tem um sistema limpo onde remove até a tela do Terminal Kernel se quiser.  
Resumindo, se eu não uso algo, então não preciso daquilo ocupando o armazenamento do meu computador.  

### Por quê o Gnome?  
Quando testei as interfaces gráficas Gnome, KDE Plasma e Cinnamon. Tentei fazer a mesma aparência nelas, modificar ao ponto de ficar idêntica ao Mac Tahoe (Que acho a interface mais bonita até o momento), e um pouco mais intuitiva por lembrar o smartphone que é algo que usamos durante o dia inteiro, então pegar o computador não causa a sensação de "OK... Agora estamos no computador aqui é tudo diferente". ISSO NÃO FAZ SENTIDO!!! Meu cérebro quer continuar no mesmo fluxo sem essas "readaptações" ao longo do dia.  

- No KDE Plasma...  
  Achei bem prático a função de clicar em personalizar e sair arrastando as coisas pela tela, incluindo ícones, baixar e aplicar temas direto das configurações de aparência. Mas... Isso é extremamente limitado, o KDE é feito para funcionar como KDE, ponto final.  

- O Cinnamon...  
É semelhante ao KDE nesse sentido, mas achei ainda mais limitado, pela falta de opções disponíveis e pela pouca variedade de coisas feitas pela comunidade.  

Além disso tudo, tem mais um ponto muito importante. No Cinnamon e no KDE a interface às vezes é mais do tipo "apontar e clicar" muito idêntico ao Windows. Não há atalhos de navegação com gestos no touchpad, e até os atalhos de teclas para as janelas de aplicativo são bem limitados.  

Ok, isso até poderia ser modificado com diversas tentativas até conseguir o resultado esperado, mas isso levaria tempo, e MUITA disposição. Coisa que pra mim  NÃO FAZ SENTIDO!  
A vida é curta de mais pra gastar tentando apenas mudar a configuração do meu computador!  

- E sobre o Gnome?  

Parti do mesmo princípio usado para a escolha do Arch: Tudo que é mais antigo tem mais conteúdo na comunidade e mais coisas desenvolvidas, testadas e estáveis.  

No Gnome achei muito mais intuitiva a função de arrastar com três dedos no touchpad do notebook. Para os lados, ele muda a área de trabalho, geralmente deixo as janelas maximizadas e uso como se estivesse apenas pulando de um aplicativo pra outro, igual no iPhone ou outros smartphones com a função de deslizar entre aplicativos.  
Arrastando de baixo pra cima, ele mostra a lista com todos os aplicativos que inclusive é idêntica ao MacOS, e ao menu dos smartphones com Android.  

Além disso, ele tem um site de extensões excelentes, quase todas estáveis e sem bugs, criadas e testadas pela comunidade de usuários, com direito a feedback nos comentários.  
Então acredite quando eu digo que tem tudo que você imaginar de funções, pra deixar o Gnome do seu jeito, só instalando uma extensão e configurando no menu próprio dela pra fazer algum ajuste fino, se quiser, pode também clicar no link e ir direto pro Git de cada uma delas e ver como ajustar.  
E se por acaso alguma extensão não for compatível, você simplesmente desativa a verificação de versão no site e instala ela mesmo assim (geralmente elas funcionam sem problemas).  
Já o gerenciamento de todas as extensões pode ser feito direto pelo site via navegador, ou pelo aplicativo de gerenciamento de extensões instalado no sistema. Isso é algo excelente!  

### Por quê o Systemd-boot?  
A maioria dos tutoriais que eu vi, falam de instalar o Grub como Bootloader, mas eu acho um desperdício. Porque o Arch já vem com um bootloader integrado, especialmente para quem usa UEFI que é o meu caso. Além disso, testando, eu também achei mais rápido iniciar com o Systemd-boot em vez do Grub.  

### Dito tudo isso... Segue o manual de instalação abaixo.
</details>

# 1 Pré-instalação  
O processo pode ser feito seguindo o [Manual da ArchWiki](https://wiki.archlinux.org/title/Installation_guide). Mas prefiro seguir meu método de instalação, para deixar ele já configurado e evitar várias etapas da pós instalação. Somente as etapas opcionais estão em `>detalhes`  

## 1.1 Baixar uma imagem de instalação  

Fazer o [Download do Arch-Linux](https://archlinux.org/download/) via Magnet Link ou Torrent.  

## 1.2 Preparar a mídia de instalação (Pendrive ou HD)  

Pode usar o [Rufus](https://rufus.ie), [Ventoy](https://www.ventoy.net/en/download.html), [Balena Etcher](https://etcher.balena.io/#download-etcher) ou [Easy2Boot](https://easy2boot.xyz/download/) (uso esse). Caso for um Mr. Robot na vida, é só usar um desses [outros métodos](https://wiki.archlinux.org/title/USB_flash_installation_medium).  

## 1.3 Inicializar em modo UEFI
1.  Entrar na BIOS da placa-mãe e Desativar o `Secure Boot` e Ativar o `Boot UEFI`.  
2.  Dar Boot pela mídia de instalação que tem UEFI no nome.  

### Depois de mostrar "Welcome to Arch-Linux" e vários [OK]. Vai abrir a raiz do instalador:  

**`root@archiso ~ #`**  

> Dica de Atalhos:  
> `CTRL`+`C` Interromper qualquer processo;  
> `CTRL`+`D` Voltar para a raiz do instalador ;  
> `CTRL`+`L` Limpar a tela.  

## 1.4 Configurar o teclado pra usar no instalador  

No Brasil se usa dois layout de teclado ABNT. No Macbook a posição das teclas é meio diferente, mas funciona igual.  

ABNT: Teclados que **não tem** a tecla `AltGr` à direita da barra de espaço e aparece no máximo dois caracteres na mesma tecla  
```
loadkeys br-abnt   
```
ABNT2: Teclados que **tem** a tecla `AltGr` à direita da barra de espaço e aparece três caracteres juntos na mesma tecla, por exemplo `+ = §`  
```
loadkeys br-abnt2   
```

<details> 

Se não selecionar o layout correto, algumas teclas ficam digitando errado no terminal.  
Caso seja um teclado internacional, esse comando mostra uma lista de todos os teclados:  
``` 
localectl list-keymaps
```
</details>

<details>  

## 1.5 Configurar o instalador no idioma pt_BR  
```
nano /etc/locale.gen
```
1. Usar o comando `Ctrl`+`F`, pra buscar pelo trecho `pt_BR`, ou descer usando a seta do teclado. Descomentar (apagar o `#` da frente) nas linhas `pt_BR.UTF-8 UTF-8` e `pt_BR ISO-8859-1`.  
> Dica: `CTRL`+`O` pra salvar, `Enter` pra confirmar. `CTRL`+`X` pra fechar.  

2. Aplicar o idioma
```
locale-gen && export LANG=pt_BR.UTF-8
```
> Feito isso. Já deve ficar tudo em portugês.  

## 1.6 Confirmar se o computador realmente iniciou em UEFI:  
```
cat /sys/firmware/efi/fw_platform_size
```
>- Se o comando retornar `64` ou `32`, o sistema será inicializado no modo UEFI e terá um UEFI x64 de 64 bits, ou UEFI IA32 de 32 bits.  
>  Ambos funcionam com Systemd-boot e vai dar certo.  
>- Se retornar `No such file or directory`, o sistema pode ter inicializado no modo BIOS (ou CSM) em vez de UEFI.  
>  Nesse caso, tem que confirmar se a placa-mãe tem suporte a UEFI e se tá habilitado, se não tiver suporte, vai ter que usar o GRUB em vez do Systemd-boot.  
</details>

## 1.7 Conectar na internet  

É obrigatório ter internet pra instalar o Arch-linux, porque os pacotes são baixados de acordo com a escolha do usuário.  

### Conexão Ethernet, via cabo de rede LAN   
Comando pra confirmar se está habilitado. Se mostrar `Enable` então já tem que estar funcionando.  
```
ip link
```

### Conexão Wireless, via Wi-Fi  
Comando pra abrir o menu de configuração:  
```
iwctl
```

<details>
  
Listar as placas de rede e saber o nome do dispositivo pra usar na próxima etapa:  
> Se for um notebook com Wi-Fi integrado ou se o computador tiver apenas uma placa de rede Wi-Fi, provavelmente o nome do dispositivo vai ser `wlan0`, então pode pular essa etapa  
```
device list
```

Buscar as redes disponíveis:  
> Aqui eu já tô considerando que o nome era `wlan0`  
> Se souber o nome exato da rede Wi-Fi, também pode pular essa etapa  
```
station wlan0 scan
```  
</details>

Selecionar o dispositivo de Wi-Fi e conectar na rede  
> No meu caso eu usei a internet da padaria, tem que ser o nome exato como aparece na busca, incluindo Maiúsculas/minúsculas, pontuações, espaços e símbolos.  
```
station wlan0 connect Padaria_5G
```
> Digitar a `passphrase` que é a senha e confirmar no `Enter`. Se em até 10 segundos não mostrar uma mensagem de erro. É porque conectou.  

`Ctrl`+`D` Sair do menu e voltar pra instalação:  

<details>

Pra testar é só usar o comando de ping em algum site, assim:  
```
ping google.com
```
> Dica: `CTRL`+`C` pra interromper, `CTRL`+`L` pra limpar a tela.  
</details>

## 1.8 Definir Hora e Data pela rede  

Sincronizar data e hora da máquina com o NTP do servidor Linux, pra evitar problema ao baixar pacotes.

```
timedatectl set-ntp true
```

<details>
  
# 2 Particionar, formatar e montar as partições  

Só pra esclarecer como funciona isso.  
1. Criar a partição, é avisar pro sistema quanto espaço do disco pode ser usado em cada partição criada. Informar que tipo de partição elas são, pra ele ver que existe partição EFI e partição normal.  
2. Formatar as partições pra definir o formato de arquivo, nesse caso vai ser só dois: Fat32 e Ext4.  
3. Montar o diretório inicial das partições, pra poder armazenar cada coisa no lugar certo durante a instalação.  
</details>

## 2.1 Particionar o disco antes de formatar  

Listar e identificar as unidades de disco pelo tipo ou pelo tamanho, o ideal é deixar conectado só o disco que vai ser formatado e a mídia de instalação, pra não apagar o disco errado por engano.  
```
lsblk
```
<details>

> Na instalação do sistema, ele entende as unidades de disco como caminhos `/dev/ ...`  e usa abreviações como `sda` pra disco Sata, `nvme0n1` pra NVME e `vda` pra disco virtual. Ex: `/dev/sda`  
> Quando tem mais de um disco do mesmo tipo, eles ficam com as abreviações diferentes em sequência alfabética ou numérica:  
> `sda`, `sdb`, `sdc` ...  `nvme0n1`, `nvme0n2`, `nvme0n3` ... `vda`, `vdb`, `vdc`  
> Nomes de disco com `rom`, `loop` or `airootfs`. ou cartões de memória removíveis com `rpmb`, `boot0` and `boot1` podem ser ignorados.  
</details>

1. Nos exemplos vou considerar que seja pra particionar o primeiro disco Sata.  
```
fdisk /dev/sda
```
2. Entrar com o comando `d` e confirmar o número da partição com `Enter`, pra ir apagando as partições que já existam no disco até retornar:    
`No partition is defined yet!`  

3. Usar o comando `g` pra criar uma nova tabela de partição em GPT.  

### Criar a partição `/dev/sda1` <sub>(Boot, só serve pra iniciar o sistema)</sub> 

> Sda1, 1Gb, UEFI  

1. Comando `n` pra criar uma nova partição  
2. Escolher um número pra identificar a partição: `1`  
3. Vai ser sugerido um setor inicial, é só pressionar `Enter`  
4. Vai perguntar o setor final, tem que colocar quanto vai ser somado no tamanho da partição e a unidade de medida, tudo junto: `+1g`
> Se conter uma assinatura. Confirmar com `y` pra remover
5. Digitar `t` pra definir o tipo de partição pra UEFI e o sistema saber pra que ela vai ser usada depois: `1`  
> Pra ver o número da opção de cada tipo de partição é só usar o comando `l` e depois `q` pra voltar  

### Criar a 2ª partição `/dev/sda2` <sub>(Root, onde fica os arquivos do sistema e do usuário)</sub>  
> Sda2, +espaço pra guardar os arquivos, Linux File System  

1. Comando `n` pra criar uma nova partição  
2. Escolher um número pra identificar a partição: `2`  
3. Vai ser sugerido um setor inicial, é só pressionar `Enter`  
4. Vai perguntar o setor final, pode definir um tamanho igual feito antes. Ou, pra usar o restante do disco é só pressionar `Enter`  
> O tipo de partição já vai ser mostrado como `Linux filesystem`  

> Se conter uma assinatura. Confirmar com `y` pra remover

Salvar usando `w` e `Enter`  

<details> 

> Dica: Usar o comando abaixo pra ver se o tamanho e o tipo das partições ficou certo  
```
lsblk
```

<img width="452" height="112" alt="image" src="https://github.com/user-attachments/assets/cf3b7796-16d7-40db-a80b-5ffec70eaff3" />

> Aqui ficou como 1gb na partição boot, e 19gb na partição root  
</details>

## 2.2 Formatar as partições criadas  

### Partição boot  
```
mkfs.fat -F32 /dev/sda1 
```

### Partição root  
```
mkfs.ext4 /dev/sda2
```

<details> 

> Dica: Usar o comando abaixo pra ver se o formato do sistema de arquivo ficou certo em cada partição  
```
lsblk -f
```

<img width="980" height="112" alt="image" src="https://github.com/user-attachments/assets/2acf2a0d-b074-4b4d-ab5f-ebc2bf2a9dcd" />

> Partição sda1: EFI, vFAT (FAT32)  
> Partição sda2: ext4  
</details>

## 2.3 Criar os pontos de montagem  

Apontar pro sistema qual é o diretório de cada partição, é importante montar os diretórios em ordem crescente, primeiro `/mnt` e depois `/mnt/boot`  

### 1. Montar o diretório Root  
```
mount /dev/sda2 /mnt
```

### 2. Montar o diretório Boot  
```
mount --mkdir /dev/sda1 /mnt/boot
```

<details> 

> Dica: Confirmar se o `mountpoints` das partições ficou certo  
```
lsblk -f
```

<img width="951" height="114" alt="image" src="https://github.com/user-attachments/assets/24d1264c-1fa5-4390-af72-df36844ea1eb" />

> Partição sda1: EFI, vFAT (FAT32), /mnt/Boot  
> Partição sda2: ext4, /mnt  
</details>

# 3 Instalação, finalmente!  

O Arch é igual um Lego, tem que ir montando cada parte do sistema. 

## 3.1 Instalar o Linux

Baixar os pacotes de arquivo pra criar a raiz do sistema. Pacotes base de configuração; kernel com módulos Linux; Firmware pra o funcionamento do hardware (drivers básicos); um editor de texto via terminal pra editar os arquivos de configuração.  
```
pacstrap /mnt base base-devel linux linux-firmware nano
```

## 3.2 Gerar a tabela de partições pra ordem de inicialização  

1. Gerar o arquivo `fstab` usando o comando:  
```
genfstab -U /mnt >> /mnt/etc/fstab
```
2. Confirmar se todas as partições foram listadas:  
```
cat /mnt/etc/fstab
```
> Se uma das partições não for listada. Repetir o processo desde a criação dos pontos de montagem.  

## 3.4 Criando uma partição de swap <sub>(Opcional)</sub>  

1. Alocar separando uma parte do armazenamento e criando um diretório de `partição swap`  
```
fallocate -l 4GB /swap
```
2. Dar as permissões necessárias para o diretório criado  
```
chmod 600 /swap
```
3. Definir o diretório pro formato swap  
```
mkswap /swap
```
4. Ativar o diretório para o Swap  
```
swapon /swap
```
5. Adicionar o diretório na lista de partições  
```
nano /etc/fstab
```
6. Usar a seta pra ir até a ultima linha em branco e digitar  

```
/swap none swap defaults 0 0 
```
> Dica: `CTRL`+`O` pra salvar, `Enter` pra confirmar. `CTRL`+`X` pra fechar.  
</details>

## 3.3 Continuar os processos no diretório root  

```
arch-chroot -S /mnt
```

## 3.5 Definir região, hora e idioma  

### Definir o layout do teclado depois de instalado  
> Usar a mesma referência de layout da instalação  
```
echo "KEYMAP=br-abnt2" >> /etc/vconsole.conf
```

### Definir idioma pra pt_BR  
```
nano /etc/locale.gen
```
1. Usar o comando `Ctrl`+`F`, pra buscar pelo trecho `pt_BR`, ou descer usando a seta do teclado. Descomentar (apagar o `#` da frente) nas linhas `pt_BR.UTF-8 UTF-8` e `pt_BR ISO-8859-1`.   

> Dica: `CTRL`+`O` pra salvar, `Enter` pra confirmar. `CTRL`+`X` pra fechar.  

2. Gerar o arquivo de idioma  
```
locale-gen && export LANG=pt_BR.UTF-8
```
### Definir os formatos de DD/MM/AAAA e outras medidas no padrão brasileiro  
```
nano /etc/locale.conf
```
Escrever o texto:  
```
LANG=pt_BR.UTF-8
LC_TIME=pt_BR.UTF-8
LC_PAPER=pt_BR.UTF-8
LC_NUMERIC=pt_BR.UTF-8
LC_MONETARY=pt_BR.UTF-8
LC_MEASUREMENT=pt_BR.UTF-8
```
>Dica: `CTRL`+`O` pra salvar, `Enter` pra confirmar. `CTRL`+`X` pra fechar.  

### Selecionar o fuso horário regional do computador, no meu caso é Norte do Brasil  
```
ln -sf /usr/share/zoneinfo/America/Belem /etc/localtime
```
<details>
  
> Dica: Pra ver todas as regiões é só usar o comando  
```
timedatectl list-timezones
```
</details>

### Sincronizar o relógio da máquina com o sistema  
```
hwclock --systohc
```

## 3.6 Definir o Hostname  

> Pode ser alterado depois de instalado. Caso isso seja feito, tem que alterar em `hosts` também.  
```
echo arch >> /etc/hostname
```

## 3.7 Definir os IP hosts

```
nano /etc/hosts  
```
Manter as linhas que já existem e escrever as linhas que estão faltando  
>  Usar a tecla `Tab` em vez da tecla `Espaço`.  
```
127.0.0.1	localhost
::1			localhost
127.0.1.1	arch.localdomain  arch
```
> Dica: `CTRL`+`O` pra salvar, `Enter` pra confirmar. `CTRL`+`X` pra fechar.  

## 3.8 Definir uma senha pra acesso root

```
passwd
```

## 3.9 Criar um usuário  

1. Criar e adicionar um usuário ao grupo `wheel`  
```
useradd -mG wheel usuario
```
2. Definir uma senha para o usuario  
```
passwd usuario
```
3. Usar o comando `Ctrl`+`F`, pra buscar pelo trecho `%wheel`, ou descer usando a seta do teclado. Descomentar (apagar o `#` da frente) apenas na linha `%wheel ALL=(ALL:ALL) ALL` pra liberar as permissões de administrador do grupo `wheel`  
```
nano /etc/sudoers
```
> Dica: `CTRL`+`O` pra salvar, `Enter` pra confirmar. `CTRL`+`X` pra fechar.

# 4 Pacotes de suporte  

### Atualizar a base de download
```
pacman -Sy
```
> Dica: O nome dos pacotes pode ser digitados na mesma linha de comando, separados pela tecla `Espaço` Ex. `pacman -Sy pacote pa-cote pa_cote`   

### Preencher com os pacotes adicionais  

- Dual boot  
```
os-prober
```
- Internet
```
networkmanager
```
> Esse serviço precisa ser habilitado depois de baixar o pacote
```
systemctl enable NetworkManager
```
- Wi-Fi  
```
iwd
```
- Bluetooth    
```
bluez
```
> Esse serviço precisa ser habilitado depois de baixar o pacote
```
systemctl enable bluetooth.service
```

# 6 Instalando a interface gráfica  

1. Instalar o Gnome puro
```
sudo pacman -S gdm gnome-shell gnome-desktop gnome-session gnome-keyring gnome-control-center gnome-settings-daemon gnome-tweak-tool gnome-software gnome-console xdg-user-dirs-gtk adwaita-icon-theme gnome-backgrounds gnome-initial-setup nautilus
```
2. Habilitar a tela de login
```
sudo systemctl enable gdm
```

# 5 Instalação do Bootloader  

## 4.1 Instalar o suporte ao Boot UEFI <sub>(Obrigatório)</sub>  

```
pacman -S efibootmgr
```

## 5.1 Instalar o system-boot no diretório Boot  

```
bootctl --path=/boot install
```

## 5.2 Configurar o Systemd-boot

1. Abrir o arquivo de configuração de entrada padrão
```
nano /boot/loader/loader.conf
```
2. Apagar a linha que começa com `default`, e substituir por:
```
default arch-*
```
> Dica: `CTRL`+`O` pra salvar, `Enter` pra confirmar. `CTRL`+`X` pra fechar.

3. Criar e configurar um arquivo de entrada padrão
```
nano /boot/loader/entries/arch.conf
```
4. Escrever isso e salvar
>  Usar a tecla `Tab` depois da primeira palavra de cada linha.   
```
title	Arch-Linux
linux	/vmlinuz-linux
initrd	/initramfs-linux.img
options	root=/dev/sda2 rw
```
<details>  

> Ao ligar/desligar o Linux, aparece várias mensagens do terminal, dá pra ocultar adicionando esse trecho no final da linha `options`  
```
quiet systemd.show_status=auto vt.global_cursor_default=0
```
</details>

> Dica: `CTRL`+`O` pra salvar, `Enter` pra confirmar. `CTRL`+`X` pra fechar.

# 7 Preparando pra reiniciar

1. Desmontar todas as partições

```
umount -a -f
```
2. Reiniciar e remover a mídia de instalação
```
reboot
``` 






















































