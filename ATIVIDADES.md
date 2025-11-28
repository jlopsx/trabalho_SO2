# Projeto Final - Capítulos 6, 7 e 9
## RELATÓRIO DE PRÁTICAS E CÓDIGOS
**Nome do Aluno:** joão Vitor Lopes Silva
**Turno:** ADS - Noite
**Data do Último Commit:** 28/11/2025
---
## ATIVIDADE 1: Relatório das Práticas de Aula
Esta seção documenta a execução das práticas de administração de sistemas realizadas em
sala, conforme solicitado no final de cada capítulo do livro-texto.
**Instrução:** Para cada prática, forneça um breve resumo do que foi feito e cole a saída de
texto dos comandos de validação solicitados. **Não use imagens (printscreens)**.
### Capítulo 6: Práticas de Discos e Montagem
#### Prática 8b65b431 01 (Livro-Texto p. 171)
* **Resumo da Prática:** comando fdisk e mount para realização da atividade
* **Evidência de Validação:**
```bash
# Saída do comando 'cat /etc/fstab'
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
# Saída do comando 'df -h'
Filesystem      Size  Used Avail Use% Mounted on
udev            462M     0  462M   0% /dev
tmpfs            97M  568K   96M   1% /run
/dev/sda1        19G  2.3G   16G  13% /
tmpfs           481M     0  481M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/sdb1       182M   14K  168M   1% /backup
tmpfs            97M     0   97M   0% /run/user/1000
```
#### Prática 8b65b431 02 (Livro-Texto p. 172)
* **Resumo da Prática:** utilização da função mkdir para criação do diretório
* **Evidência de Validação:**
```bash
# Saída do comando 'df -h'
Filesystem      Size  Used Avail Use% Mounted on
udev            462M     0  462M   0% /dev
tmpfs            97M  576K   96M   1% /run
/dev/sda1        19G  2.3G   16G  13% /
tmpfs           481M     0  481M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/sdb1       182M   14K  168M   1% /backup
tmpfs            97M     0   97M   0% /run/user/1000
/dev/sr0        364K  364K     0 100% /home/userlinux/cdrom
# Saída do comando 'cat /home/usuario/cdrom/arquivo.txt'
aiedonline
```
### Capítulo 7: Práticas de Processos
#### Prática prc0001 01 (Livro-Texto p. 233)
* **Resumo da Prática:** filtragem com grep 
* **Evidência de Validação:**
```bash
# Saída do comando 'cat /home/usuario/typescript' (após filtrar por 'python')
userlin+     612  0.0  0.2   6336  2088 pts/1    S+   23:44   0:00 grep python
```
### Capítulo 9: Práticas de Redes
#### Prática 0002 checkpoint03 (Livro-Texto p. 286)
* **Resumo da Prática:** edição a partir do comando nano e comandos seguintes, como ip a e route
* **Evidência de Validação:**
```bash
# Saída do comando 'ip address show enp0s3'
 enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:ae:3d:56 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.3/24 brd 10.0.2.255 scope global enp0s3
       valid_lft forever preferred_lft forever
    inet6 fd00::a00:27ff:feae:3d56/64 scope global dynamic mngtmpaddr
       valid_lft 86242sec preferred_lft 14242sec
    inet6 fe80::a00:27ff:feae:3d56/64 scope link
       valid_lft forever preferred_lft forever
# Saída do comando 'ip route'
10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.3
192.168.0.0/24 dev enp0s8 proto kernel scope link src 192.168.0.20
# Saída do comando 'cat /etc/network/interfaces'
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
```
#### Prática 0002 checkpoint04 (Livro-Texto p. 287)
* **Resumo da Prática:** (Descreva brevemente o que você fez: configuração da rede para
DHCP no arquivo e, em seguida, configuração de IP estático via comandos `ip address` e `ip
route`).
* **Evidência de Validação:**
```bash
# Saída do comando 'ip address show enp0s3'
enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
 link/ether 08:00:27:ae:3d:56 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 85945sec preferred_lft 85945sec
    inet 10.0.2.3/24 scope global secondary enp0s3
       valid_lft forever preferred_lft forever
    inet6 fd00::a00:27ff:feae:3d56/64 scope global dynamic mngtmpaddr
       valid_lft 85946sec preferred_lft 13946sec
    inet6 fe80::a00:27ff:feae:3d56/64 scope link
       valid_lft forever preferred_lft forever
# Saída do comando 'ip route'
10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.15
192.168.0.0/24 dev enp0s8 proto kernel scope link src 192.168.0.20
# Saída do comando 'cat /etc/network/interfaces'
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
```
#### Prática 0002 checkpoint05 (Livro-Texto p. 288)
* **Resumo da Prática:** wget para transferência de dados
* **Evidência de Validação:**
```bash
# Saída do comando 'cat /tmp/install.py'
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
```
---

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

