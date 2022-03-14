## 2.1 Learning Objectives

After completing this chapter, you should be able to do the following:

1 - Understand Configuration Order and Dependencies.

2 - Describe and create switch-related objects.

   - Agent Logins
   - Directory Numbers (DNs)
   - Places
   - Place Groups

3 - Import and export agents.

4 - Describe and create Agent objects.

   - Using Configuration Manager Menu
   - Using Agents Menu

   Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1 - Compreender a Ordem de Configuração e Dependências.

2 - Descrever e criar objetos relacionados a switch.

    - Logins de agentes
    - Números de diretório (DNs)
    - Lugares
    - Grupos de lugares

3 - Agentes de importação e exportação.

4 - Descrever e criar objetos Agente.

    - Usando o menu do Configuration Manager
    - Usando o menu de agentes

## 2.2 Review Configuration Objects

Genesys uses the term configuration object to indicate a certain resource or part of the Genesys system that must be defined using the GAX interface and within the system using the Configuration Object Management (COM) function. COM is responsible for the general management of configuration objects on your system. There are two windows available:

Genesys usa o termo objeto de configuração para indicar um determinado recurso ou parte do sistema Genesys que deve ser definido usando a interface GAX e dentro do sistema usando a função Configuration Object Management (COM). COM é responsável pelo gerenciamento geral de objetos de configuração em seu sistema. Existem duas janelas disponíveis:

 1 - Configuration Manager Window

The Configuration Manager window enables the creation and management of the Environment and Resources level configuration objects such as Applications, Switching, Alarm Conditions, Agents, Skills, and more.

A janela do Configuration Manager permite a criação e o gerenciamento dos objetos de configuração de nível de ambiente e recursos, como aplicativos, comutação, condições de alarme, agentes, habilidades e muito mais

 2 - Agent window

The Agents window consolidates all aspects of agent management into a streamlined interface to Create agents and their associated objects such as Agent Logins, Skills, and Groups.

A janela Agentes consolida todos os aspectos do gerenciamento de agentes em uma interface simplificada para Criar agentes e seus objetos associados, como Logins de Agentes, Habilidades e Grupos.

