
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

## 11.5 Simple Routing Application Example

The routing application in the example below sends calls to the Chicago Agents group. The diagram below, (bottom right) shows the routing logic that was built in the Composer. 

Routing Logic—starts with the Entry block, moves to the Target block (using the logic “send to Chicago Agents Group”), and moves to the Exit block to finish the interaction. The Default Route block is present to send the interaction to an ACD Queue if there are any errors present. 

The logic is developed using Composer, the code is generated to create an SCXML file which gets deployed to a Web Application Server. This is all part of the pre-call setup of the routing scenario mentioned above. In addition, in order for the routing application to function, it has to be associated with a routing point. In this example, the routing application is associated route point 6663. The call arrives on route point 6663 and triggers the routing process.


O aplicativo de roteamento no exemplo abaixo envia chamadas para o grupo Chicago Agents. O diagrama abaixo (canto inferior direito) mostra a lógica de roteamento que foi construída no Composer.

Lógica de roteamento—começa com o bloco de entrada, move-se para o bloco de destino (usando a lógica “enviar para o grupo de agentes de Chicago”) e move-se para o bloco de saída para finalizar a interação. O bloco Default Route está presente para enviar a interação para uma fila ACD se houver algum erro presente.

A lógica é desenvolvida usando o Composer, o código é gerado para criar um arquivo SCXML que é implantado em um Web Application Server. Tudo isso faz parte da configuração pré-chamada do cenário de roteamento mencionado acima. Além disso, para que o aplicativo de roteamento funcione, ele deve estar associado a um ponto de roteamento. Neste exemplo, o aplicativo de roteamento está associado ao ponto de rota 6663. A chamada chega no ponto de rota 6663 e aciona o processo de roteamento.

