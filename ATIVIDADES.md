# Projeto Final - Capítulos 6, 7 e 9 ## RELATÓRIO DE PRÁTICAS E CÓDIGOS **Nome do Aluno:** João Vitor Lopes Silva **Turno:** ADS- NOITE **Data do Último Commit:** [Data de Hoje] ---


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

#### Prática 0002 checkpoint05 (Livro-Texto p. 288)
 * **Resumo da Prática:** (Descreva brevemente o que você fez: download de um arquivo usando `wget` para o diretório `/tmp`).
* **Evidência de Validação:** ```bash # Saída do comando 'cat /tmp/install.py' 
#!/usr/bin/python3
import os;
import sys
import platform
machine2bits = {'AMD64': 64, 'x86_64': 64, 'i386': 32, 'x86': 32, 'i686' : 32}
os_version = machine2bits.get(platform.machine(), None)

os.system("apt update");
os.system("wget -O /tmp/libjsoncpp1_1.7.4-3_amd64.deb http://ftp.br.debian.org/debian/pool/main/libj/libjsoncpp/libjsoncpp1_1.7.4-3_amd64.deb");
os.system("dpkg -i /tmp/libjsoncpp1_1.7.4-3_amd64.deb");
#os.system("apt install libjsoncpp-dev -y");
os.system("apt install g++ -y");
os.system("apt install libcurl4-openssl-dev -y");
os.system("rm -r /etc/aied");
os.system("rm -r /etc/aied");
os.system("mkdir /etc/aied");
os.system("wget -O /tmp/aied.tar.gz http://www.aied.com.br/linux/download/aied_"+ str(os_version) +".tar.gz" );
os.system("tar -xzvf /tmp/aied.tar.gz -C /etc/aied/");
#os.system("rm /usr/sbin/aied");
#os.system("rm /usr/bin/aied.py");
os.system("ln -s /etc/aied/aied_"+ str(os_version) +" /usr/bin/aied");
os.system("chmod +x /etc/aied/aied_"+ str ( os_version ) + "   " );

#OK, será usado para isntalacao do aied.com.br

## ATIVIDADE 3: Análise e Compilação dos Códigos
**Instrução:** Para cada programa listado abaixo, você deve:
1. Colar o código-fonte limpo (sem números de linha).
2. Compilar e executar o código no seu terminal. 3. Colar a saída exata que você obteve.
4. Escrever uma breve análise do que a saída significa e se corresponde ao objetivo do código.
### Códigos do Capítulo 6 (Discos e Montagem) #### `devices.cpp` (Livro-Texto p. 151-152)
* **Objetivo do Código:** Ler o arquivo virtual `/proc/mounts` para descobrir e imprimir qual dispositivo de bloco (ex: `/dev/sda1`) está atualmente montado no diretório raiz (`/`).
* **Código-Fonte:**
```cpp #include <iostream> #include <fstream> #include <optional> #include <string> std::optional<std::string> get_device_of_mount_point(std::string path) { std::ifstream mounts("/proc/mounts"); std::string mountPoint; std::string device; while (mounts >> device >> mountPoint) { if (mountPoint == path) return device; } return std::nullopt; } int main() { if (const auto device = get_device_of_mount_point("/")) std::cout << *device << "\n"; else std::cout << "Not found\n"; } ```
* **Análise da Saída:**
* *Comando de Compilação:* `g++ -o devices devices.cpp -std=c++17`
* *Saída da Execução:* ```bash /dev/sda1
 ``` * *Breve Descrição:* A saída é o local da primeira partição do disco raíz, portanto, é o resultado esperado.