![image](https://user-images.githubusercontent.com/52088444/158223789-fa024e9b-dcf9-4e97-93f6-a0a0aca93c8c.png)

## 2.3 Configuration Order and Dependencies( Ordem de configuração e dependências )

Genesys provides a recommended order for creating configuration objects. This order is useful because some object types depend on other types. For example, create Agent Logins before creating the Agents since the Agent Logins are needed to create agents. The dependencies of the objects are outlined in the following diagram.

A Genesys fornece uma ordem recomendada para a criação de objetos de configuração. Essa ordem é útil porque alguns tipos de objetos dependem de outros tipos. Por exemplo, crie Logins de Agente antes de criar os Agentes, pois os Logins de Agente são necessários para criar agentes. As dependências dos objetos são descritas no diagrama a seguir.

![image](https://user-images.githubusercontent.com/52088444/158233919-d8280773-ba24-40bc-91e0-6e8c8e9d8f00.png)

The recommended configuration order is:

-  Switching Office
- switches
- DNs
      - Places
      - Place Groups

- Agent Logins
- Access Groups
- skills
   - agents
   - Agent Groups


A ordem de configuração recomendada é:

- Switching Office
- switches
- DN
       - Lugares
       - Grupos de lugares

- Logins de agentes
- Grupos de Acesso
- Habilidades
    - agentes
    - Grupos de Agentes


In the Framework Routing & Reporting 8.5 Foundation course, you learned about Agents, Agent Groups, and Skills. In this course, you will learn how to create DNs, Places, Place Groups, Agent Logins, Agents, and Access Groups. If you continue on and attend the Framework Routing & Reporting 8.5 Administration course, you will create the Applications, Host, Switching Office, and Switches.

No curso Framework Routing & Reporting 8.5 Foundation, você aprendeu sobre Agentes, Grupos de Agentes e Habilidades. Neste curso, você aprenderá como criar DNs, Locais, Grupos de Locais, Logins de Agentes, Agentes e Grupos de Acesso. Se você continuar e participar do curso Framework Routing & Reporting 8.5 Administration, você criará os aplicativos, Host, Switching Office e Switches.


## 2.4 Review Switch and Genesys Terminology(Revisão da terminologia do switch e da Genesys)

One of the primary reasons for companies to choose Computer Telephony Integration (CTII) involves the types of targets they can select. As a general rule, the switch knows about DNs (e.g., extensions) and Agent Logins, and occasionally agents themselves. Genesys broadens the scope of possible targets to include Skill Levels, Agent Groups, Places, and Place Groups.

A Genesys system is aware of all the possible targets at all the available sites. For example, Genesys can select the best available agent in the Mortgage group in Chicago or Milan. 

Because the switch can only send a telephone call to an actual DN, Genesys must specify a DN in its target selection. For instance, if Genesys selects a particular User as the target because that agent possesses a skill at a particular level, Genesys must assign a DN to the switch by which that User can receive the call.

The switch links the Agent ID to the DN when the agent logs in, as seen in the following image.

Uma das principais razões para as empresas escolherem a Integração com Telefonia Computadorizada (CTI) envolve os tipos de alvos que podem selecionar. Como regra geral, o switch conhece DNs (por exemplo, ramais) e Logins de Agentes e, ocasionalmente, os próprios agentes. A Genesys amplia o escopo de possíveis alvos para incluir Níveis de Habilidade, Grupos de Agentes, Locais e Grupos de Locais.

Um sistema Genesys está ciente de todos os alvos possíveis em todos os sites disponíveis. Por exemplo, a Genesys pode selecionar o melhor agente disponível no grupo Mortgage em Chicago ou Milão.

Como o switch só pode enviar uma chamada telefônica para um DN real, a Genesys deve especificar um DN em sua seleção de destino. Por exemplo, se a Genesys selecionar um usuário específico como destino porque esse agente possui uma habilidade em um nível específico, a Genesys deve atribuir um DN à central pela qual esse usuário possa receber a chamada.

O switch vincula o ID do agente ao DN quando o agente efetua login, conforme mostrado na imagem a seguir.

![image](https://user-images.githubusercontent.com/52088444/158234436-64bb35cf-f3c7-4384-9a11-fd024709d2c6.png)

This is reflected within the objects created inside Genesys: The DN is the agent’s extension and the Agent Login is the identifier for the particular Agent.

Isso se reflete nos objetos criados dentro do Genesys: O DN é o ramal do agente e o Login do Agente é o identificador do Agente em particular.

![image](https://user-images.githubusercontent.com/52088444/158234784-1e874f44-72f5-438b-9694-acb071a7d0b5.png)

The Agents themselves are represented as Persons. They have an Agent Login ID and Skill such as English or Spanish that determines whether they can handle billing questions. The DN is associated with a Place object—which represents an agent’s desk—where an Agent would be logging in.

Os próprios Agentes são representados como Pessoas. Eles têm um ID de login do agente e uma skill, como inglês ou espanhol, que determina se eles podem lidar com questões de cobrança. O DN está associado a um objeto Place – que representa a mesa de um agente – onde um Agente faria login.

![image](https://user-images.githubusercontent.com/52088444/158235020-efa2f19e-577a-4490-ac55-c95fff541b12.png)

Then there are Groups, such as Groups of Places and Groups of Agents. Groups are very useful for routing and reporting.

Depois, há Grupos, como Grupos de Places e Grupos de Agentes. Os grupos são muito úteis para roteamento e relatórios.

![image](https://user-images.githubusercontent.com/52088444/158236860-bbeadd90-f90c-467b-9602-f8d2f7836d53.png)


An Agent (Person) logs into a Place and depending on the way your company is configured, the Agent may log into a different place each time they go to work. When the Person logs in, Stat Server links the Agent (Person) with his or her Place. All associated Genesys objects are then associated with specific DNs in the switch.

This enables Stat Server to track Agents, their Skills, Places, Agent Groups, and Place Groups for reporting, routing, and other Genesys solutions across multiple sites and for all interaction types.

Um Agente (Pessoa) efetua login em um Local e dependendo da forma como sua empresa está configurada, o Agente pode efetuar login em um local diferente cada vez que for trabalhar. Quando a Pessoa faz login, o Stat Server vincula o Agente (Pessoa) ao seu Local. Todos os objetos Genesys associados são então associados a DNs específicos no switch.

Isso permite que o Stat Server rastreie Agentes, suas Habilidades, Locais, Grupos de Agentes e Grupos de Locais para relatórios, roteamento e outras soluções da Genesys em vários sites e para todos os tipos de interação.

![image](https://user-images.githubusercontent.com/52088444/158238574-f0d7a0db-1ae0-454e-87b2-46a1904282df.png)

## 2.5 GAX: Switching Configuration

A number of the objects discussed above are found in GAX under Configuration > Switching.

Vários dos objetos discutidos acima são encontrados em GAX em Configuration > Switching.

![image](https://user-images.githubusercontent.com/52088444/158239986-7e45b236-5c34-4627-ab1a-be7feb9e52ae.png)

Here you will find Agent Logins, DNs, Places, and Place Groups.

Aqui você encontrará Logins de Agentes, DNs, Locais e Grupos de Locais.

![image](https://user-images.githubusercontent.com/52088444/158240203-242c744d-fff7-44ea-88ee-1726cd82b06d.png)

**Switching Offices and Switches: Overview(Comutação de Escritórios e Comutadores: Visão Geral)**

The Switching Office object represents the PBX. The Switch object is an aggregate of telephone resources within one Switching Office. If a real switch has more than one SIP Server/T-Server, then there is one Switching Office object and multiple Switch objects.

Each Switch object is associated with one SIP Server or T-Server. All DNs and Agent Logins belong to a Switch. The number of the Agent Logins and DNs contained in the Switch object should mirror exactly the number of the Agent Logins and DNs in the physical switch with which T-Server is working or the number of the Agent Logins and DNs in SIP Server.

O objeto Switching Office representa o PBX. O objeto Switch é um agregado de recursos telefônicos dentro de um Switching Office. Se um switch real tiver mais de um servidor SIP/T-Server, haverá um objeto Switching Office e vários objetos Switch.

Cada objeto Switch está associado a um SIP Server ou T-Server. Todos os DNs e Logins de Agente pertencem a um Switch. O número de Logins de Agente e DNs contidos no objeto Switch deve espelhar exatamente o número de Logins de Agente e DNs no switch físico com o qual o T-Server está trabalhando ou o número de Logins de Agente e DNs no Servidor SIP.


## 2.6 Agent Logins


Agent Logins belong to a specific switch. To create a new Agent Login, you need to select the switch object (that belongs to the switch) and choose the Agent Logins folder. Agent Logins can be numeric or non-numeric. You can either edit an existing Agent Login or create a new one by clicking New.

Os logins do agente pertencem a um switch específico. Para criar um novo Agent Login, você precisa selecionar o objeto switch (que pertence ao switch) e escolher a pasta Agent Logins. Os Logins de Agentes podem ser numéricos ou não numéricos. Você pode editar um Login de Agente existente ou criar um novo clicando em Novo.

![image](https://user-images.githubusercontent.com/52088444/158242319-1a8d576f-c207-4e37-b8a8-0838b38c5ce2.png)

The following are the required properties of the Agent Login object that must be completed:

- Code—The Agent Login code. Refers to the Agent Login number an agent must enter to receive queued calls from the switch. You must specify a value for this property, and that value must be unique within the Switch. Once you set the value, you cannot change it.
- Switch—Refers to the name of the switch for which you are creating the Agent Login. The Agent Login you are creating will be associated with this switch. You cannot change this field, so it appears grayed-out.
- State Enabled—Defines whether or not the Agent Login is active. In Genesys, you might want an Agent Login to be inactive if, for example, an employee goes on vacation. You can deactivate the Agent Login by clearing the State Enabled checkbox.

Additional properties can be set when required.

A seguir estão as propriedades necessárias do objeto Login do Agente que devem ser concluídas:

- Código—O código de login do agente. Refere-se ao número de login do agente que um agente deve inserir para receber chamadas enfileiradas da central. Você deve especificar um valor para essa propriedade e esse valor deve ser exclusivo no Switch. Depois de definir o valor, você não pode alterá-lo.
- Switch—Refere-se ao nome do switch para o qual você está criando o Login do Agente. O Login do Agente que você está criando será associado a este switch. Você não pode alterar este campo, então ele aparece acinzentado.
- Estado Ativado—Define se o Login do Agente está ativo ou não. No Genesys, você pode desejar que um Login de agente fique inativo se, por exemplo, um funcionário sair de férias. Você pode desativar o Login do agente desmarcando a caixa de seleção Estado ativado.

Propriedades adicionais podem ser definidas quando necessário.

## 2.7 DN

For DNs using GAX, go to Configuration > Switching > DNs.

Like Agent Logins, DNs belong to a specific switch. To create a new DN, you need to select the switch object (that belongs to the switch) and choose the DN folder. You can either edit an existing DN or create a new one by clicking New.


 Para DNs usando GAX, vá para Configuration > Switching > DNs.

Assim como os Logins de Agente, os DNs pertencem a um switch específico. Para criar um novo DN, você precisa selecionar o objeto switch (que pertence ao switch) e escolher a pasta DN. Você pode editar um DN existente ou criar um novo clicando em Novo.
![image](https://user-images.githubusercontent.com/52088444/158246462-91dcc584-b6d4-4fc5-b315-d73bafc3745e.png)

To organize the different types of directory numbers into folders, click More > New Folder, as seen in the following image. You can then create subfolders, for example, as seen here for the different types of Directory Numbers–Extensions or Routing points.

Para organizar os diferentes tipos de números de diretório em pastas, clique em Mais > Nova Pasta, conforme mostrado na imagem a seguir. Você pode então criar subpastas, por exemplo, como visto aqui para os diferentes tipos de Números de Diretório – Extensões ou Pontos de Roteamento.

![image](https://user-images.githubusercontent.com/52088444/158246679-3f130459-2a4e-4e47-96e8-6058f367ba77.png)

To create a DN, you need to configure its properties, seen in step 4 of the image below. Certain properties are required, as indicated by the red asterisk next to the property name:

Para criar um DN, você precisa configurar suas propriedades, visto no passo 4 da imagem abaixo. Certas propriedades são obrigatórias, conforme indicado pelo asterisco vermelho ao lado do nome da propriedade:

![image](https://user-images.githubusercontent.com/52088444/158247129-73e3435f-7a98-4d18-9aeb-10d4e8c8d1cb.png)


- Number—Refers to the DN number. (Required)
-  Type—Refers to the type of DN. The drop-down list contains all the DN types. (Required)
- Switch—Refers to the switch object in which this DN is being configured. You cannot change this field, so it appears grayed-out.
- Register—Defines whether the DN exists within the switch or not. Extensions, queues, and routing points should all be registered. This is marked True by default. (Required)
- Association—Is an entity permanently associated with this DN. For DNs of External Routing Point type, this number may be required to substitute for the actual DN directory number and may be used when placing calls to this routing point from another Switch. See Question1/Answer1 below for more information.
- State—Defines whether the DN is active in Genesys. The DN is active if the checkbox is selected. This checkbox is selected by default. See Question2/Answer2 below for more information.

- Número — Refere-se ao número DN. (Requeridos)
- Tipo — Refere-se ao tipo de DN. A lista suspensa contém todos os tipos de DN. (Requeridos)
- Switch — Refere-se ao objeto switch no qual este DN está sendo configurado. Você não pode alterar este campo, então ele aparece acinzentado.
- Register—Define se o DN existe ou não dentro do switch. Extensões, filas e pontos de roteamento devem ser registrados. Isso é marcado como Verdadeiro por padrão. (Requeridos)
- Associação—É uma entidade permanentemente associada a este DN. Para DNs do tipo Ponto de Roteamento Externo, este número pode ser necessário para substituir o número de diretório DN real e pode ser usado ao fazer chamadas para este Ponto de Roteamento de outro Comutador. Consulte a Pergunta1/Resposta1 abaixo para obter mais informações.
- State—Define se o DN está ativo no Genesys. O DN está ativo se a caixa de seleção estiver marcada. Esta caixa de seleção é selecionada por padrão. Consulte a Pergunta2/Resposta2 abaixo para obter mais informações.

Question 1:

What is the Association field on a DN used for?

The Association field is used to instruct T-Server to dial a different DN to reach the DN to which the property belongs. 

For example, you specify an External Routing Point 2200 that is a DN on the local switch. If you want to call this DN from another switch, you may need to dial 123. T-Server will know this if you specify 123 in the Association field of 2200. Such things can often be seen and are caused by specific switch configurations and often dependent on whether there is a direct connection between two switches or the public line is used. It is mostly used in combination with a direct connection but in fact, it is also possible on only one switch. For any reason (e.g., organizational purposes), a switch administrator might configure a DN such that you can only send a call to it if you dial a different DN.

Question 2:

What is the effect of setting State Enabled on or off?

You can define an object and disable it if it should not be in use. This provides the ability to start setting objects up before you’re ready to use them. 

For example, you could define agents before they actually begin work but not enable them. When they are on board, you can enable them. A customer interaction cannot be directed to a disabled object. Disabling an object that is a parent to other objects will cause all its child objects to be disabled. Note that a DN has a State Enabled checkbox and a Register field. You can disable a DN, but T-Server will still register it with the switch. 

To configure DNs in Genesys Administrator, go to Provisioning > Switching > Switching, edit the properties of the desired switch object, and then go to the DNs tab.

Questão 1:

Para que é usado o campo Associação em um DN?

O campo Associação é usado para instruir o T-Server a discar um DN diferente para alcançar o DN ao qual a propriedade pertence.

Por exemplo, você especifica um Ponto de Roteamento Externo 2200 que é um DN no switch local. Se você quiser chamar esse DN de outro switch, talvez seja necessário discar 123. O T-Server saberá disso se você especificar 123 no campo Association de 2200. Essas coisas podem ser vistas com frequência e são causadas por configurações específicas do switch e muitas vezes dependendo se há uma conexão direta entre dois switches ou se a linha pública é usada. É usado principalmente em combinação com uma conexão direta, mas, na verdade, também é possível em apenas um switch. Por qualquer motivo (por exemplo, fins organizacionais), um administrador de switch pode configurar um DN de forma que você só possa enviar uma chamada para ele se discar um DN diferente.

Questão 2:

Qual é o efeito de ativar ou desativar o Estado Ativado?

Você pode definir um objeto e desativá-lo se não estiver em uso. Isso fornece a capacidade de começar a configurar objetos antes que você esteja pronto para usá-los.

Por exemplo, você pode definir agentes antes que eles comecem a trabalhar, mas não ativá-los. Quando eles estão a bordo, você pode habilitá-los. Uma interação do cliente não pode ser direcionada a um objeto desativado. Desabilitar um objeto que é pai de outros objetos fará com que todos os seus objetos filho sejam desabilitados. Observe que um DN tem uma caixa de seleção State Enabled e um campo Register. Você pode desabilitar um DN, mas o T-Server ainda o registrará com o switch.

Para configurar DNs no Genesys Administrator, vá para Provisioning > Switching > Switching, edite as propriedades do objeto de switch desejado e vá para a guia DNs.


## 2.8 Places and Place Groups

Places

For Places using GAX, go to Configuration > Switching > Places.

To create a new Place, click New. When you create a new Place, you configure the General section of the Place.

Para Places using GAX, vá para Configuration > Switching > Places.

Para criar um novo local, clique em Novo. Ao criar um novo Local, você configura a seção Geral do Local.

![image](https://user-images.githubusercontent.com/52088444/158247961-16fe7953-cab7-44e7-80da-80c9497b52b4.png)

- Name—Refers to the name you decide to give to the Place. Give it a name that clearly reflects the location. For example, you might give a Place a name made up of a combination of the physical location and the DNs that are associated with it. (Required)

The other properties on the General tab are optional and reference configuration objects that are not covered in this class.

- Capacity Rule—Allows you the option to specify a rule determining concurrent maximums by media type for this place.

- Cost Contract—Is to specify the cost contract (type of Objective Table) for use with cost-based routing to calculate the cost of an interaction being routed to this place.

The DNs tab is where you associate a DN to the Place. Click Add and select the extension.

- Nome—Refere-se ao nome que você decide dar ao Local. Dê-lhe um nome que reflita claramente a localização. Por exemplo, você pode dar a um Local um nome composto de uma combinação do local físico e dos DNs associados a ele. (Requeridos)

As outras propriedades na guia Geral são objetos de configuração opcionais e de referência que não são abordados nesta classe.

- Regra de capacidade—Permite que você especifique uma regra que determine os máximos simultâneos por tipo de mídia para este local.

- Contrato de Custo—É para especificar o contrato de custo (tipo de Tabela de Objetivos) para uso com roteamento baseado em custo para calcular o custo de uma interação sendo roteada para este local.

A guia DNs é onde você associa um DN ao Local. Clique em Adicionar e selecione a extensão.

![image](https://user-images.githubusercontent.com/52088444/158248460-5742f715-6aba-434a-99a3-b55e010a674f.png)

**Place Groups**

For Places Groups using GAX, go to Configuration > Switching > Place Groups.

Creating a new Place Group is very similar to creating a new Place. Click New and configure the General section of the Place Group.

Para Places Groups usando GAX, vá para Configuration > Switching > Place Groups.

A criação de um novo grupo de locais é muito semelhante à criação de um novo local. Clique em Novo e configure a seção Geral do Grupo de Locais.

![image](https://user-images.githubusercontent.com/52088444/158248568-6f48f5a5-b4ea-4acd-95d1-e050f0cbd69a.png)

Name—Refers to the name you decide to give to the Place Group. Give it a name that clearly reflects the purpose of the group and its members

Nome—Refere-se ao nome que você decide dar ao Grupo de Lugares. Dê um nome que reflita claramente o propósito do grupo e seus membros

The other properties on the General tab are optional and reference configuration objects are not covered in this class.

-  Capacity Table—Is to specify a Capacity Table (type of Statistical Table) to use. Call-processing applications compare the values specified in the Intervals list of associated Statistical Days.

- Quota Table—Is to specify the Quota Table (type of Statistical Table) to use. Call-processing applications compare the Minimum, Maximum, and Target values specified in associated Statistical Days.

- Cost Contract—Is to specify the cost contract (type of Objective Table) for use with cost-based routing to calculate the cost of an interaction being routed to this place group.

- Site—Is to specify which site contains the cost contract.

In the Places tab, add the Places that will be associated with this Place Group. You can organize Places into Place Groups for reporting or routing purposes. For example, the image below shows the Place Group ChicagoPlaces which can report and gather the statistics on the Chicago places: 8001_Chicago and 8002_Chicago.

As outras propriedades na guia Geral são opcionais e os objetos de configuração de referência não são abordados nesta classe.

- Tabela de Capacidade—É para especificar uma Tabela de Capacidade (tipo de Tabela Estatística) a ser usada. Os aplicativos de processamento de chamadas comparam os valores especificados na lista Intervalos de Dias Estatísticos associados.

- Tabela de Cotas—É para especificar a Tabela de Cotas (tipo de Tabela Estatística) a ser usada. Os aplicativos de processamento de chamadas comparam os valores Mínimo, Máximo e Destino especificados em Dias Estatísticos associados.

- Contrato de Custo—É para especificar o contrato de custo (tipo de Tabela de Objetivos) para uso com roteamento baseado em custo para calcular o custo de uma interação sendo roteada para este grupo de locais.

- Site—É para especificar qual site contém o contrato de custo.

Na guia Locais, adicione os locais que serão associados a este grupo de locais. Você pode organizar Locais em Grupos de Locais para fins de geração de relatórios ou roteamento. Por exemplo, a imagem abaixo mostra o Place Group ChicagoPlaces que pode relatar e reunir as estatísticas sobre os locais de Chicago: 8001_Chicago e 8002_Chicago.

![image](https://user-images.githubusercontent.com/52088444/158249121-b04f64b0-b343-47f6-822d-65b4652708da.png)

##  2.9 Creating Agents

Two different ways to create agents:

- GAX - Configuration Manager
- GAX - Agents View

Traduzir por voz
87 / 5.000
Resultados de tradução
Duas maneiras diferentes de criar agentes:

- GAX - Gerenciador de configuração
- GAX - Visualização de Agentes 


**GAX - Configuration Manager**


