## 4.1 Learning Objectives

After completing this chapter, you should be able to do the following: 

1 - Explain different types of database connectivity.

2- Describe Database Access Points (DAPs).

3 - Describe Genesys Database Server (DBServer).



Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1 - Explique os diferentes tipos de conectividade de banco de dados.

2- Descrever os Pontos de Acesso do Banco de Dados (DAPs).

3 - Descrever o Genesys Database Server (DBServer).


## 4.2 DAPs

The DAP provides an interface between applications in the Genesys installation and databases to which the applications require access.

The Configuration Layer uses the concept of DAPs to tell clients how to access a database.

The DAP describes a connection to one database. It is represented in the Configuration Layer as an Application object, though it does not have its own executable file and it is never started or run. The reason it is represented as an Application object is to provide specific database connection parameters for each client.

O DAP fornece uma interface entre os aplicativos na instalação do Genesys e os bancos de dados aos quais os aplicativos precisam de acesso.

A Camada de Configuração usa o conceito de DAPs para informar aos clientes como acessar um banco de dados.

O DAP descreve uma conexão com um banco de dados. Ele é representado na Camada de Configuração como um objeto Aplicativo, embora não tenha seu próprio arquivo executável e nunca seja iniciado ou executado. A razão pela qual ele é representado como um objeto Aplicativo é fornecer parâmetros de conexão de banco de dados específicos para cada cliente.

Example:

A routing application needs customer information from a database in order to route a call. To enable this connection, connect the client to a DAP that identifies the DBMS it should connect with, the specific database within the DBMS, and additional connection parameters. The routing application (the client in this client/server relationship) will request a connection to the Database using the parameters configured in the DAP you specify.

Exemplo:

Um aplicativo de roteamento precisa de informações do cliente de um banco de dados para rotear uma chamada. Para habilitar essa conexão, conecte o cliente a um DAP que identifique o DBMS com o qual ele deve se conectar, o banco de dados específico dentro do DBMS e parâmetros de conexão adicionais. A aplicação de roteamento (o cliente nesta relação cliente/servidor) solicitará uma conexão com o Banco de Dados utilizando os parâmetros configurados no DAP que você especificar.

