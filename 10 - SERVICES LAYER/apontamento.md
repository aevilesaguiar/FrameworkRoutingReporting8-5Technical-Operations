## 10.1 Objetivos de aprendizagem

Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descreva o(s) componente(s) da Camada de Serviços.

2 - Descreva as funções de cada componente.

3 - Descreva as mensagens de log do Stat Server.

## 10.2 Services Layer

The major functions of the Services Layer are a compilation of statistics and knowing the current status of configuration objects.

The Services Layer provides conversion of events-related messages to manage a single interaction into statistical data, which is then used for interaction processing and contact center reporting.

As principais funções da Camada de Serviços são a compilação de estatísticas e o conhecimento do status atual dos objetos de configuração.

A camada de serviços fornece a conversão de mensagens relacionadas a eventos para gerenciar uma única interação em dados estatísticos, que são então usados para processamento de interação e relatórios do contact center.

![image](https://user-images.githubusercontent.com/52088444/159052917-1df740bf-dd30-4c25-82e4-a9a3c80fd423.png)

The component is known as Stat Server which tracks real-time stats of interaction management resources and collects statistics about contact center performance. 

Genesys solutions use statistical data to more intelligently manage real-time interactions (Routing). Through Genesys Reporting, you can use the data to generate real-time contact center reports.


## 10.3 Framework Architecture: Services Layer

The following image outlines the five different layers of the Framework—the Services Layer is shown in detail along with its connections to the Media and Configuration Layers. The Services Layer is made up of the Stat Server.

A imagem a seguir descreve as cinco camadas diferentes da Estrutura — a Camada de Serviços é mostrada em detalhes junto com suas conexões com as Camadas de Mídia e Configuração. A Camada de Serviços é composta pelo Servidor Stat.

![image](https://user-images.githubusercontent.com/52088444/159054122-78b81a32-0c43-46df-80db-e13f2e48f11a.png)


## 10.4 Stat Server

Stat Server is a Genesys application that tracks information about customer interaction in Contact Centers. Stat Server also converts the data accumulated for Directory Numbers (DNs), agents, Agent Groups, and non-telephony-specific object types into statistically useful information, and passes these calculations to other software applications that request data.

For example, Stat Server sends data to Universal Routing Server (URS) to inform the URS about agent availability.

Stat Server provides the contact center managers with a wide range of information, allowing organizations to maximize the efficiency and flexibility of customer interaction

Monitoring Contact Centers

Stat Server tracks what is happening at any DN - whether it belongs to an agent station, an individual agent who moves between stations, an interactive voice response (IVR), or a point in a private branch exchange (PBX) used for queuing or routing.

For example, for each DN, Stat Server tracks DN activity, call activity on a DN, and other relevant derived states, such as how long a phone is not in use, how long a call is on hold, how long it takes to dial a call, how long a DN is busy with an inbound call, and so forth.

From the gathered information, Stat Server performs a variety of statistical calculations to provide its clients, such as:
- Duration in current state
- Total number of times each state occurs
- Percentage of time for each state
- Average time for each state

These statistics are defined in the Stat Server application template and are known as statistical types.

O Stat Server é um aplicativo da Genesys que rastreia informações sobre a interação do cliente em Contact Centers. O Stat Server também converte os dados acumulados para Números de Diretório (DNs), agentes, Grupos de Agentes e tipos de objetos não específicos de telefonia em informações estatisticamente úteis e passa esses cálculos para outros aplicativos de software que solicitam dados.

Por exemplo, o Stat Server envia dados ao Universal Routing Server (URS) para informar o URS sobre a disponibilidade do agente.

O Stat Server fornece aos gerentes de contact center uma ampla gama de informações, permitindo que as organizações maximizem a eficiência e a flexibilidade da interação com o cliente

Monitoramento de Contact Centers

O Stat Server rastreia o que está acontecendo em qualquer DN - se pertence a uma estação de agente, um agente individual que se move entre estações, uma resposta de voz interativa (IVR) ou um ponto em uma troca de ramal privada (PBX) usada para enfileiramento ou roteamento .

Por exemplo, para cada DN, o Stat Server rastreia a atividade do DN, a atividade da chamada em um DN e outros estados derivados relevantes, como quanto tempo um telefone não está em uso, quanto tempo uma chamada está em espera, quanto tempo leva para discar uma chamada, por quanto tempo um DN está ocupado com uma chamada de entrada e assim por diante.

A partir das informações coletadas, o Stat Server realiza diversos cálculos estatísticos para fornecer aos seus clientes, tais como:
- Duração no estado atual
- Número total de vezes que cada estado ocorre
- Porcentagem de tempo para cada estado
- Tempo médio para cada estado

Essas estatísticas são definidas no modelo de aplicativo Stat Server e são conhecidas como tipos estatísticos.

![image](https://user-images.githubusercontent.com/52088444/159055722-e835a262-38be-4d18-b56b-23172a14286f.png)

## 10.5 Services Layer Startup(Inicialização da camada de serviços)


**Starting the Stat Server**

Stat Server is started automatically using Services or daemon processes, or manually from an interface such as Genesys Administrator or GAX, a command line, an application shortcut, or a script. It connects to the Configuration Server to obtain configuration data. After connecting to the Configuration Server, Stat Server connects to other applications.

It connects to T-Server in order to receive messages from and send messages to T-Server and other Genesys components. Stat Server may also connect to the Message Server so that it can send log events to the centralized log database.

**Stat Server Registration**

Stat Server must communicate with T-Server to register the DNs it wishes to receive messages about. Since Stat Server tracks the status of all configured contact center objects (DNs, Places, Agents, and Groups), it registers every configured DN with T-Server. Stat Server performs this registration on startup (or when a new DN is created), and it receives all messages concerning these DNs.

**Iniciando o servidor de estatísticas**

O Stat Server é iniciado automaticamente usando Services ou processos daemon, ou manualmente a partir de uma interface como Genesys Administrator ou GAX, uma linha de comando, um atalho de aplicativo ou um script. Ele se conecta ao Servidor de Configuração para obter dados de configuração. Após conectar-se ao Configuration Server, o Stat Server se conecta a outros aplicativos.

Ele se conecta ao T-Server para receber e enviar mensagens para o T-Server e outros componentes Genesys. O Stat Server também pode se conectar ao Message Server para que possa enviar eventos de log para o banco de dados de log centralizado.

Registro do servidor de estatísticas

O Stat Server deve se comunicar com o T-Server para registrar os DNs sobre os quais deseja receber mensagens. Como o Stat Server rastreia o status de todos os objetos configurados do contact center (DNs, Locais, Agentes e Grupos), ele registra cada DN configurado com o T-Server. O Stat Server realiza esse registro na inicialização (ou quando um novo DN é criado) e recebe todas as mensagens referentes a esses DNs.

![image](https://user-images.githubusercontent.com/52088444/159057338-1c8fbd3d-f111-49a0-bf3c-09c35c76c37a.png)

## 10.6 Stat Server and Resource Information(Servidor de Estatísticas e Informações de Recursos)


Routing and Reporting rely on Stat Server for status and statistics.

It is helpful to understand at least the basics in the Stat Server log file so that you can confirm what Stat Server understands to be the “status of an agent”. If an agent is not being routed to, or if statistics are not being generated on that agent, check that the information belonging to that agent is available and is correct in the Stat Server log file. 

In the example below, you can see:
-  An agent logs into Workspace and Workspace communicates this to T-Server.
- T-Server notifies Stat Server that the Agent has logged in.
- When a call comes in on the agent’s extension, T-Server notifies Workspace and Stat Server that the call has arrived on the agent’s extension.
- Stat Server keeps the Routing and Reporting components up to date with the status and statistics.

Roteamento e Relatórios dependem do Stat Server para status e estatísticas.

É útil entender pelo menos o básico no arquivo de log do Stat Server para que você possa confirmar o que o Stat Server entende ser o “status de um agente”. Se um agente não estiver sendo roteado ou se as estatísticas não estiverem sendo geradas nesse agente, verifique se as informações pertencentes a esse agente estão disponíveis e estão corretas no arquivo de log do Stat Server.

No exemplo abaixo, você pode ver:
- Um agente efetua login no Workspace e o Workspace comunica isso ao T-Server.
- O T-Server notifica o Stat Server que o Agente está logado.
- Quando uma chamada chega no ramal do agente, o T-Server notifica o Workspace e o Stat Server que a chamada chegou no ramal do agente.
- O Stat Server mantém os componentes de Roteamento e Relatórios atualizados com o status e as estatísticas.

![image](https://user-images.githubusercontent.com/52088444/159057863-1b592fa7-a37f-4b68-9390-5246974e75d9.png)

It also means if you run into issues with Routing or Reporting, you will need to refer to the Stat Server log for troubleshooting.

Isso também significa que se você tiver problemas com Roteamento ou Relatório, você precisará consultar o log do Stat Server para solução de problemas.

## 10.7 Stat Server Log Categories

When using the Stat Server log file for troubleshooting, you need to be familiar with the contents of the log file. In addition to the event and request messages, you also need to know about log categories. The following are specifically categorized Debug Level log messages:

- Init—Start-up initialization and configuration changes.
- Client—Clients of the Stat Server. Events and Requests sent to clients.
- Server—The server to which Stat Server connects. Messages received from server.
- Status—State changes for objects.
- ction—Statistics: Actions/Events

The table that follows shows an example of these log categories in the Stat Server log file.
When using the Stat Server log file for troubleshooting, you need to be familiar with the contents of the log file. In addition to the event and request messages, you also need to know about log categories. The following are specifically categorized Debug Level log messages:

- Init—Start-up initialization and configuration changes.
- Client—Clients of the Stat Server. Events and Requests sent to clients.
- Server—The server to which Stat Server connects. Messages received from server.
- Status—State changes for objects.
- ction—Statistics: Actions/Events

The table that follows shows an example of these log categories in the Stat Server log file.

Ao usar o arquivo de log do Stat Server para solução de problemas, você precisa estar familiarizado com o conteúdo do arquivo de log. Além das mensagens de evento e solicitação, você também precisa conhecer as categorias de log. A seguir estão mensagens de log de nível de depuração especificamente categorizadas:

- Init—Inicialização de inicialização e alterações de configuração.
- Cliente—Clientes do Servidor Stat. Eventos e Solicitações enviadas aos clientes.
- Servidor—O servidor ao qual o Stat Server se conecta. Mensagens recebidas do servidor.
- Status—Mudanças de estado para objetos.
- ção—Estatísticas: Ações/Eventos

A tabela a seguir mostra um exemplo dessas categorias de log no arquivo de log do Stat Server.

![image](https://user-images.githubusercontent.com/52088444/159058234-675050ed-9996-45d3-b3b5-3fb13b6cd4b6.png)

The full list of categories can be found in the Stat Server documentation.

A lista completa de categorias pode ser encontrada na documentação do Stat Server.

Note: Check the value of the debug-level option, as this determines what you will see in the log file. The default value is Init,Client,Server,Action,Status. If the production debug-level option is set to all, you could overload your system.


Nota: Verifique o valor da opção debug-level, pois isso determina o que você verá no arquivo de log. O valor padrão é Inicialização, Cliente, Servidor, Ação, Status. Se a opção de nível de depuração de produção estiver definida como tudo, você poderá sobrecarregar seu sistema.


## 10.8 Capacity Snapshot(Captura de tela de capacidade)

Agents can have more than one action combined together, and only one status to determine whether an agent would be available for routing. The result is visible as a Capacity Snapshot which indicates routability. (routable= ‘0’ indicates the agent is not routable and routable= ‘1’ indicates the agent is routable) 

Once an agent receives an interaction, a new snapshot appears in the log, displaying how this interaction received affected the agent’s capability of receiving other interactions. The Capacity Snapshot will display the number and type of interactions that a particular agent can receive (you will see one row per media type the agent is logged in).


Os agentes podem ter mais de uma ação combinada e apenas um status para determinar se um agente estaria disponível para roteamento. O resultado é visível como um instantâneo de capacidade que indica a capacidade de roteamento. (roteável= '0' indica que o agente não é roteável e roteável= '1' indica que o agente é roteável)

Assim que um agente recebe uma interação, um novo instantâneo aparece no log, mostrando como essa interação recebida afetou a capacidade do agente de receber outras interações. O Capacity Snapshot exibirá o número e o tipo de interações que um determinado agente pode receber (você verá uma linha por tipo de mídia em que o agente está conectado).

![image](https://user-images.githubusercontent.com/52088444/159058710-5dc8dc29-2f99-4a17-9cff-cf722980a899.png)


## 10.9 Learning Summary

Now that you have completed this chapter, you should be able to do the following: 

1 - Describe the component(s) of Services Layer.

2 - Describe the functions of each component.

3 - Describe Stat Server log messages.

Agora que você concluiu este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descreva o(s) componente(s) da Camada de Serviços.

2 - Descreva as funções de cada componente.

3 - Descreva as mensagens de log do Stat Server.

## 10.10 Learning Check

Question
01/03
Stat Server must communicate with T-Server to register the DNs it wishes to receive messages about. It registers every configured DN with T-Server.( O Stat Server deve se comunicar com o T-Server para registrar os DNs sobre os quais deseja receber mensagens. Ele registra cada DN configurado com o T-Server. )

True( verdadeiro)

False

Question
02/03
If an agent is not being routed to, or if statistics are not being generated on that agent, you should check Workspace.(Se um agente não estiver sendo roteado ou se as estatísticas não estiverem sendo geradas nesse agente, você deve verificar o Workspace.)

True

False(FALSE - Se um agente não estiver sendo roteado ou se as estatísticas não estiverem sendo geradas nesse agente, você deve verificar o arquivo de log do Stat Server.)

Question
03/03
A capacity snapshot indicates routability.

True(verdadeiro)

False