#### `usewait.cpp` (Livro-Texto p. 193) *
**Objetivo do Código:**
Demonstrar a chamada `wait()`.
O processo-pai usa `wait(NULL)` para pausar sua própria execution e aguardar que o processo-filho termine antes de continuar.
* **Código-Fonte:**
```cpp //
(p. 193)
#include <iostream>
#include <unistd.h>
#include <sys/wait.h> // (p. 193, linha 3)
using namespace std;
int main() {
    pid_t pID = fork();
    pid_t cpid;
    if ( pID == 0 ) { // Filho
      cout << "Saindo do processo filho. " << endl;
      return 0; }
    else if (pID > 0) { // Pai
      cout << "Pai esperando o filho terminar..." << endl;
      cpid = wait(NULL); // (p. 193, linha 17) }
      else { // Erro cerr << "Failed to fork" << endl;
      return 1; }
    cout << "PID do pai: " << getpid() << endl;
    cout << "PID do filho (retornado por wait): " << cpid << endl;
    return 0; }
* **Análise da Saída:**
* *Comando de Compilação:* `g++ -o usewait usewait.cpp` * *Saída da Execução:* ```bash Pai esperando o filho terminar...
Saindo do processo filho.
PID do pai: 854
PID do filho (retornado por wait): 855
 ``` * *Breve Descrição:* É impresso pois o processo filho é finalizado antes do que o processo pai.

#### `usewait_exit.cpp` (Livro-Texto p. 194)
* **Objetivo do Código:**
Expandir o `wait()`, mostrando como o pai pode capturar o *código de saída* (status) do filho, usando `WIFEXITED` e `WEXITSTATUS`.
* **Código-Fonte:** ```c // (p. 194) (Este código é C, não C++)
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>
#include <signal.h> // Para psignal
int main() {
      pid_t pid;
      int stat; // (p. 194, linha 11)
      pid = fork();
      if(pid == 0) { // Filho
          printf("Saindo do processo filho.\n");
          exit(1); // (p. 194, linha 15)
      } else if (pid > 0) { // Pai
          wait(&stat); // (p. 194, linha 17 - modificado do NULL)
      if(WIFEXITED(stat)) { // (p. 194, linha 20)
          printf("WEXIT: %d\n", WEXITSTATUS(stat)); // (p. 194, linha 21)
      } else if (WIFSIGNALED(stat))
      { psignal(WTERMSIG(stat), "Sinal de saída: ");
      }
      printf("PID do pai: %d\n", getpid());
      printf("PID do filho: %d\n", pid); }
      return 0;
}
* **Análise da Saída:** * *Comando de Compilação:* `gcc -o usewait_exit usewait_exit.cpp` * *Saída da Execução:* ```bash Saindo do processo filho.
WEXIT: 1
PID do pai: 864
PID do filho: 865
 ``` * *Breve Descrição:* 1, significando que saiu com exit do processo filho.