#### `getuuid.c` (Livro-Texto p. 161-162)
* **Objetivo do Código:** Usar a biblioteca `libblkid` para listar todas as partições de um disco (ex: `/dev/sda`) e imprimir seus atributos, como **UUID**, **LABEL** e **TYPE**.
 * **Código-Fonte:** ```c
#include <stdio.h>
#include <string.h>
#include <err.h>
#include <blkid/blkid.h>
int main (int argc, char *argv[]) { if (argc != 2) {
fprintf(stderr, "Uso: %s <dispositivo>\nEx: %s /dev/sda\n", argv[0], argv[0]); return 1; } blkid_probe pr = blkid_new_probe_from_filename(argv[1]); if (!pr) { err(1, "Falha ao abrir %s", argv[1]); } blkid_partlist ls; int nparts, i; ls = blkid_probe_get_partitions(pr); if (!ls) { err(1, "Falha ao obter partições de %s", argv[1]); } nparts = blkid_partlist_numof_partitions(ls); printf("Número de partições em %s: %d\n", argv[1], nparts); const char *uuid, *label, *type; for (i = 0; i < nparts; i++) { char dev_name[20]; // (Cria o nome da partição, ex: /dev/sda + 1 = /dev/sda1) sprintf(dev_name, "%s%d", argv[1], (i+1)); blkid_probe pr_part = blkid_new_probe_from_filename(dev_name); if (!pr_part) continue; blkid_do_probe(pr_part); blkid_probe_lookup_value(pr_part, "UUID", &uuid, NULL); blkid_probe_lookup_value(pr_part, "LABEL", &label, NULL); blkid_probe_lookup_value(pr_part, "TYPE", &type, NULL); printf(" Partição: %s, UUID=%s, LABEL=%s, TYPE=%s\n", dev_name, (uuid ? uuid : "null"), (label ? label : "null"), (type ? type : "null")); blkid_free_probe(pr_part); } blkid_free_probe(pr); return 0; }

* *Comando de Compilação:* `gcc -o getuuid getuuid.c -lblkid` * *Saída da Execução:* (Execute com `sudo ./getuuid /dev/sda`) ```bash
Número de partições em /dev/sda: 3
 Partição: /dev/sda1, UUID=4ba97ce4-739d-4fb3-b0ae-379bfd7d888a, LABEL=null, TYPE=ext4
 Partição: /dev/sda2, UUID=▒, LABEL=null, TYPE=▒lH#V ```
* *Breve Descrição:* listou corretamente, com tipos como ext4 de formatação.



--- ### Códigos do Capítulo 7 (Processos) #### `teste.c` (Livro-Texto p. 181-182)
* **Objetivo do Código:** Um programa
"Olá, Mundo" simples para demonstrar o ciclo completo de compilação do GCC (Pré-processamento, Compilação, Montagem, Ligação). * **Código-Fonte:**

```c #include <stdio.h> int main() { printf("Aied é 10, Aied é TOP, tá no Youtube\n"); return 0; } ```
 * **Análise da Saída:** * *Comando de Compilação:* `gcc -o teste teste.c`
 * *Saída da Execução:* ```bash Aied é 10, Aied é TOP, tá no Youtube ``` * *Breve Descrição:* O programa imrpime a String passada como parametro no método printf().

#### `myblkid.cpp` (Livro-Texto p. 186-187)
* **Objetivo do Código:** Demonstrar como um programa C++ pode usar a biblioteca
`libblkid` (uma biblioteca C) para obter o UUID de uma partição específica (neste caso, `/dev/sda1`).
**Código-Fonte:** ```cpp #include <iostream> #include <blkid/blkid.h> #include <err.h> #include <string> int main (int argc, char *argv[]) { blkid_probe pr; const char *uuid;
std::string partition = "/dev/sda1"; // Codificado no fonte pr = blkid_new_probe_from_filename(partition.c_str()); if (!pr) { err(2, "Falha ao abrir %s", partition.c_str()); } blkid_do_probe(pr); blkid_probe_lookup_value(pr, "UUID", &uuid, NULL); printf("UUID=%s\n", (uuid ? uuid : "null")); blkid_free_probe(pr); return 0; } ```
* **Análise da Saída:** * *Comando de Compilação:*
`g++ -o myblkid myblkid.cpp -lblkid` * *Saída da Execução:* ```bash UUID=4ba97ce4-739d-4fb3-b0ae-379bfd7d888a
 ``` * *Breve Descrição:* Sim, é correspondente.