![image](https://user-images.githubusercontent.com/52088444/158633113-026cbe47-1cd4-4d74-bfa1-a2294efd090a.png)


## 4.3 DBServer and Multiple DAPs

A DBServer in simple terms represents a DB Translator. Currently, the application supports the following types of Databases:

Um DBServer em termos simples representa um DB Translator. Atualmente, o aplicativo suporta os seguintes tipos de Bancos de Dados:

- Oracle
- PostgreSQL
- IBM DB2
- Microsoft SQL Server

Note: The DBServer was part of the Framework release 8.1 and earlier Services Layer. Although DBServer is not needed for Framework release 8.5, it is still provided for use with products and solutions which require it.

Nota: O DBServer fazia parte do Framework versão 8.1 e anterior da Camada de Serviços. Embora o DBServer não seja necessário para a versão 8.5 do Framework, ele ainda é fornecido para uso com produtos e soluções que o requerem.

One DBServer can be used in conjunction with multiple database access points and can support connections to multiple databases.

Examples:
- Client 1 uses DAP A and DBServer to access Database A
- Client 1 uses DAP B and DBServer to access Database B
- Client 2 uses DAP B and DBServer to access Database B

DB Server operates using multiple processes. The main process is a dispatcher process. It communicates with the client applications and launches (spawns) child processes as required. Each child process is responsible for a connection between a single client application and a single database. There will be separate child processes for each connection, whether to the same database or different database. 

All the child processes operate concurrently, which means they can distribute the overall load and achieve greater performance than if all the work were handled by a single process.

The architecture shown below enables multiple clients to use one DBServer to access multiple databases.

Um DBServer pode ser usado em conjunto com vários pontos de acesso de banco de dados e pode suportar conexões com vários bancos de dados.

Exemplos:
- Cliente 1 usa DAP A e DBServer para acessar o Banco de Dados A
- Cliente 1 usa DAP B e DBServer para acessar o Banco de Dados B
- Cliente 2 usa DAP B e DBServer para acessar o Banco de Dados B

O DB Server opera usando vários processos. O processo principal é um processo despachante. Ele se comunica com os aplicativos cliente e inicia (gera) processos filho conforme necessário. Cada processo filho é responsável por uma conexão entre um único aplicativo cliente e um único banco de dados. Haverá processos filho separados para cada conexão, seja para o mesmo banco de dados ou banco de dados diferente.

Todos os processos filhos operam simultaneamente, o que significa que eles podem distribuir a carga geral e obter maior desempenho do que se todo o trabalho fosse tratado por um único processo.

A arquitetura mostrada abaixo permite que vários clientes usem um DBServer para acessar vários bancos de dados.

![image](https://user-images.githubusercontent.com/52088444/158635465-93d98fec-e4d7-4742-bddc-5f5fe7664961.png)

## 4.4 Two Types of DAPs

There are two types of database connectivity. Framework release 8.5 uses DAP (seen in the following image) which has the accessing client using Java Database Connectivity (JDBC) to connect with the database. The client can communicate with the database without any additional applications.

Existem dois tipos de conectividade de banco de dados. A versão 8.5 do Framework usa DAP (visto na imagem a seguir) que tem o cliente acessando usando Java Database Connectivity (JDBC) para se conectar ao banco de dados. O cliente pode se comunicar com o banco de dados sem nenhum aplicativo adicional.

![image](https://user-images.githubusercontent.com/52088444/158635778-3e013651-9487-4b04-ad5a-5ff767b652e8.png)

Before Framework release 8.5, a DAP that required an additional component, Genesys Database Server or DBServer (seen in the following image) was used. The Genesys Database Server is an additional application that needs to be installed, configured, and running. It translates information between the Genesys messaging and the database management system. Several applications and solutions still require this DAP_DBServer, which contains all of the information needed to access their database, including which database server to use, database username, password, etc. For this reason, DBServer is still included in Framework release 8.5.

Antes da versão 8.5 do Framework, era usado um DAP que exigia um componente adicional, Genesys Database Server ou DBServer (visto na imagem a seguir). O Genesys Database Server é um aplicativo adicional que precisa ser instalado, configurado e executado. Ele traduz informações entre o sistema de mensagens Genesys e o sistema de gerenciamento de banco de dados. Várias aplicações e soluções ainda requerem este DAP_DBServer, que contém todas as informações necessárias para acessar seu banco de dados, incluindo qual servidor de banco de dados usar, nome de usuário do banco de dados, senha, etc. Por esse motivo, o DBServer ainda está incluído no Framework versão 8.5.

![image](https://user-images.githubusercontent.com/52088444/158636036-6a635587-835e-4790-9efa-0bb17cd836de.png)

**Shortened Representation Diagrams(Diagramas de representação reduzidos**

In this class, two types of DAPs have been set up with a shortened representation for clarity and space in the architecture diagrams. 

This classroom environment has one DBServer configured and installed, but it is used by many DAPs requiring a DBServer. These are represented by the client connecting to the DAP_DBS which accesses the database, seen below. An octagonal shape represents the DBServer in the following image.


Nesta classe, dois tipos de DAPs foram configurados com uma representação reduzida para maior clareza e espaço nos diagramas de arquitetura.

Este ambiente de sala de aula tem um DBServer configurado e instalado, mas é usado por muitos DAPs que requerem um DBServer. Estes são representados pelo cliente conectando-se ao DAP_DBS que acessa o banco de dados, visto abaixo. Uma forma octogonal representa o DBServer na imagem a seguir.

![image](https://user-images.githubusercontent.com/52088444/158636371-42becf59-70be-4091-85ba-ed5b883695a6.png)

**Database Connections Using Genesys DBServer(Conexões de banco de dados usando Genesys DBServer)**

Framework 8.1 and earlier versions connect to DBServer by the traditional approach where an additional component is required to run and establish the connection between client and database. The image below shows the default connection between client and database through DBServer in GAX.

To configure the database connections using Genesys DBServer, go to: GAX > Configuration Manager > Environment > Applications, and select DAP_log_DBS. As shown in the below image, we have to provide DBServer credentials.

O Framework 8.1 e versões anteriores se conectam ao DBServer pela abordagem tradicional, onde um componente adicional é necessário para executar e estabelecer a conexão entre o cliente e o banco de dados. A imagem abaixo mostra a conexão padrão entre cliente e banco de dados através do DBServer no GAX.

Para configurar as conexões de banco de dados usando o Genesys DBServer, vá para: GAX > Configuration Manager > Environment > Applications e selecione DAP_log_DBS. Conforme mostrado na imagem abaixo, temos que fornecer as credenciais do DBServer.

![image](https://user-images.githubusercontent.com/52088444/158636751-378462e9-5c47-4f53-be2d-6699b81001b7.png)

**Database Connections Using JDBC**

There are many DAPs that use JDBC and do not reference nor need a DBServer. They are represented by the client connecting to the DAP_JDBC which accesses the database.

Existem muitos DAPs que usam JDBC e não fazem referência nem precisam de um DBServer. Eles são representados pelo cliente conectando-se ao DAP_JDBC que acessa o banco de dados.

![image](https://user-images.githubusercontent.com/52088444/158636971-7634ff6c-303e-4fd2-a831-b03351ab9317.png)

In 8.5 Framework, Client Applications can connect to the Database by using a JDBC connection. You can establish a JDBC Connection by using the path: GAX > Configuration Manager > Environment > Applications and selecting the DAP_log_JDBC object. Here you can find the required fields to create the JDBC connection without using the DBServer component. The image below shows the information required to configure the JDBC connection.

No Framework 8.5, os Aplicativos Clientes podem se conectar ao Banco de Dados usando uma conexão JDBC. Você pode estabelecer uma conexão JDBC usando o caminho: GAX > Configuration Manager > Ambiente > Aplicativos e selecionando o objeto DAP_log_JDBC. Aqui você encontra os campos necessários para criar a conexão JDBC sem usar o componente DBServer. A imagem abaixo mostra as informações necessárias para configurar a conexão JDBC.

![image](https://user-images.githubusercontent.com/52088444/158637260-41c0ec82-cc66-465d-b510-77b19974f040.png)


4.5 Learning Summary

Now that you have completed this chapter, you should be able to do the following: 

1- Explain different types of database connectivity.

2- Describe Database Access Points (DAPs).

3- Describe Genesys Database Server (DBServer).

4.5 Resumo de Aprendizagem

Agora que você concluiu este capítulo, você deve ser capaz de fazer o seguinte:

1- Explique os diferentes tipos de conectividade de banco de dados.

2- Descrever os Pontos de Acesso do Banco de Dados (DAPs).

3- Descrever o Genesys Database Server (DBServer).

## 4.6 Learning Check

Question
01/03
There must be one DBServer per Database Access Point.

True

False(One DB Server can be used in conjunction with multiple database access points and can support connections to multiple databases.)Um servidor de banco de dados pode ser usado em conjunto com vários pontos de acesso de banco de dados e pode suportar conexões com vários bancos de dados.

Question
02/03
Database Access Points include information about the database such as its name.

True(verdadeiro)

False

Question
03/03
Applications might use JDBC or a DBServer to connect to a database.

True(verdadeiro)

False


