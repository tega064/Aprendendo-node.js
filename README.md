# Aprendendo-node.js
A tecnologia node.js vem conquistando o mercado por sua ampla ferramenta de construção de códigos, pensando nisso entendi que é extremamente útil o registro do entendimento e o aprendizado dessa tecnologia. Aqui eu iria mostrar meu processo evolucionário dessa linguagem e meu entendimento de como ela funciona.
Inicialmente é necessário entendermos como funciona o sistema de criação de servidor, para programar em web.
var  http =  require('http');
http.createServer(function(req,res){     
/*req é a função de requerir um arquivo, e o res é a resposta de uma ação(exemplo responder qual é o nome)*/
    res.end("Olá Mundo");
}).listen(8180);
Console.log ("o servidor está rodando!");
/*após criar o servidor,chame ele no terminal, e enseguida abra-o no localhost de seu navegador*/
Agora que aprendemos a criar um servidor em http usando o node, iremos usar o framework express para exemplificar a criação desse servidor.
Quando estamos utilizando o node é necessário entendermos sobre comandos para chamar bibliotecas, utilizamos o npm para instalação dessas bibliotecas dentro do projeto fonte e utilizamos as ferramentas de acordo com o seu desenvolvimento.
o código que digitamos no terminal para a instalação dessas bibliotecas é: npm install (nome do pacote, no momento vamos usar o express) --save
/* chamando o modulo express*/
var express = require ("express");
const app = express() /*recebe a função do express copiando todos os comandos que existe no express e se torna a variável principal do sistema. O comando const evita modificações na "variável"*/
app.get("/", function(req,res){ /* a barra ("/") é a rota principal do projeto*/
  res.send("Welcome to my website");
});
app.get("/sobre", function(req,res){
  res.send("Minha pagina sobre");
});
app.get("/blog", function(req,res){
  res.send("Bem vindo ao meu blog");
});
/* as rotas acima buscam a página e respondem de acordo com o caminho que foi criado, o exemplo sobre leva o usuário para a pagina sobre do projeto.*/
A criação de parametros é composta por (":") após a barra ("/") do http. Os parametros são importantes para receber requisições ("req")
Exemplo:
app.get("/blog:cargo/:nome", function(req,res){
  res.send("req.params");
});/* a função ("send") só pode ser enviada uma única vez, utilizando-se então uma chamada de arquivos com:("res.sendFile(diretório do arquivo);)
exemplo:
res.sendFile(_dirname+"/html/index.html) /*("O _dirname serve para preencher o caminho do arquivo até o local onde ele está.")*/
A interação com o html é importante para que seu projeto seja mais dinâmico e não tenha linhas de códigos "suja". Sendo assim o _dirname modo bruto de chamar arquivos.

O nodemon serve para atualizar o código sem precisar reiniciar o node no terminal.
Introdução ao MySql ("utilizando o sistema tela de comandos")
O comando ("mysql -h") serve para informar com qual servidor estamos querendo nos conectar
o comando ("-u root") para usuario
o comando ("-p") para a senha
Após ter iniciado a sessão no mysql podemos conferir quais os bancos de dados existem através do comando ("SHOW DATABASES");
Para criar um banco utilizamos o ("create database" + "o nome do banco;")
Para utilizar o banco ("Use" + 'O nome do banco;')

tipos de dados que utilizamos no mysql para criação de tabelas:
Texto,
char ("caractere")
int para números inteiros
float para decimais
date para datas
Blob para arquivos("não recomendado")

consulta de tabelas: ("SHOW TABLES;")
CRIANDO UMA TABELA: ("CREATE TABLE")
exemplo:
CREATE TABLE usuario(
nome varchar (25),
email varchar(50),
idade int
);
para ver a estrutura da tabela escreva no comando: ("DESCRIBE (nome da tabela)")
o select mostra dados da tabela;
o delete deleta dados da tabela;
o where especifica o que vc quer que seja alterado;
update junto com o set atualiza dados da tabela juno com o where;
exemplo:
select * from usuario where nome= "mateus" (procure na tabela usuario todos os campos onde o nome é mateus).

****sequelize***
abre o terminal em seu diretório e execute o comando: npm install --save sequelize
em seguida digite o comando npm install --save mysql2
**no editor de códigos digite**
const Sequelize = require('sequelize')
const sequelize = new Sequelize('test', 'root','',{  /*conectando ao banco*/
    host: "localhost", /* onde é o banco? No meu caso é no meu pc/local */
    dialect: 'mysql'    /* É necessário dizer qual banco pois sequelize utiliza vários*/
})

sequelize.authenticate().then(function(){//call back para dizer que está tudo certo com a conexão com o banco de dados
    console.log("Conectado com sucesso!")
}).catch(function(erro){//call back para dizer que houve erro em se conectar ao banco de dados.
    console.log("Falha ao se conectar:" + erro)
})