![image](https://user-images.githubusercontent.com/52088444/159262435-8e66a3b3-489b-4712-b9d3-55c4628d393e.png)

**Step 1a:  Route Request**

When the customer calls the contact center, the call arrives at the switch. Next, the switch places the call on route point 6663 and sends a message across the CTI link to T-Server. The T-Server creates a unique record for the call, which is maintained until the call is released.
T-Server tracks the status of every call through each step of the process and provides updated information to all the relevant client applications, which are Stat Server (Routing Stat Server), URS, and ORS.

**Step 1b:  Route Request(Etapa 1a: Solicitação de Rota)**

T-Server generates and sends an EventRouteRequest to URS and ORS asking for routing instructions. It is very important to know this message for Genesys Routing. You can see in the example below, T-Server sends EventRouteRequest to all the client applications that are registered to receive messages regarding DN 6663—this includes Universal Routing Server, Orchestration Server, and Stat Server.

Quando o cliente liga para o contact center, a chamada chega na central. Em seguida, o switch coloca a chamada no ponto de rota 6663 e envia uma mensagem através do link CTI para o T-Server. O T-Server cria um registro exclusivo para a chamada, que é mantido até que a chamada seja liberada.
O T-Server rastreia o status de cada chamada em cada etapa do processo e fornece informações atualizadas para todos os aplicativos clientes relevantes, que são Stat Server (Routing Stat Server), URS e ORS.

Note: In all of the following routing interaction flow diagrams, you will see a highlighted server and a corresponding log file that belongs to that highlighted server. For example, in the diagram below, T-Server is highlighted and the log file displayed is a T-Server log file.

Nota: Em todos os diagramas de fluxo de interação de roteamento a seguir, você verá um servidor destacado e um arquivo de log correspondente que pertence a esse servidor destacado. Por exemplo, no diagrama abaixo, o T-Server está destacado e o arquivo de log exibido é um arquivo de log do T-Server.

![image](https://user-images.githubusercontent.com/52088444/159262971-15151c1c-80b0-4a63-a4a6-8f1229b4389a.png)

**T-Server Log: EventRouteRequest**

A piece of the T-Server log is displayed in the diagram above (not all attributes and details are being shown). This log displays the attributes that belong to the EventRouteRequest:

- AttributeThisDN—Corresponds to the route point (DN) that triggered this routing request.
- AttributeANI—Customer's phone number.
- AttributeDNIS—The number the customer dialed.
- AttributeConnID—The identifier that the T-Server is using for tracking this particular interaction. If you were looking for all the messages referencing this interaction, you would look for this ConnID.
- AttributeCallID—Corresponds to the switch’s identifier. If you need to troubleshoot something on the switch, you can use the CallID.

The log also shows any applications to which the interaction has been sent. 

The EventRouteRequest has been triggered and the call is sent to ORS.


Uma parte do log do T-Server é exibida no diagrama acima (nem todos os atributos e detalhes estão sendo mostrados). Este log exibe os atributos que pertencem ao EventRouteRequest:

- AttributeThisDN — Corresponde ao ponto de rota (DN) que acionou esta solicitação de roteamento.
- AttributeANI—Número de telefone do cliente.
- AttributeDNIS—O número que o cliente discou.
- AttributeConnID — O identificador que o T-Server está usando para rastrear essa interação específica. Se você estivesse procurando por todas as mensagens que fazem referência a essa interação, você procuraria por este ConnID.
- AttributeCallID—Corresponde ao identificador do switch. Se você precisar solucionar algo no switch, poderá usar o CallID.

O log também mostra todos os aplicativos para os quais a interação foi enviada.

O EventRouteRequest foi acionado e a chamada é enviada ao ORS.


**Step 2:  Fetch Routing Application(Etapa 2: Buscar Aplicativo de Roteamento)**

The ORS takes action and issues the HTTP GET request to the Web Application Server to fetch the routing application. The Web Application Server executes the request and returns the requested SCXML documents to ORS. ORS passes the received SCXML document to its SCXML engine. The SCXML engine runs the SCXML application, invoking ORS or URS services as needed.

In the example below, you see part of the T-Server log file.


O ORS entra em ação e emite a solicitação HTTP GET para o Web Application Server para buscar o aplicativo de roteamento. O Web Application Server executa a solicitação e retorna os documentos SCXML solicitados ao ORS. O ORS passa o documento SCXML recebido para seu mecanismo SCXML. O mecanismo SCXML executa o aplicativo SCXML, invocando serviços ORS ou URS conforme necessário.

No exemplo abaixo, você vê parte do arquivo de log do T-Server.

Nota: The log file has been simplified for this example and not all attributes and details are shown. The entries in the log files are for the interaction process diagram, "IPD_default_defaultWorkflow.scxml”. Additional files would also be fetched, such as the workflow diagram and other referenced files.

Nota: O arquivo de log foi simplificado para este exemplo e nem todos os atributos e detalhes são mostrados. As entradas nos arquivos de log são para o diagrama do processo de interação, "IPD_default_defaultWorkflow.scxml". Arquivos adicionais também seriam buscados, como o diagrama de fluxo de trabalho e outros arquivos referenciados.


Important actions of ORS to be aware of in the Orchestration Server log file are as follows:

- Processing GET request—This is followed by the full URL (Host Name:Port Number/full path to SCXML file) of where ORS is going to retrieve the routing logic.
- Request Successful—Indicates the routing logic was retrieved successfully.
- HTTP request completed—Indicates the request has completed successfully and the HTTP code response is 200.

As ações importantes do ORS a serem observadas no arquivo de log do Orchestration Server são as seguintes:

- Processando solicitação GET—Isso é seguido pela URL completa (Nome do host:Número da porta/caminho completo para o arquivo SCXML) de onde o ORS irá recuperar a lógica de roteamento.
- Solicitação bem-sucedida — indica que a lógica de roteamento foi recuperada com êxito.
- Solicitação HTTP concluída — indica que a solicitação foi concluída com êxito e a resposta do código HTTP é 200.

![image](https://user-images.githubusercontent.com/52088444/159264049-541fb819-c908-43bf-a3e0-88a8b5bc0808.png)


**Step 3a:  Target Selection (Etapa 3a: Seleção de alvo)**

ORS processes the SCXML application. At the Target Block, ORS submits a request to Universal Routing Server which invokes routing from URS—URS is the component that performs the routing target services. URS identifies the target, Chicago Agent Group, and checks with Stat Server to find an available agent. 

In the example below, you see part of the Orchestration Server log file. ORS requests to URS for Targeting log entries:
- ORS & URS: InvokeFunctionModule—Indicates ORS is requesting URS to perform routing logic.
- Method—The specific method used for targeting - SCXMLSubmit.
- refID—To assist with tracking, use the refID to locate the corresponding request in the URS log.
- args—List of values from the routing application Target block. URS will use these values to perform the routing target function. In this example, you can see: ChicagoAgentGroup@RoutingStatServer.GA


O ORS processa o aplicativo SCXML. No Target Block, o ORS envia uma solicitação ao Universal Routing Server que invoca o roteamento do URS—URS é o componente que executa os serviços de destino do roteamento. O URS identifica o destino, Chicago Agent Group, e verifica com o Stat Server para encontrar um agente disponível.

No exemplo abaixo, você vê parte do arquivo de log do Orchestration Server. Solicitações de ORS ao URS para entradas de registro de segmentação:
- ORS & URS: InvokeFunctionModule — Indica que o ORS está solicitando o URS para executar a lógica de roteamento.
- Método—O método específico usado para direcionamento - SCXMLSubmit.
- refID — Para ajudar no rastreamento, use o refID para localizar a solicitação correspondente no log do URS.
- args—Lista de valores do bloco de destino do aplicativo de roteamento. O URS usará esses valores para executar a função de destino de roteamento. Neste exemplo, você pode ver: ChicagoAgentGroup@RoutingStatServer.GA

**Step 3b:  Target Selection(Etapa 3b: Seleção de alvo) **

URS receives the routing message from ORS. This can be seen in the URS log file below as:
message RequestInvoke.

Correspondingly, you can also see the function SCXML submit and the same arguments, including ChicagoAgentGroup@RoutingStatServer.GA, that were seen in the ORS log file above.

![image](https://user-images.githubusercontent.com/52088444/159266236-c410a1b4-7c8d-465e-aae7-795d06e9a323.png)

**Step 3c:  Target Selection (Etapa 3c: Seleção de alvo) **

As part of targeting, URS opens and receives statistics from Stat Server. URS uses its target-seeking algorithm to select the best component (resource) for the interaction. 

In the Universal Routing Server log file below, you see URS starts the targeting process with HERE IS TARGETS, followed by the winner of the algorithm used to determine who is the best resource to handle this call. 

In this example below, the target is: ChicagoAgentGroup
- TRG “ChicagoAgentGroup”: Cmp IAllende: SELECTED
- Agent Ian Allende from Chicago Agents Group has been selected as the best resource to handle this call.

Como parte da segmentação, o URS abre e recebe estatísticas do Stat Server. O URS usa seu algoritmo de busca de destino para selecionar o melhor componente (recurso) para a interação.

No arquivo de log do Universal Routing Server abaixo, você vê que o URS inicia o processo de direcionamento com HERE IS TARGETS, seguido pelo vencedor do algoritmo usado para determinar quem é o melhor recurso para lidar com essa chamada.

Neste exemplo abaixo, o destino é: ChicagoAgentGroup
- TRG “ChicagoAgentGroup”: Cmp IAllende: SELECTED
- O agente Ian Allende do Chicago Agents Group foi selecionado como o melhor recurso para lidar com esta chamada.

![image](https://user-images.githubusercontent.com/52088444/159274195-923e3bc8-1d4b-4277-9d5c-8ad23ec97096.png)


**Step 4:  Routing Results (Etapa 4: resultados de roteamento) **

URS passes the chosen target DN to the T-Server using a RequestRouteCall message. The RequestRouteCall message provides T-Server with target information for the given interaction. This message includes the target specification (DN), and T-Server forwards this request to the switch. 

Once URS has selected a target, it sends a RequestRouteCall message to the T-Server. This message includes the target DN. 

T-Server forwards the request to the switch to actually route the call. In the example below, you can see that the URS log file includes the following attributes:

- AttributeExtensions—Include, the Agent, Place, DN, etc. In this example, we can see the call is going to IAllende at Place 6001_ Chicago, DN 6001 on Switch ‘ChicagoSwitch’.
- AttributeConnID—The identifier which identifies the interaction.
- AttributeOtherDN—The DN where the call is going to be routed.
- AttributeThisDN—The DN where the call is currently located.

O URS passa o DN de destino escolhido para o T-Server usando uma mensagem RequestRouteCall. A mensagem RequestRouteCall fornece ao T-Server informações de destino para a interação fornecida. Esta mensagem inclui a especificação de destino (DN), e o T-Server encaminha esta solicitação ao switch.

Uma vez que o URS tenha selecionado um alvo, ele envia uma mensagem RequestRouteCall para o T-Server. Essa mensagem inclui o DN de destino.

O T-Server encaminha a solicitação ao switch para realmente rotear a chamada. No exemplo abaixo, você pode ver que o arquivo de log URS inclui os seguintes atributos:

- AttributeExtensions—Incluir, o Agente, Local, DN, etc. Neste exemplo, podemos ver que a chamada está indo para IAllende no Local 6001_ Chicago, DN 6001 no Switch 'ChicagoSwitch'.
- AttributeConnID—O identificador que identifica a interação.
- AttributeOtherDN — O DN para onde a chamada será roteada.
- AttributeThisDN — O DN onde o atendimento está localizado atualmente.

![image](https://user-images.githubusercontent.com/52088444/159274836-ad9629d7-2acc-408a-bb93-db397ee996b5.png)


Composer Version: You can have either the URS or ORS sending the RouteRequestCall. In the Target Object Properties session detach = true means ORS will send the RequestRouteCall message to SIP Server. detach = false means URS will send the RequestRouteCall message to SIP Server. In the standard routing operations, ORS will be sending the Request. We have in class some projects with true and some with the false settings.
 
Versão do Composer: Você pode ter o URS ou ORS enviando o RouteRequestCall. Na sessão Target Object Properties detach = true significa que o ORS enviará a mensagem RequestRouteCall para o servidor SIP. detach = false significa que o URS enviará a mensagem RequestRouteCall para o servidor SIP. Nas operações de roteamento padrão, o ORS estará enviando a Solicitação. Temos em aula alguns projetos com configurações verdadeiras e outras com configurações falsas.

**Step 5:  Call Routed (Etapa 5: Chamada roteada)**

T-Server distributes an EventRouteUsed message to all the client applications that are registered for route point 6663. 

When the call arrives at the agent’s extension, the T-Server will be notified and EventRinging would be sent to the agent’s desktop. After the agent answers the call and the connection is made, then EventEstablished would be sent. These messages go to the applications that are registered to be informed of activity on the agent extension including not only the agent’s desktop, but also the Stat Server, ORS, and URS. 

In this example, the call has been routed to Agent Ian Allende at place 6001_Chicago. This message is distributed to URS and ORS, and Stat Server.

O T-Server distribui uma mensagem EventRouteUsed para todos os aplicativos clientes registrados para o ponto de rota 6663.

Quando a chamada chega ao ramal do agente, o T-Server será notificado e EventRinging será enviado para a área de trabalho do agente. Depois que o agente atender a chamada e a conexão for feita, EventEstablished será enviado. Essas mensagens vão para os aplicativos registrados para serem informados da atividade no ramal do agente, incluindo não apenas a área de trabalho do agente, mas também o Stat Server, ORS e URS.

Neste exemplo, a chamada foi roteada para o Agente Ian Allende no local 6001_Chicago. Esta mensagem é distribuída para URS e ORS e Stat Server.

![image](https://user-images.githubusercontent.com/52088444/159275378-c949c73a-7400-4755-8bcc-4b49fd9fce9a.png)

## 11.6 Routing Interaction Flow: Stick Diagram (Fluxo de Interação de Roteamento: Diagrama Stick)

As you saw in the Media Layer lesson, stick diagrams can be very helpful when troubleshooting and trying to see message names and follow the flow of interaction. 

As you learned previously, the vertical lines in a stick diagram represent software and devices. Their names are along the top. Messages are shown as horizontal lines with the earliest message at the top and the latest message at the bottom. 

In this example, different colors are used for different messaging: The black solid lines represent the device information, the red dotted lines represent the routing logic, the green dotted lines represent the Genesys TLibrary Events from T-Server, and the blue dotted lines represent the Genesys TLibrary requests from T-Server.

Como você viu na lição sobre camada de mídia, diagramas em bastão podem ser muito úteis ao solucionar problemas e tentar ver nomes de mensagens e seguir o fluxo de interação.

Como você aprendeu anteriormente, as linhas verticais em um diagrama de bastão representam software e dispositivos. Seus nomes estão no topo. As mensagens são mostradas como linhas horizontais com a mensagem mais antiga na parte superior e a mensagem mais recente na parte inferior.

Neste exemplo, cores diferentes são usadas para mensagens diferentes: as linhas sólidas pretas representam as informações do dispositivo, as linhas pontilhadas vermelhas representam a lógica de roteamento, as linhas pontilhadas verdes representam os eventos Genesys TLibrary do T-Server e as linhas pontilhadas azuis representam as solicitações do Genesys TLibrary do T-Server.

![image](https://user-images.githubusercontent.com/52088444/159275723-d6f77516-e515-449b-adb8-489656e9451b.png)

![image](https://user-images.githubusercontent.com/52088444/159275752-27f99695-49f1-4f85-8123-1a0c25b659c1.png)

![image](https://user-images.githubusercontent.com/52088444/159275806-3a9c22fe-5202-467d-9989-10e85fe11671.png)

![image](https://user-images.githubusercontent.com/52088444/159275832-dbea77bc-f267-4eb6-8e65-5d6ee7c05963.png)

![image](https://user-images.githubusercontent.com/52088444/159275885-a3b1ebf8-dcf6-49e0-9c8f-c9c4afdd6772.png)

**Understanding the Routing Interaction Flow: Simple Routing Application (Compreendendo o fluxo de interação de roteamento: aplicativo de roteamento simples) **

Stat Server provides a centralized collection of statistics and calculation of the status of contact center objects (Agents, Places, DNs, and their groups).

1 - A new interaction arrives. The Switch sends a route request to the T-Server.
2 - T-server notifies both ORS and URS with EventRouteRequest.
3 - ORS fetches the routing application from the Web Application Server. (HTTP GET)
4 - The Web Application Server provides the routing application to ORS. You will see a HTTP 200 OK when the fetch is successful.
5 - ORS starts execution of the SCXML routing application. The action state of the application is the Target block.
6 - ORS invokes (RequestInvoke) URS to select the appropriate target.
7 - URS carries out its target seeking algorithm, by pulling statistics from Stat Server. URS selects the best available Target based on the results of the algorithm.
8 - URS then requests the T-Server to route to the agent (RequestRouteCall).
9 - T-Server communicates with the switch to take action and have the call routed.
10 - Once the call has been routed and the T-Server has been notified, T-Server sends EventRouteUsed to URS, ORS, and Stat Server to let them know the call has left that route point and the routing has been completed successfully.

1 - Chega uma nova interação. O Switch envia uma solicitação de rota para o T-Server.
2 - T-server notifica ORS e URS com EventRouteRequest.
3 - O ORS busca o aplicativo de roteamento do Web Application Server. (HTTP GET)
4 - O Web Application Server fornece o aplicativo de roteamento para o ORS. Você verá um HTTP 200 OK quando a busca for bem-sucedida.
5 - O ORS inicia a execução do aplicativo de roteamento SCXML. O estado de ação do aplicativo é o bloco Target.
6 - O ORS invoca (RequestInvoke) URS para selecionar o destino apropriado.
7 - O URS executa seu algoritmo de busca de alvos, extraindo estatísticas do Stat Server. O URS seleciona o melhor alvo disponível com base nos resultados do algoritmo.
8 - O URS então solicita que o T-Server roteie para o agente (RequestRouteCall).
9 - O T-Server se comunica com o switch para agir e ter a chamada roteada.
10 - Uma vez que a chamada foi roteada e o T-Server foi notificado, o T-Server envia EventRouteUsed para URS, ORS e Stat Server para que eles saibam que a chamada saiu daquele ponto de rota e o roteamento foi concluído com sucesso.


 **Understanding the Routing Interaction Flow: Routing Application Specific Example-Treatment (Entendendo o Fluxo de Interação de Roteamento: Exemplo de Tratamento Específico do Aplicativo de Roteamento) **
 
 
While executing the SCXML, the routing application can do more than just specify a target. This routing application uses a “treatment” to prompt and collect an account number using the caller’s entered digits in order to perform a database lookup, then a routing decision is performed based on the customer type. 

Treatment or User input: Referring to the routing application shown in the diagram below, the first state is to prompt the user to enter their account number. To accomplish this task, URS requests the T-Server to process this treatment. T-Server then sends the interaction to an IVR or in this example, to a Media Server, to prompt the customer to enter their account number.

Ao executar o SCXML, o aplicativo de roteamento pode fazer mais do que apenas especificar um destino. Este aplicativo de roteamento usa um “tratamento” para solicitar e coletar um número de conta usando os dígitos inseridos do chamador para realizar uma pesquisa no banco de dados, em seguida, uma decisão de roteamento é executada com base no tipo de cliente.

Tratamento ou entrada do usuário: Referindo-se ao aplicativo de roteamento mostrado no diagrama abaixo, o primeiro estado é solicitar ao usuário que insira seu número de conta. Para realizar esta tarefa, o URS solicita ao T-Server que processe este tratamento. O T-Server então envia a interação para um IVR ou, neste exemplo, para um Media Server, para solicitar ao cliente que insira seu número de conta.

1 - The SCXML session initiates the application of a treatment to a voice call.
2 - ORS sends RequestInvoke SCXMLStartTreatment to URS.
3 - URS sends RequestApplyTreatment to T-Server/SIP Server.
4 - T-Server delegates to the Media Server to play the announcement and collect digits back.
5 - Once this has occurred, the T-Server is notified and EventTreatmentApplied and EventTreatmentEnd are sent from T-Server to Stat Server, ORS, and URS.
6 - URS sends EventOnInvoke to ORS to notify completion of its part so that ORS knows it is time to continue with any logic in the application.

1 - A sessão SCXML inicia a aplicação de um tratamento a uma chamada de voz.
2 - O ORS envia RequestInvoke SCXMLStartTreatment para o URS.
3 - URS envia RequestApplyTreatment para T-Server/SIP Server.
4 - O T-Server delega ao Media Server a reprodução do anúncio e a coleta dos dígitos de volta.
5 - Uma vez ocorrido, o T-Server é notificado e EventTreatmentApplied e EventTreatmentEnd são enviados do T-Server para o Stat Server, ORS e URS.
6 - O URS envia EventOnInvoke ao ORS para notificar a conclusão de sua parte para que o ORS saiba que é hora de continuar com qualquer lógica na aplicação.

![image](https://user-images.githubusercontent.com/52088444/159277549-4e88b50c-e167-4d09-9047-b0641fc00d07.png)

![image](https://user-images.githubusercontent.com/52088444/159277593-0c3799a9-1852-442d-8ee9-7d57a2d60e01.png)

![image](https://user-images.githubusercontent.com/52088444/159277648-86220016-9cf0-4d7e-b752-dcaedc6b22f9.png)


Understanding the Routing Interaction Flow: Routing Application Specific Example-Database Lookup Treatments and Database Access: Database Lookup

The next application looks up the customer’s account information based on the digits entered in the previous routing application. Based on the digits the caller entered, ORS requests a database lookup. The database returns the customer records. Database integration is accomplished via the SCXML application. When routing applications are developed using Composer, JBDC or OLEDB drivers are provided. The database lookup is carried out by ORS and Web Application Server. The resulting data, or variables, are returned to ORS to determine which routing logic will be executed next.

- ORS sends HTTP POST to the Web Application Server. This fetches and returns the data from the database. Then, returns a HTTP 200 OK message to ORS along with the data.

Compreendendo o fluxo de interação de roteamento: exemplos específicos de aplicativos de roteamento - tratamentos de pesquisa de banco de dados e acesso ao banco de dados: pesquisa de banco de dados

O próximo aplicativo pesquisa as informações da conta do cliente com base nos dígitos inseridos no aplicativo de roteamento anterior. Com base nos dígitos inseridos pelo chamador, o ORS solicita uma pesquisa no banco de dados. O banco de dados retorna os registros do cliente. A integração do banco de dados é realizada por meio do aplicativo SCXML. Quando os aplicativos de roteamento são desenvolvidos usando o Composer, são fornecidos drivers JBDC ou OLEDB. A pesquisa do banco de dados é realizada pelo ORS e pelo Web Application Server. Os dados ou variáveis resultantes são retornados ao ORS para determinar qual lógica de roteamento será executada em seguida.

- O ORS envia HTTP POST para o Servidor de Aplicativos Web. Isso busca e retorna os dados do banco de dados. Em seguida, retorna uma mensagem HTTP 200 OK para ORS junto com os dados.

![image](https://user-images.githubusercontent.com/52088444/159277779-504cf101-873f-45d8-84bb-063ff98d7e31.png)

![image](https://user-images.githubusercontent.com/52088444/159277844-37dc5aeb-a049-4a90-a039-8bd8eb8d0bb8.png)


## 11.7 Learning Summary

Now that you have completed this chapter, you should be able to do the following: 

1 - Describe the components of Genesys Routing.

2 - Describe the functions of each component.

3 - Understand Routing Interaction Flows.

4 - Identify major messages involved in Routing.


Agora que você concluiu este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descrever os componentes do Genesys Routing.

2 - Descreva as funções de cada componente.

3 - Compreender os Fluxos de Interação de Roteamento.

4 - Identificar as principais mensagens envolvidas no Roteamento.


