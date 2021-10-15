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

<p>Após ter acesso ao vdi de sua VM é de extrema importância que você não realize mais nenhuma modificação em seu servidor, portante <b>certifique-se que o projeto está finalizado</b>.</p>

#### Parte Obrigatória

##### Visão Geral do Projeto

<p>Como funciona uma VM e qual sua finalidade?</p>

> A VM, através do hardware do seu computador, irá emular um sistema operacional em um ambiente controlado de teste, sem interferir nos dados de seu computador.

<p>Qual a diferença entre Debian e CentOs?

> O Debian, além de ser mais amigável com o úsuario, possui uma ampla distribuição, logo, seu suporte é mais facilitado.
Já o CentOs é voltada para o setor empresárial, possuindo mais estabilidade, porém com menos suporte e atualizações.

<p>Qual a diferença entre apt e aptitude?

> O apt já vem instalado por padrão no sistema Debian.
A principal diferença entre os dois gerenciadores é sua interface gráfica.

<p>O que é APPArmor?

> É responsável pela liberação de úsuarios/aplicativos para a realização de determinadas tarefas.

##### Configuração Simples

<p>Verifique se o UFW está ativado.</p>

> No terminal execute o comando ```ufw status```.

<p>Verifique se o SSH está ativado.</p>

> No terminal execute o comando ```service ssh status```.

<p>Verifique se o sistema operacional foi escolhido corretamenta.</p>

> No terminal execute o comando ```uname -a```.

##### Configuração Simples

<p>Verifique se o UFW está ativado.</p>

> No terminal execute o comando ```ufw status```.
