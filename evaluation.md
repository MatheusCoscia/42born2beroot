## Quem não cola, não sai da escola!

<p>Chegou o momento mais importante do projeto, o momento da avaliação entre pares.</p>
<p>A régua de avaliação sugerida pela 42 engloba assuntos e conceitos que você pode ter deixado passar em branco, então é recomendável revisar seu projeto e se preparar.</p><br>

### Avaliação

#### "signature.txt"

<p>Um arquivo chamado "signature.txt" deve ser enviado através do git para a avaliação da 42.</p>
<p>Este arquivo deve conter o Virtual Disk Image (vdi) de sua VM recem criada, para tal é necessário através de seu CMD ou PowerShell executar os seguintes comandos:</p>

> Acesse a pasta a qual seu software de virtualização foi instalado e rode o código.

```
$ 	cd Vir...
$	certUtil -hashfile "file.vdi" sha1
```

<p>Após ter acesso ao vdi de sua VM é de extrema importância que você não realize mais nenhuma modificação em seu servidor, portante <b>certifique-se que o projeto está finalizado</b>.</p><br>

#### Parte Obrigatória

##### Visão Geral do Projeto

<p>Como funciona uma VM e qual sua finalidade?</p>

> A VM, através do hardware do seu computador, irá emular um sistema operacional em um ambiente controlado de teste, sem interferir nos dados de seu computador.

<br>

<p>Qual a diferença entre Debian e CentOs?

> O Debian, além de ser mais amigável com o úsuario, possui uma ampla distribuição, logo, seu suporte é mais facilitado.
Já o CentOs é voltada para o setor empresárial, possuindo mais estabilidade, porém com menos suporte e atualizações.

<br>

<p>Qual a diferença entre apt e aptitude?

> O apt já vem instalado por padrão no sistema Debian.
A principal diferença entre os dois gerenciadores é sua interface gráfica.

<br>

<p>O que é APPArmor?

> É responsável pela liberação de úsuarios/aplicativos para a realização de determinadas tarefas.

<br>
<br>

##### Configuração Simples

<p>Verifique se o UFW está ativado.</p>

> No terminal execute o comando ```ufw status```.

<br>

<p>Verifique se o SSH está ativado.</p>

> No terminal execute o comando ```service ssh status```.

<br>

<p>Verifique se o sistema operacional foi escolhido corretamenta.</p>

> No terminal execute o comando ```uname -a```.

<br>
<br>

##### Do Utilizador

<p>Verifique se o úsuario criado pelo avaliador com o nome "login42" está presente nos grupos "sudo" e "user42".</p>

> No terminal execute o comando ```getent group user42``` e em seguida o comando ```getent group sudo```.

<br>

<p>Crie um novo úsuario e verifique se a política de senhas fortes está implementada.</p>

> No terminal execute o comando ```adduser <username>```.

<br>

<p>Como você adicionou as regras para criar uma política de senhas?</p>

> No terminal acesse o diretório do libpam-pwquality através do comando ```nano /etc/pam.d/common-password```.

> As regras presentes na linha 25 são responsáveis pela política de senhas, sendo que cada uma delas significa:
<ol>
	<ul>
		<li>retry = quantas vezes posso errar a senha;</li>
		<li>minlen = temanho minímo da senha;</li>
		<li>ucredit = quantidade de caracteres em uppercase;</li>
		<li> dcredit = quantidade de números;</li>
		<li>maxrepeat = quantas vezes um caractere pode se repetir;</li>
		<li>reject_username = não permitir que seu username esteja presente na senha;</li>
		<li>difok = ao alterar a senha, quantos caracteres podem ser iguais;</li>
		<li>enforce_for_root = não permite que um úsuario altere a senha do root.</li>
	</ul>
</ol>

<br>

<p>Crie um novo grupo chamado "evaluation" e adicione o novo úsuario a ela.</p>

> No terminal execute o comando ```addgroup evaluation``` e em seguida para adicionar o úsuario ao novo grupo utilize o comando ```gpasswd -a <username> evaluation```.

> Para verificar se o úsuario foi adicionado corretamente ao grupo execute o comando ```getent group evaluation```.

<br>

<p>Por que devemos utilizar uma política de senhas?</p>

> A política de senhas serve para que você não seja hackeado, evitando assim perdas de dados ou acesso de terceiros a seu servidor.

<br>
<br>

##### Nome do Host e Partições

<p>Verifique se o nome do host está formatado corretamente.</p>

> No terminal execute o comando ```hostname```.

<br>

<p>Redefina o nome do host.</p>

