
## 9.1 Learning Objectives

After completing this chapter, you should be able to do the following: 

1 - Describe the components of the Media Layer.

2 - Describe the functions of each component.

3 - Investigate log messages for a voice interaction.

4 - Describe a high level call flow.

Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descreva os componentes da camada de mídia.

2 - Descreva as funções de cada componente.

3 - Investigue as mensagens de log para uma interação de voz.

4 - Descreva um fluxo de chamadas de alto nível.


## 9.2 Review: Media Layer

The Media layer also provides:
- Interfaces to communication media
- Distribution of interaction-related business data within and across solutions

A camada de mídia também fornece:
- Interfaces com os meios de comunicação
- Distribuição de dados de negócios relacionados à interação dentro e entre soluções

![image](https://user-images.githubusercontent.com/52088444/159009159-b2b1b9b1-ae00-4564-9076-4d4586fd70ce.png)

##  9.3 Review: Media Layer Components

Media Servers, such as T-Server (or other media servers such as Interaction Server or SIP Server) are at the center of any Genesys system, receiving and distributing messages as directed by the other components. 

The Media Layer enables solutions to communicate with a variety of media including traditional telephony systems, voice over IP, email, and the Web.

Servidores de mídia, como T-Server (ou outros servidores de mídia, como Interaction Server ou SIP Server) estão no centro de qualquer sistema Genesys, recebendo e distribuindo mensagens conforme indicado pelos outros componentes.

A camada de mídia permite que as soluções se comuniquem com uma variedade de mídias, incluindo sistemas de telefonia tradicionais, voz sobre IP, e-mail e a Web.


Traditional/TDM Telephony

T-Server–Provides an interface with traditional telephony systems. T-Server is the heart of the Media Layer—translating the information of the media-device realm into information that Genesys solutions can use. It enables your contact center to handle the computer-based form of the interactions that arrive and it translates the information surrounding a customer contact into reportable and actionable data.

VoIP

SIP Server–Provides an interface with Voice over IP (VoIP) telephony systems. SIP Server has the same position in the Genesys Media Layer as all Genesys T-Servers. SIP Server is an application server that integrates Genesys telephony based applications to various SIP based products.

Multimedia

Interaction Server–Provides an interface with non-voice media such as web chat, email, and other non-voice work items.


Telefonia Tradicional/TDM

T-Server–Fornece uma interface com sistemas de telefonia tradicionais. O T-Server é o coração da camada de mídia — traduzindo as informações do domínio do dispositivo de mídia em informações que as soluções da Genesys podem usar. Ele permite que seu contact center lide com o formulário baseado em computador das interações que chegam e traduz as informações em torno de um contato do cliente em dados relatáveis e acionáveis.

VoIP

Servidor SIP–Fornece uma interface com sistemas de telefonia de Voz sobre IP (VoIP). O SIP Server tem a mesma posição na Genesys Media Layer que todos os Genesys T-Servers. O SIP Server é um servidor de aplicativos que integra aplicativos baseados em telefonia da Genesys a vários produtos baseados em SIP.

Multimídia

Interaction Server–Fornece uma interface com mídia sem voz, como chat na web, e-mail e outros itens de trabalho sem voz.

![image](https://user-images.githubusercontent.com/52088444/159011484-83b4ed27-e2a7-4bbf-96ab-89972cdf11de.png)

In this class, we will use the SIP Server as our Media Layer. The concepts in this lesson also apply to T-Servers. eServices courses cover the additional considerations, messaging, and components involved for an Interaction Server.

Nesta aula, usaremos o servidor SIP como nossa camada de mídia. Os conceitos desta lição também se aplicam a T-Servers. Os cursos de eServices abrangem as considerações adicionais, mensagens e componentes envolvidos em um Interaction Server.

##  9.4 Framework Architecture: Media Layer

The following image outlines the five different layers of the Framework—the Media Layer is shown in detail along with its connections to the Management, User Interaction, and Configuration Layers. The Media Layer is made up of:

- T-Server
- Switch

A imagem a seguir descreve as cinco camadas diferentes da estrutura — a camada de mídia é mostrada em detalhes junto com suas conexões com as camadas de gerenciamento, interação com o usuário e configuração. A camada de mídia é composta por:

- T-Server
- Switch

![image](https://user-images.githubusercontent.com/52088444/159013343-a0e096cd-beeb-4e9c-aa06-8e0109d05777.png)

## 9.5 Media Layer Startup(Inicialização da camada de mídia)

When a solution includes voice interactions, the Media Layer component you must start is SIPServer/T‑Server.

Quando uma solução inclui interações de voz, o componente Media Layer que você deve iniciar é SIPServer/T‑Server.

Before starting SIPServer/T-Server, License Manager must be running. License Manager is a third-party product. Genesys uses License Manager for the license control of Genesys components. License control will be covered in more detail in the  Framework Routing & Reporting 8.5 Administration course.

For T-Server to work, a CTI-link must be working with the Switch.

Antes de iniciar o SIPServer/T-Server, o License Manager deve estar em execução. O License Manager é um produto de terceiros. A Genesys usa o License Manager para o controle de licenças dos componentes da Genesys. O controle de licença será abordado com mais detalhes no curso Framework Routing & Reporting 8.5 Administration.

Para que o T-Server funcione, um link CTI deve estar funcionando com o Switch.

SIPServer/T-Server Startup

SIPServer/T-Server is started automatically using Services or daemon processes, or manually from Genesys Administrator or GAX, a command line, an application shortcut, or a script. Upon startup, SIPServer/T-Server gathers configuration data via the Configuration Server. SIPServer/T-Server connects to the Message Server for logging.
 
T-Server connects to the switch via the CTI‑Link.

**Inicialização do SIPServer/T-Server**

O SIPServer/T-Server é iniciado automaticamente usando Services ou processos daemon, ou manualmente do Genesys Administrator ou GAX, uma linha de comando, um atalho de aplicativo ou um script. Na inicialização, o SIPServer/T-Server reúne dados de configuração por meio do Configuration Server. O SIPServer/T-Server conecta-se ao Message Server para registro.
 
O T-Server conecta-se ao switch através do CTI‑Link.

**T-Server Registration(Registro do T-Server)**

For the Genesys system to be able to coordinate with the telephone system in the contact center, it must know what activity is taking place on the switch. T-Server finds out about this activity by receiving messages from the switch via the CTI link.

T-Server does not need to know about all the activity on the switch. It only needs to know about events that affect the DNs -- routing points, queues, extensions, and so on -- that are used for calls to and from the contact center. T-Server can identify these DNs because they are defined in the configuration data that T-Server retrieves from the Configuration Server on startup.

As part of its initialization, T-Server communicates with the switch to register the DNs which it wants to track. Now, whenever there is activity on these DNs, the switch alerts the T-Server to this activity via messaging over the CTI link.



Para que o sistema Genesys possa se coordenar com o sistema telefônico no contact center, ele deve saber qual atividade está ocorrendo no switch. O T-Server descobre esta atividade recebendo mensagens do switch através do link CTI.

O T-Server não precisa saber sobre toda a atividade no switch. Ele só precisa saber sobre os eventos que afetam os DNs – pontos de roteamento, filas, ramais e assim por diante – que são usados para chamadas de e para o contact center. O T-Server pode identificar esses DNs porque eles são definidos nos dados de configuração que o T-Server recupera do Configuration Server na inicialização.

Como parte de sua inicialização, o T-Server se comunica com o switch para registrar os DNs que deseja rastrear. Agora, sempre que houver atividade nesses DNs, o switch alertará o T-Server sobre essa atividade por meio de mensagens no link CTI.

Note:Genesys uses the term DN to describe a number on the switch where a call is parked (routing point or queue) or a line to an agent’s phone set (extension or ACD position).

Observação: a Genesys usa o termo DN para descrever um número na central onde uma chamada está estacionada (ponto de roteamento ou fila) ou uma linha para o telefone do agente (ramal ou posição ACD).

![image](https://user-images.githubusercontent.com/52088444/159014546-dc2207cd-05eb-46be-ac08-545f1ba3915e.png)

## 9.6 Genesys T-Server

The T-Server and the switch are communicating over the CTI-Link. The messaging between the switch and the T-Server and the format of those messages is switch specific. However, messaging between T-Server and the rest of Genesys uses Genesys messaging, more specifically the T-library protocol (Tlib). For example, between T-Server and routing or T-Server and the desktop applications.

O T-Server e o switch estão se comunicando pelo CTI-Link. As mensagens entre o switch e o T-Server e o formato dessas mensagens são específicos do switch. No entanto, o envio de mensagens entre o T-Server e o restante do Genesys usa o sistema de mensagens do Genesys, mais especificamente o protocolo T-library (Tlib). Por exemplo, entre T-Server e roteamento ou T-Server e os aplicativos de desktop.

![image](https://user-images.githubusercontent.com/52088444/159015194-b9ff78e8-5241-4298-8f7a-6f1613c1a7cd.png)


As you can see below, Genesys T-Server has two major functional areas:
- T-Server Common Part—This is a module responsible for all direct interaction with the Framework library. For all T-Servers and each different switch, this module is common to every T-Server.
- Device Dependent–Specific to the switch with which the T-Server is working. For example, a T-Server for Avaya has a different device dependent portion than a T-Server for Alcatel.

The T-Server common part provides a lot of the common functionality that we expect from the T-Server. It is also responsible for communicating with the rest of Genesys using the TLibrary protocol.

The device dependent portion of the T-Server knows how to talk to the specific switch.

Como você pode ver abaixo, o Genesys T-Server possui duas áreas funcionais principais:
- T-Server Common Part—Este é um módulo responsável por toda interação direta com a biblioteca Framework. Para todos os T-Servers e cada switch diferente, este módulo é comum a todos os T-Servers.
- Dependente de Dispositivo – Específico para o switch com o qual o T-Server está trabalhando. Por exemplo, um T-Server para Avaya tem uma parte dependente de dispositivo diferente de um T-Server para Alcatel.

A parte comum do T-Server fornece muitas das funcionalidades comuns que esperamos do T-Server. Também é responsável pela comunicação com o restante da Genesys usando o protocolo TLibrary.

A parte dependente do dispositivo do T-Server sabe como falar com o switch específico.

![image](https://user-images.githubusercontent.com/52088444/159015686-90fcc518-6b36-4d6c-bed9-d430748e23b8.png)

## 9.7 Genesys SIP Server

SIP Server acts very similarly to the T-Server, except SIP Server also has the ability to act as a SIP Softswitch. SIP Server is a combination of T-Server and a call switching component. The call-switching element functions as a SIP Back-to-Back User Agent (B2BUA). Call switching and control can be performed by Genesys.

SIP Server supports many modes of deployment. SIP Server can be used in a stand-alone mode or integrated with other third-party Gateways and Softswitches. Depending on the kind of integration and architecture, different SIP Server options and DNs need to be configured. SIP Server is fully integrated in Genesys Framework and Routing.

O SIP Server atua de forma muito semelhante ao T-Server, exceto que o SIP Server também tem a capacidade de atuar como um Softswitch SIP. SIP Server é uma combinação de T-Server e um componente de comutação de chamadas. O elemento de comutação de chamadas funciona como um SIP Back-to-Back User Agent (B2BUA). A comutação e o controle de chamadas podem ser realizados pela Genesys.

O Servidor SIP oferece suporte a muitos modos de implantação. O Servidor SIP pode ser usado em modo autônomo ou integrado a outros Gateways e Softswitches de terceiros. Dependendo do tipo de integração e arquitetura, diferentes opções de servidor SIP e DNs precisam ser configurados. O SIP Server é totalmente integrado ao Genesys Framework and Routing.

![image](https://user-images.githubusercontent.com/52088444/159016043-832e95d1-6e16-41ca-b13b-22a61207287a.png)

Genesys SIP Server has two major functional areas:

- T-Server Common Part–This is a module responsible for all direct interaction with the Framework library. For all T-Servers and each different switch, this module is common to every T-Server.
- SIP Switch–This is responsible for SIP signaling. Instead of communicating with a PBX, it has the ability to operate as a SIP Softswitch itself and communicate using SIP and IP network.

O Genesys SIP Server tem duas áreas funcionais principais:

- T-Server Common Part – Este é um módulo responsável por toda interação direta com a biblioteca do Framework. Para todos os T-Servers e cada switch diferente, este módulo é comum a todos os T-Servers.
- Switch SIP – Responsável pela sinalização SIP. Em vez de se comunicar com um PBX, ele tem a capacidade de operar como um Softswitch SIP e se comunicar usando a rede SIP e IP.

![image](https://user-images.githubusercontent.com/52088444/159016972-f8937a97-6518-46de-80dd-d719293bc8b1.png)

SIP Server acts as a standard T-Server which accepts TLibrary protocol. TLibrary clients can register for DNs and send and receive TLibrary requests and events on those DNs. SIP Server is also a SIP Switch, which accepts SIP protocol from other SIP endpoints.

A client application employs T-Library functions to create telephony requests understood by SIP Server. SIP Server translates these requests to SIP messages and forwards them to the IP network.

In the opposite direction, SIP Server receives SIP messages from the IP network, generates standard TLibrary messages called TEvents, and distributes these events to all the clients registered to receive the event.

O SIP Server atua como um T-Server padrão que aceita o protocolo TLibrary. Os clientes TLibrary podem se registrar para DNs e enviar e receber solicitações e eventos TLibrary nesses DNs. O servidor SIP também é um switch SIP, que aceita o protocolo SIP de outros terminais SIP.

Um aplicativo cliente emprega funções T-Library para criar solicitações de telefonia compreendidas pelo Servidor SIP. O Servidor SIP converte essas solicitações em mensagens SIP e as encaminha para a rede IP.

Na direção oposta, o SIP Server recebe mensagens SIP da rede IP, gera mensagens padrão TLibrary chamadas TEvents e distribui esses eventos para todos os clientes cadastrados para receber o evento.

## 9.8 T-Server Common Part Features(Recursos de Parte Comum do T-Server)


**Call Model Consistency**

Genesys provides call model consistency across the different switch platforms. The following are unified by the T-Server common part:

-  Agent State Event–The state of the Agent (Connected, alerting, held, for example) is unified across T-Server types.
-  Identification of call termination across different switches–Consistency in the Events and Requests associated with an Event Released, or the termination of a call, across T-Server types.
-  After call work state across different switches–Consistency in the Events and Requests associated with “AfterCallWork” across T-Server types.

These make reporting consistent across switches.

**Consistência do modelo de chamada**

A Genesys fornece consistência de modelo de chamada em diferentes plataformas de switch. Os seguintes são unificados pela parte comum do T-Server:

- Evento de estado do agente – o estado do agente (conectado, alertando, retido, por exemplo) é unificado nos tipos de T-Server.
- Identificação de terminação de chamada em diferentes centrais – Consistência nos Eventos e Pedidos associados a um Evento Liberado, ou terminação de uma chamada, entre os tipos de T-Server.
- Estado de trabalho pós-chamada em diferentes switches – Consistência nos Eventos e Solicitações associados ao “AfterCallWork” nos tipos de T-Server.

Isso torna os relatórios consistentes entre os switches.

![image](https://user-images.githubusercontent.com/52088444/159046937-5c660bf5-f0b6-4dee-a070-0c14ddd3423f.png)


**Connection ID (ConnID)**


The T-Server common part also establishes a connection ID (ConnID) for each call. In the example below, the ConnID is shown as it would appear in a log file.

A parte comum do T-Server também estabelece um ID de conexão (ConnID) para cada chamada. No exemplo abaixo, o ConnID é mostrado como apareceria em um arquivo de log.

![image](https://user-images.githubusercontent.com/52088444/159047156-1800844d-5a82-4b3e-9988-3ef9ef666b56.png)

The ConnID is used in Management Layer log events for call traceability. Even if the call is being transferred across different switches and different T-Servers, you can follow the interaction because of the ConnID.

Note: In some interfaces, such as GAX, the ConnID is visible as ‘IID’ (short for ‘Interaction ID’) under Interaction Level log messages’ properties.

O ConnID é usado em eventos de log da camada de gerenciamento para rastreabilidade de chamadas. Mesmo que a chamada esteja sendo transferida entre diferentes switches e diferentes T-Servers, você pode acompanhar a interação por causa do ConnID.

Observação: em algumas interfaces, como GAX, o ConnID é visível como 'IID' (abreviação de 'ID de interação') nas propriedades das mensagens de log do nível de interação.

## 9.9 Interaction Flow Messaging(Mensagens de Fluxo de Interação)

Interaction flow messaging involves events and requests. Events are generated when something happens on the PBX (or with T-Server) such as the ringing of an agent’s phone. Requests are generated when a client application is asking to accomplish a call-handling or related task such as an agent desktop requesting to hang up a call. 

T-Server has standard event and request messaging to communicate with its clients. These standard messages enable developers to integrate custom applications with T-Server. This messaging differs from the messaging that the T-Server and the PBX use. T-Server communicates with the PBX in the language that the CTI link uses. In essence, T-Server serves as a translator between the CTI link and its clients.


O sistema de mensagens do fluxo de interação envolve eventos e solicitações. Os eventos são gerados quando algo acontece no PBX (ou com o T-Server), como o toque do telefone de um agente. As solicitações são geradas quando um aplicativo cliente está solicitando a realização de uma tarefa de tratamento de chamadas ou relacionada, como um desktop de agente solicitando o desligamento de uma chamada.

O T-Server possui mensagens padrão de eventos e solicitações para se comunicar com seus clientes. Essas mensagens padrão permitem que os desenvolvedores integrem aplicativos personalizados com o T-Server. Este sistema de mensagens difere do sistema de mensagens que o T-Server e o PBX usam. O T-Server se comunica com o PBX no idioma que o link CTI usa. Em essência, o T-Server serve como um tradutor entre o link CTI e seus clientes.


Interaction Flow Messaging(Mensagens de fluxo de interação)

The following diagram depicts how the PBX, T-Server, and T-Server clients communicate with each other.

1 - The PBX sends switch messages to T-Server via the CTI link.

2 - T-Server sends event messages to its clients.

3 - T-Server clients send request messages to T-Server.

4 - T-Server sends switch messages to the PBX via the CTI link.



O diagrama a seguir descreve como os clientes PBX, T-Server e T-Server se comunicam entre si.

1 - O PABX envia mensagens de switch ao T-Server através do link CTI.

2 - T-Server envia mensagens de eventos para seus clientes.

3 - Os clientes T-Server enviam mensagens de solicitação ao T-Server.

4 - T-Server envia mensagens de switch para o PBX através do link CTI.

![image](https://user-images.githubusercontent.com/52088444/159047804-99ab2f86-661e-440e-a096-2f36723ea816.png)

SIP Server/T-Server maintains a T-Event structure – also known as the call object – for each interaction between a customer and the contact center. The T-Event structure is comprised of attributes that maintain information for each active call. The T-Event structure is created no matter what medium (phone, email, or web) the customer uses to initiate contact.

- T-Event is a T-Server message used to provide notification of call activity to the appropriate Genesys platform components.
- T-Event is a one-directional event from the T-Server to the Genesys platform components.
- T-Request runs in the opposite direction: It is a message from platform components to the T-Server requesting some action.
- T-Server then responds back with a T-Event.

O SIP Server/T-Server mantém uma estrutura T-Event – também conhecida como objeto de chamada – para cada interação entre um cliente e o contact center. A estrutura T-Event é composta por atributos que mantêm informações para cada chamada ativa. A estrutura do T-Event é criada independentemente do meio (telefone, e-mail ou web) que o cliente usa para iniciar o contato.

- T-Event é uma mensagem T-Server usada para fornecer notificação de atividade de chamada aos componentes apropriados da plataforma Genesys.
- T-Event é um evento unidirecional do T-Server para os componentes da plataforma Genesys.
- T-Request é executado na direção oposta: é uma mensagem dos componentes da plataforma para o T-Server solicitando alguma ação.
- O T-Server então responde com um T-Event.

## 9.10 SIP Server/T-Server as a Messaging Engine(Servidor SIP/T-Server como mecanismo de mensagens)


SIP Server/T-Server controls the delivery and routing of messages between client applications and switches.

SIP Server/T-Server provides a registration mechanism that enables applications to be notified about activity on all DNs that concern their proper operation. Each client asks SIP Server/T‑Server to "register" one or more DNs. SIP Server/T-Server builds an internal table of clients and their DN registrations.

When the switch passes messages to T-Server, each one of which is associated with a DN, T‑Server distributes those messages to its clients according to the table.

T-Server only knows about activity on devices (e.g., DNs) that it is monitoring. T-Server will monitor those DNs configured (and enabled) on a Switch object that the T-Server is associated with. SIP Server will monitor devices registered on SIP Server.

Clients of SIP Server can receive notification about activity on a switch device by registering for that device on SIP Server. For example, a Genesys Desktop can be registered for DN 6001. From then on it will be notified of all activity occurring on DN 6001.

The client must issue RequestRegisterAddress against the DN and receive an EventRegistered response.

O SIP Server/T-Server controla a entrega e o roteamento de mensagens entre aplicativos clientes e switches.

O SIP Server/T-Server fornece um mecanismo de registro que permite que os aplicativos sejam notificados sobre a atividade em todos os DNs que dizem respeito à sua operação adequada. Cada cliente solicita ao SIP Server/T‑Server para "registrar" um ou mais DNs. SIP Server/T-Server cria uma tabela interna de clientes e seus registros de DN.

Quando o switch passa mensagens para o T-Server, cada um associado a um DN, o T‑Server distribui essas mensagens para seus clientes de acordo com a tabela.

O T-Server só sabe sobre a atividade nos dispositivos (por exemplo, DNs) que está monitorando. O T-Server monitorará os DNs configurados (e habilitados) em um objeto Switch ao qual o T-Server está associado. O Servidor SIP monitorará os dispositivos registrados no Servidor SIP.

Os clientes do servidor SIP podem receber notificações sobre a atividade em um dispositivo switch registrando-se para esse dispositivo no servidor SIP. Por exemplo, um Genesys Desktop pode ser registrado para DN 6001. A partir de então, ele será notificado de todas as atividades que ocorrerem no DN 6001.

O cliente deve emitir RequestRegisterAddress no DN e receber uma resposta EventRegistered.

Example 1:

The following image is an excerpt from the ChicagoSIPServer log.

Request messages are typically sent to the T-Server and the names of the messages begin with the word Request.

Event messages are typically sent out by the T-Server and the names of the messages begin with the word Event. Events are sent in response to requests and also to notify of activity.

In this example, Workspace sent a RequestRegisterAddress message to the ChicagoSIPServer. ChicagoSIPServer responded with the message EventRegistered.

AttributeReferenceID can be used to match a request with its corresponding event when looking at a log file.

Example 1:

The following image is an excerpt from the ChicagoSIPServer log.

Request messages are typically sent to the T-Server and the names of the messages begin with the word Request.

Event messages are typically sent out by the T-Server and the names of the messages begin with the word Event. Events are sent in response to requests and also to notify of activity.

In this example, Workspace sent a RequestRegisterAddress message to the ChicagoSIPServer. ChicagoSIPServer responded with the message EventRegistered.

AttributeReferenceID can be used to match a request with its corresponding event when looking at a log file.


Exemplo 1:

A imagem a seguir é um trecho do log ChicagoSIPServer.

As mensagens de solicitação são normalmente enviadas ao T-Server e os nomes das mensagens começam com a palavra Request(solicitação).

As mensagens de evento são normalmente enviadas pelo T-Server e os nomes das mensagens começam com a palavra Event(Evento). Os eventos são enviados em resposta a solicitações e também para notificação de atividade.

Neste exemplo, o Workspace enviou uma mensagem RequestRegisterAddress para o ChicagoSIPServer. ChicagoSIPServer respondeu com a mensagem EventRegistered.

AttributeReferenceID pode ser usado para combinar uma solicitação com seu evento correspondente ao examinar um arquivo de log.

![image](https://user-images.githubusercontent.com/52088444/159049065-5547a52c-4a5f-4d71-b7fe-6faff95994f1.png)

![image](https://user-images.githubusercontent.com/52088444/159049097-93cdcb38-b70a-4427-8c17-498120bae846.png)

Example 2:

The following image is an excerpt from the ChicagoSIPServer log.

After the word “message” is the message name, in this case, it is EventRinging. The attributes sent with the message provide additional details. In a log file, the attributes are very helpful for troubleshooting and finding the desired messages. Let’s consider a few attributes:

-  AttributeThisDN—The DN that this message is primarily about.
- AttributeANI—The customer’s phone number.
- AttributeDNIS—The number the customer dialed.
- AttributeConnID—The ConnectionID for the call associated with the message. This attribute is referenced to find the messages associated with a particular call.

For more information, see the Genesys Events and Models Reference Manual.
Example 2:

The following image is an excerpt from the ChicagoSIPServer log.

After the word “message” is the message name, in this case, it is EventRinging. The attributes sent with the message provide additional details. In a log file, the attributes are very helpful for troubleshooting and finding the desired messages. Let’s consider a few attributes:

- AttributeThisDN—The DN that this message is primarily about.
- AttributeANI—The customer’s phone number.
- AttributeDNIS—The number the customer dialed.
- AttributeConnID—The ConnectionID for the call associated with the message. This attribute is referenced to find the messages associated with a particular call.

For more information, see the Genesys Events and Models Reference Manual.

Exemplo 2:

A imagem a seguir é um trecho do log ChicagoSIPServer.

Após a palavra “mensagem” está o nome da mensagem, neste caso, é EventRinging. Os atributos enviados com a mensagem fornecem detalhes adicionais. Em um arquivo de log, os atributos são muito úteis para solucionar problemas e localizar as mensagens desejadas. Vamos considerar alguns atributos:

- AttributeThisDN — O DN sobre o qual esta mensagem trata principalmente.
- AttributeANI—O número de telefone do cliente.
- AttributeDNIS—O número que o cliente discou.
- AttributeConnID — O ConnectionID para o atendimento associado à mensagem. Esse atributo é referenciado para localizar as mensagens associadas a uma chamada específica.

Para obter mais informações, consulte o Genesys Events and Models Reference Manual.

![image](https://user-images.githubusercontent.com/52088444/159049429-9d1a86ea-61e2-4131-b949-7badef5353fe.png)

## 9.11 Sample Call Flow(Fluxo de Chamada de Amostra)


Although you will often look at log messages in log files when troubleshooting, it can be helpful to see message names in the form of a stick diagram. You will see similar types of diagrams in Genesys Documentation and other courses.

Vertical lines represent software and devices. Their names are along the top. Messages are shown as horizontal lines with the earliest message at the top and the latest message at the bottom. In this example, different colors are used for different messaging: The black solid lines represent the device information, the red dotted lines represent the phone signaling, the green dotted lines represent the Genesys TLibrary Events from T-Server, and the blue dotted lines represent the Genesys TLibrary requests from T-Server.

Embora muitas vezes você observe as mensagens de log em arquivos de log ao solucionar problemas, pode ser útil ver os nomes das mensagens na forma de um diagrama de bastão. Você verá tipos semelhantes de diagramas na Documentação da Genesys e em outros cursos.

As linhas verticais representam software e dispositivos. Seus nomes estão no topo. As mensagens são mostradas como linhas horizontais com a mensagem mais antiga na parte superior e a mensagem mais recente na parte inferior. Neste exemplo, cores diferentes são usadas para mensagens diferentes: as linhas pretas sólidas representam as informações do dispositivo, as linhas pontilhadas vermelhas representam a sinalização telefônica, as linhas pontilhadas verdes representam os eventos Genesys TLibrary do T-Server e as linhas pontilhadas azuis representam as solicitações do Genesys TLibrary do T-Server.

![image](https://user-images.githubusercontent.com/52088444/159049883-828d541c-44b5-48f0-8b4e-c15160bee486.png)
![image](https://user-images.githubusercontent.com/52088444/159050738-fa2f102d-90aa-48ea-946c-9dec10a3628f.png)
![image](https://user-images.githubusercontent.com/52088444/159050787-e46b3d8f-335d-4573-a4a5-315e61dbc7ec.png)
![image](https://user-images.githubusercontent.com/52088444/159050830-b2579f02-10d9-424d-be63-f5104f0d9325.png)




he Call Flow in the diagram above occurs as follows:
- ringing—Customer dials in and the CustomerPhone connects to the Agent phone.
- phone ringing—Phone ringing notification is sent from the Switch to T-Server.
- EventRinging—Based on that and the extension ringing on the Agent’s phone, T-Server is going to notify Workspace which is registered for that DN with the message of EventRinging.
- RequestAnswerCall—The agent accepts the call and the request to answer the call is sent from Workspace to T-Server.
- Connection—Switch then makes the connection from the CustomerPhone to the Agent Phone.
- Connection made—T-Server receives notification that the connection has been made successfully.
- EventEstablished—T-Server sends the TLibrary event ‘EventEstablished’ to Workspace. The customer is now talking to the Agent and the Agent is looking at all the information about the call in Workspace.
- RequestReleaseCall—When the call is done and the Agent disconnects the call, the TLibrary Request "RequestReleaseCall" is sent from Workspace to T-Server.
- Release command—T-Server sends the command to Switch to release the call.
- Connection released—The notification is sent from Switch to T-Server that the connection has been released.
- EventReleased—T-Server sends the TLibrary event "EventReleased" to Workspace.
- Connected Ended—The connection is actually ended.

There are typically more messages for a call than just the ones shown in the diagram above. Other messages can include:
- EventCallCreated
- EventCallPartyAdded
- EventCallPartyState
- RequestUpdateUserData
- EventAttachedDataChanged
- EventCallDataChanged
- EventCallPartyDeleted
- EventCallDeleted

O fluxo de chamadas no diagrama acima ocorre da seguinte forma:
- tocando(ringing) — o cliente disca e o CustomerPhone se conecta ao telefone do agente.
- toque de telefone (phone ringing) —A notificação de toque de telefone é enviada do Switch para o T-Server.
- EventRinging —Com base nisso e no ramal que está tocando no telefone do Agente, o T-Server notificará o Workspace que está registrado para esse DN com a mensagem EventRinging.
- RequestAnswerCall — O agente aceita a chamada e a solicitação para atender a chamada é enviada do Workspace para o T-Server.
- Conexão—O switch então faz a conexão do CustomerPhone ao telefone do agente.
- Conexão feita—T-Server recebe a notificação de que a conexão foi feita com sucesso.
- EventEstablished—T-Server envia o evento TLibrary 'EventEstablished' para o Workspace. O cliente agora está conversando com o Agente e o Agente está verificando todas as informações sobre a chamada no Workspace.
- RequestReleaseCall—Quando a chamada é feita e o Agente desconecta a chamada, a Solicitação TLibrary "RequestReleaseCall" é enviada do Workspace para o T-Server.
- Solte o comando — o T-Server envia o comando ao Comutador para liberar a chamada.
- Conexão liberada—A notificação é enviada do Switch ao T-Server que a conexão foi liberada.
- EventReleased—T-Server envia o evento TLibrary "EventReleased" para o Workspace.
- Connected Ended—A conexão foi realmente encerrada.

Normalmente, há mais mensagens para uma chamada do que apenas as mostradas no diagrama acima. Outras mensagens podem incluir:
- EventCallCreated
- EventCallPartyAdicionado
- EventCallPartyState
- RequestUpdateUserData
- EventAttachedDataChanged
- EventCallDataChanged
- EventCallPartyDeleted
- EventCallDeleted

## 9.12 Inbound and Agent Interaction in Action(Interação de entrada e agente em ação)


The Beyond System Administrator team needs to understand the TLib messages that are associated with a typical interaction within their business including attributes. The Interaction arrives onto a route point and then a script is executed and a target is assigned. In this case, the agent is the target. 

The administrator also requires knowledge on TLib messages which are not related to interactions such as agents logged in, agent status, and change of reason codes. Let's now apply an example of the above actions and save them onto a file for later use in Lab 7.

A equipe do Beyond System Administrator precisa entender as mensagens TLib que estão associadas a uma interação típica dentro de seus negócios, incluindo atributos. A Interação chega a um ponto de rota e, em seguida, um script é executado e um destino é atribuído. Nesse caso, o agente é o alvo.

O administrador também requer conhecimento sobre mensagens TLib que não estão relacionadas a interações, como agentes conectados, status do agente e alteração de códigos de motivo. Vamos agora aplicar um exemplo das ações acima e salvá-las em um arquivo para uso posterior no Laboratório 7.

## 9.13 Learning Summary

Now that you have completed this chapter, you should be able to do the following: 

1 - Describe the components of the Media Layer.

2 - Describe the functions of each component.

3 - Investigate log messages for a voice interaction.

4 - Describe a high level call flow.

Agora que você concluiu este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descreva os componentes da camada de mídia.

2 - Descreva as funções de cada componente.

3 - Investigue as mensagens de log para uma interação de voz.

4 - Descreva um fluxo de chamadas de alto nível.