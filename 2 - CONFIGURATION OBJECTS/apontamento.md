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