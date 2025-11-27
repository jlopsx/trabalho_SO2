## ATIVIDADE 1: Relatório das Práticas de Aula Esta seção documenta a execução das práticas de administração de sistemas realizadas em sala, conforme solicitado no final de cada capítulo do livro-texto. 
**Instrução:** Para cada prática, forneça um breve resumo do que foi feito e cole a saída de texto dos comandos de validação solicitados. 
**Não use imagens (printscreens)**. 
### Capítulo 6: Práticas de Discos e Montagem #### Prática 8b65b431 01 (Livro-Texto p. 171) * 
**Resumo da Prática:** 
(Descreva brevemente o que você fez: adição do disco, particionamento com `fdisk`, formatação com `mkfs.ext4` e configuração da montagem automática no `/etc/fstab` para o diretório `/backup`). * **Evidência de Validação:** 
```bash # Saída do comando 'cat /etc/fstab' # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# systemd generates mount units based on this file, see systemd.mount(5).
# Please run 'systemctl daemon-reload' after making changes here.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4ba97ce4-739d-4fb3-b0ae-379bfd7d888a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=17d63c63-4675-4422-bf37-643e675ac07f none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=fb8fca2f-2847-40c7-9968-1673311aeee9 /backup ext4 defaults 0 2
 # Saída do comando 'df -h' Filesystem      Size  Used Avail Use% Mounted on
udev            462M     0  462M   0% /dev
tmpfs            97M  568K   96M   1% /run
/dev/sda1        19G  2.3G   16G  13% /
tmpfs           481M     0  481M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/sdb1       182M   14K  168M   1% /backup
tmpfs            97M     0   97M   0% /run/user/1000
``` #### Prática 8b65b431 02 (Livro-Texto p. 172) * **Resumo da Prática:** (Descreva brevemente o que você fez: criação do diretório `cdrom` e montagem manual do dispositivo `/dev/sr0` nele).
```bash # Saída do comando 'df -h' 
Filesystem      Size  Used Avail Use% Mounted on
udev            462M     0  462M   0% /dev
tmpfs            97M  576K   96M   1% /run
/dev/sda1        19G  2.3G   16G  13% /
tmpfs           481M     0  481M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/sdb1       182M   14K  168M   1% /backup
tmpfs            97M     0   97M   0% /run/user/1000
/dev/sr0        364K  364K     0 100% /home/userlinux/cdrom
 # Saída do comando 'cat /home/usuario/cdrom/arquivo.txt aiedonline'
#### Prática prc0001 01 (Livro-Texto p. 233)
* **Resumo da Prática:** (Descreva brevemente o que você fez: execução dos comandos `locale-gen`, `script`, a listagem de processos com `ps` e a filtragem por `python`).
* **Evidência de Validação:** ```bash # Saída do comando 'cat /home/usuario/typescript' userlin+     612  0.0  0.2   6336  2088 pts/1    S+   23:44   0:00 grep python
### Capítulo 9: Práticas de Redes #### Prática 0002 checkpoint03 (Livro-Texto p. 286)
* **Resumo da Prática:** (Descreva brevemente o que você fez: configuração de IP estático editando o arquivo `/etc/network/interfaces` e reiniciando a máquina).
* **Evidência de Validação:** ```bash # Saída do comando 'ip address show enp0s3' 
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:ae:3d:56 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.3/24 brd 10.0.2.255 scope global enp0s3
       valid_lft forever preferred_lft forever
    inet6 fd00::a00:27ff:feae:3d56/64 scope global dynamic mngtmpaddr
       valid_lft 86242sec preferred_lft 14242sec
    inet6 fe80::a00:27ff:feae:3d56/64 scope link
       valid_lft forever preferred_lft forever
 # Saída do comando 'ip route' default via 10.0.2.2 dev enp0s3 onlink
10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.3
192.168.0.0/24 dev enp0s8 proto kernel scope link src 192.168.0.20
 # Saída do comando 'cat /etc/network/interfaces' # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#allow-hotplug enp0s3
#iface enp0s3 inet dhcp
auto enp0s3
iface enp0s3 inet static
    address 10.0.2.3
    netmask 255.255.255.0
    gateway 10.0.2.2
    dns-nameservers 8.8.8.8


#### Prática 0002 checkpoint04 (Livro-Texto p. 287) * **Resumo da Prática:** (Descreva brevemente o que você fez: configuração da rede para DHCP no arquivo e, em seguida, configuração de IP estático via comandos `ip address` e `ip route`). * **Evidência de Validação:** ```bash # Saída do comando 'ip address show enp0s3' 2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:ae:3d:56 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 85945sec preferred_lft 85945sec
    inet 10.0.2.3/24 scope global secondary enp0s3
       valid_lft forever preferred_lft forever
    inet6 fd00::a00:27ff:feae:3d56/64 scope global dynamic mngtmpaddr
       valid_lft 85946sec preferred_lft 13946sec
    inet6 fe80::a00:27ff:feae:3d56/64 scope link
       valid_lft forever preferred_lft forever

# Saída do comando 'ip route' default via 10.0.2.2 dev enp0s3
10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.15
192.168.0.0/24 dev enp0s8 proto kernel scope link src 192.168.0.20
 # Saída do comando 'cat /etc/network/interfaces' # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug enp0s3
iface enp0s3 inet dhcp
#auto enp0s3
#iface enp0s3 inet static
#    address 10.0.2.3
#    netmask 255.255.255.0
#    gateway 10.0.2.2
#    dns-nameservers 8.8.8.8












