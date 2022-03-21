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

