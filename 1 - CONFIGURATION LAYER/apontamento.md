# 1.1 Learning Objectives

After completing this chapter, you should be able to do the following:

1 - Describe the components of the Configuration Layer.

2 - Describe the functions of each component of the Configuration Layer.

3 - Explain the data flow of the Configuration Layer.

Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descreva os componentes da Camada de Configuração.

2 - Descreva as funções de cada componente da Camada de Configuração.

3 - Explique o fluxo de dados da Camada de Configuração.

## 1.2 Configuration Layer

The Configuration Layer processes and stores the contact center data required by Genesys Solutions to work in a particular environment. What is in the contact center environment? PBXs, host computers, server applications, and more. What are the available resources? Agents, and more. 
This layer provides:

A Camada de Configuração processa e armazena os dados do contact center exigidos pela Genesys Solutions para trabalhar em um ambiente específico. O que está no ambiente do contact center? PBXs, computadores host, aplicativos de servidor e muito mais. Quais são os recursos disponíveis? Agentes e muito mais. 
Esta camada fornece:

- Access control functions to regulates user access to solution functions and data based on the access privileges set for each item.
- An advanced configuration data distribution mechanism, so applications can read their configuration upon startup and be notified of updates at runtime without service interruptions.

- Funções de controle de acesso para regular o acesso do usuário às funções e dados da solução com base nos privilégios de acesso definidos para cada item.
- Um mecanismo avançado de distribuição de dados de configuração, para que os aplicativos possam ler sua configuração na inicialização e serem notificados sobre atualizações em tempo de execução sem interrupções de serviço.

