
## 11.1 Learning Objectives

After completing this chapter, you should be able to do the following:

1 - Describe the components of Genesys Routing.

2 - Describe the functions of each component.

3 - Understand Routing Interaction Flows.

4 - Identify major messages involved in Routing.

Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descrever os componentes do Genesys Routing.

2 - Descreva as funções de cada componente.

3 - Compreender os Fluxos de Interação de Roteamento.

4 - Identificar as principais mensagens envolvidas no Roteamento.


## 11.2 Routing Architecture

The following image outlines Routing architecture — Orchestration/Routing is shown in detail along with its connections to the Media, Services, and Configuration Layers of Framework. Routing is made up of the following:

- Composer
- Web Application Server
- Orchestration Server (ORS)
- URS


A imagem a seguir descreve a arquitetura de roteamento — a orquestração/roteamento é mostrada em detalhes junto com suas conexões com as camadas de mídia, serviços e configuração da estrutura. O roteamento é composto por:

- Compositor
- Servidor de Aplicativos Web
- Servidor de Orquestração (ORS)
- URS

![image](https://user-images.githubusercontent.com/52088444/159060620-974cc5cb-c44b-4db2-b6ac-d9709d657de2.png)

For the purposes of logging and alarms, Routing could also connect to the Management Layer—it is not demonstrated in this diagram.

Para fins de registro e alarmes, o roteamento também pode se conectar à camada de gerenciamento — isso não é demonstrado neste diagrama.

**Composer**

Composer is the Eclipse-based, graphical Integrated Development Environment (IDE) routing application development tool used to define routing logic for the following:

- URS—Enables intelligent distribution of voice and multimedia interactions throughout the enterprise.
- ORS—An open standards-based platform with an SCXML engine, which enables the customer service process.

Composer provides both drag-and-drop graphical development of voice applications (or “callflows”) and routing applications (or “workflows”) as well as syntax-directed editing of these applications. 

The use of eclipse as the underlying framework enables the use of third-party IDE plug-ins, supporting integration with third-party source code control systems, server-side development enhancements, and side-by-side development of any business logic required to support your applications. 

Composer generates routing applications using SCXML, an XML-based markup language.

For more information on State Chart XML, click here.

O Composer é a ferramenta de desenvolvimento de aplicativo de roteamento gráfico do Ambiente de Desenvolvimento Integrado (IDE) baseado em Eclipse usado para definir a lógica de roteamento para o seguinte:

- URS—Permite a distribuição inteligente de interações de voz e multimídia em toda a empresa.
- ORS—Uma plataforma baseada em padrões abertos com um mecanismo SCXML, que permite o processo de atendimento ao cliente.

O Composer fornece desenvolvimento gráfico de arrastar e soltar de aplicativos de voz (ou “fluxos de chamada”) e aplicativos de roteamento (ou “fluxos de trabalho”), bem como edição direcionada pela sintaxe desses aplicativos.

O uso do Eclipse como estrutura subjacente permite o uso de plug-ins IDE de terceiros, suportando integração com sistemas de controle de código-fonte de terceiros, aprimoramentos de desenvolvimento do lado do servidor e desenvolvimento lado a lado de qualquer lógica de negócios necessária para suportar seus aplicativos.

O Composer gera aplicativos de roteamento usando SCXML, uma linguagem de marcação baseada em XML.

Para obter mais informações sobre o XML do gráfico de estado, clique aqui.

[(https://www.w3.org/TR/scxml/)](https://www.w3.org/TR/scxml/)

![image](https://user-images.githubusercontent.com/52088444/159061659-fdbce85a-b308-471c-acc4-04b2fd398a0e.png)

To make the SCXML routing applications available to the ORS and URS Servers, the SCXML applications need to be deployed to a Web Application Server.

Para disponibilizar os aplicativos de roteamento SCXML para os servidores ORS e URS, os aplicativos SCXML precisam ser implantados em um servidor de aplicativos Web.

**Web Application Server(Servidor de aplicativos da Web)**

Once you have developed and tested your SCXML-based routing applications, they need to be uploaded to a supported Web Application Server, which then performs two main functions:

- Upon HTTP request, the Web Application Server is responsible for providing the routing application logic to ORS in the form of a document (or series of documents).
- The Web Application Server may interact with ORS during the strategy processing to perform business-specific tasks, or to provide access to other enterprise systems.

For lab testing purposes, there is a web application server embedded within Composer, called TomCat. For production, a web application server outside of the Composer environment needs to be used. For .NET projects, you can use any Microsoft IIS compatible with the Windows versions supported by Composer. For Java projects, the web application server needs to support Java Runtime Environment 1.7.0_0 or higher, be J2EE 5 compliant, and support the JSP 2.1/Servlet 2.5 specifications (such as Tomcat and JBoss application servers).

![image](https://user-images.githubusercontent.com/52088444/159062386-08eb71ed-d0d6-4da4-ba61-f023cc936463.png)

**Orchestration Server**

The two routing components that are responsible for executing the routing logic make up the Orchestration Platform. These are ORS and URS. The ORS communicates with the Web Application Server and GET or FETCH the SCXML file. It gets the desired logic for handling the interaction. ORS also executes this logic and carry out the instructions it contains. Some of the logic is delegated, to be handled by URS—of which an important step is target seeking. ORS submits a request to URS to delegate this logic.

Os dois componentes de roteamento responsáveis pela execução da lógica de roteamento compõem a Plataforma de Orquestração. Estes são ORS e URS. O ORS se comunica com o Web Application Server e GET ou FETCH o arquivo SCXML. Ele obtém a lógica desejada para lidar com a interação. O ORS também executa esta lógica e executa as instruções que ela contém. Parte da lógica é delegada, para ser tratada pelo URS – do qual um passo importante é a busca de alvos. O ORS envia uma solicitação ao URS para delegar essa lógica.

![image](https://user-images.githubusercontent.com/52088444/159063327-8ccfd0e5-a48e-4a14-b3ee-d259dc056da7.png)

**Universal Routing Server(Servidor de roteamento universal)**

Once URS receives the request from ORS, URS carries out the requested routing service to ORS and executes the rules specified in the strategies created in Composer. URS creates a list of destinations or targets based on the routing application, determines which target is most appropriate, and instructs T-Server where to route the interaction. Part of this requires URS to run strategic target seeking algorithms. Using statistics and statuses from Stat Server (which Agents are logged in, which Agents have been ready the longest, etc.) URS selects the best agent as the target to route the interaction.


Uma vez que o URS recebe a solicitação do ORS, o URS realiza o serviço de roteamento solicitado ao ORS e executa as regras especificadas nas estratégias criadas no Composer. O URS cria uma lista de destinos ou destinos com base no aplicativo de roteamento, determina qual destino é mais apropriado e instrui o T-Server para onde rotear a interação. Parte disso requer que o URS execute algoritmos estratégicos de busca de alvos. Usando estatísticas e status do Stat Server (quais agentes estão conectados, quais agentes estão prontos há mais tempo, etc.), o URS seleciona o melhor agente como destino para rotear a interação.

![image](https://user-images.githubusercontent.com/52088444/159064006-095d22f4-aaa7-401e-80d5-280fd8abbac8.png)

URS is sometimes referred to as “router”.
O URS às vezes é chamado de “roteador”.

##  11.3 Routing Interaction Flows(Fluxos de interação de roteamento)


An inbound call interaction flow maps the messages that define the life of an interaction. The flow of an interaction in a Universal Routing/Orchestration Platform deployment is dependent on the routing application that was developed to handle the interaction. Interaction flows are helpful in understanding how the Routing components work together. 

Interaction flows in Universal Routing with Orchestration Server have a set of common messaging. For example, the basic messages that trigger the starting of the routing process, and communicate the results of the routing process. 

Additionally, they have further messaging based on the routing applications functionality, such as gathering customer information from a database or using skills-based routing. These messages will vary based on the logic that has been written into the routing applications. 

We will use a sample routing application with some common elements to describe a typical customer interaction flow. Keep in mind that not every interaction is handled exactly the same way. In the following call flow example, we will examine an interaction flow where the routing logic sends calls to the Chicago Agents group. In particular, the focus will be on some key messages that would appear in the application logs.

Um fluxo de interação de chamada de entrada mapeia as mensagens que definem a vida de uma interação. O fluxo de uma interação em uma implantação de Plataforma de Roteamento/Orquestração Universal depende do aplicativo de roteamento que foi desenvolvido para lidar com a interação. Os fluxos de interação são úteis para entender como os componentes de roteamento funcionam juntos.

Os fluxos de interação no roteamento universal com o Orchestration Server têm um conjunto de mensagens comuns. Por exemplo, as mensagens básicas que acionam o início do processo de roteamento e comunicam os resultados do processo de roteamento.

Além disso, eles têm mais mensagens com base na funcionalidade dos aplicativos de roteamento, como coletar informações do cliente de um banco de dados ou usar roteamento baseado em habilidades. Essas mensagens variam com base na lógica que foi gravada nos aplicativos de roteamento.

Usaremos um aplicativo de roteamento de amostra com alguns elementos comuns para descrever um fluxo típico de interação com o cliente. Tenha em mente que nem todas as interações são tratadas exatamente da mesma maneira. No exemplo de fluxo de chamadas a seguir, examinaremos um fluxo de interação em que a lógica de roteamento envia chamadas para o grupo Chicago Agents. Em particular, o foco estará em algumas mensagens-chave que apareceriam nos logs do aplicativo.

## 11.4 Routing Interaction Flow Example

**Pre-Call Setup(Configuração de pré-chamada)**

Before we look at the flow of a typical call through the Routing Solution, let’s clarify some of the basic settings in the sample system.
- Enable CTI and Script the switch—In a traditional telephony environment, the first step is for the System Administrator to connect Genesys software to the hardware switch (PBX, PABX, ACD) through a switch-specific CTI-Link. To allow the Genesys Routing Solution to control the call, the switch must be programmed to request routing instructions through the CTI-Link. The Switch Technician does this by specifying a routing point in the switch. All calls arriving at this routing point will require routing instructions through the CTI-Link.
- Register the DNs—Genesys components are configured to be registered for certain DNs in the switch. Once an application has registered for a particular DN, the T‑Server provides it with all the messaging related to that DN.
- Build and test— Using Composer build and test the routing application.
- Deploy—On a web application server, deploy the routing application. For this step, the routing developer or system administrator will need to copy the SCXML application (routing application) files and other required application resources to a supported Web Application Server.
- Provide routing application URI and DNs— In Genesys Administrator or GAX, provide routing application URI and DNs. Once the routing application has been deployed to the web application server, the Enhanced Routing Script object, Configuration Tab, and URI needs to point to this server.

Antes de examinarmos o fluxo de uma chamada típica por meio da solução de roteamento, vamos esclarecer algumas das configurações básicas no sistema de amostra.

- Habilite o CTI e faça o script do switch—Em um ambiente de telefonia tradicional, o primeiro passo é o administrador do sistema conectar o software Genesys ao switch de hardware (PBX, PABX, ACD) por meio de um CTI-Link específico do switch. Para permitir que a Genesys Routing Solution controle a chamada, o switch deve ser programado para solicitar instruções de roteamento por meio do CTI-Link. O técnico do switch faz isso especificando um ponto de roteamento no switch. Todas as chamadas que chegam a este ponto de roteamento exigirão instruções de roteamento através do CTI-Link.
- Registre os DNs — os componentes Genesys são configurados para serem registrados para determinados DNs no switch. Depois que um aplicativo é registrado para um determinado DN, o T‑Server fornece a ele todas as mensagens relacionadas a esse DN.
- Construir e testar— Usando o Composer, crie e teste o aplicativo de roteamento.
- Implantar—Em um servidor de aplicativos da Web, implante o aplicativo de roteamento. Para esta etapa, o desenvolvedor de roteamento ou administrador do sistema precisará copiar os arquivos do aplicativo SCXML (aplicativo de roteamento) e outros recursos de aplicativo necessários para um servidor de aplicativos da Web com suporte.
- Fornecer URI e DNs do aplicativo de roteamento— No Genesys Administrator ou GAX, forneça URI e DNs do aplicativo de roteamento. Depois que o aplicativo de roteamento for implementado no servidor de aplicativos da Web, o objeto Enhanced Routing Script, a guia Configuration e o URI precisam apontar para esse servidor.
