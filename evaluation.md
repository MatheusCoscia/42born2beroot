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

<p>Verifique se o úsuario criado pelo avaliador com o nome <login42> está presente nos grupos "sudo" e "user42".</p>

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