> No terminal execute o comando ```hostnamectl set-hostname <username>```.
Em seguida utilize o comando ```reboot``` para reiniciar sua VM e conferir o novo hostname.

<br>

<p>Visualize as partições de memória da sua VM.</p>

> No terminal execute o comando ```lsblk```.

<br>

<p>O que é LVM e qual sua função?</p>

> O Gerenciador de Volumes Lógicos é responsável por realizar o gerenciamento do disco rígido através de grupamentos lógicos.
A vantagem de sua utilização se da graças a facilidade de redimensionamento de memória e modificações gerais.

<br>
<br>

##### Sudo

<p>Verifique se o Sudo está corretamente instalado.</p>

> No terminal execute o comando ```dpkg -l | grep sudo```.

<br>

<p>Adicione seu novo usuário ao grupo Sudo e verifique se a operação ocorreu corretamente.</p>

> No terminal execute o comando ```adduser <username> sudo``` e em seguida utilize o comando ```getent group sudo```.

<br>

<p>O que é o Sudo?</p>

> O sudo é um "super usuário", ou seja, um administrador que pode executar tarefas restritas ao usuário root.
Além de tudo já visto até aqui, é possível citar como um exemplo de ação do Sudo o comando ```apt update```.

<br>

<p>Acesse a pasta /var/log/sudo e verifique se existe o historico de comandos utilizados pelo grupo Sudo.</p>

> Acesse a pasta ```cat /var/log/sudo/sudo.log``` e confira o historica de comandos.

> Em seu terminal execute o comando ```apt update```.

> Na pasta ```cat /var/log/sudo/sudo.log``` confira se um novo diretório foi criado.

<br>
<br>

##### UFW

<p>Verifique se o UFW está corretamente instalado.</p>

> No terminal execute o comando ```dpkg -l | grep ufw```.

<br>

<p>Verifique se o UFW está funcionando corretamente.</p>

> No terminal execute o comando ```ufw status```.

<br>

<p>O que é o UFW?</p>

> O Uncomplicated Firewall é um firewall simplificado, que tem como objetivo filtrar o tráfego da internet ou de um acesso SSH.

<br>

<p>Adicione a porta 8080 ao UFW e verifique se ela esta ativa.</p>

> No terminal execute o comando ```ufw allow 8080``` e em seguida utilize o comando ```ufw status```.

<br>

<p>Delete a porta 8080.</p>

> O comando para deletar uma porta exige sua posição dentra da lista de regras. No exemplo abaixo, a regra 8080, a qual queremos deletar, se encontra na posição 2 e 4.
<ol>
	<ul>
		<li>1	4242</li>
		<li>2	8080</li>
		<li>3	4242(v6)</li>
		<li>4	8080(v6)</li>
	</ul>
</ol>

> Ao descobrir a posição da porta 8080 execute o comando ```ufw delete #```.

<br>
<br>

##### SSH

<p>Verifique se o SSH está corretamente instalado.</p>

> No terminal execute o comando ```dpkg -l | grep ssh```.

<br>

<p>Verifique se o SSH está funcionando corretamente.</p>

> No terminal execute o comando ```service ssh status```.

<br>

<p>O que é o SSH?</p>

> O SSH é uma ferramenta de segurança que permite a troca de dados entre um cliente e um servidor remoto. Graças a sua comunicação criptografada entre pares ele se torna o meio mais seguro e dinâmico de efetuar está atividade.

<br>

<p>Através de um outro dispositivo, utilize a porta 4242 e faça login com o novo usuário recém criado.</p>

> Dentro de sua VM localize seu endereço de ip através do comando ```ifconfig``` ou ```ifconfig | grep inet | sed 1q```.

> Através do CMD ou PowerShell de seu computador digite o comando ```ssh <username>@<ip-address> -p 4242``` e efetue o login.

<br>

<p>Por fim, através de um outro dispositivo, utilize a porta 4242 e tente efetuar login com o usuário root.</p>

> O acesso deve ser negado graças a regra criada em nossa arquivo sshd_config.

<br>
<br>

##### Monitoramento de Script

<p>Como o script funciona?</p>
<p>No terminal acesse sua pasta de script e explique seu código linha a linha...</p><br>

<details>

<br>

> uname -a | busca as informações sobre o sistema.

```
echo -ne "ARCHITECTURE: "; uname -a
```

<br>

> grep -c | imprime a contagem de linhas do arquivo.

```
echo -ne "CPU PHYSICAL: "; grep -c processor /proc/cpuinfo
```

<br>

