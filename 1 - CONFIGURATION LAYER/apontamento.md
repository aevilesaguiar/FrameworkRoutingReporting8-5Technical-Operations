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