![image](https://user-images.githubusercontent.com/52088444/158178378-ef569fa5-d617-4883-8525-67def08a3b96.png)

To summarize, the Configuration Layer provides two key functions to the Framework and the Genesys solutions: Configuration and Access Control.

Para resumir, a Camada de Configuração fornece duas funções principais para as soluções Framework e Genesys: Configuração e Controle de Acesso.

**Configuration**

The Configuration Layer centralizes the processing and storage of all the configuration data required for Genesys Solutions to work within a particular environment. Users can enter contact center data in one location and the Configuration Layer will send the changes to the rest of Genesys. This helps ensure consistency, reliability, and integrity of the data.

A camada de configuração centraliza o processamento e armazenamento de todos os dados de configuração necessários para que a Genesys Solutions funcione em um ambiente específico. Os usuários podem inserir os dados do contact center em um local e a camada de configuração enviará as alterações para o restante da Genesys. Isso ajuda a garantir consistência, confiabilidade e integridade dos dados.

**Access Control**

The Configuration Layer enables system administrators to set and verify user’s permissions for access to solution functions and data.

A Camada de Configuração permite que os administradores do sistema definam e verifiquem as permissões do usuário para acesso às funções e dados da solução.

**Dynamic Reconfiguration and Notification**

Changes made to the configuration during runtime are typically propagated throughout the Genesys system without the need to restart applications. In some rare well-documented cases, dynamic change propagation and notification does not occur and a restart of the application is required.

As alterações feitas na configuração durante o tempo de execução normalmente são propagadas por todo o sistema Genesys sem a necessidade de reiniciar os aplicativos. Em alguns casos raros e bem documentados, a propagação e a notificação de alterações dinâmicas não ocorrem e é necessário reiniciar o aplicativo.

##  1.3 Architecture Diagram Conventions(Convenções do Diagrama de Arquitetura)

In this course, we examine the architecture of the Genesys clients and servers by viewing architecture diagram conventions.

One convention is the Client Server model shown below. In a client-server relationship, an arrow points to the Genesys application that has the server role. Here the term server is not referring to a computer, but is referring to the relationship between applications—where one application acts as a client and another application acts as a server. The client initiates the connection to the server.

Neste curso, examinamos a arquitetura dos clientes e servidores Genesys exibindo as convenções do diagrama de arquitetura.

Uma convenção é o modelo Client Server mostrado abaixo. Em uma relação cliente-servidor, uma seta aponta para o aplicativo Genesys que possui a função de servidor. Aqui, o termo servidor não se refere a um computador, mas ao relacionamento entre aplicativos – onde um aplicativo atua como cliente e outro aplicativo atua como servidor. O cliente inicia a conexão com o servidor.

![image](https://user-images.githubusercontent.com/52088444/158184437-98bfcc75-329a-4a25-a837-9aa5a3781559.png)

Another convention is the use of specific shapes to signify the types of components in the architecture diagrams, shown in the following image:

Outra convenção é o uso de formas específicas para significar os tipos de componentes nos diagramas de arquitetura, mostrados na imagem a seguir:

![image](https://user-images.githubusercontent.com/52088444/158184795-2a809e92-3997-4c97-8ca3-262d68e8dfa6.png)


**Note:**DB Server was part of the Framework release 8.1 and earlier Services Layer. Although DBServer is not needed for Framework release 8.5, it is still provided for use with some products and solutions that still require it, such as Genesys Administrator (part of centralized logging access), ICON (part of Infomart reporting), and OCS (part of outbound).

**Nota:** O DB Server fazia parte da versão 8.1 do Framework e da camada de serviços anterior. Embora o DBServer não seja necessário para a versão 8.5 do Framework, ele ainda é fornecido para uso com alguns produtos e soluções que ainda o exigem, como Genesys Administrator (parte do acesso de log centralizado), ICON (parte do relatório do Infomart) e OCS (parte do de saída).

## 1.4 Framework Architecture: Configuration Layer

The following image outlines the five different layers of the Framework starting with the Configuration Layer. The Configuration Layer is made up of:

A imagem a seguir descreve as cinco camadas diferentes do Framework, começando com a camada de configuração. A camada de configuração é composta por:

- Configuration Database(Banco de dados de configuração)
- Configuration Server(Servidor de configuração)

![image](https://user-images.githubusercontent.com/52088444/158185294-f607d54d-4054-4963-9a3d-6f6b4d34a374.png)

## 1.5 Configuration Database

In any Genesys environment, there is only one database (or a database cluster, if configured on the DBMS level) that is intended for use by Configuration Layer – this is the Configuration Database. The Configuration Database is the central repository for all configuration data.

Em qualquer ambiente Genesys, há apenas um banco de dados (ou um cluster de banco de dados, se configurado no nível DBMS) destinado ao uso pela Camada de Configuração – este é o Banco de Dados de Configuração. O banco de dados de configuração é o repositório central para todos os dados de configuração.

![image](https://user-images.githubusercontent.com/52088444/158186966-1a5711d7-ad2f-4258-a001-0a6fc1d6fbed.png)

The Genesys Configuration Database can be supported in any of the following DBMS:

- IBM DB2
- MS SQL Server
- Oracle
- PostgreSQL (free open source database similar to MS SQL)

Consult with your Genesys Sales Engineer and Genesys Technical Support for specific versions and requirements. You can also find information about supported databases in the Genesys 8.x Supported Operating Systems and Databases Reference Manual.

Consulte seu engenheiro de vendas da Genesys e o suporte técnico da Genesys para obter versões e requisitos específicos. Você também pode encontrar informações sobre bancos de dados suportados no Genesys 8.x Supported Operating Systems and Databases Reference Manual.

## 1.6 Configuration Server

The functions of Configuration Server:

-  Centralized configuration data storage
- Data integrity control
- Access Control
- Runtime notifications

As funções do Servidor de Configuração:

- Armazenamento de dados de configuração centralizado
- Controle de integridade de dados
- Controle de acesso
- Notificações de tempo de execução


Configuration Server provides centralized access to the Configuration Database, based on permissions that administrators can grant to any user for any configuration object. 

Configuration Server also maintains the logical integrity of configuration data and notifies the applications about the changes made to the data.


O Configuration Server fornece acesso centralizado ao banco de dados de configuração, com base nas permissões que os administradores podem conceder a qualquer usuário para qualquer objeto de configuração.

O Configuration Server também mantém a integridade lógica dos dados de configuração e notifica os aplicativos sobre as alterações feitas nos dados.

![image](https://user-images.githubusercontent.com/52088444/158190275-33a9c476-0e9c-4e58-9f9f-7829a775a031.png)

The clients of Configuration Server, such as T-Server, will not start unless they successfully connect to the Configuration Server. This is because most applications cannot perform any essential functions without access to the configuration data. Clients do not have to remain connected to the Configuration Server to stay operational. They will continue working with the configuration data they have already read into their own memory. On a reconnect, they will receive new and/or changed configuration data that the Configuration Server maintains in a history log for this purpose.

Os clientes do Configuration Server, como o T-Server, não serão iniciados a menos que se conectem com sucesso ao Configuration Server. Isso ocorre porque a maioria dos aplicativos não pode executar nenhuma função essencial sem acesso aos dados de configuração. Os clientes não precisam permanecer conectados ao Servidor de Configuração para permanecerem operacionais. Eles continuarão trabalhando com os dados de configuração que já leram em sua própria memória. Em uma reconexão, eles receberão dados de configuração novos e/ou alterados que o Servidor de Configuração mantém em um log de histórico para essa finalidade.

## 1.7 Starting Configuration Layer

Your first step is starting the Configuration Server application. As outlined in the following image, (1) Configuration Server reads its configuration file—confserv.cfg which contains the information about how to access Configuration Database.

Sua primeira etapa é iniciar o aplicativo Configuration Server. Conforme descrito na imagem a seguir, (1) o Configuration Server lê seu arquivo de configuração—confserv.cfg que contém as informações sobre como acessar o banco de dados de configuração.

![image](https://user-images.githubusercontent.com/52088444/158191231-53649ef4-e0d8-413d-9f7c-409b782fea91.png)

Using the information from the confserv.cfg file, Configuration Server then locates and establishes a connection to Config DB, (2) requesting the configuration data. Config DB returns the configuration data to the Configuration Server. 

Usando as informações do arquivo confserv.cfg, o Configuration Server localiza e estabelece uma conexão com o Config DB, (2) solicitando os dados de configuração. O Config DB retorna os dados de configuração para o Configuration Server.

![image](https://user-images.githubusercontent.com/52088444/158192718-24ac660e-7eb2-4799-9fc6-ac6c6710a6ca.png)

When you launch the GUI application (based on the details supplied in its login dialog box), Genesys Administrator Extension (GAX) or Genesys Administrator (GA) locates and establishes a connection with Configuration Server. Then, GAX or GA requests and receives the configuration data from the Configuration Server.

This process of Configuration Server loading all the configuration data into its memory is called initialization.

Ao iniciar o aplicativo GUI (com base nos detalhes fornecidos em sua caixa de diálogo de login), o Genesys Administrator Extension (GAX) ou o Genesys Administrator (GA) localiza e estabelece uma conexão com o Configuration Server. Em seguida, o GAX ou GA solicita e recebe os dados de configuração do Configuration Server.

Esse processo de carregamento de todos os dados de configuração do Configuration Server em sua memória é chamado de inicialização.

![image](https://user-images.githubusercontent.com/52088444/158193433-4ce88bec-0108-43fb-b964-07656db8c996.png)

The Configuration Layer can be started manually or automatically in Windows using Services (UNIX/LINUX daemon processes), or manually from a command line, an application shortcut, or a script.

A Camada de Configuração pode ser iniciada manualmente ou automaticamente no Windows usando Serviços (processos de daemon UNIX/LINUX) ou manualmente a partir de uma linha de comando, um atalho de aplicativo ou um script.


## 1.8 Configuration Data: Read

At this point, the Configuration Server has already obtained the data from the database which is held in its memory.

Neste ponto, o Configuration Server já obteve os dados do banco de dados que estão em sua memória.

As seen in the image below:

Como pode ser visto na imagem abaixo:

When a (1) read request for information is sent to the Configuration Server from one of the Genesys applications, either a GUI (GAX or GA) or another Genesys server application, the Configuration Server responds with the requested (2) configuration data.

Quando uma (1) solicitação de leitura de informações é enviada ao Servidor de Configuração de um dos aplicativos Genesys, seja uma GUI (GAX ou GA) ou outro aplicativo de servidor Genesys, o Servidor de Configuração responde com os (2) dados de configuração solicitados.

![image](https://user-images.githubusercontent.com/52088444/158194159-3eee4ad2-cd49-49bd-8f86-16efede58b5b.png)

Notice that the Configuration Server does not need to re-read data from the database to answer these read requests since all the configuration data is held in memory.

Observe que o Configuration Server não precisa reler os dados do banco de dados para responder a essas solicitações de leitura, pois todos os dados de configuração são mantidos na memória.

## 1.9 Configuration Data: Write

![image](https://user-images.githubusercontent.com/52088444/158194582-b3e446a5-81cc-4a37-9545-6d1430ef0afa.png)

Every time a change is made, all client applications are supplied with dynamic updates relevant to the functions they perform, as seen in the image above:

1 -  Write—A request to update configuration data (a write process) is sent from a Genesys GUI application or server application.

2 - Write—Configuration Server sends a message to DBMS requesting updates be made to the Configuration Database.

3 - Configuration Data—The DBMS communicates the success of statements, along with a refresh of the configuration data.

4 - Dynamic Update—Configuration Server sends changes in the configuration to relevant clients.

Toda vez que uma mudança é feita, todos os aplicativos cliente são fornecidos com atualizações dinâmicas relevantes para as funções que executam, como pode ser visto na imagem acima:

1 - Gravação—Uma solicitação para atualizar os dados de configuração (um processo de gravação) é enviada de um aplicativo Genesys GUI ou aplicativo de servidor.

2 - Gravação—O Servidor de Configuração envia uma mensagem ao DBMS solicitando que atualizações sejam feitas no Banco de Dados de Configuração.

3 - Dados de configuração—O SGBD comunica o sucesso das instruções, juntamente com uma atualização dos dados de configuração.

4 - Atualização Dinâmica—O Servidor de Configuração envia alterações na configuração para clientes relevantes.
