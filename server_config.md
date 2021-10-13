## Configurando o Servidor

<p>Durante o processo de configuração do servidor é recomendável estar logado como <b>root</b> para ter acesso total a todas as ferramentas de edição necessárias para a criação do projeto.</p>
<p>Todas as etapas aqui apresentadas seguem estritamente o PDF fornecido pela 42 para a criação do born2beroot.</p><br>

#### Configurações Básicas

##### Sistema Operacionaç

<p>Consulte o sistema operacional instalado em sua VM.</p>

```
	# consultar as somente as linhas que informam o sistema
$	head -n 2 /etc/os-release
	# consultar o arquivo em sua totalidade
$	cat /etc/os-release
```

##### Repartição de Memória

<p>Confira se o particionamento de memória esta correto através do comando lsblk.</p>

```
$	lsblk
```

<p>Caso ocorra alguma divergência entre sua repartição de memória e a informada pelo PDF do projeto será necessário recomeçar o processo de criação da VM.</p>
