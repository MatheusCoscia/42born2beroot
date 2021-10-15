## Configurando o Servidor

<p>Durante o processo de configuração do servidor é recomendável estar logado como <b>root</b> para ter acesso total a todas as ferramentas de edição necessárias para a criação do projeto.</p>
<p>Todas as etapas aqui apresentadas seguem estritamente o PDF fornecido pela 42 para a criação do born2beroot.</p><br>

#### ~Configurações Básicas

##### Sistema Operacional

<p>Consulte o sistema operacional instalado em sua VM.</p>

```
$	head -n 2 /etc/os-release	# consultar somente as linhas que informam o sistema
$	cat /etc/os-release		# consultar o arquivo em sua totalidade
```

##### Repartição de Memória

<p>Confira se o particionamento de memória esta correto através do comando lsblk.</p>

```
$	lsblk
```

<p>Caso ocorra alguma divergência entre sua repartição de memória e a informada pelo PDF do projeto será necessário recomeçar o processo de criação da VM.</p><br>

#### ~Gerenciador de Pacotes

<p>O <b>apt</b> é um gerenciador de pacotes de nível inferiorque não possui uma interface gráfica.</p>
<p>Mesmo com duas opções de gerenciadores de pacotes, o <b>apt já vem instalado como gerenciador padrão no Debian</b>.</p>

##### Conferindo a Instalação do apt

<p>Sendo o gerenciador de pacotes padrão do Debian é necessário somente verificar sua instalação.</p>

```
$	apt-get update
```

<br>

#### ~Configuração e Instalação do Sudo

##### Instalando o Sudo

<p>Realize a instalação do sudo.</p>

```
$	apt-get install sudo
```

<p>Verifique a instalação do sudo.</p>

```
$	dpkg -l | grep sudo
```

##### Adicionando/Removendo um Úsuario ao Sudo

<p>Adicione o úsuario root ao grupo do Sudo. Esse processo pode ser realizado para adicionar qualquer úsuario ao grupo.</p>

```
$	gpasswd -a <username> sudo
```

<p>Verifique se o úsuario foi adicionado corretamente ao grupo Sudo.</p>

```
$	getent group sudo
```

<p>Ao adicionar um novo úsuario ao grupo Sudo é necessário reiniciar sua máquina e conferir as instruções do grupo.</p>

```
$	reboot
$	sudo -v
```

<p>Verifique os privilégios do grupo Sudo.</p>

```
$	sudo apt update
```

<p>Caso necessário é possível remover um úsuario do grupo Sudo.</p>

```
$	gpasswd -d <username> sudo
```

##### Configurando o Sudo

<p>Crie um novo diretório para registrar os logins e logouts do grupo.</p>

```
$	sudo mkdir /var/log/sudo
```

<p>Abra o arquivo de configuração do Sudo, tanto através do comando ou do diretório.</p>

```
$	sudo visudo -f etc/sudoers.d/<file>	# acessar as confgs do sudo através do diretório
$	sudo visudo				# comando para acessar as confgs do sudo
```

<p>Configure as tentativas de autentificações de entrada.</p>

```
Defaults	passwd_tries = 3
Defaults	badpass_message = "WRONG PASSWORD"
```

<p>Registre os logins e logouts do grupo.</p>

```
Defaults	logfile="/var/log/sudo/<filename>"
Defaults	log_input, log_output
Defaults	iolog_dir="/var/log/sudo"
```

<p>Adicione o Requiretty, habilitando o modo TTY.</p>

```
Defaults	requiretty
```

<p>Por fim, altere o caminho do secure_path.</p>

> O antigo caminho será ```secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin:```

```
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
```

<br>

#### ~Configurações do SSH e Firewall (UFW)

##### Instalando e Configurando o SSH

<p>Realize a instalação do SSH.</p>

```
$	apt install openssh-server
```

<p>Verifique a instalação do SSH.</p>

```
$	dpkg -l | grep ssh
```

<p>Acesse o diretório em que o SSH foi instalado e comece a configurar o programa.</p>

```
$	nano etc/ssh/ssh_config
```

<p>As configurações do SSH são simples e exigem pequenas alterações nas linahs de código já existentes.</p>

> Na linha 13 teremos o comentário: #Port 22.

```
13	Port 4242
```

> Na linha 32 teremos co comentário: #PermitRootLogin prohibit-password.

```
32	PermitRootLogin no
```

<p>Por fim verifique se as modificações foram bem sucedidas.</p>

```
$	service ssh status
```

##### Instalando e Configurando o UFW

<p>Realize a instalação do UFW.</p>

```
$	apt install ufw
```

<p>Habilite o UFW.</p>

```
$	ufw enable
```

<p>Permita conexões ao seu servidor através da porta 4242.</p>

```
$	ufw allow 4242
```

<p>Confira as configurações do UFW.</p>

```
$	dpkg -l | grep ufw
$	ufw status
```

<br>

#### ~Configurações de Úsuario

##### Política de Senha - Tempo de Utilização

<p>Acesse o diretório em que as configurações de senha estão presentes.</p>

```
$	nano /etc/login.defs
```

<p>Para instaurar uma política de senhas fortes é necessário realizar a modificação de alguns parâmetros já pré-estabelecidos pelo Debian.</p>

> Na linha 160 altere o tempo em dias que sua senha ira expirar. Modifique de 99999 para 30.

