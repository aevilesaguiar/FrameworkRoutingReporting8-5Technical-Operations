## Course Objectives


## 6.1 Learning Objectives

After completing this chapter, you should be able to do the following:

1 - Describe the components of the User Interaction Layer.

2 - Describe the functions of each component.

3 - Explain monitoring in Genesys Administrator Extension.

## 6.1 Objetivos de Aprendizagem

Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descrever os componentes da Camada de Interação do Usuário.

2 - Descreva as funções de cada componente.

3 - Explicar o monitoramento no Genesys Administrator Extension.

## 6.2 User Interaction Layer

The User Interaction Layer provides centralized web-based functionality and interfaces for the following:

- Configuring, monitoring, and control of applications, and solutions.

This layer provides a comprehensive user interface to configure, monitor, and control the management environment.

O Interaction Layer(camada de interação) do usuário fornece funcionalidades e interfaces centralizadas baseadas na web para o seguinte:

- Configuração, monitoramento e controle de aplicativos e soluções.(MONITORA OBJETOS , APLICAÇÕES, SOLUÇÕES E HOSTS e ver o estado dos alarmes)

Essa camada fornece uma interface de usuário abrangente para configurar, monitorar e controlar o ambiente de gerenciamento.

![image](https://user-images.githubusercontent.com/52088444/158852287-1ca8e0c9-4791-4e14-a1fc-346658fd3e34.png)

The User Interaction Layer consists of two components, GA and GAX. Both are deployed on a web server and accessed using a web browser.

O User Interaction Layer (camada de interação do usuário) consiste em dois componentes, GA e GAX. Ambos são implantados em um servidor da Web e acessados usando um navegador da Web.

## 6.3 Framework Architecture: User Interaction Layer

The following image outlines the five different layers of the Framework—the User Interaction Layer is shown in detail along with its connections to the Management and Configuration Layers. The User Interaction Layer is made up of the following elements:

-  Web browser
-  Genesys Administrator
- DAP to Log Database (DAP_DBS)
- Genesys Administrator Extension
- DAP to GAX Database (DAP_JDBC) and log DB
- GAX Database

A imagem a seguir descreve as cinco camadas diferentes da estrutura — a camada de interação do usuário é mostrada em detalhes junto com suas conexões com as camadas de gerenciamento e configuração. A camada de interação do usuário é composta pelos seguintes elementos:

- Navegador de Internet
- Administrador Genesys
- DAP para banco de dados de log (DAP_DBS)
- Extensão Administrador Genesys
- DAP para banco de dados GAX (DAP_JDBC) e banco de dados de log
- Banco de dados GAX

![image](https://user-images.githubusercontent.com/52088444/158854350-29856660-001d-4e59-9b58-b4ea0664f93e.png)

**Web Browser**

GA and GAX are both accessed using a web browser. You need to open a web browser, such as Firefox, type in the URL (web address), and access to the login for the corresponding interface (either GA or GAX). Genesys Administrator and GAX have different URLs.

Navegador da Web

GA e GAX são acessados usando um navegador da web. Você precisa abrir um navegador da web, como o Firefox, digitar a URL (endereço da web) e acessar o login da interface correspondente (GA ou GAX). Genesys Administrator e GAX têm URLs diferentes.

![image](https://user-images.githubusercontent.com/52088444/158854618-3c9a3b5e-5791-4f8e-a659-5261f32d9c09.png)

**Genesys Administrator and Genesys Administrator Extension**

GA and GAX are both connected to Configuration Server which gives access to Configuration Layer information. Both interfaces authenticate logins, read and make changes to configuration objects. Both GA and GAX also have connections to Solution Control Server. This gives the interfaces the ability to see status information about applications, start and stop applications, see if any alarms have been triggered, and clear triggered alarms.

Even though the interfaces may look different, much of the functionality in Genesys Administrator and Genesys Administrator Extension is the same. That being said, there are some differences of which you should be aware as shown below:

GA e GAX estão ambos conectados ao Servidor de Configuração, que dá acesso às informações da Camada de Configuração. Ambas as interfaces autenticam logins, leem e fazem alterações nos objetos de configuração. Tanto o GA quanto o GAX também possuem conexões com o Solution Control Server. Isso dá às interfaces a capacidade de ver informações de status sobre aplicativos, iniciar e parar aplicativos, ver se algum alarme foi acionado e limpar alarmes acionados.

Embora as interfaces possam parecer diferentes, grande parte da funcionalidade do Genesys Administrator e do Genesys Administrator Extension é a mesma. Dito isto, existem algumas diferenças das quais você deve estar ciente, conforme mostrado abaixo:

![image](https://user-images.githubusercontent.com/52088444/158855104-bfda8e26-38f2-4dba-ab50-a1a97f8b82ca.png)

**DAP to Log Database(DAP para registrar o banco de dados)**

Genesys Administrator and GAX has the ability to view application logs thanks to their connection to the Log Database. Genesys Administrator uses a Database Access Point with DBServer connectivity (DAP_DBS), while GAX uses a Database Access Point with JDBC connectivity (DAP_JDBC) to communicate with the DBMS. These DAPs describe the parameters for connecting to the Log Database, such as Database Name, Username and Password, etc.

Genesys Administrator e GAX têm a capacidade de visualizar logs de aplicativos graças à sua conexão com o banco de dados de logs. O Genesys Administrator usa um Database Access Point com conectividade DBServer (DAP_DBS), enquanto o GAX usa um Database Access Point com conectividade JDBC (DAP_JDBC) para se comunicar com o DBMS. Esses DAPs descrevem os parâmetros para se conectar ao banco de dados de log, como nome do banco de dados, nome de usuário e senha, etc.


**Genesys Administrator Extension**

Genesys Administrator Extension also has a functionality that you will not find in Genesys Administrator:

- The ability to work with Operational Parameters. Operational Parameters will be covered in more detail in the Routing lesson. Operational Parameters allows you to set values in the GAX interface which impacts the behavior of routing logic.

Extensão do Administrador Genesys

O Genesys Administrator Extension também possui uma funcionalidade que você não encontrará no Genesys Administrator:
- A capacidade de trabalhar com Parâmetros Operacionais. Os Parâmetros Operacionais serão abordados com mais detalhes na lição Roteamento. Parâmetros operacionais permite definir valores na interface GAX que afetam o comportamento da lógica de roteamento.

![image](https://user-images.githubusercontent.com/52088444/158857596-89570b13-24ec-4fce-b0d9-6d671a1fdad4.png)


**DAP to GAX Database(Banco de dados DAP para GAX)**

GAX have its own database for storing information. Associated with this database is a Database Access Point (DAP_JDBC). It does not rely on a DBServer for its connection. Instead it uses JDBC to provide the parameters for connecting the database.


A GAX possui um banco de dados próprio para armazenamento de informações. Associado a este banco de dados está um Database Access Point (DAP_JDBC). Ele não depende de um DBServer para sua conexão. Em vez disso, ele usa JDBC para fornecer os parâmetros para conectar o banco de dados.

**GAX Database(Banco de dados GAX)**

The GAX database stores information for GAX such as Audio Resource Management (including the audio resource files and personalities), Operational Parameter Management, and Bulk Change Sets.

O banco de dados GAX armazena informações para GAX, como gerenciamento de recursos de áudio (incluindo os arquivos de recursos de áudio e personalidades), gerenciamento de parâmetros operacionais e conjuntos de alterações em massa.

![image](https://user-images.githubusercontent.com/52088444/158858164-b43f6a6a-c52f-4f9c-867c-a01db367172a.png)


## 6.4 Monitoring

The following diagram demonstrates how the connection to SCS—a component of Management Layer—gives both Genesys Administrator and Genesys Administrator Extension the ability to monitor the Genesys environment.

O diagrama a seguir demonstra como a conexão com o SCS — um componente da camada de gerenciamento — oferece ao Genesys Administrator e ao Genesys Administrator Extension a capacidade de monitorar o ambiente Genesys.

![image](https://user-images.githubusercontent.com/52088444/158859381-7dfa0bec-8fb9-49ce-b2a2-ed3ba532f4f1.png)

SCS gathers data from one or more LCAs. 

Every host in the Genesys environment has an LCA that is responsible for the applications on that host. The LCA reports its status back to SCS, which makes the information available for viewing using GA or GAX.

The following monitoring functions can be performed using GA or GAX:

- Control and view the status for Applications. If applications have been grouped into Solutions, the status of solutions can also be viewed.
- View and clear any alarms that have been triggered.
- View the status of the host, along with information about the host.

O SCS reúne dados de um ou mais LCAs.

Cada host no ambiente Genesys tem um LCA que é responsável pelos aplicativos nesse host. O LCA informa seu status de volta ao SCS, que disponibiliza as informações para visualização usando GA ou GAX.

As seguintes funções de monitoramento podem ser executadas usando GA ou GAX:

- Controle e visualize o status dos Aplicativos. Se os aplicativos tiverem sido agrupados em Soluções, o status das soluções também poderá ser visualizado.
- Visualize e limpe todos os alarmes que foram acionados.
- Visualize o status do host, juntamente com informações sobre o host.

## 6.5 System Dashboard(Painel de Sistema)



The System Dashboard helps you to monitor your contact center. It shows a high-level summary of the current operations of your environment, which includes:
 
- Applications—A summary of the applications in your environment, and their status.
- Solutions—A summary of the solutions in your environment, and their status.
- Alarms—A summary of active alarms.
- Hosts—A summary of the hosts in your environment, and their status.

To view the detail and work with the different tabs in your environment, click the three dots (…) at the top of each widget. This opens a corresponding tab for each widget.


The System Dashboard helps you to monitor your contact center. It shows a high-level summary of the current operations of your environment, which includes:
 
- Applications—A summary of the applications in your environment, and their status.
- Solutions—A summary of the solutions in your environment, and their status.
- Alarms—A summary of active alarms.
- Hosts—A summary of the hosts in your environment, and their status.

To view the detail and work with the different tabs in your environment, click the three dots (…) at the top of each widget. This opens a corresponding tab for each widget.

![image](https://user-images.githubusercontent.com/52088444/158860569-2ee6d1ac-c917-42c2-8f83-c3e220784804.png)

![image](https://user-images.githubusercontent.com/52088444/158860686-62cd9dd8-8bb6-449e-b4bd-00d1f7cd5cc9.png)

**Applications Tab(Guia de aplicativos)**

The Applications tab shown below contains details about the applications on the host. Here you can see the name, current status, type, version, mode, host, and if the application is part of a solution.

Applications with a status of Unknown are shown at the top of the list. This widget updates automatically when the status of an application changes. 

You can start and stop individual applications, or you can select multiple applications using checkboxes and choose to start or stop them from the More menu.

A guia Aplicativos mostrada abaixo contém detalhes sobre os aplicativos no host. Aqui você pode ver o nome, status atual, tipo, versão, modo, host e se o aplicativo faz parte de uma solução.

Os aplicativos com status Desconhecido são exibidos no topo da lista. Este widget é atualizado automaticamente quando o status de um aplicativo é alterado.

Você pode iniciar e interromper aplicativos individuais ou selecionar vários aplicativos usando caixas de seleção e optar por iniciá-los ou interrompê-los no menu Mais.

![image](https://user-images.githubusercontent.com/52088444/158860951-3cb56b1a-0db1-455e-83af-74964ab9739f.png)

![image](https://user-images.githubusercontent.com/52088444/158861034-2b38f3db-a4da-484f-8910-10efc9da18a9.png)

**Solutions Tab(Guia Soluções)**

Similar to the Applications tab, the Solutions tab displays the solution name, status, type, version, and all associated applications. Here, individual solutions can be stopped and started, or checkboxes can be used to stop and start multiple solutions from the More menu.

NOTA:Complete Solution startup can take some time. The amount of time varies depending on the number and location of Solution components and the time required to initialize each component.

Semelhante à guia Aplicativos, a guia Soluções exibe o nome da solução, status, tipo, versão e todos os aplicativos associados. Aqui, soluções individuais podem ser interrompidas e iniciadas, ou caixas de seleção podem ser usadas para interromper e iniciar várias soluções no menu Mais.

NOTA:A inicialização completa da solução pode levar algum tempo. A quantidade de tempo varia dependendo do número e localização dos componentes da solução e do tempo necessário para inicializar cada componente.

![image](https://user-images.githubusercontent.com/52088444/158861788-4f7e1170-ea40-480f-8292-804da96ea605.png)

![image](https://user-images.githubusercontent.com/52088444/158861924-27d2dc4d-224d-49e3-8615-ae99c56e6255.png)

Possible Solution Statuses are as follows:

Stopped: Indicates that one or more of the Solution’s mandatory components (as opposed to those configured as optional) do not have Started status and, therefore, the Solution cannot perform its function. Stopped status can indicate that a Solution either has not been activated or has failed because one of its mandatory components is unavailable.

Started: Indicates that a Solution is ready to perform its major function. That is, all mandatory Solution components have reported Started status.  This status does not necessarily mean that the Solution is actually performing its function. To start working, some Solutions might require additional solution-specific control operations through their user interfaces. See the solution-specific documentation.

Unknown: Indicates that the Management Layer cannot provide reliable information about the Solution status. This does not necessarily mean that the Solution is unable to perform its function.

Alarms Tab: The Alarms tab displays any current alarms, the application that triggered the alarm, a message about it, and how long ago it was triggered. The list of active Critical, Major, and Minor alarms in the system are sorted by priority. The widget updates automatically when a new alarm is activated.

Each Alarm in the list displays one of the following statuses:
- Critical
-  Major
- Minor
- Unknown

In some circumstances, you may have already dealt with the issue that triggered the alarm, but the alarm is still displayed. In this case, you will want to clear the alarm from the list. To do so, you need to select the checkbox next to the alarm you wish to clear, and choose Clear from the More menu. This removes it from the list of currently active alarms.

Os possíveis status de solução são os seguintes:

Parado: Indica que um ou mais componentes obrigatórios da Solução (ao contrário dos configurados como opcionais) não estão com o status Iniciado e, portanto, a Solução não pode desempenhar sua função. O status Parado pode indicar que uma Solução não foi ativada ou falhou porque um de seus componentes obrigatórios não está disponível.

Iniciado: Indica que uma Solução está pronta para desempenhar sua função principal. Ou seja, todos os componentes obrigatórios da solução relataram o status Iniciado. Esse status não significa necessariamente que a Solução esteja realmente desempenhando sua função. Para começar a trabalhar, algumas soluções podem exigir operações de controle específicas da solução adicionais por meio de suas interfaces de usuário. Consulte a documentação específica da solução.

Desconhecido: indica que a camada de gerenciamento não pode fornecer informações confiáveis ​​sobre o status da solução. Isso não significa necessariamente que a Solução não possa desempenhar sua função.

Guia Alarmes: A guia Alarmes exibe todos os alarmes atuais, o aplicativo que acionou o alarme, uma mensagem sobre ele e há quanto tempo foi acionado. A lista de alarmes Críticos, Principais e Secundários ativos no sistema é classificada por prioridade. O widget é atualizado automaticamente quando um novo alarme é ativado.

Cada alarme na lista exibe um dos seguintes status:
- Crítico
- Principal
- Menor
- Desconhecido

Em algumas circunstâncias, você pode já ter lidado com o problema que acionou o alarme, mas o alarme ainda é exibido. Neste caso, você desejará limpar o alarme da lista. Para fazer isso, você precisa marcar a caixa de seleção ao lado do alarme que deseja limpar e escolher Limpar no menu Mais. Isso o remove da lista de alarmes ativos no momento.

![image](https://user-images.githubusercontent.com/52088444/158862525-71b5806e-279b-409c-b7d6-dc3608d08d9b.png)

![image](https://user-images.githubusercontent.com/52088444/158862646-bbf6c574-daa3-4d8d-afc1-f69acd159ff9.png)

**Hosts Tab(Guia de host)**

The Hosts tab typically displays multiple hosts. In this classroom environment, we only have one host displayed, Roswell. In your work environment, you will probably see more than one host, in which case each host will be listed with its individual name, status, IP Address, LCA Port, OS, and list of applications on the Host. There is a (...) next to the Applications on Host column. Clicking this (...) expands the row to show the entire list of applications associated with this host. On the far right, there is an icon (View Details) which gives you additional details about the host.

A guia Hosts normalmente exibe vários hosts. Neste ambiente de sala de aula, temos apenas um apresentador exibido, Roswell. Em seu ambiente de trabalho, você provavelmente verá mais de um host, caso em que cada host será listado com seu nome individual, status, endereço IP, porta LCA, sistema operacional e lista de aplicativos no host. Há um (...) ao lado da coluna Aplicativos no Host. Clicar neste (...) expande a linha para mostrar toda a lista de aplicativos associados a este host. Na extrema direita, há um ícone (Exibir detalhes) que fornece detalhes adicionais sobre o host.

![image](https://user-images.githubusercontent.com/52088444/158863155-2a93bdb6-55cc-4f2b-a7d0-31fc73307653.png)

![image](https://user-images.githubusercontent.com/52088444/158863233-63d7e360-9c36-42ce-860e-55acfff8b166.png)

Clicking the View Details icon opens an additional dialogue box which has options located at the top right. These options display the following additional host information:

Host(Hospedeiro)

The Host option gives you details about the CPUs and Virtual Memory usage.

Clicar no ícone Exibir detalhes abre uma caixa de diálogo adicional com opções localizadas no canto superior direito. Essas opções exibem as seguintes informações adicionais do host:



A opção Host fornece detalhes sobre o uso de CPUs e memória virtual.

![image](https://user-images.githubusercontent.com/52088444/158863396-fc51fcfe-88dd-400a-a508-d094972fa76a.png)

**Processes**

The Processes option gives you details about the processes that are running on the host. If you feel that the host is performing poorly and you wish to check the system performance, this screen can be used to check which of the processes are using too much memory.

A opção Processos fornece detalhes sobre os processos que estão sendo executados no host. Se você sentir que o host está com um desempenho ruim e deseja verificar o desempenho do sistema, esta tela pode ser usada para verificar quais dos processos estão usando muita memória.

![image](https://user-images.githubusercontent.com/52088444/158864673-b5b7eb47-b765-4dbc-a91c-9229d19071b2.png)


**Services**

The Services option gives you details about the services running on the host. You have the ability to view the services not only on the current host, but on any host listed, if you are in a multi-host environment.

A opção Serviços fornece detalhes sobre os serviços executados no host. Você tem a capacidade de visualizar os serviços não apenas no host atual, mas em qualquer host listado, se estiver em um ambiente de vários hosts.

![image](https://user-images.githubusercontent.com/52088444/158864496-7aae1d30-e255-4946-aad7-a5a8302f2274.png)

**Charts(Gráficos)**

The Charts option is blank when you first select this option. It populates in real time with a timeline in seconds. As you wait, the chart generates data with the information on the CPU and memory usage of the host.

A opção Gráficos fica em branco quando você seleciona essa opção pela primeira vez. Ele é preenchido em tempo real com uma linha do tempo em segundos. Enquanto você espera, o gráfico gera dados com as informações sobre o uso de CPU e memória do host.

![image](https://user-images.githubusercontent.com/52088444/158864752-dfd52d07-a825-4b4a-a5dd-f2e8655b7018.png)

## 6.6 Additional Information

The Plug-in Management screen displays all installed plug-ins in your GAX environment. To access the screen, navigate to Administration > Plug-in Management.

GAX supports several plug-ins to allow users to manage additional solutions. Some of the Plug-ins supported by GAX are given in the below table.

A tela Plug-in Management exibe todos os plug-ins instalados em seu ambiente GAX. Para acessar a tela, navegue até Administração > Gerenciamento de plug-in.

O GAX suporta vários plug-ins para permitir que os usuários gerenciem soluções adicionais. Alguns dos plug-ins suportados pelo GAX são fornecidos na tabela abaixo.

![image](https://user-images.githubusercontent.com/52088444/158865064-15d967c1-858d-4cfe-a81c-5719a4469504.png)

![image](https://user-images.githubusercontent.com/52088444/158865275-62766f91-4e0d-4142-b431-846e2d9692f9.png)

## 6.7 Learning Summary

Now that you have completed this chapter, you should be able to do the following: 

1 - Describe the components of the User Interaction Layer.

2 - Describe the functions of each component.

3 - Explain monitoring in Genesys Administrator Extension.

Agora que você concluiu este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descrever os componentes da Camada de Interação do Usuário.

2 - Descreva as funções de cada componente.

3 - Explicar o monitoramento no Genesys Administrator Extension.