#### `calcfb.cpp` (Livro-Texto p. 187) *(Esta prática requer dois arquivos)* * **Objetivo do Código:** Demonstrar como criar e usar uma biblioteca de cabeçalho (`.h`) local. O `calcfb.cpp` (programa principal) incluirá `fibonacci.h` (biblioteca) para calcular um número da sequência. * **Código-Fonte (`fibonacci.h`):** ```cpp // (p. 187) int fibonacci(int n) { if (n <= 1) return n; return fibonacci(n - 1) + fibonacci(n - 2); } ``` * **Código-Fonte (`calcfb.cpp`):** ```cpp // (p. 187) #include <stdio.h> #include "fibonacci.h" // Aspas "" para incluir um arquivo local int main(int argc, char* argv[]) { printf("F%d: %d \n", 4, fibonacci(4)); return 0;
} ``` * **Análise da Saída:** * *Comando de Compilação:* `g++ -o calcfb calcfb.cpp` * *Saída da Execução:* ```bash F4: 3
 ``` * *Breve Descrição:* O quarto indicie da série de fibonacci resulta em 3, a soma de seus dois antecessores, 1 e 2.

#### `thread.cpp` (Livro-Texto p. 190)
* **Objetivo do Código:**
Demonstrar a criação de múltiplas threads que executam concorrentemente com a thread principal (`main`).
* **Código-Fonte:** ```cpp // (p. 190)
#include <iostream>
#include <thread>
#include <string>
using namespace std; // (Função de exemplo baseada no livro)
void task1(string msg) {
cout << "A thread está falando: " << msg << endl; }
int main() {
thread t1(task1, "Olá");
cout << "A 'main' executou..." << endl;
t1.join(); // A main espera a thread t1 terminar
return 0; } ``` * **Análise da Saída:** * *Comando de Compilação:* `g++ thread.cpp -o thread -pthread -std=c++11` * *Saída da Execução:* ```bash A 'main' executou...
A thread está falando: Olá
 ``` * *Breve Descrição:* "A 'main' executou" dispara primeiro, pois o main é chamada primeiro, e não é possívle ter controle total sobre as prioridades de execução das threads. O método join() faz com que exista um período de espera enquanto uma thread é executada.

#### `usefork.cpp` (Livro-Texto p. 191)
* **Objetivo do Código:
** Demonstrar a chamada `fork()`. O programa se clona; o pai e o filho executam o *mesmo* código, mas alteram variáveis diferentes, provando que têm espaços de memória separados.
* **Código-Fonte:** ```cpp // (p. 191)
#include <iostream>
#include <string>
#include <unistd.h> // Para fork()
#include <stdlib.h> // Para exit()
using namespace std;
int variavelGlobal = 2; // (p. 191, linha 5)
int main() {
    string identidade;
    int variavelFuncao = 20; // (p. 191, linha 9)
    pid_t pID = fork(); // (p. 191, linha 11)
    if (pID == 0) { // Processo filho
           identidade = "Processo filho: ";
           variavelGlobal++;
           variavelFuncao++; }
    else if (pID < 0) { // Erro
           cerr << "Failed to fork" << endl;
           exit(1); }
    else { // Processo pai
           identidade = "Processo pai:"; } // Este código é executado por AMBOS
cout << identidade;
cout << " Variavel Global: " << variavelGlobal;
cout << " Variável Funcao: " << variavelFuncao << endl;
return 0;
} 

* **Análise da Saída:** * *Comando de Compilação:* `g++ -o usefork usefork.cpp` * *Saída da Execução:* ```bash Processo pai: Variavel Global: 2 Variável Funcao: 20
userlinux@debian:~$ Processo filho:  Variavel Global: 3 Variável Funcao: 21
 ``` * *Breve Descrição:* Tem valores diferentes pois as instruções para cada processo são distintos, de aoordo com seu PID. O primeiro processo a ser disparado foi o processo pai.









