## Configurando o Servidor

<p>Durante o processo de configuração do servidor é recomendável estar logado como <b>root</b> para ter acesso total a todas as ferramentas de edição necessárias para a criação do projeto.</p>
<p>Todas as etapas aqui apresentadas seguem estritamente o PDF fornecido pela 42 para a criação do born2beroot.</p><br>

#### ~Configurações Básicas

##### Sistema Operacional

<p>Consulte o sistema operacional instalado em sua VM.</p>

```
$	head -n 2 /etc/os-release	# consultar as somente as linhas que informam o sistema
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