#### `waitpid.cpp` (Livro-Texto p. 195)
* **Objetivo do Código:**
Demonstrar o `waitpid()` para gerenciar *múltiplos* filhos.
O pai cria 5 filhos, e então espera por *cada um* deles especificamente, coletando seus códigos de saída (100 a 104).
* **Código-Fonte:** ```cpp // (p. 195)
#include <iostream>
#include <sys/wait.h>
#include <unistd.h>
using namespace std;
int main() {
    pid_t pid[5];
    int i, stat;
    for (i = 0; i < 5; i++) {
        pid[i] = fork(); // (p. 195, linha 11)
        if( pid[i] == 0) { // Filho
              sleep(1); // (p. 195, linha 14)
              exit(100 + i); // (p. 195, linha 15) }
    }
    for (i = 0; i < 5; i++) {
        pid_t cpid = waitpid(pid[i], &stat, 0); // (p. 195, linha 19)
        if (WIFEXITED(stat)) {
              cout << "O filho " << cpid << " terminou com o status: " << WEXITSTATUS(stat) << endl;
        }
    }
return 0;
}
* **Análise da Saída:**
* *Comando de Compilação:* `g++ -o waitpid waitpid.cpp` * *Saída da Execução:* ```bash O filho 877 terminou com o status: 100
O filho 878 terminou com o status: 101
O filho 879 terminou com o status: 102
O filho 880 terminou com o status: 103
O filho 881 terminou com o status: 104
``` * *Breve Descrição:* Sim, estão em ordem. Ele aguarda a conclusão do atual processo para o inicio do outro, resultando em uma ordem de fato.

#### `system.cpp` (Livro-Texto p. 196)
* **Objetivo do Código:** Demonstrar a função `system()`, que é um atalho (e geralmente inseguro) para `fork + exec + wait`. O programa C++ pausa, executa um comando de shell (`ls -l`) e depois continua. * **Código-Fonte:** ```cpp // (p. 196)
#include <iostream>
#include <stdlib.h> // Para system()
int main() {
system("ls -l");
std::cout << "Executado" << std::endl;
return 0;
} ``` * **Análise da Saída:** * *Comando de Compilação:* `g++ -o system system.cpp` * *Saída da Execução:* ```bash total 312
-rwxr-xr-x 1 userlinux userlinux 16000 Nov 27 12:11 calcfb
-rw-r--r-- 1 userlinux userlinux   182 Nov 27 12:10 calcfb.cpp
drwxr-xr-x 2 userlinux userlinux  4096 Nov 26 23:20 cdrom
-rwxr-xr-x 1 userlinux userlinux 30840 Nov 27 11:40 devices
-rw-r--r-- 1 userlinux userlinux   541 Nov 27 11:37 devices.cpp
-rw-r--r-- 1 userlinux userlinux    94 Nov 27 12:09 fibonacci.h
-rwxr-xr-x 1 userlinux userlinux 16528 Nov 27 11:47 getuuid
-rw-r--r-- 1 userlinux userlinux  1463 Nov 27 11:47 getuuid.c
-rwxr-xr-x 1 userlinux userlinux 24168 Nov 27 12:05 myblkid
-rw-r--r-- 1 userlinux userlinux   534 Nov 27 12:04 myblkid.cpp
-rwxr-xr-x 1 userlinux userlinux 16624 Nov 27 14:34 pop
-rw-r--r-- 1 userlinux userlinux   437 Nov 27 14:34 pop.cpp
-rwxr-xr-x 1 userlinux userlinux 16600 Nov 27 14:35 system
-rw-r--r-- 1 userlinux userlinux   138 Nov 27 14:23 system.cpp
-rwxr-xr-x 1 userlinux userlinux 15960 Nov 27 11:58 teste
-rw-r--r-- 1 userlinux userlinux   112 Nov 27 11:58 teste.c
-rwxr-xr-x 1 userlinux userlinux 26288 Nov 27 12:22 thread
-rw-r--r-- 1 userlinux userlinux   338 Nov 27 12:21 thread.cpp
-rw-r--r-- 1 userlinux userlinux   960 Nov 26 23:45 typescript
-rwxr-xr-x 1 userlinux userlinux 17496 Nov 27 12:31 usefork
-rw-r--r-- 1 userlinux userlinux   810 Nov 27 12:31 usefork.cpp
-rwxr-xr-x 1 userlinux userlinux 16800 Nov 27 13:49 usewait
-rw-r--r-- 1 userlinux userlinux   622 Nov 27 13:49 usewait.cpp
-rwxr-xr-x 1 userlinux userlinux 16272 Nov 27 13:54 usewait_exit
-rw-r--r-- 1 userlinux userlinux   754 Nov 27 13:54 usewait_exit.cpp
-rwxr-xr-x 1 userlinux userlinux 16792 Nov 27 13:59 waitpid
-rw-r--r-- 1 userlinux userlinux   611 Nov 27 13:59 waitpid.cpp
Executado
 ``` * *Breve Descrição:* Apareceram as permissões de modificação do usuário, antes do executando. Pois sua chamada ocorre antes.

#### `pop.cpp` (Livro-Texto p. 197)
* **Objetivo do Código:**
Demonstrar a função `popen()` (pipe open).
Similar ao `system()`, ele executa um comando, mas permite ao programa C++ *capturar* a saída do comando (`ls -l`) e processá-la linha por linha.
* **Código-Fonte:** ```cpp // (p. 197)
#include <iostream>
#include <stdio.h> // Para popen, pclose, FILE
#include <stdlib.h> // Para exit
int main() {
FILE *fpipe;
char *command = (char *)"ls -l";
char line[256];
if ( !(fpipe = (FILE*)popen(command,"r")) ) { // (p. 197, linha 9)
perror("Falha ao abrir um pipe");
exit(1); }
while ( fgets( line, sizeof line, fpipe))
{ // (p. 197, linha 13)
std::cout << "Linha: " << line; // line já contém \n
}
pclose(fpipe);
return 0; } ``` * **Análise da Saída:** * *Comando de Compilação:* `g++ -o pop pop.cpp` * *Saída da Execução:* ```bash Linha: total 312
Linha: -rwxr-xr-x 1 userlinux userlinux 16000 Nov 27 12:11 calcfb
Linha: -rw-r--r-- 1 userlinux userlinux   182 Nov 27 12:10 calcfb.cpp
Linha: drwxr-xr-x 2 userlinux userlinux  4096 Nov 26 23:20 cdrom
Linha: -rwxr-xr-x 1 userlinux userlinux 30840 Nov 27 11:40 devices
Linha: -rw-r--r-- 1 userlinux userlinux   541 Nov 27 11:37 devices.cpp
Linha: -rw-r--r-- 1 userlinux userlinux    94 Nov 27 12:09 fibonacci.h
Linha: -rwxr-xr-x 1 userlinux userlinux 16528 Nov 27 11:47 getuuid
Linha: -rw-r--r-- 1 userlinux userlinux  1463 Nov 27 11:47 getuuid.c
Linha: -rwxr-xr-x 1 userlinux userlinux 24168 Nov 27 12:05 myblkid
Linha: -rw-r--r-- 1 userlinux userlinux   534 Nov 27 12:04 myblkid.cpp
Linha: -rwxr-xr-x 1 userlinux userlinux 16624 Nov 27 14:34 pop
Linha: -rw-r--r-- 1 userlinux userlinux   437 Nov 27 14:34 pop.cpp
Linha: -rwxr-xr-x 1 userlinux userlinux 16600 Nov 27 14:24 system
Linha: -rw-r--r-- 1 userlinux userlinux   138 Nov 27 14:23 system.cpp
Linha: -rwxr-xr-x 1 userlinux userlinux 15960 Nov 27 11:58 teste
Linha: -rw-r--r-- 1 userlinux userlinux   112 Nov 27 11:58 teste.c
Linha: -rwxr-xr-x 1 userlinux userlinux 26288 Nov 27 12:22 thread
Linha: -rw-r--r-- 1 userlinux userlinux   338 Nov 27 12:21 thread.cpp
Linha: -rw-r--r-- 1 userlinux userlinux   960 Nov 26 23:45 typescript
Linha: -rwxr-xr-x 1 userlinux userlinux 17496 Nov 27 12:31 usefork
Linha: -rw-r--r-- 1 userlinux userlinux   810 Nov 27 12:31 usefork.cpp
Linha: -rwxr-xr-x 1 userlinux userlinux 16800 Nov 27 13:49 usewait
Linha: -rw-r--r-- 1 userlinux userlinux   622 Nov 27 13:49 usewait.cpp
Linha: -rwxr-xr-x 1 userlinux userlinux 16272 Nov 27 13:54 usewait_exit
Linha: -rw-r--r-- 1 userlinux userlinux   754 Nov 27 13:54 usewait_exit.cpp
Linha: -rwxr-xr-x 1 userlinux userlinux 16792 Nov 27 13:59 waitpid
Linha: -rw-r--r-- 1 userlinux userlinux   611 Nov 27 13:59 waitpid.cpp
 ``` * *Breve Descrição:* O popen utiliza do nome do arquivo para executa-lo diretamente em um pipeline.
#### `receivesignal.cpp` (Livro-Texto p. 203)
* **Objetivo do Código:**
Demonstrar como um processo pode "capturar" (handle) um sinal.
Este programa entra em loop infinito, mas se o usuário pressionar `Ctrl+C` (que envia o sinal `SIGINT`), o programa executa a função `signal_handler` em vez de fechar imediatamente.
* **Código-Fonte:** ```cpp // (p. 203)
#include <iostream>
#include <csignal>
#include <unistd.h>
using namespace std;
void signal_handler (int signum) { // (p. 203, linha 6)
cout << "Processo será interrompido pelo sinal: (" << signum << ")." << endl;
exit(signum); }
int main () {
signal(SIGINT, signal_handler); // (p. 203, linha 12)
while(1) { cout << "Dentro do laço de repetição infinito." << endl;
sleep(1); } return 0; } ``` * **Análise da Saída:** * *Comando de Compilação:* `g++ -o receivesignal receivesignal.cpp` * *Saída da Execução:* (Deixe o programa rodar por 3 segundos e então pressione `Ctrl+C`) ```bash Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
^CProcesso será interrompido pelo sinal: (2).
 ``` * *Breve Descrição:* O programa fechou exibindo o sinal do método, com código 2.

#### `ignoresignal.cpp` (Livro-Texto p. 204)
* **Objetivo do Código:**
Demonstrar como um processo pode *ignorar* ativamente um sinal.
Este programa é similar ao anterior, mas usa `SIG_IGN` para se tornar imune ao `Ctrl+C` (SIGINT).
* **Código-Fonte:** ```cpp // (p. 204)
#include <iostream>
#include <csignal>
#include <unistd.h>
using namespace std;
int main () { signal(SIGINT, SIG_IGN);
// (p. 204, linha 8)
int i = 0;
while(1) {
cout << "Estou em loop imune... (" << ++i << ")" << endl;
sleep(1);
} return 0; } ``` * **Análise da Saída:** * *Comando de Compilação:* `g++ -o ignoresignal ignoresignal.cpp` * *Saída da Execução:* (Pressione `Ctrl+C` várias vezes. Para parar, use `Ctrl+\` (SIGQUIT) ou `kill -9` de outro terminal).
```bash Estou em loop imune... (1)
Estou em loop imune... (2)
Estou em loop imune... (3)
Estou em loop imune... (4)
Estou em loop imune... (5)
Estou em loop imune... (6)
Estou em loop imune... (7)
Estou em loop imune... (8)
Estou em loop imune... (9)
Estou em loop imune... (10)
Estou em loop imune... (11)
Estou em loop imune... (12)
Estou em loop imune... (13)
Estou em loop imune... (14)
Estou em loop imune... (15)
Estou em loop imune... (16)
Estou em loop imune... (17)
Estou em loop imune... (18)
Estou em loop imune... (19)
Estou em loop imune... (20)
Estou em loop imune... (21)
Estou em loop imune... (22)
Estou em loop imune... (23)
Estou em loop imune... (24)
Estou em loop imune... (25)
Estou em loop imune... (26)
Estou em loop imune... (27)
Estou em loop imune... (28)
Estou em loop imune... (29)
Estou em loop imune... (30)
Estou em loop imune... (31)
Estou em loop imune... (32)
Estou em loop imune... (33)
Estou em loop imune... (34)
Estou em loop imune... (35)
^CEstou em loop imune... (36)
^C^C^CEstou em loop imune... (37)
^C^C^CEstou em loop imune... (38)
^C^C^CEstou em loop imune... (39)
Estou em loop imune... (40)
Estou em loop imune... (41)
Estou em loop imune... (42)
Estou em loop imune... (43)
Estou em loop imune... (44)
Estou em loop imune... (45)
Estou em loop imune... (46)
Estou em loop imune... (47)
Estou em loop imune... (48)
Estou em loop imune... (49)
Estou em loop imune... (50)
Estou em loop imune... (51)
Estou em loop imune... (52)
Estou em loop imune... (53)
Estou em loop imune... (54)
Estou em loop imune... (55)
Estou em loop imune... (56)
Estou em loop imune... (57)
Estou em loop imune... (58)
Estou em loop imune... (59)
Estou em loop imune... (60)
Estou em loop imune... (61)
Estou em loop imune... (62)
Estou em loop imune... (63)
Estou em loop imune... (64)
Estou em loop imune... (65)
Estou em loop imune... (66)
^\Quit
 ``` * *Breve Descrição:* O programa ignora o sinal de parada, somente matando o processo com o comando Ctrl+\

#### `raisesignal.cpp` (Livro-Texto p. 204-205)
* **Objetivo do Código:** Demonstrar como um processo pode enviar um sinal *para si mesmo* usando a função `raise()`.
O programa irá rodar por 5 segundos e então se autoenviar um SIGINT.
* **Código-Fonte:** ```cpp // (p. 204-205)
#include <iostream>
#include <csignal>
#include <unistd.h>
using namespace std;
void signal_handler(int signum)
{ cout << "Auto-sinal recebido: (" << signum << ")." << endl;
exit(signum); }
int main () { int i = 0;
signal(SIGINT, signal_handler); // (p. 205, linha 14)
while (++i) { cout << "Dentro do laço de repetição infinito." << endl;
if( i == 5) { raise(SIGINT); // (p. 205, linha 19)
}
sleep(1); }
return 0; } ``` * **Análise da Saída:** * *Comando de Compilação:* `g++ -o raisesignal raisesignal.cpp` * *Saída da Execução:* ```bash Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Auto-sinal recebido: (2).
 ``` * *Breve Descrição:* O programa se interrompeu, pois após cinco segundos, o SIGINT é chamado.

#### `killsignal.cpp` (Livro-Texto p. 205)
* **Objetivo do Código:** Demonstrar como um processo pode enviar um sinal para si mesmo usando `kill()`. É similar ao `raise()`, mas requer que o processo saiba o seu próprio PID. * **Código-Fonte:** ```cpp // (p. 205)
#include <iostream>
#include <csignal>
#include <unistd.h>
using namespace std;
void signal_handler(int signum)
{ cout << "Processo será interrompido pelo sinal: (" << signum << ")." << endl;
exit(signum); }
int main () { int pid, i = 0; pid = getpid(); // (p. 205, linha 19) // (Nota: O livro usa SIGUSR1, vamos capturar SIGUSR1)
signal(SIGUSR1, signal_handler);
while (++i) { cout << "Dentro do laço de repetição infinito." << endl;
if( i == 5) { kill(pid, SIGUSR1); // (p. 205, linha 22)
} sleep(1); } return 0; } ```
* **Análise da Saída:** * *Comando de Compilação:* `g++ -o killsignal killsignal.cpp` * *Saída da Execução:* ```bash Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Dentro do laço de repetição infinito.
Processo será interrompido pelo sinal: (10).
 ``` * *Breve Descrição:* O programa se auto-encerrou, com um sinal 10.

#### `forksignal.cpp` (Livro-Texto p. 206)
* **Objetivo do Código:** Um exemplo complexo de IPC usando sinais. O processo-pai e o processo-filho se comunicam: o pai envia um sinal para o filho (`SIGUSR1`), e o filho envia um sinal de volta para o pai (`SIGUSR1`).
* **Código-Fonte:** ```cpp // (p. 206)
#include <iostream>
#include <csignal>
#include <unistd.h>
#include <sys/wait.h>
using namespace std;
void signal_parent_handler(int signum) {
cout << "Processo (PAI) recebeu sinal: (" << signum << ")." << endl; }
void signal_child_handler(int signum) { cout << "Processo (FILHO) recebeu sinal: (" << signum << ")." << endl; }
int main () { pid_t pid; pid = fork(); if (pid < 0) { cerr << "Erro no fork" << endl; return 1; } else if (pid == 0) { // Processo Filho
signal(SIGUSR1, signal_child_handler); cout << "Processo filho aguardando sinal..." << endl; pause(); // Espera pelo sinal do pai (p. 206, linha 32)
cout << "Filho enviando sinal de volta ao pai..." << endl; kill(getppid(), SIGUSR1); // Envia sinal para o pai (p. 206, linha 34)
exit(0); } else { // Processo Pai
signal(SIGUSR1, signal_parent_handler); sleep(2); // Garante que o filho está pronto e esperando
cout << "Pai enviando sinal para o filho " << pid << "." << endl;
kill(pid, SIGUSR1); // (p. 206, linha 38)
cout << "Processo pai aguardando resposta..." << endl;
pause(); // Espera pelo sinal do filho (p. 206, linha 40)
wait(NULL); // Limpa o filho
cout << "Pai terminando." << endl; }
return 0; } ``` * **Análise da Saída:** * *Comando de Compilação:* `g++ -o forksignal forksignal.cpp` * *Saída da Execução:* ```bash Processo filho aguardando sinal...
Pai enviando sinal para o filho 607.
Processo pai aguardando resposta...
Processo (FILHO) recebeu sinal: (10).
Filho enviando sinal de volta ao pai...
Processo (PAI) recebeu sinal: (10).
Pai terminando.
 ``` * *Breve Descrição:* Pai e filho recebem o sinal. Pause faz com que o processo aguard o sinal.

--- ### Códigos do Capítulo 9 (Redes) #### `resolveaied.cpp` (Livro-Texto p. 264) * **Objetivo do Código:** Demonstrar uma consulta DNS básica. O programa usa a função `gethostbyname` para traduzir um nome de domínio (`www.aied.com.br`) em seu endereço IP. * **Código-Fonte:** ```cpp // (p. 264, versão simples)
#include <netdb.h>
#include <arpa/inet.h>
#include <iostream> int main() { struct hostent *he; char *ip; he = gethostbyname("[www.aied.com](https://www.aied.com).br"); // (p. 264, linha 9)
if (he) { ip = inet_ntoa(*(struct in_addr*) he->h_addr_list[0]);
 std::cout << ip << std::endl; }
