
## 8.1 Learning Objectives

After completing this chapter, you should be able to do the following: 

1 - Explain Alarm Management.

2 - Configure Alarm Conditions.

3 - Configure Alarm Reactions. 

4 - View, clear, and test Alarms. 

Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1 - Explicar o Gerenciamento de Alarmes.

2 - Configure as Condições de Alarme.

3 - Configure as reações de alarme.

4 - Visualize, limpe e teste os alarmes.

## 8.2 Alarm Detection

Alarms involve the Management Layer. The Management Layer detects the conditions that trigger the alarms, processes the alarms so that they can be seen in the interfaces (Genesys Administrator and GAX), and reacts in response to these alarms. 

There are two forms of alarm detection: Standard and Advanced.

Os alarmes envolvem a camada de gerenciamento. A camada de gerenciamento detecta as condições que acionam os alarmes, processa os alarmes para que possam ser vistos nas interfaces (Genesys Administrator e GAX) e reage em resposta a esses alarmes.

Existem duas formas de detecção de alarme: Padrão e Avançado.


**Standard Alarm Detection(Detecção de Alarme Padrão)**

If an alarm is configured to be triggered based on the condition of a particular log event ID, it uses standard alarm detection. SCS will subscribe to the event with the Message Server. Message Server is the application that will actually detect the log event having occurred and notify SCS. To support this, the application generating the log event must have been configured for network logging, namely sending its logging to the Message Server.

Se um alarme estiver configurado para ser acionado com base na condição de um determinado ID de evento de log, ele usará a detecção de alarme padrão. O SCS assinará o evento com o Message Server. O Message Server é o aplicativo que realmente detectará a ocorrência do evento de log e notificará o SCS. Para isso, a aplicação que gera o evento de log deve estar configurada para log de rede, ou seja, enviar seu log para o Message Server.

**Advanced Alarm Detection(Detecção de alarme avançada)**

Advanced Alarm Detection allows an alarm to be triggered based on a variable reaching a threshold. The variable can be a system variable such as CPU or memory usage. If your environment using SNMP functionality, an alarm can be triggered based on an SNMP variable. Advanced Alarm Detection is handled by SCS and requires the creation of a Detection Script to define the variable and threshold to be used.

A Detecção de Alarme Avançada permite que um alarme seja acionado com base em uma variável que atinge um limite. A variável pode ser uma variável do sistema, como CPU ou uso de memória. Se o seu ambiente usa a funcionalidade SNMP, um alarme pode ser acionado com base em uma variável SNMP. A Detecção de Alarme Avançada é tratada pelo SCS e requer a criação de um Script de Detecção para definir a variável e o limite a ser utilizado.

