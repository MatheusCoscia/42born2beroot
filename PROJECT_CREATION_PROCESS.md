## Criação do Projeto

### Configurando a Máquina Virtual

<p>A configuração da VM é uma das partes mais simples do projeto e pode ser dividida em duas etapas, sendo elas a instalação de um sistema operacional dentro da VM e sua configuração.</p>

##### Escolhendo o Sistema Operacional

<p>Caso você não possua um software de virtualização em seu computador é recomendável a utilização do <a href="https://www.virtualbox.org">VirtualBox</a>. Lembre-se de ativar a opção de virtualização na BIOS de seu computador.</p>
<p>Após da instalação de seu software de virtualização, você deve escolher o sistema operacional com o qual irá criar seu servidor.</p>
<p>Caso você ainda não possua experiência com esse tipo de atividade é extremamente recomendável utilizar o sistema <a href="https://www.debian.org/download">Linux Debian</a>. Caso você já tenha experiência, sinta-se livre para aventurar-se no sistema <a href="https://www.centos.org/download">Linux CentOs</a>.</p>
<br>
<p>Agora é o momento de iniciar a criação de sua Máquina Virtual! Não tem mistério e nenhum segredo mirabolante e eu recomendo seguir <a href="https://www.treinaweb.com.br/blog/criando-uma-maquina-virtual-com-a-virtualbox">este tutorial</a>.</p><br>

##### Instalação e Configuração do Sistema Operacional

<p>A instalação e configuração do Debian é simples, mas pode dar um pouco de dor de cabeça caso seu software de virtualização esteja desatualizado ou você esqueça sua senha de criptografia.</p>
<br>
<p>Para começar a instalação do Debian devemos iniciar nossa Máquina Virtual e escolher o modo de <b>Instalação/Install</b>. Lembre-se de não escolher o modo de Instalação Gráfica, pois está não é permitida.</p>
<p>Agora você deve informar o idioma da sua máquina, tipo de teclado, localização...</p>
<p>Após a finalização das etapas acima o jogo começa de verdade! A partir daqui todas as configurações e adições devem seguir o que é pedido no PDF entregue pela 42.</p><br>

> Crie um *Hostname*, sendo ele seu Login + 42.

![alt text](https://user-images.githubusercontent.com/82785772/136550067-b2c83493-613f-4d94-8f63-417c9e67ea3d.png)

> Caso deseje, informe o nome de domínio.

![alt text](https://user-images.githubusercontent.com/82785772/136550144-c367b72a-5a64-443c-9886-7cf3ac7198af.png)

> Crie uma senha para o root, lembrando de seguir a política de senha.
Caso você não tenha criatividade utilize a senha 123Qwedsaz.

![alt text](https://user-images.githubusercontent.com/82785772/136550617-6859ea60-e521-4eaf-8e41-e7cfa2e63705.png)

> Crie um úsuario e em seguida confirme sua senha.

![alt text](https://user-images.githubusercontent.com/82785772/136550803-c4c55a4a-7c78-448b-a60d-b3dec7c5bd83.png)

![alt text](https://user-images.githubusercontent.com/82785772/136550862-d74698b3-52f0-498b-b5af-c20c5be80584.png)

> Configure o fuso horário de sua máquina.
Caso você tenha selecionado o idioma inglês tente localizar um dos fusos mais próximos ao do Brasil.

![alt text](https://user-images.githubusercontent.com/82785772/136551018-fa4378d4-b2b7-4453-a38d-c4bbc2568c12.png)

### Configurando nosso Servidor


##### CRÉDITOS

<p>MCoscia<br>
Matheus Coscia / / designer gráfico</p>
