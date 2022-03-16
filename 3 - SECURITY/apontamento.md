## 3.1 Learning Objectives

After completing this chapter, you should be able to do the following: 

1- Recall Permissions and Roles.

2 - Create a new Access Group.

3 - Assign Permissions.

4 - Describe Permissions.

5- Describe Configuration Units.

6 -Create a new Role.

7 -Assign Privileges to a Role.

8 -Assign Access Group and Role to a User.

Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1- Recuperar Permissões e Funções.

2 - Crie um novo Grupo de Acesso.

3 - Atribuir Permissões.

4 - Descreva as Permissões.

5- Descreva as Unidades de Configuração.

6 -Crie uma nova Função.

7 -Atribuir privilégios a uma função.

8 -Atribuir Grupo de Acesso e Função a um Usuário.

This lesson addresses some security-related tools available in Genesys, but not all of them. Security is covered in the [Genesys Security Deployment Guide](https://docs.genesys.com/Documentation/System/8.5.x/SDG/Welcome). It can be found on the Documentation Website under System-Level Guides.

Esta lição aborda algumas ferramentas relacionadas à segurança disponíveis no Genesys, mas não todas. A segurança é abordada no [Guia de implantação de segurança da Genesys](https://docs.genesys.com/Documentation/System/8.5.x/SDG/Welcome). Ele pode ser encontrado no site de documentação em Guias de nível de sistema.


##  3.2 Review: Permissions and Roles


There are two levels of security access settings in the Genesys environment:

1- Permissions

2- Role-Based Access

Existem dois níveis de configurações de acesso de segurança no ambiente Genesys:

1- Permissões

2- Acesso Baseado em Funções

**Permissions**

Permissions provide object-based access control. This security mechanism implemented in the Configuration Server controls access to the configuration data. The system administrator defines the level of access per object and/or folder for any account separately. User authorization is provided by the combination of a set of permissions. The following image demonstrates how different logins may see (permission: read) different objects.

As permissões fornecem controle de acesso baseado em objeto. Este mecanismo de segurança implementado no Configuration Server controla o acesso aos dados de configuração. O administrador do sistema define o nível de acesso por objeto e/ou pasta para qualquer conta separadamente. A autorização do usuário é fornecida pela combinação de um conjunto de permissões. A imagem a seguir demonstra como diferentes logins podem ver (permissão: ler) objetos diferentes.

![image](https://user-images.githubusercontent.com/52088444/158386684-690027ce-c705-42d5-a297-7092bd275391.png)

**Roles**

Roles are functionality-based security feature for graphical interfaces (Genesys Administrator, Genesys Administrator Extension, Workspace Desktop Edition, etc.). Roles control the features of the graphical interface a user can access. The system administrator (or a designated individual) defines the access to objects based on what is to be done (viewed, modified, deleted) to the objects. Roles are Application-specific and must be defined for each Application that supports them.

For example, assume that you are assigned a Role which grants you the privilege to access all of the features of Workspace. Another agent is assigned a role with fewer privileges in the Workspace application. When you log in, you will see a different Workspace interface as shown in the example below. For you, all the options are available. For the other agent, some sections are hidden.

As funções são recursos de segurança baseados em funcionalidade para interfaces gráficas (Genesys Administrator, Genesys Administrator Extension, Workspace Desktop Edition, etc.). As funções controlam os recursos da interface gráfica que um usuário pode acessar. O administrador do sistema (ou um indivíduo designado) define o acesso aos objetos com base no que deve ser feito (visualizado, modificado, excluído) aos objetos. As funções são específicas do aplicativo e devem ser definidas para cada aplicativo que as suporta.

Por exemplo, suponha que você recebeu uma função que concede a você o privilégio de acessar todos os recursos do Workspace. Outro agente é atribuído a uma função com menos privilégios no aplicativo Workspace. Ao fazer login, você verá uma interface de área de trabalho diferente, conforme mostrado no exemplo abaixo. Para você, todas as opções estão disponíveis. Para o outro agente, algumas seções estão ocultas.

![image](https://user-images.githubusercontent.com/52088444/158386912-40b66a3e-586d-4865-9a7f-6aaeb97361ca.png)

## 3.3 Access Groups

Permissions and roles can be assigned to individual users, but a more efficient way is to use Access Groups. Users can be grouped together based on having the same security access. Permissions and roles are assigned to the Access Group and everyone who is a member of that group receives the same permissions and roles.

Permissões e funções podem ser atribuídas a usuários individuais, mas uma maneira mais eficiente é usar grupos de acesso. Os usuários podem ser agrupados com base no mesmo acesso de segurança. Permissões e funções são atribuídas ao Grupo de Acesso e todos que são membros desse grupo recebem as mesmas permissões e funções.

![image](https://user-images.githubusercontent.com/52088444/158387061-98da9e1c-ac49-421f-bf68-3af9627b456f.png)

## 3.4 Persons

Every user of a Genesys Interface requires an account. When an established user starts a client application (like GAX) and enters the password for his or her assigned user account, a session is opened between the client application and the Configuration Server. During that session, access to objects is provided based on the permissions granted to the assigned account and based on the roles assigned to the user.

Todo usuário de uma Interface Genesys requer uma conta. Quando um usuário estabelecido inicia um aplicativo cliente (como GAX) e insere a senha para sua conta de usuário atribuída, uma sessão é aberta entre o aplicativo cliente e o Configuartion Server. Durante essa sessão, o acesso aos objetos é fornecido com base nas permissões concedidas à conta atribuída e nas funções atribuídas ao usuário.

![image](https://user-images.githubusercontent.com/52088444/158387357-f42d906d-395d-46ef-8a37-d69bdd502538.png)

## 3.5 Special Accounts

Genesys has two special accounts set up within the environment: The Master Account and the System Account.
A Genesys tem duas contas especiais configuradas no ambiente: a conta principal e a conta do sistema.

A Genesys tem duas contas especiais configuradas no ambiente: a conta principal e a conta do sistema.

![image](https://user-images.githubusercontent.com/52088444/158387763-5074f5e4-f26e-4423-9447-813b62512afc.png)

**The Master Account: default/password(A conta principal: padrão/senha)**

The default user account is not related to roles and, therefore, does not need to be assigned a role. 

When the Configuration Database is initialized, a master account with username = default and a password = password is created. The default user is not assigned to a role. All other users have to be assigned to a role(s) to access applications like GAX and Workspace. 

The Master account always exists in the system and by design is always granted Full Control permissions for all objects in the Configuration Database and the default user’s access to all objects in the configuration cannot be deleted or modified. This account is used when logging in to the Configuration Layer for the first time. 

This Master account is the same by default in all Genesys implementations, so for obvious reasons, you are advised to change the password associated with this account. Given the importance of this account, take special care never to misplace the password, as it cannot be recovered. 

The default user account is not related to Access Groups and, therefore, does not appear as a member of any Access Group. 

A conta de usuário padrão não está relacionada a funções e, portanto, não precisa ser atribuída a uma função.

Quando o Configuration DataBase é inicializado, uma conta mestre com nome de usuário = padrão e uma senha = senha é criada. O usuário padrão não é atribuído a uma função. Todos os outros usuários precisam ser atribuídos a uma(s) função(ões) para acessar aplicativos como GAX e Workspace.

A conta master sempre existe no sistema e, por design, sempre é concedida permissões de controle total para todos os objetos no Configuration DataBase e o acesso do usuário padrão a todos os objetos na configuração não pode ser excluído ou modificado. Essa conta é usada ao efetuar login no Configuration Layer pela primeira vez.

Essa conta Master é a mesma por padrão em todas as implementações da Genesys, portanto, por motivos óbvios, é recomendável alterar a senha associada a essa conta. Dada a importância dessa conta, tome cuidado especial para nunca perder a senha, pois ela não pode ser recuperada.

A conta de usuário padrão não está relacionada a Grupos de Acesso e, portanto, não aparece como membro de nenhum Grupo de Acesso.

**The System Account**

The System Account is an internal account for Server Application Access. Daemon applications do not have an explicit login procedure. Instead, their access permissions are determined by the permissions of the account with which they are associated: a personal account or the SYSTEM account. Any personal account registered as a Person object in the Configuration Database can be used as an account for any daemon application. By default, every daemon application is associated with a special account SYSTEM that has Read and Execute permissions for all objects in the Configuration Database except Access Groups. The SYSTEM account is not listed with Persons/Users in GAX.

A conta do sistema é uma conta interna para acesso ao aplicativo do servidor. Os aplicativos daemon não têm um procedimento de login explícito. Em vez disso, suas permissões de acesso são determinadas pelas permissões da conta à qual estão associados: uma conta pessoal ou a conta SYSTEM. Qualquer conta pessoal registrada como um objeto Person no Configuration Database pode ser usada como uma conta para qualquer aplicativo daemon. Por padrão, cada aplicativo daemon está associado a uma conta especial SYSTEM que possui permissões de leitura e execução para todos os objetos no Configuration DataBase, exceto grupos de acesso. A conta SYSTEM não está listada com Pessoas/Usuários no GAX.

## 3.6 Access Groups

Access Groups are groups of Users who need the same set of permissions for
configuration objects.

Grupos de acesso são grupos de usuários que precisam do mesmo conjunto de permissões para objetos de configuração.

Access Groups provide an efficient way to assign access to data. Group permissions for each folder are set one time and users are added to or removed from the groups. This eliminates the necessity of going to every folder to make changes or granting each user special access to an object. Working with groups instead of individual users helps simplify security maintenance and administration.

Os grupos de acesso fornecem uma maneira eficiente de atribuir acesso aos dados. As permissões de grupo para cada pasta são definidas uma vez e os usuários são adicionados ou removidos dos grupos. Isso elimina a necessidade de ir a todas as pastas para fazer alterações ou conceder a cada usuário acesso especial a um objeto. Trabalhar com grupos em vez de usuários individuais ajuda a simplificar a manutenção e a administração da segurança.

For Access Groups in GAX, go to Configuration > Accounts > Access Groups.

For Access Groups in GAX, go to Configuration > Accounts > Access Groups.
Para grupos de acesso no GAX, vá para configuração > contas > grupos de acesso.

In addition to the three default access groups, the following three access groups are as follows:
- EVERYONE–An Access Group that includes every user registered in the Configuration Database. You cannot delete or modify this group, which, by default, has no permissions set for any configuration objects.
- SYSTEM–The default configuration grants Read and Execute permissions for this Access Group to all objects in the Configuration Database (except Access Groups). The default configuration also associates this Access Group with every server application—a requirement for full functionality.
- Tenant Creators–Added during setup for multi-tenant, this access group is not set up out of the box. It’s a special access group which gives members the ability to add tenants.

Além dos três grupos de acesso padrão, os três grupos de acesso a seguir são os seguintes:

- TODOS–Um Grupo de Acesso que inclui todos os usuários cadastrados no Banco de Dados de Configuração. Você não pode excluir ou modificar este grupo, que, por padrão, não possui permissões definidas para nenhum objeto de configuração.
- SISTEMA – A configuração padrão concede permissões de Leitura e Execução para este Grupo de Acesso a todos os objetos do Banco de Dados de Configuração (exceto Grupos de Acesso). A configuração padrão também associa esse grupo de acesso a todos os aplicativos de servidor — um requisito para a funcionalidade completa.
- Criadores de locatários – adicionados durante a configuração para vários locatários, esse grupo de acesso não é configurado imediatamente. É um grupo de acesso especial que oferece aos membros a capacidade de adicionar inquilinos.

![image](https://user-images.githubusercontent.com/52088444/158396729-819af300-2058-43be-a88e-62a03c1d922c.png)

Administrators, Super Administrators, and Users are the Default Access Groups for Persons.

Administradores, superadministradores e usuários são os grupos de acesso padrão para pessoas.

## 3.7 Default Access Groups

Genesys offers these preconfigured Default Access Groups:

- Users–Members have Read and Execute permissions with respect to all objects except Access Groups.
- Administrators–Members have a full set of permissions with respect to all objects except the Super Administrators Access Group.
- Super Administrators–Members have a full set of permissions with respect to every object in the Configuration Database. No person is added to this group by default.

A Genesys oferece estes grupos de acesso padrão pré-configurados:

- Usuários–Membros têm permissões de Leitura e Execução em relação a todos os objetos, exceto Grupos de Acesso.
- Administradores – os membros têm um conjunto completo de permissões com relação a todos os objetos, exceto o grupo de acesso de superadministradores.
- Super administradores – os membros têm um conjunto completo de permissões em relação a cada objeto no Configuration DataBase. Nenhuma pessoa é adicionada a este grupo por padrão.

![image](https://user-images.githubusercontent.com/52088444/158397900-b856fc8d-0788-4aeb-a139-1e807e321e85.png)


Important: You cannot delete or rename Default Access Groups, although you can change their default privileges.

Super Administrators have the additional privilege of being able to put the system into Read-Only and Emergency Mode. This is done using Genesys Administrator.

Importante: Você não pode excluir ou renomear Grupos de Acesso Padrão, embora possa alterar seus privilégios padrão.

Os superadministradores têm o privilégio adicional de poder colocar o sistema em modo somente leitura e emergência. Isso é feito usando o Genesys Administrator.

Importante: Você não pode excluir ou renomear Grupos de Acesso Padrão, embora possa alterar seus privilégios padrão.

Os superadministradores têm o privilégio adicional de poder colocar o sistema em modo somente leitura e emergência. Isso é feito usando o Genesys Administrator.


![image](https://user-images.githubusercontent.com/52088444/158398262-1f886301-97a0-4d94-9cfc-e517ff497f6c.png)

## 3.8 Creating New Access Groups

Administrators and Super Administrators can create new Access Groups. To create a new Access Group, go to GAX > Accounts > Access Groups, click New and give the Access Group a name.

Administradores e Superadministradores podem criar novos Grupos de Acesso. Para criar um novo Grupo de Acesso, vá para GAX > Contas > Grupos de Acesso, clique em Novo e dê um nome ao Grupo de Acesso.

![image](https://user-images.githubusercontent.com/52088444/158398527-d044f93c-9046-4f4c-b7df-136359f4a320.png)

Once a new group has been created, you must do the following:

- Assign members to the access group
- Assign permissions/roles for the access group

A user cannot grant any permissions to a new access group if they are not a part of the group themselves.

Depois que um novo grupo for criado, você deve fazer o seguinte:

- Atribuir membros ao grupo de acesso
- Atribuir permissões/funções para o grupo de acesso

Um usuário não pode conceder permissões a um novo grupo de acesso se ele próprio não fizer parte do grupo.

**Assign Members to an Access Group**

You can assign members to an Access groups in one of the following two ways:
- Using the Members tab of the Access Groups screen. Here you can add users as members of the Access Group, as seen in the example below.

Você pode atribuir membros a um grupo do Access de uma das duas maneiras a seguir:
- Usando a aba Membros da tela Grupos de Acesso. Aqui você pode adicionar usuários como membros do Grupo de Acesso, como visto no exemplo abaixo.

![image](https://user-images.githubusercontent.com/52088444/158400536-4a0f79a8-1938-45bc-8ebf-e2da42532034.png)

Using the Member Of tab of the Person properties screen. The Member Of tab allows you to add the person to an Access Group, as seen in the example below.

Usando a guia Membro de da tela de propriedades da pessoa. A guia Membro de permite adicionar a pessoa a um grupo de acesso, conforme mostrado no exemplo abaixo.

![image](https://user-images.githubusercontent.com/52088444/158400692-763f2f52-dff3-4075-bb5f-ffd6d3ef59ac.png)

## 3.9 Object Permissions


Use caution when assigning permissions. Remember, the more complex the security system is, the more difficult it becomes to manage the data and the more it affects the performance of the Configuration Layer software.

User authorization is provided by the combination of a set of elementary permissions, shown in the following table. This security mechanism implemented in the Configuration Server allows the system administrator to define the level of access for any account with respect to any object separately.

Once the members have been assigned to the Access Groups, the permissions need to be assigned to the Access Groups. The different levels of access are as follows:

Tenha cuidado ao atribuir permissões. Lembre-se, quanto mais complexo for o sistema de segurança, mais difícil será gerenciar os dados e mais afetará o desempenho do software da camada de configuração.

A autorização do usuário é fornecida pela combinação de um conjunto de permissões elementares, mostradas na tabela a seguir. Este mecanismo de segurança implementado no Configuration Server permite que o administrador do sistema defina o nível de acesso para qualquer conta em relação a qualquer objeto separadamente.

Uma vez que os membros tenham sido atribuídos aos Grupos de Acesso, as permissões precisam ser atribuídas aos Grupos de Acesso. Os diferentes níveis de acesso são os seguintes:

![image](https://user-images.githubusercontent.com/52088444/158402838-bdc90c3b-12b6-40e9-a2a1-015ac906cb61.png)

*Assigning Permissions**

Permissions are accessed in the Permissions tab of an object’s or folder’s properties screen. There is a row for each individual Access Group or Account. If there is an Access Group or Person not listed, it can be added using the Add functionality.

As permissões são acessadas na guia Permissões da tela de propriedades de um objeto ou pasta. Há uma linha para cada Grupo de Acesso ou Conta individual. Se houver um Grupo de Acesso ou Pessoa não listado, ele poderá ser adicionado usando a funcionalidade Adicionar.

![image](https://user-images.githubusercontent.com/52088444/158402985-947ae22f-40dc-47c7-8657-8c3ece6d4089.png)

The individual permissions are assigned using the checkboxes, as shown in the following image.

As permissões individuais são atribuídas usando as caixas de seleção, conforme mostrado na imagem a seguir.

![image](https://user-images.githubusercontent.com/52088444/158403119-2aeb64e3-cdbc-484d-a113-376dcc96e6a4.png)

In addition to selecting permissions, you can choose how these permissions are applied in the folder or object hierarchy.

- Assign Permissions to a single folder or object–With this method, the permissions are applied only to the folder or object in question. The Permissions for the objects and the child folders that already exist within a given folder (or parent object) are not affected.

- Propagate Permissions–The permission settings for an account in a child object are actively linked to the permissions of that account in the parent object and are controlled by the status of the propagate switch. If the propagate switch is checked for the account in the parent object, then the child object will have the same permission settings for that account. If the propagate switch is not checked, then the child object will not have the permission settings of the parent and all child objects become independent and maintain their own permission settings.

Além de selecionar permissões, você pode escolher como essas permissões são aplicadas na pasta ou hierarquia de objetos.

- Atribuir permissões a uma única pasta ou objeto – Com este método, as permissões são aplicadas apenas à pasta ou objeto em questão. As permissões para os objetos e as pastas filho que já existem em uma determinada pasta (ou objeto pai) não são afetadas.

- Permissões de propagação – As configurações de permissão para uma conta em um objeto filho estão ativamente vinculadas às permissões dessa conta no objeto pai e são controladas pelo status da opção de propagação. Se a opção de propagação for verificada para a conta no objeto pai, o objeto filho terá as mesmas configurações de permissão para essa conta. Se a opção de propagação não estiver marcada, o objeto filho não terá as configurações de permissão do pai e todos os objetos filho se tornarão independentes e manterão suas próprias configurações de permissão.

![image](https://user-images.githubusercontent.com/52088444/158403448-14e1ab18-ea33-44d6-adc3-9ff881ceae0e.png)

Nota: Group permissions removed from a parent object are also removed from its child objects, regardless of the status of the Propagate checkbox. However, when adding permissions to a parent object, the permissions will not be added to child objects if the propagate checkbox is cleared for the group or account you are adding. Note that any new objects or folders (child objects) created within this folder (parent object) will not inherit the permissions of the parent object because the Propagate box is not checked on the parent object.

Nota:As permissões de grupo removidas de um objeto pai também são removidas de seus objetos filho, independentemente do status da caixa de seleção Propagar. No entanto, ao adicionar permissões a um objeto pai, as permissões não serão adicionadas a objetos filho se a caixa de seleção de propagação estiver desmarcada para o grupo ou conta que você está adicionando. Observe que quaisquer novos objetos ou pastas (objetos filho) criados nessa pasta (objeto pai) não herdarão as permissões do objeto pai porque a caixa Propagar não está marcada no objeto pai.

Replace Recursively–Checking this box removes all security settings for all child folders and objects within the folder, or parent object replacing all settings with the current set of permissions displayed on the screen.

Substituir recursivamente – marcar esta caixa remove todas as configurações de segurança de todas as pastas e objetos filho dentro da pasta ou objeto pai substituindo todas as configurações pelo conjunto atual de permissões exibidas na tela.

![image](https://user-images.githubusercontent.com/52088444/158403893-0ebeed78-5bf8-43ff-82a8-8b60dd964efa.png)

## 3.10 Access and Permissions in Action(Acesso e Permissões em Ação)

Scenario 1 - Promoting Agents to Supervisors

The contact center manager decides to promote agent HBalzac as a Supervisor for the Engage Sales Team and wants HBalzac to operate Skill assignments only for that team using the GAX application. The System admin will need to create an Access Group with specific objects permission setting to view and make changes.

Cenário 1 - Promovendo Agentes a Supervisores

O gerente do contact center decide promover o agente HBalzac como Supervisor da Equipe de Vendas do Engage e deseja que a HBalzac opere atribuições de Habilidades apenas para essa equipe usando o aplicativo GAX. O administrador do sistema precisará criar um grupo de acesso com configuração de permissão de objetos específicos para visualizar e fazer alterações.

## 3.11 GAX: Configuration Units(GAX: Unidades de Configuração)

Configuration Units/Sites enable you to group configuration objects of various types of business, geographical, and other reasons. Also, within each configuration unit/site, you can create sub-entities. This enables you to build the hierarchies required by your enterprise. A Site is a special type of Configuration Unit used in Cost-Based Routing to build and represent infrastructure cost tables.

Configuration Units or Sites are the easiest way to implement access control. Permissions can be propagated to subfolders and objects.

Within a Configuration Unit/Site, you can add folders of various types. Subfolders can hold various configurations objects. For example, you could add a Persons folder and a Skills folder. Existing Person and/or Skill objects can be moved into their respective folders. You can also create new objects directly within each folder.

As Unidades/Locais(Units/Sites) de Configuração permitem agrupar objetos de configuração de vários tipos de negócios, geográficos e outros motivos. Além disso, dentro de cada unidade/local(Units/Sites) de configuração, você pode criar subentidades. Isso permite que você crie as hierarquias exigidas pela sua empresa. Um Site é um tipo especial de Unidade de Configuração(Configuration Unit) usado no Roteamento Baseado em Custo para construir e representar tabelas de custos de infraestrutura.

Unidades de configuração ou sites(Configuration Units or Sites) são a maneira mais fácil de implementar o controle de acesso. As permissões podem ser propagadas para subpastas e objetos.

Dentro de uma Unidade/Local de Configuração (Configuration Unit/Site), você pode adicionar pastas de vários tipos. As subpastas podem conter vários objetos de configuração. Por exemplo, você pode adicionar uma pasta Pessoas e uma pasta Habilidades. Os objetos Pessoa e/ou Habilidade existentes podem ser movidos para suas respectivas pastas. Você também pode criar novos objetos diretamente dentro de cada pasta.

![image](https://user-images.githubusercontent.com/52088444/158406266-048e6cab-77d2-41e4-9d12-0c23351e98bc.png)

## 3.12 GAX: Creation of Configuration Units

In GAX, you usually navigate to Configuration as a starting point, but to create a Configuration Unit, you need to start from a different location. Navigate to a configuration object, such as Skills. In the object folder, change from the object to the root directory.

No GAX, você normalmente navega para Configuração como ponto de partida, mas para criar uma Unidade de Configuração, você precisa começar de um local diferente. Navegue até um objeto de configuração, como Skills. Na pasta de objetos, mude do objeto para o diretório raiz.

![image](https://user-images.githubusercontent.com/52088444/158406748-abdc94c0-a05e-4e5f-b49b-8275de8f0b88.png)

Clicking More will display the screen as seen in the following image, where you can name each Configuration Unit/Site according to the entity it represents.

Clicar em Mais exibirá a tela conforme a imagem a seguir, onde você pode nomear cada Unidade/Local de Configuração de acordo com a entidade que representa.

## 3.13 Read-Only and Emergency Modes: Genesys Administrator

The Read-only and Emergency modes are not currently available in GAX. These can be viewed only in GA. So, log into GA to enable or disable these modes.

Os modos Somente leitura e Emergência não estão disponíveis atualmente no GAX. Estes podem ser vistos apenas no GA. Portanto, faça login no GA para ativar ou desativar esses modos.

If you are logged on to the Master Account or as a Super Administrator, the Read-only Mode and Emergency Mode menu items are enabled from the Preferences drop-down in Genesys Administrator as shown in the following image. Selecting these items switches the entire Configuration Layer to the selected mode.

Se você estiver conectado à conta principal ou como superadministrador, os itens de menu Modo somente leitura e Modo de emergência serão ativados na lista suspensa Preferências no Genesys Administrator, conforme mostrado na imagem a seguir. A seleção desses itens alterna toda a Camada de Configuração para o modo selecionado.

![image](https://user-images.githubusercontent.com/52088444/158407943-92164d13-1545-41f3-895b-ec615a1f1604.png)

When the Read-only Mode is enabled, no users, including the Master Account user, will be able to make changes to the Configuration Database. All users working in the Configuration Layer are notified that the Read-only Mode is activated.

When the Configuration Layer is in Read-only Mode, client applications that attempt to make configuration changes receive an error message. (These client apps are clients of Configuration Server such as Genesys Administrator, GAX, Wizards, and so on.)

Quando o modo somente leitura estiver habilitado, nenhum usuário, incluindo o usuário da conta principal, poderá fazer alterações no Configuration Database. Todos os usuários que trabalham na Configuration Database são notificados de que o modo somente leitura está ativado.

Quando a Configuration Database está no modo somente leitura, os aplicativos cliente que tentam fazer alterações na configuração recebem uma mensagem de erro. (Esses aplicativos cliente são clientes do Configuration Server, como Genesys Administrator, GAX, Wizards e assim por diante.)

Note: If Configuration Server itself is restarted, it will switch out of Read-only Mode.

Nota:Se o próprio Configuration Server for reiniciado, ele sairá do modo somente leitura.

In Emergency Mode, the read-only restriction applies to all users except those who are members of the predefined Super Administrators user group. That is, only users who are members of the Super Administrators group can make changes to the Configuration Database.

No Modo de Emergência, a restrição somente leitura se aplica a todos os usuários, exceto aqueles que são membros do grupo de usuários Super Administradores predefinido. Ou seja, apenas os usuários que são membros do grupo Super Administradores podem fazer alterações no Configuration Database.

## 3.14 Role-Based Access Control

Role-based access control is an additional layer of security configured using GAX or Genesys Administrator. These control the features that can be seen and used within a particular interface, such as Workspace. Roles are application-specific and must be defined for each application that supports them.

Example:

Assume that you are assigned a Role which grants you the privilege to access Agents View in GAX. No other Roles have been assigned to you. When you log in, only the Agents View section is displayed under the GAX header. All other sections are hidden. 

O controle de acesso baseado em função é uma camada adicional de segurança configurada usando GAX ou Genesys Administrator. Eles controlam os recursos que podem ser vistos e usados em uma interface específica, como o Workspace. As funções são específicas do aplicativo e devem ser definidas para cada aplicativo que as suporta.

Exemplo:

Suponha que você recebeu uma função que concede a você o privilégio de acessar a visualização de agentes no GAX. Nenhuma outra função foi atribuída a você. Ao fazer login, apenas a seção Visualização de agentes é exibida no cabeçalho GAX. Todas as outras seções estão ocultas.

## 3.15 GAX: Create a New Role

To add a new role, go to GAX > Configuration > Accounts > Roles and give the new role a name. Using the Role Template Selection, select a role template to prepopulate the set of privileges for this new role—you can start with no privileges (None) or all privileges (Super User).

Para adicionar uma nova função, vá para GAX > Configuration > Accounts > Roles e dê um nome à nova função. Usando a Seleção de modelo de função, selecione um modelo de função para preencher previamente o conjunto de privilégios para essa nova função — você pode começar sem privilégios (Nenhum) ou com todos os privilégios (Superusuário).


![image](https://user-images.githubusercontent.com/52088444/158628362-3f29fdbb-0b4f-4b19-a80a-597cd074cb58.png)

Within the properties of the role, there is a Role Members tab. This allows you to assign Access Groups and Persons to the role you just created. Anyone who is added to the Access Group will inherit the privileges of this role.

Dentro das propriedades da função, há uma guia Membros da função. Isso permite que você atribua grupos de acesso e pessoas à função que você acabou de criar. Qualquer pessoa adicionada ao Grupo de Acesso herdará os privilégios dessa função.

![image](https://user-images.githubusercontent.com/52088444/158628781-0fc29a89-e32d-4767-90a2-a4c6f9c55280.png)

Assigning privileges to the members of the role is the next step. You can select or unselect privileges using the checkbox seen in the image below. The privileges are organized in a hierarchy. The top level of the hierarchy indicates the application.

A atribuição de privilégios aos membros da função é a próxima etapa. Você pode selecionar ou desmarcar privilégios usando a caixa de seleção vista na imagem abaixo. Os privilégios são organizados em uma hierarquia. O nível superior da hierarquia indica o aplicativo.

Example:

CfgGenesysAdministratorServer is for GAX. Module Codes appear next in the hierarchy to indicate to which parts of the application you are giving privileges. If the box is unchecked in the upper part of the hierarchy, it indicates that all items underneath are not checked.

Exemplo:

CfgGenesysAdministratorServer é para GAX. Os Códigos de Módulo aparecem a seguir na hierarquia para indicar a quais partes do aplicativo você está concedendo privilégios. Se a caixa estiver desmarcada na parte superior da hierarquia, isso indica que todos os itens abaixo não estão marcados.

![image](https://user-images.githubusercontent.com/52088444/158629346-0fefd420-8fad-4b48-9dab-c03c2db7a477.png)

Examples of GAX Modules Codes:

- OPM = Operational Parameter Management
- AMUI = Agent Management User Interface
- ARM = Audio Resource Management
- ASD = Automated Service Deployment
- BULKOPS = Bulk Operations
- COM = Configuration Object Management
- GA = Genesys Administrator
- gax-lrm = LRM Plug-in
- UMUI = User Management User Interface

Together, these modules collect associated privileges in the hierarchy.

Exemplos de Códigos de Módulos GAX:

- OPM = Gerenciamento de Parâmetros Operacionais
- AMUI = Interface de usuário de gerenciamento de agentes
- ARM = Gerenciamento de recursos de áudio
- ASD = Implantação de serviço automatizada
- BULKOPS = Operações em Massa
- COM = Gerenciamento de Objetos de Configuração
- GA = Administrador Genesys
- gax-lrm = Plug-in LRM
- UMUI = Interface de usuário de gerenciamento de usuários

Juntos, esses módulos coletam privilégios associados na hierarquia.


On the right-hand side of the screen, the prerequisite privileges are indicated. In order to give the privileges, you have to ensure that the required prerequisite privileges have been assigned. In the example shown above, to assign the Modify Agents in Agent Management privilege, you must make sure that the AGENT_MGMT_READ_AGENTS (read) privilege has been assigned first.

No lado direito da tela, os privilégios de pré-requisito são indicados. Para conceder os privilégios, você deve garantir que os privilégios de pré-requisito necessários tenham sido atribuídos. No exemplo mostrado acima, para atribuir o privilégio Modificar Agentes no Gerenciamento de Agentes, você deve certificar-se de que o privilégio AGENT_MGMT_READ_AGENTS (leitura) tenha sido atribuído primeiro.

**Multiple Roles**

You can assign more than one Role to a User or Access Group, sometimes resulting in privileges being granted differently between Roles. In this case, the User or Access Group will have the combined set of privileges granted by each Role. In other words, the User or Access Group is granted any privilege which is granted by at least one of the assigned Roles.

Privileges are detailed in the Genesys Documentation. For example, the GAX privileges are covered in Genesys Administrator Extension Deployment Guide.

Você pode atribuir mais de uma função a um usuário ou grupo de acesso, às vezes resultando em privilégios concedidos de forma diferente entre funções. Nesse caso, o Usuário ou Grupo de Acesso terá o conjunto combinado de privilégios concedidos por cada Função. Em outras palavras, o usuário ou grupo de acesso recebe qualquer privilégio concedido por pelo menos uma das funções atribuídas.

Os privilégios são detalhados na Documentação da Genesys. Por exemplo, os privilégios GAX são abordados no Genesys Administrator Extension Deployment Guide.

## 3.16 Roles in Action

Scenario 2 - Agent Supervisor for GAX

As HBalzac is promoted, he now requires access to the GAX application and needs permissions to view and assign skills to his allocated team. The System admin will need to create a new role and set up the required privileges.


## 3.17 Access Control Plan

The default security settings are designed to meet the most common needs of enterprises that implement Genesys Framework. For businesses in this category, the security implementation is as easy as creating new user accounts and assigning them to the default Access Groups (Super Administrator and Administrator).

As configurações de segurança padrão são projetadas para atender às necessidades mais comuns das empresas que implementam o Genesys Framework. Para empresas nesta categoria, a implementação de segurança é tão fácil quanto criar novas contas de usuário e atribuí-las aos Grupos de Acesso padrão (Super Administrador e Administrador).

![image](https://user-images.githubusercontent.com/52088444/158630864-d0fb3b06-90a3-4c7b-abab-d1a66bc9cffe.png)

Complex Systems

For environments with a very large number of configuration objects, a more complex security plan may be required. If you have many administrators, each one assigned to different tasks in the Genesys environment, then you may need to customize the security implementation.

Sistemas Complexos

Para ambientes com um número muito grande de objetos de configuração, pode ser necessário um plano de segurança mais complexo. Se você tiver muitos administradores, cada um atribuído a tarefas diferentes no ambiente Genesys, talvez seja necessário personalizar a implementação de segurança.


Creating New Subfolders 

You may need to sub-divide the configuration objects in your Genesys Administrator by using subfolders. For example, the Users objects that identify the agents assigned to a particular manager can be placed in a subfolder located in the Persons folder. Access Rights can then be set at the subfolder level.

Criando novas subpastas

Você pode precisar subdividir os objetos de configuração em seu Genesys Administrator usando subpastas. Por exemplo, os objetos Usuários que identificam os agentes atribuídos a um determinado gerente podem ser colocados em uma subpasta localizada na pasta Pessoas. Os Direitos de Acesso podem ser definidos no nível da subpasta.

European Data Protection Directive 

The Genesys suite of products is designed to make up part of a fully functioning contact center solution, which may include certain non-Genesys components and customer systems. Genesys products are intended to provide customers with reasonable flexibility in designing their own contact center solutions. As such, it is possible for a customer to use the Genesys suite of products in a manner that complies with the European Data Protection Directive (EDPD). Of course, the Genesys products are tools to be used by the customer and by themselves do not ensure or enforce compliance with the EDPD. Genesys recommends that customers take steps to ensure compliance with the EDPD as well as any other applicable local security requirements. Many features of the Management Framework are designed to assist in this effort. Previously, in the lesson on Logging, we saw how the Management Framework’s logging subsystem enables selective filtering of sensitive data in logs on a per-application basis.

Diretiva Europeia de Proteção de Dados

O conjunto de produtos da Genesys foi projetado para fazer parte de uma solução de contact center totalmente funcional, que pode incluir determinados componentes e sistemas de clientes não pertencentes à Genesys. Os produtos Genesys destinam-se a fornecer aos clientes uma flexibilidade razoável na concepção de suas próprias soluções de contact center. Como tal, é possível que um cliente use o conjunto de produtos Genesys em conformidade com a Diretiva Europeia de Proteção de Dados (EDPD). É claro que os produtos Genesys são ferramentas a serem utilizadas pelo cliente e por si só não garantem ou impõem a conformidade com o EDPD. A Genesys recomenda que os clientes tomem medidas para garantir a conformidade com o EDPD, bem como com quaisquer outros requisitos de segurança locais aplicáveis. Muitos recursos do Management Framework são projetados para auxiliar nesse esforço. Anteriormente, na lição sobre Logging, vimos como o subsistema de log do Management Framework permite a filtragem seletiva de dados confidenciais em logs por aplicativo.


3.18 Learning Summary

Now that you have completed this chapter, you should be able to do the following: 

1 - Recall Permissions and Roles.

2 - Create a new Access Group.

3 - Assign Permissions.

4 - Describe Permissions.

5 - Describe Configuration Units.

6 - Create a new Role.

7 - Assign Privileges to a Role.

8 - Assign Access Group and Role to a User.

3.18 Resumo de Aprendizagem

Agora que você concluiu este capítulo, você deve ser capaz de fazer o seguinte:

1 - Recuperar Permissões e Funções.

2 - Crie um novo Grupo de Acesso.

3 - Atribuir Permissões.

4 - Descreva as Permissões.

5 - Descreva as Unidades de Configuração.

6 - Crie uma nova Função.

7 - Atribuir privilégios a uma função.

8 - Atribuir Grupo de Acesso e Função a um Usuário.