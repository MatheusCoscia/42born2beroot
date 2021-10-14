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

#### ~Configurações do SSH e Firewall (UFW)

##### Instalando e Configurando o SSH

<p>Realize a instalação do SSH.</p>

```
$	#
```

##### Instalando e Configurando o UFW

<p>Realize a instalação do UFW.</p>

```
$	#
```

#### ~Política de Senhas

#### ~Cron e Scripts

##### CRÉDITOS

<p><a href="https://github.com/vangoncalez/42sp_borntoberoot">vangoncalez</a><br>
<a href="https://github.com/hanshazairi/42-born2beroot#installation">hanshazairi</a></p>