![image](https://user-images.githubusercontent.com/52088444/159000004-5b840be1-55c1-47f8-ab70-5ee97427bb85.png)


**Processing and Reacting to Alarms(Processando e Reagindo a Alarmes)**

Regardless of whether standard or advanced detection was used, the processing of alarms is the same. SCS processes the alarms and provides them to GAX and GA. Scripts can also be executed in reaction to an alarm to take action such as to email an administrator.

The Standard Alarm Detection Subsystem, part of the Alarm Detection Module of SCS, subscribes with Message Server to receive notification of application log events which match those in Alarm Conditions SCS loads into active memory on startup.

The Advanced Alarm Detection Subsystem, part of the Alarm Detection Module, monitors host and process information (system variables), through SNMP clients and LCA, watching for violations of thresholds defined in all Host Resource Threshold Alarm Conditions.

Independentemente de ter sido usada a detecção padrão ou avançada, o processamento dos alarmes é o mesmo. O SCS processa os alarmes e os fornece ao GAX e GA. Os scripts também podem ser executados em reação a um alarme para executar uma ação, como enviar um e-mail a um administrador.

O Subsistema de Detecção de Alarme Padrão, parte do Módulo de Detecção de Alarme do SCS, assina com o Message Server para receber notificação de eventos de log do aplicativo que correspondem àqueles em Condições de Alarme que o SCS carrega na memória ativa na inicialização.

O Subsistema de Detecção de Alarme Avançado, parte do Módulo de Detecção de Alarme, monitora informações de host e processo (variáveis de sistema), por meio de clientes SNMP e LCA, observando violações de limites definidos em todas as Condições de Alarme de Limite de Recursos de Host.

**Question:**

How does the standard alarm detection subsystem work?

**Answer:**

A publish/subscribe mechanism is used to implement the system. SCS reads defined Alarm Conditions on startup (and is notified of new ones dynamically). SCS notifies the Message Server that it wants to receive notification of any log events on which the defined Alarm Conditions are based. That is, SCS is subscribing for messaging about this specific set of log events. This subscription process causes the Message Server to store a record in an internal data structure for each of the log events SCS has subscribed for. More specifically, this record contains the log event (which includes the App-type prefix followed by the unique message number) and the name of the subscribing application (e.g., SCS or its dbid).
**Pergunta:**

Como funciona o subsistema de detecção de alarme padrão?

**Responda:**

Um mecanismo de publicação/assinatura é usado para implementar o sistema. O SCS lê as Condições de Alarme definidas na inicialização (e é notificado de novas dinamicamente). O SCS notifica o Message Server que deseja receber notificação de quaisquer eventos de log nos quais as Condições de Alarme definidas se baseiam. Ou seja, o SCS está assinando mensagens sobre esse conjunto específico de eventos de log. Esse processo de assinatura faz com que o Message Server armazene um registro em uma estrutura de dados interna para cada um dos eventos de log para os quais o SCS se inscreveu. Mais especificamente, esse registro contém o evento de log (que inclui o prefixo do tipo de aplicativo seguido pelo número exclusivo da mensagem) e o nome do aplicativo de assinatura (por exemplo, SCS ou seu dbid).

## 8.3 View and Clear Alarms

Once an alarm condition has been triggered, it will become active and visible by GAX. In GAX, go to the System Dashboard > Alarms. 

Uma vez que uma condição de alarme tenha sido acionada, ela se tornará ativa e visível pelo GAX. No GAX, vá para Painel do sistema > Alarmes.

![image](https://user-images.githubusercontent.com/52088444/159000608-5fb6ddec-2367-42ff-ad30-005dc5582d40.png)

Alarms are cleared automatically when the alarm condition is configured with a Cancel Log Event and, once this event is received by SCS, it understands that the alarm previously raised was solved, or when a timeout was reached. For example, an alarm based on an application terminating could be configured to clear when an event occurs indicating that the application has started. 

You can manually clear an alarm from the list by selecting the checkbox to the left of it and then choosing Clear from the More menu. This is useful if the alarm does not clear itself or if you are troubleshooting and trying different solutions—you can tell easily if the alarm was retriggered.

Os alarmes são apagados automaticamente quando a condição de alarme é configurada com Cancel Log Event e, uma vez que este evento é recebido pelo SCS, ele entende que o alarme disparado anteriormente foi solucionado, ou quando um timeout foi atingido. Por exemplo, um alarme baseado no encerramento de um aplicativo pode ser configurado para apagar quando ocorrer um evento indicando que o aplicativo foi iniciado.

Você pode limpar manualmente um alarme da lista marcando a caixa de seleção à esquerda dele e escolhendo Limpar no menu Mais. Isso é útil se o alarme não se apagar sozinho ou se você estiver solucionando problemas e tentando soluções diferentes - você pode saber facilmente se o alarme foi acionado novamente.

![image](https://user-images.githubusercontent.com/52088444/159000722-8e408d62-2c5e-44af-b77e-f88a2c527cac.png)

![image](https://user-images.githubusercontent.com/52088444/159001725-3fe42976-4e60-452f-9913-ac2699549503.png)


Even after an alarm is cleared from active alarms, it will still show in past logs, such as when you look at the Centralized Log in GAX.

Mesmo depois que um alarme é apagado dos alarmes ativos, ele ainda será exibido em logs anteriores, como quando você olha o Log Centralizado no GAX.

## 8.4 Alarm Conditions(Condições de Alarme)

Alarm Conditions define the conditions under which to trigger an alarm. They are created in interfaces such as GAX or GA and are stored in the Configuration Layer. When SCS starts, it gets the alarm conditions from the Configuration Server. 

There are ten pre-defined alarm conditions provided by Genesys. Additional information on these are provided in the Management Layer User’s Guide. 

As Condições de Alarme definem as condições sob as quais disparar um alarme. Eles são criados em interfaces como GAX ou GA e são armazenados na Camada de Configuração. Quando o SCS é iniciado, ele obtém as condições de alarme do Servidor de Configuração.

Existem dez condições de alarme pré-definidas fornecidas pela Genesys. Informações adicionais sobre eles são fornecidas no Guia do usuário da camada de gerenciamento.

![image](https://user-images.githubusercontent.com/52088444/159004404-47e49bf7-8549-42bd-8873-c2f5e3bf6dae.png)

## 8.5 Configuring Alarm Conditions(Configurando Condições de Alarme)

In addition to the pre-defined alarm conditions, you can define your own custom alarm conditions. In GAX, go to Configuration > Environment > Alarm Conditions. Here you can create a new custom alarm condition by clicking New, as seen in the following image. 

Além das condições de alarme predefinidas, você pode definir suas próprias condições de alarme personalizadas. No GAX, vá para Configuração > Ambiente > Condições de alarme. Aqui você pode criar uma nova condição de alarme personalizada clicando em Novo, como pode ser visto na imagem a seguir.

![image](https://user-images.githubusercontent.com/52088444/159004578-dd619e0c-3018-42ee-821a-9ff980037fd1.png)

![image](https://user-images.githubusercontent.com/52088444/159004608-a8aa2ccd-fc04-4398-b634-92b60ead21c9.png)

All of the alarm conditions are stored in the Configuration Layer, including the custom alarm conditions. When you create your alarm condition you must complete the following required fields: 

- Name—Give the Alarm Condition a Name. This is what you will see as the name of the alarm when viewing active alarms. Optionally you may enter a description.
- Category—Specify the severity of the alarm. This is simply a descriptor. Category assignments are not used by the Genesys software, but you can use them to help define business policies for handling some alarms before others. The category can be set as Critical, Major, or Minor.
- Cancel Timeout—Specify the amount of time before the alarm should be automatically cleared. Cancel Timeout is the length of time after which an alarm will be automatically cleared from active alarms if it is still there. The default, 86400 seconds, is equivalent to 24 hours.

![image](https://user-images.githubusercontent.com/52088444/159005070-f5f022b1-4ff3-47f1-ab96-b597ff82f906.png)

- Detection Script—When an Alarm Condition object refers to an Alarm Detection Script, the alarm detection for this Alarm Condition is performed according to the specified Alarm Detection Script, regardless of whether any log event is specified as a Detection Event. Alarm Detection Scripts identify the system variables which the Management Layer must monitor in order to trigger an alarm. An Alarm Detection Script does nothing unless it's associated with an Alarm Condition.
- Detect Log Event ID—Specify the Detect Log Event ID, which is the code for the log event that triggers the alarm. The Framework 8.x Combined Log Events Help file contains descriptions of Log Events generated by Genesys components.  

Note:To access the Log Events file, you may be required to log into your Customer Care account. For more information, please contact Customer Care. The Log Events Help file is available here.

Observação: para acessar o arquivo de eventos de log, pode ser necessário fazer login em sua conta de atendimento ao cliente. Para obter mais informações, entre em contato com o Atendimento ao cliente. O arquivo de ajuda de eventos de log está disponível aqui.

In this example, log event "5064" was chosen as the event that would trigger the alarm. 

If you want the alarm to be triggered by an application, you have three different options. The alarm can be triggered by any application, any application of a certain type, or by a specific application. All three options are configured using Detect Selection, Application, and Type. In this example, only ChicagoSIPServer is being watched. It is configured under Detect Selection > Select By Application > Application > ChicagoSIPServer.

Specify which Cancel Log Event ID you would like to clear the alarm. If the cancel log event occurs, then the alarm is cleared. In this example, log event "5064" corresponds to the application being terminated and log event "5060" corresponds to the application being started. Log event "5060" clears the alarm, but it still shows in the alarm history in GAX. 

Neste exemplo, o evento de log "5064" foi escolhido como o evento que acionaria o alarme.

Se você quiser que o alarme seja acionado por um aplicativo, você tem três opções diferentes. O alarme pode ser acionado por qualquer aplicativo, qualquer aplicativo de um determinado tipo ou por um aplicativo específico. Todas as três opções são configuradas usando Detect Selection, Application e Type. Neste exemplo, apenas ChicagoSIPServer está sendo observado. Ele é configurado em Detect Selection > Select By Application > Application > ChicagoSIPServer.

Especifique qual ID de evento de registro de cancelamento você gostaria de limpar o alarme. Se o evento de registro de cancelamento ocorrer, o alarme será apagado. Neste exemplo, o evento de log "5064" corresponde ao aplicativo que está sendo encerrado e o evento de log "5060" corresponde ao aplicativo que está sendo iniciado. O evento de log "5060" limpa o alarme, mas ainda aparece no histórico de alarmes no GAX.

![image](https://user-images.githubusercontent.com/52088444/159005269-e20e74ff-b727-4e48-9e0b-bd282f61d0a9.png)


## 8.6 Alarm Reaction Scripts(Scripts de Reação de Alarme)

Alarm Reaction Scripts identify what the Management Layer must do when alarms occur in, or are cleared from, the system. Alarm Reaction Scripts that identify what happens when alarms are cleared are referred to as Alarm Clearance Scripts.

- There are no predefined Alarm Reaction Scripts. 
- Once created, you can reuse reaction scripts by assigning them to more than one condition.

SCS can execute one or more reaction scripts when an alarm is triggered and/or when an alarm is cleared. Reaction scripts can be specified for pre-defined alarm conditions and custom alarm conditions.

Os scripts de reação de alarme identificam o que a Managment Layer deve fazer quando os alarmes ocorrem ou são eliminados do sistema. Os scripts de reação de alarme que identificam o que acontece quando os alarmes são eliminados são chamados de scripts de liberação de alarme( Alarm Clearance Scripts).

- Não há scripts de reação de alarme predefinidos.
- Uma vez criado, você pode reutilizar os scripts de reação atribuindo-os a mais de uma condição.

O SCS pode executar um ou mais scripts de reação quando um alarme é acionado e/ou quando um alarme é liberado. Os scripts de reação podem ser especificados para condições de alarme predefinidas e condições de alarme personalizadas.

![image](https://user-images.githubusercontent.com/52088444/159005653-35f221de-6e6e-4f0b-8745-97f9cb49477c.png)

Alarm Reactions are stored in the Scripts folder (table cfg_alarm_script in the database) and instruct SCS of the behavior it will execute upon notification of a configured Alarm Condition. 

Not every condition needs a reaction. Alarm Conditions don’t necessarily need to have automatic reactions, but there are many instances when they can handle situations without the need for intervention by a system administrator. 

On the other hand, there may be highly critical situations that require the system administrator’s immediate attention. Some businesses may choose not to have this person watching the status of every component every moment of the day. In cases like this, the administrator can be notified via email, for example, that certain conditions exist in the environment.

As Reações de Alarme são armazenadas na pasta Scripts (tabela cfg_alarm_script no banco de dados) e instruem o SCS sobre o comportamento que ele executará mediante notificação de uma Condição de Alarme configurada.

Nem toda condição precisa de uma reação. As Condições de Alarme não precisam necessariamente ter reações automáticas, mas há muitos casos em que podem lidar com situações sem a necessidade de intervenção de um administrador do sistema.

Por outro lado, pode haver situações altamente críticas que exijam a atenção imediata do administrador do sistema. Algumas empresas podem optar por não ter essa pessoa observando o status de cada componente a cada momento do dia. Em casos como esse, o administrador pode ser notificado por e-mail, por exemplo, que existem determinadas condições no ambiente.

## 8.7 Configuring Alarm Reaction Scripts(Configurando Scripts de Reação de Alarme)

To create alarm reaction scripts in GAX, go to Configuration > Environment > Detection/Reaction Scripts. 

To create the reaction script, you need to specify a Name. 

Set the Script Type, which would either be Alarm Reaction or Alarm Detection. Alarm Detection is used to set up a script for advanced alarm detection. 

In this example, you are creating an alarm reaction. 

Para criar scripts de reação de alarme no GAX, vá para Configuration > Environment > Detection/Reaction Scripts.

Para criar o script de reação, você precisa especificar um Nome.

Defina o Tipo de Script, que seria Reação de Alarme ou Detecção de Alarme. A detecção de alarme é usada para configurar um script para detecção avançada de alarme.

Neste exemplo, você está criando uma reação de alarme.

![image](https://user-images.githubusercontent.com/52088444/159006520-d871253f-bed8-4264-9109-ce83bd05cbe7.png)

Specify the Alarm Reaction Type. There are nine possible reaction types to choose from in the drop-down list:

1 - Start a Specified Application

2 - Stop a Specified Application

Example:

Start or Stop an Application controls a third-party server in response to a failure.

3 - Restart the Application that Generated the Alarm

Normally not used if autorestart is enabled on the application object. If autorestart is disabled and restart is desired based only on a certain condition, then a reaction of this type could be used.

Example:

There is a leak in system resources and an application can't work properly or is unstable. You know that the application will issue a particular log event in this case and you know that after a restart the situation will be improved because the OS will clean up the leak. So you implement a "restart application" in response to this event.

4 - Start a Specified Solution

Example:

A failure might be due to some components being down. One reaction might be to issue a start command for all components in the solution.

5 - Send an Email

Example:

Administrators can be notified of critical alarms by email. 

See the Framework 8.x Management Layer User’s Guide for configuration requirements for Windows and Unix.

Especifique o Tipo de Reação de Alarme. Existem nove tipos de reação possíveis para escolher na lista suspensa:

1 - Iniciar um aplicativo especificado

2 - Parar um aplicativo especificado

Exemplo:

Iniciar ou parar um aplicativo controla um servidor de terceiros em resposta a uma falha.

3 - Reinicie o Aplicativo que Gerou o Alarme

Normalmente não é usado se a inicialização automática estiver habilitada no objeto do aplicativo. Se a reinicialização automática estiver desabilitada e a reinicialização for desejada com base apenas em uma determinada condição, uma reação desse tipo poderá ser usada.

Exemplo:

Há um vazamento nos recursos do sistema e um aplicativo não pode funcionar corretamente ou está instável. Você sabe que o aplicativo emitirá um evento de log específico nesse caso e sabe que após uma reinicialização a situação será melhorada porque o sistema operacional limpará o vazamento. Então você implementa um "reiniciar aplicativo" em resposta a esse evento.

4 - Iniciar uma solução especificada

Exemplo:

Uma falha pode ser devido a alguns componentes estarem inativos. Uma reação pode ser emitir um comando de início para todos os componentes da solução.

5 - Envie um e-mail

Exemplo:

Os administradores podem ser notificados de alarmes críticos por e-mail.

Consulte o Guia do usuário da camada de gerenciamento do Framework 8.x para obter os requisitos de configuração para Windows e Unix.

Nota: Alarm signaling functionality enables email reactions to be sent via Simple Mail Transfer Protocol (SMTP) as well as Messaging API (MAPI.)

Nota: A funcionalidade de sinalização de alarme permite que as reações de e-mail sejam enviadas via Simple Mail Transfer Protocol (SMTP), bem como API de mensagens (MAPI).

You can customize the Subject line and body of an Alarm Reaction email by creating a template using plain text and any of the following reserved variables:

$REACT_NAME—The name of the Alarm Reaction
$COND_ID—The Alarm Condition ID
$COND_CTGR—The category of the Alarm Condition
$APP_ID—The Application ID
$APP_NAME—The name of the Application
$APP_TYPE—The Application type
$MSG_ID—The Message ID
$MSG_DESCR—The text of the Message
$$—The dollar sign character ($)
For each use of the Alarm Reaction script, the email text will be customized for the specific situation.

Você pode personalizar a linha de assunto e o corpo de um e-mail de reação de alarme criando um modelo usando texto simples e qualquer uma das seguintes variáveis reservadas:

$REACT_NAME—O nome da reação de alarme
$COND_ID—O ID da condição de alarme
$COND_CTGR—A categoria da Condição de Alarme
$APP_ID—O ID do aplicativo
$APP_NAME—O nome do aplicativo
$APP_TYPE—O tipo de aplicativo
$MSG_ID—O ID da mensagem
$MSG_DESCR—O texto da mensagem
$$—O caractere cifrão ($)
Para cada uso do script Alarm Reaction, o texto do e-mail será personalizado para a situação específica.

Example:

Assume the following email message is in the Alarm Reaction cpu_overload_mail: 

Subject: $COND_ID detected in $APP_NAME
Message: CPU Overload has been detected by Genesys Solution Management

Layer for Host1.
Alarm Reaction: $REACT_NAME

Alarm Condition:
ID: $COND_ID
NAME: $COND_NAME
Category: $COND_CTGR
Application: ID: $APP_ID
Name: $APP_NAME
Type: $APP_TYPE

If the alarm is triggered, the following email is sent in response:

Subject: CPU_overload detected in Solution Control Server
Message: CPU Overload has been detected by Genesys Solution Management

Layer for Host1.
Alarm Reaction: cpu_overload_mail

Alarm Condition:
ID: 118
NAME: CPU_overload
Category: Major
Application: ID: 105
Name: SolutionControlServer
Type: SCS



Exemplo:

Suponha que a seguinte mensagem de e-mail esteja na reação de alarme cpu_overload_mail:

Assunto: $COND_ID detectado em $APP_NAME
Mensagem: A sobrecarga da CPU foi detectada pelo Genesys Solution Management

Camada para Host1.
Reação de alarme: $REACT_NAME

Condição de alarme:
Código: $COND_ID
NOME: $COND_NAME
Categoria: $COND_CTGR
Aplicativo: ID: $APP_ID
Nome: $APP_NAME
Tipo: $APP_TYPE

Se o alarme for acionado, o seguinte e-mail será enviado em resposta:

Assunto: CPU_overload detectado no Solution Control Server
Mensagem: A sobrecarga da CPU foi detectada pelo Genesys Solution Management

Camada para Host1.
Reação de alarme: cpu_overload_mail

Condição de alarme:
ID: 118
NOME: CPU_overload
Categoria: Maior
Aplicação: ID: 105
Nome: SolutionControlServer
Tipo: SC

Note:How the variable names have been replaced with actual values that are appropriate to the alarm scenario.

Observação: como os nomes das variáveis foram substituídos por valores reais que são apropriados para o cenário de alarme.


6 - Send an SNMP Trap(Envie uma trap SNMP)

To transmit the content of an alarm message to an SNMP-compliant third-party NMS, the Management Layer converts that information into an SNMP trap. A license is required for this functionality. 

A diagram of the process is shown below:

Para transmitir o conteúdo de uma mensagem de alarme para um NMS de terceiros compatível com SNMP, a camada de gerenciamento converte essas informações em uma interceptação SNMP. É necessária uma licença para esta funcionalidade.

Um diagrama do processo é mostrado abaixo:

![image](https://user-images.githubusercontent.com/52088444/159007637-71329e4b-b7b0-45d8-9bab-b024e9b352a8.png)

7 - Switch Over to the Backup Application

You must have a high-availability (HA) license to enable Solution ControlServer to successfully process an Alarm Reaction of the Switchover type. The lack of the license prevents the switchover between primary and backup applications of any type.

Example:

If the primary T-Server gets a CTI Link Disconnected log event, the backup can be made primary.

8 - Execute OS Command

SCS executes the specified command on its own host computer. Therefore, the user account used to start SCS must have sufficient permissions to execute the specified operating system command.

SCS passes information about a detected alarm to the operating system command to be executed. Some applications started as a result of the Execute OS Command Alarm Reaction may not recognize the command line arguments added by SCS. This means, these applications might not work properly in this circumstance. For instance, they might exit. To make them work, you can call such applications indirectly. For instance, from within a script that passes correct command-line parameters to these applications. You then specify the name of this script in the Command property of the Alarm Reaction.

9 - Change Application Option

Example:

You might configure this Alarm Reaction so that an application changes its log level to a more detailed one once the application reports the first signs of a critical situation in a particular log event.

7 - Mude para o aplicativo de backup

Você deve ter uma licença de alta disponibilidade (HA) para permitir que o Solution ControlServer processe com sucesso uma reação de alarme do tipo Switchover. A falta da licença impede a alternância entre aplicativos primários e de backup de qualquer tipo.

Exemplo:

Se o T-Server primário obtiver um evento de log CTI Link Disconnected, o backup poderá se tornar primário.

8 - Execute o comando do SO

O SCS executa o comando especificado em seu próprio computador host. Portanto, a conta de usuário usada para iniciar o SCS deve ter permissões suficientes para executar o comando do sistema operacional especificado.

O SCS passa informações sobre um alarme detectado para o comando do sistema operacional a ser executado. Alguns aplicativos iniciados como resultado da reação de alarme do comando Execute OS podem não reconhecer os argumentos de linha de comando adicionados pelo SCS. Isso significa que esses aplicativos podem não funcionar corretamente nessa circunstância. Por exemplo, eles podem sair. Para fazê-los funcionar, você pode chamar esses aplicativos indiretamente. Por exemplo, de dentro de um script que passa parâmetros de linha de comando corretos para esses aplicativos. Em seguida, você especifica o nome desse script na propriedade Command da Reação de alarme.

9 - Alterar Opção de Aplicação

Exemplo:

Você pode configurar essa reação de alarme para que um aplicativo altere seu nível de log para um mais detalhado assim que o aplicativo relatar os primeiros sinais de uma situação crítica em um evento de log específico.

Note:The Alarm Reaction will not work unless the SYSTEM account has at least change permission against the application.

Observação: a reação de alarme não funcionará a menos que a conta SYSTEM tenha pelo menos permissão de alteração no aplicativo.

If you don’t specify the application name, the Management Layer updates the option configuration of the application that triggers the alarm. 

Once you select the alarm reaction type you wish to use, the remaining properties of the Alarm reaction, if any, are determined by the reaction type you choose. (See the list of alarm reaction types above.) 

If you choose the Alarm Reaction Type: Start a specified application, you would be required to specify which application you wish to start. 

If you choose the Alarm Reaction Type: Send an email, you would be presented with additional parameters to complete. You would have to specify the email address of the recipient, the subject of the email, and the body of the email message (including the variables for customization).

Se você não especificar o nome do aplicativo, a camada de gerenciamento atualiza a configuração da opção do aplicativo que aciona o alarme.

Depois de selecionar o tipo de reação de alarme que deseja usar, as propriedades restantes da reação de alarme, se houver, são determinadas pelo tipo de reação escolhido. (Consulte a lista de tipos de reação de alarme acima.)

Se você escolher o Tipo de Reação de Alarme: Iniciar um aplicativo especificado, você deverá especificar qual aplicativo deseja iniciar.

Se você escolher o Tipo de Reação de Alarme: Envie um e-mail, você receberá parâmetros adicionais para completar. Você teria que especificar o endereço de e-mail do destinatário, o assunto do e-mail e o corpo da mensagem de e-mail (incluindo as variáveis para personalização).

![image](https://user-images.githubusercontent.com/52088444/159007879-84eace5f-e88a-4e35-927a-e6e0effa3849.png)

## 8.8 Assign Reactions Scripts and Clearance Scripts(Atribuir Scripts de Reação e Scripts de Liberação)

To associate the script to the alarm condition, go to GAX > Configuration > Environment > Alarm Conditions. This can be a pre-defined alarm condition or a custom alarm condition that you have created. Start by editing the properties of the alarm condition. The basic information is found on the General tab, including Name, Category, and what is triggering the alarm.

Para associar o script à condição de alarme, acesse GAX > Configuration > Environment > Alarm Conditions. Esta pode ser uma condição de alarme predefinida ou uma condição de alarme personalizada que você criou. Comece editando as propriedades da condição de alarme. As informações básicas são encontradas na guia Geral, incluindo Nome, Categoria e o que está acionando o alarme.

![image](https://user-images.githubusercontent.com/52088444/159008025-9a82ff10-4f22-4b5e-a134-b6f9a4f872ca.png)

Reaction Scripts can be used for multiple alarm conditions. Within an alarm condition, you can specify reaction script(s) for when the alarm is triggered and also reaction script(s) for when the alarm is cleared. The latter is also referred to as a Clearance Script. 

Os Scripts de Reação podem ser usados para várias condições de alarme. Dentro de uma condição de alarme, você pode especificar script(s) de reação para quando o alarme é acionado e também script(s) de reação para quando o alarme é apagado. Este último também é referido como um Script de Autorização.

![image](https://user-images.githubusercontent.com/52088444/159008127-07dc0eef-85a6-4c89-b788-d79f3ee8c6cf.png)

The reaction scripts are added by clicking Add on the Reaction Scripts tab. Using this screen, you can associate one or more reaction scripts that you want to execute when the Alarm is triggered. 

An Alarm Clearance Reaction is created if the Alarm Condition you are configuring has a Cancel Event (also known as a "clearance event"). The Alarm Clearance Reaction will occur in response to the Cancel Event. 

There is also a Clearance Script tab which allows the addition of scripts that will execute when the alarm is cleared. Associate these by clicking Add on the Clearance Scripts tab.

Os scripts de reação são adicionados clicando em Adicionar na guia Scripts de reação. Usando esta tela, você pode associar um ou mais scripts de reação que deseja executar quando o Alarme for acionado.

Uma reação de liberação de alarme é criada se a condição de alarme que você está configurando tiver um evento de cancelamento (também conhecido como "evento de liberação"). A Reação de Liberação de Alarme ocorrerá em resposta ao Evento de Cancelamento.

Há também uma guia Clearance Script que permite a adição de scripts que serão executados quando o alarme for cancelado. Associe-os clicando em Adicionar na guia Scripts de liberação.

![image](https://user-images.githubusercontent.com/52088444/159008217-d0d0b0d4-7b0d-4cf7-8fef-25fcec964da9.png)

## 8.9 Test Alarm Conditions and Reactions(Condições e reações de alarme de teste)

You can test an alarm condition by causing the condition that will trigger the alarm, but that is not always easy or possible. Another way is to manually trigger the alarm for testing its appearance and the reactions. 

To manually activate an alarm condition, in GAX go to Configuration > Environment > Alarm Conditions. Check the box to the left of the alarm condition you want to activate. Next, from the More menu, choose Activate Alarm. 

Você pode testar uma condição de alarme causando a condição que acionará o alarme, mas isso nem sempre é fácil ou possível. Outra maneira é acionar manualmente o alarme para testar sua aparência e as reações.

Para ativar manualmente uma condição de alarme, no GAX vá para Configuração > Ambiente > Condições de Alarme. Marque a caixa à esquerda da condição de alarme que deseja ativar. Em seguida, no menu Mais, escolha Ativar alarme.

![image](https://user-images.githubusercontent.com/52088444/159008336-59d1a839-1b39-40d1-aa56-0631391196c4.png)

Specify the application that "caused" the alarm to occur in this test. Browse to select the application name, and click Activate.

Especifique o aplicativo que "causou" a ocorrência do alarme neste teste. Navegue para selecionar o nome do aplicativo e clique em Ativar.

Note:In order for the alarm test to work, the SYSTEM account needs to have Read and Execute permissions on the Alarm Condition object. If the test does not work, check the permissions. 

Observação: para que o teste de alarme funcione, a conta SYSTEM precisa ter permissões de leitura e execução no objeto de condição de alarme. Se o teste não funcionar, verifique as permissões.

![image](https://user-images.githubusercontent.com/52088444/159008506-426e0dbd-c5d2-43ae-987a-97a6d7b8969b.png)

O alarme então aparece em Alarmes Ativos como se tivesse sido acionado com a condição real e o script de reação é executado como se o alarme realmente tivesse ocorrido, mesmo sendo um teste. Isso permite que você veja o comportamento do alarme e dos scripts antes de colocá-los em produção.

8.10 Learning Summary

Now that you have completed this chapter, you should be able to do the following: 

1 - Explain Alarm Management.

2 - Configure Alarm Conditions. 

3 - Configure Alarm Reactions. 

4 - View, clear, and test Alarms. 

Agora que você concluiu este capítulo, você deve ser capaz de fazer o seguinte:

1 - Explicar o Gerenciamento de Alarmes.

2 - Configure as Condições de Alarme.

3 - Configure as reações de alarme.

4 - Visualize, limpe e teste os alarmes.