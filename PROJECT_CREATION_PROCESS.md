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

> Crie uma senha para o root, lembrando de seguir a *política de senha*.<br>
Caso você não tenha criatividade utilize a senha 123Qwedsaz.

![alt text](https://user-images.githubusercontent.com/82785772/136550617-6859ea60-e521-4eaf-8e41-e7cfa2e63705.png)

> Crie um úsuario e em seguida confirme sua senha.

![alt text](https://user-images.githubusercontent.com/82785772/136550803-c4c55a4a-7c78-448b-a60d-b3dec7c5bd83.png)

![alt text](https://user-images.githubusercontent.com/82785772/136550862-d74698b3-52f0-498b-b5af-c20c5be80584.png)

> Configure o fuso horário de sua máquina.<br>
Caso você tenha selecionado o idioma inglês tente localizar um dos fusos mais próximos ao do Brasil.

![alt text](https://user-images.githubusercontent.com/82785772/136551018-fa4378d4-b2b7-4453-a38d-c4bbc2568c12.png)

> Inicie o *particionamento de memória*, selecionando o modo manual.

![alt text](https://user-images.githubusercontent.com/82785772/136551102-35e56aab-10bf-4676-9c51-130f72ca67b4.png)

> Selecione uma unidade de memória e confirme clicando em *sim*.

![alt text](https://user-images.githubusercontent.com/82785772/136551254-df0d978a-a8db-4858-951b-f74dacdb3862.png)

> Selecione o *espaço livre* e *crie uma nova partição*.

![alt text](https://user-images.githubusercontent.com/82785772/136551406-3f0b0b9c-263f-4c40-b222-14dc77b4eda6.png)

![alt text](https://user-images.githubusercontent.com/82785772/136551458-3f43c36d-f79a-4311-8b4c-0627175b098e.png)

> Defina a *quantidade de memória* que a primeira partição irá utilizar.<br>
Vale ressaltar que está será a *partição responsável pelo boot* da máquina, logo, 500MB serão suficientes para essa ação.

![alt text](https://user-images.githubusercontent.com/82785772/136551651-67fac43f-ed2b-4d67-bd04-1630c93c37c3.png)

> Selecione *Primária* como o tipo da instalação e a defina como *Inicial*.

![alt text](https://user-images.githubusercontent.com/82785772/136551689-bcb8600c-3f57-48f4-a9f0-ebf37c1effd6.png)

![alt text](https://user-images.githubusercontent.com/82785772/136551722-be4c467f-5461-4074-a0a7-935260a3f1bd.png)

> Nesta etapa será necessário definir dois parâmetros, não sendo necessário alterar os demais.<br>
Em *Usar Como*, defina *ext4 "journaling"*.<br>
Em *Ponto de Montagem*, defina */boot*.

![alt text](https://user-images.githubusercontent.com/82785772/136551841-2292350a-d963-43a7-a6eb-c936455c854f.png)

> Finalize a partição do boot.

![alt text](https://user-images.githubusercontent.com/82785772/136551976-bb7f4e8a-6b29-4b0e-9a1b-9647fba64c53.png)

### Configurando nosso Servidor


##### CRÉDITOS

<p>MCoscia<br>
Matheus Coscia / / designer gráfico</p>
