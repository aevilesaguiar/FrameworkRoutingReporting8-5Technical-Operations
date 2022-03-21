## 12.1 Learning Objectives

After completing this chapter, you should be able to do the following:

1 - Describe basic Composer concepts.

2 - Generate code for a routing application.

3 - Define SCXML.

4 - Publish a routing application to the Configuration Layer.

5 - Load a routing application on a DN.

6 - Explain deploying a routing application to production.

7 - Import a Composer routing application.

Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descrever os conceitos básicos do Composer.

2 - Gerar código para uma aplicação de roteamento.

3 - Defina SCXML.

4 - Publique um aplicativo de roteamento na Camada de Configuração.

5 - Carregue um aplicativo de roteamento em um DN.

6 - Explicar a implantação de um aplicativo de roteamento para produção.

7 - Importe um aplicativo de roteamento Composer.

## 12.2 Composer


The following diagram shows some examples of what can be done with Composer and Orchestration:

O diagrama a seguir mostra alguns exemplos do que pode ser feito com o Composer e o Orchestration:

![image](https://user-images.githubusercontent.com/52088444/159290718-7232dc2f-a7e4-4bd8-bc57-da66c1131033.png)

Here, we will focus on routing, not voice applications for Genesys Voice Portal (GVP). 

Of course, more of the capabilities are covered in the training for routing developers. Nonetheless, some knowledge is valuable for operations as well. 

Composer is an Eclipse-based development environment. It supports the development of routing applications (SCXML) and also the development of voice applications
(VXML) for the GVP.

Aqui, vamos nos concentrar no roteamento, não nos aplicativos de voz para o Genesys Voice Portal (GVP).

É claro que mais recursos são abordados no treinamento para desenvolvedores de roteamento. No entanto, algum conhecimento também é valioso para as operações.

O Composer é um ambiente de desenvolvimento baseado em Eclipse. Suporta o desenvolvimento de aplicativos de roteamento (SCXML) e também o desenvolvimento de aplicativos de voz (VXML) 
para o GVP.

## Example of Advanced Orchestration(Exemplo de orquestração avançada)

![image](https://user-images.githubusercontent.com/52088444/159291106-cbb5d567-442e-4dbe-a963-1a55e11cf27a.png)

![image](https://user-images.githubusercontent.com/52088444/159292767-dfdc4d61-9f67-42b9-a31b-d40bd7636759.png)

Orchestration and SCXML can provide many benefits beyond traditional Enterprise Routing. One benefit of using Composer is that both GVP callflows and ORS workflows can be built into the same project and interactions can seamlessly flow between them. In addition, SCXML allows for parallel processing so different subroutines can function at the same time for one interaction. The screenshot above uses both of those ideas. 

This application uses three threads to do three separate tasks. The first thread is the GVP application for interacting with the customer to gather the ZIP code to look up the weather. 

The second thread is the Web Service Application to go to the Internet to look up the weather for the ZIP code provided in the first thread. 

The third thread provides a counter to track loops of the application.

A orquestração e o SCXML podem fornecer muitos benefícios além do roteamento corporativo tradicional. Um benefício de usar o Composer é que tanto os fluxos de chamadas GVP quanto os fluxos de trabalho ORS podem ser incorporados ao mesmo projeto e as interações podem fluir perfeitamente entre eles. Além disso, o SCXML permite o processamento paralelo para que diferentes sub-rotinas possam funcionar ao mesmo tempo para uma interação. A captura de tela acima usa essas duas ideias.

Este aplicativo usa três threads para realizar três tarefas separadas. O primeiro segmento é o aplicativo GVP para interagir com o cliente para coletar o CEP para consultar o clima.

O segundo encadeamento é o Aplicativo de Serviço da Web para acessar a Internet para procurar o clima para o CEP fornecido no primeiro encadeamento.

A terceira thread fornece um contador para rastrear os loops do aplicativo.

## 12.3  Composer User Interface

![image](https://user-images.githubusercontent.com/52088444/159293550-b703ead8-b4bd-464f-8c80-78a57f823e24.png)

The Composer User Interface elements include:

- Canvas is where you create flows by placing and connecting blocks.
- The Palette contains blocks grouped in various categories --- Drag and drop blocks from the palette to the canvas to build the diagram.
- A Block is the fundamental element of a routing workflow diagram.
- - Block Properties allows you to change or set the properties corresponding to a block.
- For large workflows, the Outline View allows you to navigate to the portion of the workflow to view in the main canvas.
- Project Explorer shows all Project files in one tree. In general, a Project consists of a predefined, structured set of files and folders that contain all resources for the routing application.
- In Eclipse, the Perspective is a visual container for a set of views and editors (parts).- 

Os elementos da interface do usuário do Composer incluem:

- Canvas é onde você cria fluxos colocando e conectando blocos.
- A Paleta contém blocos agrupados em várias categorias --- Arraste e solte blocos da paleta para a tela para construir o diagrama.
- Um bloco é o elemento fundamental de um diagrama de fluxo de trabalho de roteamento.
- - Propriedades do bloco permite alterar ou definir as propriedades correspondentes a um bloco.
- Para fluxos de trabalho grandes, a Exibição de Esquema permite que você navegue até a parte do fluxo de trabalho para visualizar na tela principal.
- Project Explorer mostra todos os arquivos do projeto em uma árvore. Em geral, um projeto consiste em um conjunto pré-definido e estruturado de arquivos e pastas que contêm todos os recursos para o aplicativo de roteamento.
- No Eclipse, a Perspectiva é um contêiner visual para um conjunto de visualizações e editores (partes).-

**Views**

Uma View é um componente visual dentro do Workbench.

- Usado para navegar em uma lista ou hierarquia de informações. Por exemplo, o Explorador de Projetos.

![image](https://user-images.githubusercontent.com/52088444/159293952-879a5743-ac50-4bb6-a005-2571cb119e46.png)

- Used to display properties for the active editor. For example, the Building Blocks Properties.
- Usado para exibir propriedades para o editor ativo. Por exemplo, as Propriedades dos Blocos de Construção.

![image](https://user-images.githubusercontent.com/52088444/159294071-7a90ed7d-5c44-430c-841a-7e5b60c686c4.png)

**Workbench and Perspectives**

**Workbench:**

- The overall workplace that you will use for building your applications.
- O local de trabalho geral que você usará para criar seus aplicativos.

Perspective:

- Task oriented layouts for organizing the views and windows in your workbench.
- Default perspective is called Composer.

- Layouts orientados a tarefas para organizar as visualizações e janelas em seu workbench.
- A perspectiva padrão é chamada Composer.

![image](https://user-images.githubusercontent.com/52088444/159328081-ff5dbd1c-3873-4bfe-aa3c-5322d6d27a84.png)

The Composer Workbench is the overall workplace that you will use for building your applications. The workbench is a collection of windows. Each window contains a menu bar, a toolbar, a shortcut bar, and one or more perspectives. By default, when you enter the workbench for the first time, you will be taken inside the Composer Perspective. Perspectives are arrangements of different sections of the GUI in a manner that facilitates easy use of a particular feature. 

A perspective is like a page within a book. It exists within a window along with any number of other perspectives and, like a page within a book, only one perspective is visible at any time.
The Composer Perspective includes four default views:

-Project Explorer
-Outline
-History
-Interaction Process Diagram and Workflow Editors with the Palettes

O Composer Workbench é o local de trabalho geral que você usará para construir seus aplicativos. O Workbench é uma coleção de janelas. Cada janela contém uma barra de menus, uma barra de ferramentas, uma barra de atalhos e uma ou mais perspectivas. Por padrão, ao entrar no workbench pela primeira vez, você será levado para dentro da Composer Perspective. Perspectivas são arranjos de diferentes seções da GUI de uma maneira que facilita o uso fácil de um recurso específico.

Uma perspectiva é como uma página dentro de um livro. Ela existe dentro de uma janela junto com várias outras perspectivas e, como uma página dentro de um livro, apenas uma perspectiva é visível a qualquer momento.
A Perspectiva do Compositor inclui quatro visualizações padrão:

- Explorador de Projetos
- Contorno
- História
- Diagrama de processo de interação e editores de fluxo de trabalho com as paletas

Best Practice: Restoring a Perspective

Restoring a perspective's layout:

Rearranging and closing the views in a perspective can sometimes render it unrecognizable and hard to work with.

To return it to a familiar state, select: Window > Reset Perspective or right-click the 
Perspective > Reset


**Best Practice: Restoring a Perspective**

Restoring a perspective's layout:

Rearranging and closing the views in a perspective can sometimes render it unrecognizable and hard to work with.

To return it to a familiar state, select: Window > Reset Perspective or right-click the 
Perspective > Reset

![image](https://user-images.githubusercontent.com/52088444/159328841-a48d9597-ddcc-4001-9c36-ffb891897e3a.png)

## 12.4 Routing Application Process Overview

![image](https://user-images.githubusercontent.com/52088444/159328933-c06e2a74-0de8-4a78-90e7-35ca3938354b.png)


**Building a Routing Application**

1 - Create a Composer Project—The first step in building a routing application is to create a Java or .NET project.

2 - Develop Routing Application—This will include an IPD and a workflow developed within a Composer project. A workflow is a collection of blocks that route an interaction to a target. At a minimum, you need an Entry, Target, and Exit blocks. The IPD functions as the starting routing application (SCXML) page. It must reference the workflow. During runtime, this results in using the same session across the entire interaction process.

3 - Validate—Next, you validate the routing application. This will identify any errors or determine that the application is valid.

4 - Generate SCXML Code—Orchestration Server contains an SCXML interpreter. As a result, the blocks need to be turned into SCXML code. Use the Generate Code button to create the required code.

5 - Publish Interaction Process Diagram (IPD) to Configuration Server—For each routing application, the IPD needs to be published to the Configuration Server. This creates an Enhanced Routing Script Object, in other words, an Orchestration Routing Application where a uniform resource identifier (URI) is defined and DN’s are associated.

6 - Load the routing application onto route point(s)—The routing application needs to be associated with the desired route point(s). This is done with the User Interaction Layer.

7 - Test & Debug the application—Use a softphone and agent desktop, execute the application, and review the Orchestration Server and Universal Routing Server logs.

Many of the steps will be the responsibility of the routing developer. Typical responsibilities for technical operations will be steps 5 and 6: Publishing to the configuration server and loading the application onto a routing point.

1 - Criar um projeto do Composer—A primeira etapa na construção de um aplicativo de roteamento é criar um projeto Java ou .NET.

2 - Desenvolver Aplicativo de Roteamento—Isso incluirá um IPD e um fluxo de trabalho desenvolvido dentro de um projeto do Composer. Um fluxo de trabalho é uma coleção de blocos que roteiam uma interação para um destino. No mínimo, você precisa de blocos de entrada, destino e saída. O IPD funciona como a página do aplicativo de roteamento inicial (SCXML). Ele deve fazer referência ao fluxo de trabalho. Durante o tempo de execução, isso resulta no uso da mesma sessão em todo o processo de interação.

3 - Validar—Em seguida, você valida o aplicativo de roteamento. Isso identificará quaisquer erros ou determinará que o aplicativo é válido.

4 - Gerar Código SCXML—O Servidor de Orquestração contém um interpretador SCXML. Como resultado, os blocos precisam ser transformados em código SCXML. Use o botão Gerar Código para criar o código necessário.

5 - Publicar diagrama de processo de interação (IPD) no servidor de configuração — Para cada aplicativo de roteamento, o IPD precisa ser publicado no servidor de configuração. Isso cria um Objeto de Script de Roteamento Aprimorado, em outras palavras, um Aplicativo de Roteamento de Orquestração onde um identificador de recurso uniforme (URI) é definido e os DNs são associados.

6 - Carregar o aplicativo de roteamento no(s) ponto(s) de rota—O aplicativo de roteamento precisa estar associado ao(s) ponto(s) de rota desejado(s). Isso é feito com a camada de interação do usuário.

7 - Teste e depure o aplicativo—Use um softphone e desktop de agente, execute o aplicativo e revise os logs do Orchestration Server e do Universal Routing Server.

Muitas das etapas serão de responsabilidade do desenvolvedor de roteamento. As responsabilidades típicas para operações técnicas serão as etapas 5 e 6: Publicar no servidor de configuração e carregar o aplicativo em um ponto de roteamento.

## 12.5 Projects (1 of 3)

![image](https://user-images.githubusercontent.com/52088444/159330308-0c074cee-1d09-47cf-b438-a9b54d32f4a9.png)

In the example shown, there are three projects: Bankers, OperationalParameters, and RouteToChicago. All three are Java projects.

No exemplo mostrado, existem três projetos: Bankers, OperationalParameters e RouteToChicago. Todos os três são projetos Java.

**Workspace and Projects**

When you first enter Composer, you will be prompted for the folder location of your Composer Workspace. That is where your projects will be stored and the contents which will be shown in the Project Explorer.

Ao entrar no Composer pela primeira vez, você será solicitado a informar o local da pasta do seu espaço de trabalho do Composer. É onde seus projetos serão armazenados e o conteúdo que será mostrado no Project Explorer.

![image](https://user-images.githubusercontent.com/52088444/159330760-03d4bb6d-cbac-42e6-8535-517b26706688.png)

Within Composer, the term workspace refers to a location (folder) for your Projects and files in addition to any special folders that Eclipse needs to maintain for its internal bookkeeping. The dialog box that appears when you first start Composer gives the option of changing the workspace to a different location. New Projects created in Composer will be created under this workspace as subfolders. 

No Composer, o termo workspace refere-se a um local (pasta) para seus Projetos e arquivos, além de quaisquer pastas especiais que o Eclipse precisa manter para sua contabilidade interna. A caixa de diálogo que aparece quando você inicia o Composer pela primeira vez oferece a opção de alterar a área de trabalho para um local diferente. Novos projetos criados no Composer serão criados nesta área de trabalho como subpastas.

Projects are as follows:

- Containers for organizing the resources that relate to a specific area.
- Organized into files and folders.
- New Projects created in Composer will be created under the workspace as subfolders.
- Projects built with earlier versions of Composer can be updated by right-clicking on the Project and choosing Update Project.
Projects are as follows:

- Containers for organizing the resources that relate to a specific area.
- Organized into files and folders.
- New Projects created in Composer will be created under the workspace as subfolders.
- Projects built with earlier versions of Composer can be updated by right-clicking on the Project and choosing Update Project.


Os projetos são os seguintes:

- Containers para organizar os recursos que dizem respeito a uma área específica.
- Organizado em arquivos e pastas.
- Novos projetos criados no Composer serão criados na área de trabalho como subpastas.
- Projetos construídos com versões anteriores do Composer podem ser atualizados clicando com o botão direito do mouse no Projeto e escolhendo Atualizar Projeto.

Workspace and projects can be accessed from the following:


- Project Explorer in Composer
- File system

Best Practice Tip: If you want to make changes to the workspace, always use the Project Explorer.


O espaço de trabalho e os projetos podem ser acessados a partir do seguinte:

- Explorador de Projetos no Composer
- Sistema de arquivo

Dica de prática recomendada: Se você quiser fazer alterações no workspace, sempre use o Project Explorer.

![image](https://user-images.githubusercontent.com/52088444/159331350-42f5c19e-14fb-4856-b4e8-49ba3f333ace.png)

## 12.6 Projects (2 of 3)

![image](https://user-images.githubusercontent.com/52088444/159331416-b3664cd5-2b30-4b95-ae50-4e79454dc249.png)

Composer offers two different types of Projects:

Java Project
- For routing applications which will be deployed on Apache, JBoss, and IBM WebSphere application servers.
- Composer ships with a bundled Tomcat and it is used as the web/application server for Java Composer Projects during the development and testing phase.

.Net Project
- For routing applications which will be deployed on MS Internet Information Services (IIS).
- Composer allows you to define an IIS instance which should be used as the test server.

O Composer oferece dois tipos diferentes de projetos:

Projeto Java
- Para aplicativos de roteamento que serão implementados em servidores de aplicativos Apache, JBoss e IBM WebSphere.
- O Composer vem com um Tomcat empacotado e é usado como servidor web/aplicativo para projetos Java Composer durante a fase de desenvolvimento e teste.

Projeto .Net
- Para aplicativos de roteamento que serão implantados no MS Internet Information Services (IIS).
- O Composer permite definir uma instância do IIS que deve ser usada como servidor de teste.

Folders

Common routing project folders, both Java and .NET include:
- Callflows—Folder for storing all the GVP callflow diagrams (.callflow files) as Composer allows you to create integrated Voice and Route Projects.
- db—Database connection properties and .sql files are stored here.
- include—Composer-provided standard include files used by Backend logic blocks.
- Interaction Processes—Folder for storing all the interaction process diagrams (.ixnprocess files).
- Resources—Folder for the audio and grammar resources. Used only for VXML voice applications.
- Workflows—Folder for storing all the workflow diagrams (.workflow files).
- Scripts—Folder for user-written ECMAScript.
- src—Folder for custom code such as backend logic pages written by the user.
- src-gen—Folder for the code generated SCXML or VXML files. This folder is also used to store any hand-coded VXML or SCXML files that may be part of a Project.
- lib (only in Java Projects)—For external dependency libraries such as JAR files
- META-INF (only in Java Projects)—For Java meta-data files.
- App_Code (only in .NET Projects)—Includes files with C# classes (.cs).
- bin (only in .NET Projects)—Any libraries used in a .NET Composer project.

As pastas comuns do projeto de roteamento, tanto Java quanto .NET, incluem:
- Callflows—Pasta para armazenar todos os diagramas de fluxo de chamadas GVP (arquivos .callflow) já que o Composer permite que você crie Projetos de Voz e Rota integrados.
- db—As propriedades de conexão do banco de dados e os arquivos .sql são armazenados aqui.
- include—Arquivos de inclusão padrão fornecidos pelo Composer usados ​​por blocos lógicos de back-end.
- Processos de Interação—Pasta para armazenar todos os diagramas de processos de interação (arquivos .ixnprocess).
- Recursos—Pasta para os recursos de áudio e gramática. Usado apenas para aplicativos de voz VXML.
- Workflows—Pasta para armazenar todos os diagramas de workflow (arquivos .workflow).
- Scripts—Pasta para ECMAScript escrito pelo usuário.
- src—Pasta para código personalizado, como páginas de lógica de backend escritas pelo usuário.
- src-gen—Pasta para os arquivos SCXML ou VXML gerados por código. Essa pasta também é usada para armazenar qualquer arquivo VXML ou SCXML codificado à mão que possa fazer parte de um projeto.
- lib (somente em projetos Java)—Para bibliotecas de dependência externa, como arquivos JAR
- META-INF (somente em Projetos Java)—Para arquivos de metadados Java.
- App_Code (somente em projetos .NET)—Inclui arquivos com classes C# (.cs).
- bin (somente em projetos .NET)—Quaisquer bibliotecas usadas em um projeto .NET Composer.

## 12.7 Projects (3 of 3)

![image](https://user-images.githubusercontent.com/52088444/159332192-76a18ae7-e278-4c45-b75d-a0e95df4e8d3.png)


- IPD: Este diagrama contém blocos que representam o fluxo de trabalho de uma chamada de voz. Em alguns casos, também contém outros blocos que representam a lógica que inclui quaisquer interações que não sejam de voz.

- Fluxo de trabalho: Maioria da lógica de processamento para uma interação. Por exemplo, os destinos são especificados no fluxo de trabalho.

Interaction Process Diagram(IPD)

At the top level of a Composer, routing application is an IPD:
-  Functions as the starting page for a routing application, which results in using the same session across the entire interaction process.
- Automatically created when you start a new Project and points to a workflow resource.

When used for voice interactions, an IPD contains a single Workflow block.
Routing projects for multimedia interactions can contain additional blocks.



Diagrama de Processo de Interação (IPD)

No nível superior de um Composer, o aplicativo de roteamento é um IPD:
- Funciona como a página inicial de um aplicativo de roteamento, o que resulta no uso da mesma sessão em todo o processo de interação.
- Criado automaticamente quando você inicia um novo projeto e aponta para um recurso de fluxo de trabalho.

Quando usado para interações de voz, um IPD contém um único bloco de fluxo de trabalho.
Projetos de roteamento para interações multimídia podem conter blocos adicionais.


**Workflow (Fluxo de trabalho)**

The workflow diagram that the IPD references defines the actual workflow. 

Each workflow diagram will have at least three blocks:

- The Entry block to start the application.
- At least one other block to perform specific functions.
- The Exit block to end the application.

O diagrama de fluxo de trabalho ao qual o IPD faz referência define o fluxo de trabalho real.

Cada diagrama de fluxo de trabalho terá pelo menos três blocos:

- O bloco de entrada para iniciar o aplicativo.
- Pelo menos um outro bloco para executar funções específicas.
- O bloco Exit para encerrar o aplicativo.


## 12.8 Connect Composer to Configuration Server

![image](https://user-images.githubusercontent.com/52088444/159332924-4f2adbf1-dc78-4f14-99a1-23db6f67affb.png)

Composer itself is independent from Genesys Framework and is not restricted by any user accounts or permissions. 

But, Composer can connect to Configuration Server to download or create data needed for routing applications.

O próprio Composer é independente do Genesys Framework e não é restringido por nenhuma conta ou permissão de usuário.

Mas, o Composer pode se conectar ao Configuration Server para baixar ou criar dados necessários para aplicativos de roteamento.

**Examples:**
- Download configuration data (Agent Groups, Skills, etc.)
- Upload strategy information (publish IPD).

Connection status is shown in lower status bar. 

You may develop routing applications with a connection to Configuration Server in “online” mode or in an “offline” mode, without connecting to the Configuration Server. For example, you would need to connect to the Configuration Server in order to access configuration objects to be used in a Target block. Keep in mind that you must be connected to the Configuration Server when you publish the routing application’s IPD.


**Exemplos:**
- Baixe os dados de configuração (Grupos de Agentes, Habilidades, etc.)
- Carregar informações de estratégia (publicar IPD).

O status da conexão é mostrado na barra de status inferior.

Você pode desenvolver aplicativos de roteamento com uma conexão ao Servidor de Configuração em modo “online” ou em modo “offline”, sem se conectar ao Servidor de Configuração. Por exemplo, você precisaria se conectar ao Configuration Server para acessar os objetos de configuração a serem usados em um bloco Target. Lembre-se de que você deve estar conectado ao servidor de configuração ao publicar o IPD do aplicativo de roteamento.

## 12.9 Validate Diagrams

![image](https://user-images.githubusercontent.com/52088444/159333241-a0d5055e-ff4a-4c9c-a033-9d559a29cee7.png)

Composer can validate your diagram files and other source files for completeness and accuracy. You can initiate standalone workflow validation in a couple of ways:
- Diagram > Validate from the menu.
- Click the Validate icon on the upper-right of the Composer main window.

In case of errors, the Problems view will become visible and error markers are put on the workflow blocks that contain errors. Double-clicking on an error in the Problems view will take you to the corresponding blocks that contain the errors. Review each of the errors and do the fixes, then validate again.


O Composer pode validar seus arquivos de diagrama e outros arquivos de origem para integridade e precisão. Você pode iniciar a validação do fluxo de trabalho autônomo de duas maneiras:
- Diagrama > Validar no menu.
- Clique no ícone Validar no canto superior direito da janela principal do Composer.

Em caso de erros, a visualização Problemas ficará visível e marcadores de erro serão colocados nos blocos de fluxo de trabalho que contêm erros. Clicar duas vezes em um erro na visualização Problemas levará você aos blocos correspondentes que contêm os erros. Revise cada um dos erros e faça as correções, depois valide novamente.

## 12.10 Generate All Code

![image](https://user-images.githubusercontent.com/52088444/159333651-9a74fc4f-d75f-4e6e-aeb6-bd6479cf319d.png)

Before a routing application can run, IPD and Workflow diagrams need to be converted to SCXML. ORS executes the SCXML file. 

Use Generate All icon to generate code for all IPDs and Workflows in specified project. You can also right-click on the name of a project and choose Generate All. 

SCXML code is saved in the new created src-gen folder:

- Composer generates a single SCXML Page per workflow and one for Interaction Process Diagram.
- Name format:

Interaction Process Diagram: 

         - IPD_<ipd_diagram_name>_<workflow_block_name>.scxml 
         - Workflow: <workflow_diagram_name>.scxml

Click on the file to open it in the SCXML editor.

Antes que um aplicativo de roteamento possa ser executado, os diagramas IPD e Workflow precisam ser convertidos em SCXML. O ORS executa o arquivo SCXML.

Use o ícone Gerar tudo para gerar código para todos os IPDs e fluxos de trabalho no projeto especificado. Você também pode clicar com o botão direito do mouse no nome de um projeto e escolher Gerar tudo.

O código SCXML é salvo na nova pasta src-gen criada:

- O Composer gera uma única página SCXML por fluxo de trabalho e uma para o diagrama de processo de interação.
- Formato do nome:

Diagrama do Processo de Interação:

          - IPD_<ipd_diagram_name>_<workflow_block_name>.scxml
          - Fluxo de trabalho: <workflow_diagram_name>.scxml

Clique no arquivo para abri-lo no editor SCXML.

![image](https://user-images.githubusercontent.com/52088444/159334131-df175218-2d21-4075-8bd2-033e2b50a3ed.png)

## 12.11 SCXML-State Chart Extensible Markup Language


SCXML stands for State Chart XML:
-  Open Standard, XML-Based
- Event-based state machine

For more information, please see: http://www.w3.org/TR/scxml/

SCXML significa State Chart XML:
- Padrão aberto, baseado em XML
- Máquina de estado baseada em eventos

Para obter mais informações, consulte: http://www.w3.org/TR/scxml/

![image](https://user-images.githubusercontent.com/52088444/159334284-e8914f13-fe90-49b9-ae0e-f05a9ab0cd6c.png)

An application is a collection of state machines.

- States are a set of instructions that will be executed in response to the machine's input.
- Actions are SCXML elements that do something.
- Transitions between states are triggered by events.

In Composer, each block is a state. The name of the block is the ID of the state.

In Composer, the connector lines are transitions. To move from state to state, a transition is used. An event occurring triggers a transition. Based on the occurrence of the event CheckIfEmergency checks the logic and may transit to the EmergencyTarget state or the Bankers state.

Um aplicativo é uma coleção de máquinas de estado.

- Estados são um conjunto de instruções que serão executadas em resposta à entrada da máquina.
- Ações são elementos SCXML que fazem alguma coisa.
- As transições entre estados são desencadeadas por eventos.

No Composer, cada bloco é um estado. O nome do bloco é o ID do estado.

No Composer, as linhas de conexão são transições. Para mover de estado para estado, uma transição é usada. A ocorrência de um evento desencadeia uma transição. Com base na ocorrência do evento CheckIfEmergency verifica a lógica e pode transitar para o estado EmergencyTarget ou para o estado Bankers.

![image](https://user-images.githubusercontent.com/52088444/159334487-676f7e46-dd27-4646-a293-b99b9f840910.png)

**Code Snippet**

![image](https://user-images.githubusercontent.com/52088444/159334577-e503da4b-27b8-457d-b0ff-2881eec4c42a.png)

**More about SCXML and Orchestration**

SCXML is an XML-based markup language (state machine language) that can be used in many ways. It is well-suited to event-driven solutions, but can also be used for sequential workflow solutions. State machines are one of the classic constructions of computer science. They express how a computer goes from one state to another according to the basic rules in order to accomplish a task. A state is a particular set of instructions that will be executed in response to the machine's input.

SCXML provides the backbone logic for Orchestration applications and is generated using Composer. URS provides functional modules to achieve domain-specific functions such as queue handling, eServices, and interaction handling. ORS uses these functional modules from URS for queue, target and statistics information.

Once the SCXML engine has been initialized, the state machine progresses based on the events that are triggered on it. When an event is triggered, if the current set of states have transitions waiting for that event, and the guard condition on one of those transitions is satisfied, the state machine is said to follow that transition, which may possibly yield a new set of current states. Most state machines will ultimately reach a final state, wherein the state machine has said to have executed to completion.

**Mais sobre SCXML e orquestração**

SCXML é uma linguagem de marcação baseada em XML (linguagem de máquina de estado) que pode ser usada de várias maneiras. Ele é adequado para soluções orientadas a eventos, mas também pode ser usado para soluções de fluxo de trabalho sequencial. As máquinas de estado são uma das construções clássicas da ciência da computação. Eles expressam como um computador vai de um estado para outro de acordo com as regras básicas para realizar uma tarefa. Um estado é um conjunto particular de instruções que serão executadas em resposta à entrada da máquina.

O SCXML fornece a lógica de backbone para aplicativos de orquestração e é gerado usando o Composer. O URS fornece módulos funcionais para obter funções específicas de domínio, como manipulação de filas, eServices e manipulação de interações. O ORS usa esses módulos funcionais do URS para informações de fila, destino e estatísticas.

Depois que o mecanismo SCXML for inicializado, a máquina de estado avança com base nos eventos que são acionados nela. Quando um evento é acionado, se o conjunto atual de estados tem transições esperando por esse evento, e a condição de guarda em uma dessas transições é satisfeita, diz-se que a máquina de estado segue essa transição, o que pode possivelmente produzir um novo conjunto de estados atuais. estados. A maioria das máquinas de estado acabará por atingir um estado final, em que a máquina de estado disse ter executado até a conclusão.