else { std::cerr << "Erro ao resolver host." << std::endl; } return 0; } ``` * **Análise da Saída:**
* *Comando de Compilação:* `g++ -o resolveaied resolveaied.cpp` * *Saída da Execução:* ```bash (212.1.209.207
 ``` * *Breve Descrição:* 212.1.209.207
#### `testport.cpp` (Livro-Texto p. 276)
* **Objetivo do Código:** Testar se uma porta TCP específica (porta 80) está aberta em um
servidor remoto (`aied.com.br`). Requer a biblioteca SFML.
* **Código-Fonte:**
```cpp
// (p. 276)
#include <iostream>
#include <SFML/Network.hpp> // (p. 276, linha 2)
#include <string>
static bool port_is_open(const std::string& address, int port) { // (p. 276, linha 5)
return (sf::TcpSocket().connect(address, port) == sf::Socket::Done);
}
int main() {
std::cout << "Testando Porta 80: aied.com.br" << std::endl; // (p. 276, linha 13)
if ( port_is_open("aied.com.br", 80) )
std::cout << "Porta está ABERTA" << std::endl;
else
std::cout << "Porta está FECHADA" << std::endl;
return 0;
}
```
* **Análise da Saída:**
* *Comando de Compilação:* `g++ -o testport testport.cpp -lsfml-network -lsfml-system`
* *Saída da Execução:*
```bash
Testando Porta 80: aied.com.br
Porta está ABERTA

```
* *Breve Descrição:* Porta aberta

#### `getcurl.cpp` (Livro-Texto p. 283-284)
* **Objetivo do Código:** Demonstrar como fazer o download de um arquivo (uma imagem
`.iso`) de uma URL usando a biblioteca `libcurl` em C++.
* **Código-Fonte:**
```cpp
// (p. 283-284)
#include <stdio.h>
#include <curl/curl.h> // (p. 283, linha 2)
int main(void) {
CURL *curl;
FILE *fp;
CURLcode res;
char url[] =
"[http://www.aied.com.br/linux/download/output_image.iso](http://www.aied.com.br/linux/download/out
put_image.iso)"; // (p. 283, linha 8)
char outfilename[FILENAME_MAX] = "/tmp/output_image.iso"; // (p. 283, linha 9)
curl = curl_easy_init();
if (curl) {
fp = fopen(outfilename, "wb"); // (p. 284, linha 12)
curl_easy_setopt(curl, CURLOPT_URL, url);
curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, NULL);
curl_easy_setopt(curl, CURLOPT_WRITEDATA, fp);
res = curl_easy_perform(curl);
curl_easy_cleanup(curl);
fclose(fp);
if (res == CURLE_OK)
printf("Download concluído com sucesso para /tmp/output_image.iso\n");
else
printf("Erro no download: %s\n", curl_easy_strerror(res));
}
return 0;
}
```
* **Análise da Saída:**
* *Comando de Compilação:* `g++ -o getcurl getcurl.cpp -lcurl`
* *Saída da Execução:*
```bash
(Cole aqui a saída exata do seu terminal ao rodar ./getcurl)
```
* *Breve Descrição:* (O programa reportou sucesso? Verifique com `ls -lh /tmp/output_image.iso` se
o arquivo realmente foi baixado e qual o seu tamanho.)

#### `getcurl.cpp` (Livro-Texto p. 283-284)
* **Objetivo do Código:** Demonstrar como fazer o download de um arquivo (uma imagem
`.iso`) de uma URL usando a biblioteca `libcurl` em C++.
* **Código-Fonte:**
```cpp
// (p. 283-284)
#include <stdio.h>
#include <curl/curl.h> // (p. 283, linha 2)
int main(void) {
CURL *curl;
FILE *fp;
CURLcode res;
char url[] =
"[http://www.aied.com.br/linux/download/output_image.iso](http://www.aied.com.br/linux/download/out
put_image.iso)"; // (p. 283, linha 8)
char outfilename[FILENAME_MAX] = "/tmp/output_image.iso"; // (p. 283, linha 9)
curl = curl_easy_init();
if (curl) {
fp = fopen(outfilename, "wb"); // (p. 284, linha 12)
curl_easy_setopt(curl, CURLOPT_URL, url);
curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, NULL);
curl_easy_setopt(curl, CURLOPT_WRITEDATA, fp);
res = curl_easy_perform(curl);
curl_easy_cleanup(curl);
fclose(fp);
if (res == CURLE_OK)
printf("Download concluído com sucesso para /tmp/output_image.iso\n");
else
printf("Erro no download: %s\n", curl_easy_strerror(res));
}
return 0;
}
```
* **Análise da Saída:**
* *Comando de Compilação:* `g++ -o getcurl getcurl.cpp -lcurl`
* *Saída da Execução:*
```bash
Download concluído com sucesso para /tmp/output_image.iso
```
* *Breve Descrição:* -rw-r--r-- 1 userlinux userlinux 795 Nov 28 00:09 /tmp/output_image.iso

#### `postjson.cpp` (Livro-Texto p. 284-285)
* **Objetivo do Código:** Demonstrar como enviar dados (um payload JSON) para um
servidor web usando o método `POST` com a `libcurl`.
* **Código-Fonte:**
```cpp
// (p. 284-285)
#include <stdio.h>
#include <curl/curl.h>
#include <string>
int main(void) {
CURLcode ret;
CURL *hnd;
struct curl_slist *slist1;
std::string jsonstr = "{\"username\":\"aied\",\"password\":\"123456\"}"; // (p. 284, linha 10)
slist1 = NULL;
slist1 = curl_slist_append(slist1, "Content-Type: application/json"); // (p. 284, linha 13)
hnd = curl_easy_init();
curl_easy_setopt(hnd, CURLOPT_URL,
"[http://www.aied.com.br/linux/download/echo.php](http://www.aied.com.br/linux/download/echo.php)")
; // (p. 284, linha 18)
curl_easy_setopt(hnd, CURLOPT_POSTFIELDS, jsonstr.c_str());
curl_easy_setopt(hnd, CURLOPT_USERAGENT, "curl/7.38.0");
curl_easy_setopt(hnd, CURLOPT_HTTPHEADER, slist1);
curl_easy_setopt(hnd, CURLOPT_CUSTOMREQUEST, "POST"); // (p. 285, linha 23)
ret = curl_easy_perform(hnd);
curl_easy_cleanup(hnd);
hnd = NULL;
curl_slist_free_all(slist1);
slist1 = NULL;
return 0;
}
```
* **Análise da Saída:**
* *Comando de Compilação:* `g++ -o postjson postjson.cpp -lcurl`
* *Saída da Execução:*
```bash
<!DOCTYPE html>
<html style="height:100%">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
<title> 301 Moved Permanently
</title><style>@media (prefers-color-scheme:dark){body{background-color:#000!important}}</style></head>
<body style="color: #444; margin:0;font: normal 14px/20px Arial, Helvetica, sans-serif; height:100%; background-color: #fff;">
<div style="height:auto; min-height:100%; ">     <div style="text-align: center; width:800px; margin-left: -400px; position:absolute; top: 30%; left:50%;">
        <h1 style="margin:0; font-size:150px; line-height:150px; font-weight:bold;">301</h1>
<h2 style="margin-top:20px;font-size: 30px;">Moved Permanently
</h2>
<p>The document has been permanently moved.</p>
</div></div></body></html>
userlinux@debian:~$ ./postjson
<!DOCTYPE html>
<html style="height:100%">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
<title> 301 Moved Permanently
</title><style>@media (prefers-color-scheme:dark){body{background-color:#000!important}}</style></head>
<body style="color: #444; margin:0;font: normal 14px/20px Arial, Helvetica, sans-serif; height:100%; background-color: #fff;">
<div style="height:auto; min-height:100%; ">     <div style="text-align: center; width:800px; margin-left: -400px; position:absolute; top: 30%; left:50%;">
        <h1 style="margin:0; font-size:150px; line-height:150px; font-weight:bold;">301</h1>
<h2 style="margin-top:20px;font-size: 30px;">Moved Permanently
</h2>
<p>The document has been permanently moved.</p>
</div></div></body></html>
userlinux@debian:~$ nano postjson.cpp
userlinux@debian:~$ ./postjson
<!DOCTYPE html>
<html style="height:100%">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
<title> 301 Moved Permanently
</title><style>@media (prefers-color-scheme:dark){body{background-color:#000!important}}</style></head>
<body style="color: #444; margin:0;font: normal 14px/20px Arial, Helvetica, sans-serif; height:100%; background-color: #fff;">
<div style="height:auto; min-height:100%; ">     <div style="text-align: center; width:800px; margin-left: -400px; position:absolute; top: 30%; left:50%;">
        <h1 style="margin:0; font-size:150px; line-height:150px; font-weight:bold;">301</h1>
<h2 style="margin-top:20px;font-size: 30px;">Moved Permanently
</h2>
<p>The document has been permanently moved.</p>
</div></div></body></html>
userlinux@debian:~$ g++ -o postjson postjson.cpp -lcurl
userlinux@debian:~$ ./postjson
<!DOCTYPE html>
<html style="height:100%">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
<title> 301 Moved Permanently
</title><style>@media (prefers-color-scheme:dark){body{background-color:#000!important}}</style></head>
<body style="color: #444; margin:0;font: normal 14px/20px Arial, Helvetica, sans-serif; height:100%; background-color: #fff;">
<div style="height:auto; min-height:100%; ">     <div style="text-align: center; width:800px; margin-left: -400px; position:absolute; top: 30%; left:50%;">
        <h1 style="margin:0; font-size:150px; line-height:150px; font-weight:bold;">301</h1>
<h2 style="margin-top:20px;font-size: 30px;">Moved Permanently
</h2>
<p>The document has been permanently moved.</p>
</div></div></body></html>

```
* *Breve Descrição:* Enviou uma pagina html, retornando seus dados.

#### `download.sh` (Livro-Texto p. 285-286)
* **Objetivo do Código:** Criar um script de download robusto que baixa arquivos de uma lista
(`urls.txt`) e tenta novamente (`--retry`) em caso de falha, continuando de onde parou (`-C`).
* **Código-Fonte:**
*(Nota: Crie o arquivo `urls.txt` em `~/Downloads/` antes, contendo a URL:
http://www.aied.com.br/linux/download/output_image.iso)*
```bash
#!/bin/bash
# (p. 285-286)
# (Variável para o diretório de downloads do usuário atual)
DOWNLOAD_DIR="/home/$(whoami)/Downloads"
URL_FILE="$DOWNLOAD_DIR/urls.txt"
# (Cria o diretório e o arquivo se não existirem)
mkdir -p $DOWNLOAD_DIR
echo
"[http://www.aied.com.br/linux/download/output_image.iso](http://www.aied.com.br/linux/download/out
put_image.iso)" > $URL_FILE
cd $DOWNLOAD_DIR
while true
do
# (O comando xargs lê o arquivo e passa a URL para o curl)
# (Removido o parâmetro -x socks5h... para TOR, conforme nota do manual)
xargs -n 1 curl -L -O --output-dir $DOWNLOAD_DIR -k --retry 999999999999 --retry-max-time 0
-C - < $URL_FILE
echo "Loop esperando 30s..."
sleep 30
done
```
* **Análise da Saída:**
* *Comando de Execução:* `chmod +x download.sh` e depois `./download.sh` (use `Ctrl+C` para
parar o loop)
* *Saída da Execução:*
```bash
link quebrado
```
* *Breve Descrição:* (O `curl` baixou o arquivo? O que o `xargs` fez? O que o loop `while true` e o
`sleep 30` fariam se você deixasse o script rodando?






