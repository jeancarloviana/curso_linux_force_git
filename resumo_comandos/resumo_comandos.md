## Comando linux:


### Mostra o nivel no sistema de arquivos:

>pwd - mostra o nivel na arvore de diretórios

```
jeancviana@DESKTOP-6SOQARG:~$ pwd
/home/jeancviana
``` 

### Verificar informações do usuario:

>whoami - mostra o user logado

```
jeancviana@DESKTOP-6SOQARG:~$ whoami
jeancviana
```

### Verificar informações do usuario:

> id - verificar os grupos que o usuario faz parte

```
jeancviana@DESKTOP-6SOQARG:~$ id
uid=1000(jeancviana) gid=1000(jeancviana) grupos=1000	(jeancviana),4	(adm),24(cdrom),27(sudo),30(dip),46	(plugdev),119(lxd)
jeancviana@DESKTOP-6SOQARG:~$
```

### Tipos de usuarios:

>usuario comum: poucos privilégios
>usuario root: usuario adm do sistema

### Comando su:

> su - : para subir a sessão como root com as variaveis de sistema do usuario

```
jeancviana@DESKTOP-6SOQARG:~$ su - root
Palavra-passe:
root@DESKTOP-6SOQARG:~#
```

### Nome da máquina:

> hostname : traz o nome da máquina

```
root@DESKTOP-6SOQARG:/etc# hostname
DESKTOP-6SOQARG
root@DESKTOP-6SOQARG:/etc#
```

### Vendo informações da máquina:

> hostnamectl : traz maiores informações sobre a máquina  

```
analista@debian:~$ hostnamectl
   	Static hostname: debian
         Icon name: computer-vm
           Chassis: vm
        Machine ID: ff5ce99eac784cddb2ebb3a00b1d1eb9
           Boot ID: 87bb4c2fb0724e2da268c03a0241afdb
    	Virtualization: oracle
  	Operating System: Debian GNU/Linux 11 (bullseye)
            Kernel: Linux 5.10.0-20-amd64
      Architecture: x86-64
```

### Setando o nome da máquina:

> hostnamectl set-hostname interno.asf.com (TROCANDO O HOSTNAME DA MÁQUINA)
EX.: analista@debian:~$ hostnamectl set-hostname interno.asf.com
analista@debian:~$ hostnamectl 
   Static hostname: interno.asf.com
         Icon name: computer-vm
           Chassis: vm
        Machine ID: ff5ce99eac784cddb2ebb3a00b1d1eb9
           Boot ID: 87bb4c2fb0724e2da268c03a0241afdb
    Virtualization: oracle
  Operating System: Debian GNU/Linux 11 (bullseye)
            Kernel: Linux 5.10.0-20-amd64
      Architecture: x86-64
analista@debian:~$ 


### Comando para caminhar na arvore de diretórios:

> cd + caminho do arquivo por exemplo cd /home/analista ou cd ~/analista
> cd /: vai para o diretório raiz
> cd ~: vai para o diretório home
> cd .. ou cd ../../ : volta a quantidade de niveis digitados
> cd - : volta para o diretório anterior
> 
> . caminho do diretório atual
> .. caminho do diretório anterior

## Sistema de diretórios FHS Filesystem Hierarchy Standard:

> O Filesystem Hierarchy Standard (“FHS”) é um padrão na hierarquia do sistema GNU/Linux.

> /       :diretório raiz
> 
> /bin    : Este diretório contém os comandos básicos para todos os usuários (cp, mv, rm…). Esses são os comandos necessários para iniciar o sistema.
> 
> /boot   :Aqui é onde os arquivos do seu carregador de boot (GRUB, por exemplo) e os kernels do Linux estão localizados.
> 
> /dev    :Links para periféricos físicos (CDs, discos rígidos, etc.), bem como periféricos virtuais (/dev/null, /dev/random). Observe que os dispositivos físicos são nomeados como /dev/sdXN com X sendo uma letra e N um número: /dev/sda1 representa a primeira partição (1) de seu primeiro disco rígido (a) ou /dev/sdd6 representa a sexta partição (6) de seu quarto disco rígido (d) …
> 
> /etc    :Este é o local dos arquivos globais de configuração dos programas instalado.
> 
> /home   :Diretório que contém as pastas do usuário no formato /home/nome-do-usuário.
> 
> /lib:   Diretório onde as bibliotecas do sistema estão instaladas.
> 
> /mnt    :Ponto de montagem para partições internas montadas temporariamente. As partições de discos rígidos internos geralmente são montadas aqui. Para partições externas, usaremos /media em seu lugar.
> 
> /media  :Equivalente a /mnt, mas para mídia removível/externa.
> 
> /opt    :É reservado para instalar pacotes de aplicativos extras, baixados da Internet, como o Google Chrome.
> 
> /proc   :Sistema de arquivos virtual apresenta informações sobre processos e outras informações de sistema em uma estrutura hierárquica semelhante a arquivos, fornecendo um método mais conveniente e padronizado para acessar dinamicamente dados de processos armazenados no núcleo do que os métodos de rastreamento tradicionais ou acesso direto à memória do núcleo. (Wikipedia, 2020)
> 
> /root   :Diretório do usuário root.
> 
> /sbin   :Série de executáveis ​​para administradores.
> 
> /srv    :Dados para serviços hospedados pelo sistema. Por exemplo, conteúdo de um servidor web (HTTP) ou de um banco de dados.
> 
> /tmp    :Diretório de arquivos temporários, esvaziado cada vez que o sistema é iniciado.
> 
> /usr    :Pasta contendo os executáveis ​​do sistema que não são vitais para sua inicialização e seu funcionamento mínimo.
> 
> /var    :Pasta com conteúdos de dados variáveis ​​do sistema, indicando seu status. Dividido em subpastas.

### Criando arquivos vazios:

> touch : cria arquivo em branco
> touch arquivo1: cria o arquivo em branco arquivo1 podem sem criados varios arquivos em sequencia touch arquivo1 touch arquivo2 
> touch doc0{1..5}.txt para criar arquivos em sequênciacd ..

### Apagando diretório e arquivos:

> rm - apaga arquivos
> rm -rf : -r forma recursiva para apagar arquivos, -f força apagar sem pedir permissão (sem chance de salvação)
> rm -rfd : -d apaga o diretório (sem chance de salvação)

> rmdir: apaga diretório mas tem que estar vazio

### Comando de cópia:

> cp arquivo ou diretório a copiar + caminho do diretório de destino

```
cp -rp /var/log/   /tmp/
```