> grep | busca pela palavra processor;<br>
wc -l | imprime a quantidade de linhas.

```
echo -ne "VIRTUAL CPU: "; cat /proc/cpuinfo | grep processor | wc -l
```

<br>

> free -m | busca as informações da memória ram;<br>
awk NR==2 | seleciona somente as colunas já processadas;<br>
printf | imprime na tela as informações passadas como parâmetro.

```
echo -ne "MEMORY USAGE: "; free -m | awk 'NR==2{printf "%s/%sMB (%.2f%%)\n", $3,$2,$3*100/$2}'
```

<br>

> df -h | busca as informações sobre o disco de memória;<br>
awk NF==/ | seleciona as colunas que estão sendo processadas;<br>
printf | imprime na tela as informações passadas como parâmetro.

```
echo -ne "DISK USAGE: "; df -h | awk '$NF=="/"{printf "%d/%dGB (%s)\n", $3,$2,$5}'
```

<br>

> top -bn1 | durante 'n' vezes envie um arquivo para outro;<br>
grep | busca pela palavra load;<br>
awk printf | manipula o texto e imprime somente os números.

```
echo -ne "CPU LOAD: "; top -bn1 | grep load | awk '{printf"%.2f%%\n", $(NF-2)}'
```

<br>

> who -b | horário do último boot do sistema;<br>
awk printf | imprime a coluna selecionada;<br>
tr | substitui um caractere por outro.

```
echo -ne "LAST BOOT: "; who -b | awk '{printf $3 }' | tr '\n' ' ' && who -b | awk '{printf " " $4}'
```

<br>

> if fi | demonstra uma condição específica;<br>
grep -q | verifica se existe algo no diretório.

```
echo -ne "\nLVM USE: "; if cat /etc/fstab | grep -q "/dev/mapper/"; then echo "yes"; else echo "no";fi
```

<br>

> wc -l | realiza a contagem de linhas;<br>
awk printf | imprime o texto selecionado;<br>
tr | substitui os caracteres.

```
echo -ne "CONNEXIONS TCP: "; cat /proc/net/tcp | wc -l | awk '{print $1-1}' | tr '\n' ' ' && echo "ESTABLISHED"
```

<br>

> w | qual usuário esta logado no mento;<br>
wc -l | realiza a contagem de linhas;<br>
awk print | imprime o texto selecionado.

```
echo -ne "USER LOG: "; w | wc -l | awk '{print $1-2}'
```

<br>

> echo -n | demonstra o argumento;<br>
grep | busca a palavra;<br>
awk print | imprime o texto selecionado;<br>
tr | substitui os caracteres.

```
echo -ne "NETWORK: "; echo -n "IP" && ip route list | grep default | awk '{print $3}' | tr '\n' ' ' && echo -n "9" && ip link show | grep link/ether | awk '{print $2}' | tr '\n' ')' && printf "\n"
```

<br>

> journalctl _COMM= | registra os comandos realizados por um grupo;<br>
grep | busca por uma palavra;<br>
wc -l | realiza a contagem de linhas;<br>
tr | substitui os caracteres.

```
echo -ne "SUDO COUNTER: "; journalctl _COMM=sudo | grep COMMAND | wc -l | tr '\n' ' ' && echo Comands
```

<br>

> printf | imprime uma quebra de linha.

```
printf "\n"
```
</details>
<br>

> Para rodar o código sem precisar esperar os 10min execute o comando ```bash monitoring.sh```

<br>

<p>Ativando e desativando o Cron</p>
<p>Uma das maneiras de desativar o cron é acessando suas configurações e comentando a linha de código referente a regra criada.</p>

```
$		crontab -e
23		#*/10 * * * * sh path/to/script
```
<p>A segunda maneira para desativar o cron é, no próprio terminal, escrever a seguinte linha de comando:</p>

```
$		etc/init.d/cron stop
```

<br>

<p>O que é o Cron?</p>

> O Cron é um programa que atua em segundo plano criando schedules, que atuam de acordo com as configurações criadas por você.

<br>

<p>Como o Contrab foi configurado?</p>

> O Crontab é configurado informando os minutos, horas, dias, meses e semana em que você desneha que o script configurado seja rodado.

> A configuração foi feita de forma a qual a cada 10 minutos de todas as horas, dias, meses e semanas o nosso script seja executado.

> Para conferir o crontab utilize o comando ```crontab -e```.

<br>
<br>

##### CRÉDITOS

<p>MCoscia<br>
Matheus Coscia / / designer gráfico</p>
<p><a href="https://github.com/gsilva-v">gsilva-v</a></p>