```
160		PASS_MAX_DAYS   30
```

>  Na linha 161 altere o delay em que sua senha poderá ser alterada. Modifique de 0 para 2.

```
161		PASS_MIN_DAYS   2
```

>  Na linha 162 adicione uma mensagem de alerta 7 dias antes de sua senha expirar.

```
162		PASS_WARN_AGE   7
```

##### Política de Senha - Senha Forte

<p>Realize a instalação do "plugin" libpam-pwquality, responsável por monitorar uma política de senha forte.</p>

```
$	apt install libpam-pwquality
```

<p>Acesse o diretório em que o libpam-pwquality foi instalado.</p>

```
$	nano /etc/pam.d/common-password
```

<p>Para instaurar uma política de senhas fortes é necessário acrescebtar algumas regras ao "plugin".</p>

> Na linha 25 você deverá acrescentar a linha de regras abaixo.
A antiga regra, que deve ser substituída será: ```25 password requisite pam_pwquality.so retry=3```

```
25	password	requisite	pam_pwquality.so retry=3 minlen=10 ucredit=-1 dcredit=-1 maxrepeat=3 reject_username difok=7 enforce_for_root

```

<p>Por fim, verifique se o "plugin" foi instalado corretamente.</p>

```
$	dpkg -l | grep libpam-pwquality
```

##### Verificando seus Úsuarios

<p>Caso seja necessário realizar a criação de um novo úsuario o comando abaixo deverá ser utilizado.</p>

```
$	adduser <username>
```

<p>Caso seja necessário realizar a remoção de um úsuario o comando abaixo deverá ser utilizado.</p>

```
$	deluser <username>
```

<p>Para verificar a existência de um úsuario é necessário utilizar o código abaixo.</p>

```
$	getent passwd <username>
```

<p>Para verificar quanto tempo falta para que uma senha de um úsuario esteja prestes a expirar utilize o código abaixo.</p>

```
$	chage -l <username>
```

##### Gerenciando Grupos

<p>Dando continuidade ao projeto, o novo grupo 'user42' deverá ser criado.</p>

```
$	addgroup user42
```

<p>Para deletar um grupo já existente é necessário utilizar o código abaixo.</p>

```
$	delgroup <group_name>
```

<p>Para verificar a existência de um grupo é necessário acessar o diretório group.</p>

```
$	cat etc/group
```

<p>Para verificar se um úsuario foi corretamente adicionado a um grupo utilize o código abaixo.</p>

```
$	getent group user42
```

<br>

#### ~Configuração do Cron

##### Regras do Cron

<p>Acesse as configurações do Cron.</p>

```
$	crontab -e
```

<p>Configure uma regra para que um Script seja transmitido a cada 10min.</p>

> Na linha 23 você deverá acrescentar a linha de regras abaixo.
A antiga regra, que deve ser substituída será: ```23 # m h dom mon dow command```

```
23		*/10 * * * * sh /path/to/script
```

##### Script

<p>Crie um novo diretório para armazenar o script que deverá ser transmitido através do Cron.</p>

```
$	mkdir scripts
```

<p>Acesse sua nova pasta criada para criar (copiar e colar) um código em Shell que irá transmitir algumas as informações básicas sobre sua VM.</p>

```
echo -ne "ARCHITECTURE: "; uname -a
echo -ne "CPU PHYSICAL: "; grep -c processor /proc/cpuinfo
echo -ne "VIRTUAL CPU: "; cat /proc/cpuinfo | grep processor | wc -l
echo -ne "MEMORY USAGE: "; free -m | awk 'NR==2{printf "%s/%sMB (%.2f%%)\n", $3,$2,$3*100/$2}'
echo -ne "DISK USAGE: "; df -h | awk '$NF=="/"{printf "%d/%dGB (%s)\n", $3,$2,$5}'
echo -ne "CPU LOAD: "; top -bn1 | grep load | awk '{printf"%.2f%%\n", $(NF-2)}'
echo -ne "LAST BOOT: "; who | awk '{printf $3 }' | tr '\n' ' ' && who | awk '{printf $4}'
echo -ne "\nLVM USE: "; if cat /etc/fstab | gre -q "/dev/mapper/"; then echo "yes"; else echo "no";fi
echo -ne "CONNEXIONS TCP: "; cat /proc/net/tcp | wc -l | wak '{print $1-1}' | tr '\n' ' ' && echo "ESTABLISHED"
echo -ne "USER LOG: "; w | wc -l | awk '{print$1-2}'
echo -ne "NETWORK: "; echo -n "IP" && ip route list | grep default | wak '{print $3}' | tr '\n' ' ' && echo -n "9" && ip link show | grep link/ether | awk '{print $2}' | tr '\n' ')' && printf "\n"
echo -ne "SUDO COUNTER: "; journalctl _COMM=sudo | grep COMMAND | wc -l | tr '\n' ' ' && echo Comands
printf "\n"
```

<p>Caso você queira testar a funcionalidade do script utilize o código abaixo.</p>

```
$	crontab -u root -l
```

<br>

##### CRÉDITOS

<p><a href="https://github.com/vangoncalez/42sp_borntoberoot">vangoncalez</a><br>
<a href="https://github.com/hanshazairi/42-born2beroot#installation">hanshazairi</a></p>
