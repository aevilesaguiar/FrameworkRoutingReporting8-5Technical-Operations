## 7.1 Learning Objectives

After completing this chapter, you should be able to do the following: 

1- Describe log levels.

2 - Describe log elements.

3 - Describe where to view Genesys logs (log outputs).

4 - Use Genesys Administrator Extension to view logs.

5 - Configure logging.

Depois de concluir este capítulo, você deve ser capaz de fazer o seguinte:

1- Descreva os níveis de log.

2 - Descreva os elementos do log.

3 - Descreva onde visualizar os logs do Genesys (saídas de log).

4 - Use o Genesys Administrator Extension para visualizar os logs.

5 - Configure o log.


## 7.2 Logging: Log Messages (Events)

Genesys logging provides information about how your Genesys system is running. It provides detail information of interaction flows, client-server communication, server information, and server problems. 

A log is a record of data about an application event. Logging is the main tool used to diagnose and troubleshoot a Genesys installation. 

Log events include status changes and error conditions that can be logged by an application.
When a log event occurs in run time, the application must determine (a) whether or not to record the event and (b) where to send the event message if it should be recorded.

Administrators configure the log options that determine application logging behavior, as well as the location they wish to store or view the logs: The Log Database (viewable in Genesys Administrator), log files, or console windows.

Each log message belongs to a particular logging level:

- Standard—The errors and major events, e.g., application started   
- Interaction—The event and request messaging from interaction flows, e.g., requestanswercall 
- Trace—The minor events
- Debug—The detailed actions and data 

Administrators can set up the logging capabilities of each application in the manner that is most useful to that specific environment. If you are in a test environment, then you may want the most detailed logs—debug level—to help you troubleshoot and tune.

O registro Genesys fornece informações sobre como seu sistema Genesys está funcionando. Ele fornece informações detalhadas de fluxos de interação, comunicação cliente-servidor, informações do servidor e problemas do servidor.

Um log é um registro de dados sobre um evento de aplicativo. O registro é a principal ferramenta usada para diagnosticar e solucionar problemas de uma instalação do Genesys.

Os eventos de log incluem alterações de status e condições de erro que podem ser registradas por um aplicativo.
Quando um evento de log ocorre em tempo de execução, o aplicativo deve determinar (a) se deve ou não registrar o evento e (b) para onde enviar a mensagem do evento caso ela seja gravada.

Os administradores configuram as opções de log que determinam o comportamento de log do aplicativo, bem como o local em que desejam armazenar ou visualizar os logs: O banco de dados de log (visível no Genesys Administrator), arquivos de log ou janelas do console.

Cada mensagem de log pertence a um nível de log específico:

- Padrão—Os erros e eventos principais, por exemplo, aplicação iniciada
- Interação—As mensagens de evento e solicitação dos fluxos de interação, por exemplo, requestanswercall
- Trace—Os eventos menores
- Depurar—As ações e dados detalhados

Os administradores podem configurar os recursos de log de cada aplicativo da maneira mais útil para esse ambiente específico. Se você estiver em um ambiente de teste, talvez queira os logs mais detalhados — nível de depuração — para ajudá-lo a solucionar problemas e ajustar.

nota: Debug level logging is only accessible via log files and console windows.

nota: O log de nível de depuração só é acessível por meio de arquivos de log e janelas do console.

##  7.3 Viewing Log Messages(Visualizando Mensagens de Log)

Log files can be viewed in various locations and formats, as long as the administrator has configured the applications to create them.

Os arquivos de log podem ser visualizados em vários locais e formatos, desde que o administrador tenha configurado os aplicativos para criá-los.

![image](https://user-images.githubusercontent.com/52088444/158866871-2242a2bf-4fe3-4770-bebc-730c38498221.png)

Logging can be sent to a log file. In this instance, a plain text file is opened in a text editor and the details of the log file can be viewed. 

Similar information can be sent to a console window. This would normally be used in a lab environment, and not in a production environment. The console window is only helpful when the application itself is started using a console window (for example, using the DOS Command Prompt to start the application you are trying to run). If logging is configured to go to the console, it would display directly in the window. This is especially helpful for troubleshooting the startup of an application that is not generating a log file.

Another option is Genesys Administrator or Genesys Administrator Extension. They rely on the Management Layer, putting logs into the Log Database. GA or GAX is set up to retrieve the logs from there. The interface from either GAX or GA only retrieves records from three of the four log levels. The Standard, Interaction, and Trace levels all follow the same format in terms of the information provided in each record.

Debug level records do not follow the same format. Therefore, they are not stored in the log database and will not be available for viewing in Genesys Administrator Extension.

O registro pode ser enviado para um arquivo de registro. Nesse caso, um arquivo de texto simples é aberto em um editor de texto e os detalhes do arquivo de log podem ser visualizados.

Informações semelhantes podem ser enviadas para uma janela do console. Isso normalmente seria usado em um ambiente de laboratório e não em um ambiente de produção. A janela do console só é útil quando o próprio aplicativo é iniciado usando uma janela do console (por exemplo, usando o prompt de comando do DOS para iniciar o aplicativo que você está tentando executar). Se o registro estiver configurado para ir para o console, ele será exibido diretamente na janela. Isso é especialmente útil para solucionar problemas de inicialização de um aplicativo que não está gerando um arquivo de log.

Outra opção é Genesys Administrator ou Genesys Administrator Extension. Eles contam com a camada de gerenciamento, colocando logs no banco de dados de logs. GA ou GAX está configurado para recuperar os logs de lá. A interface do GAX ou GA recupera apenas registros de três dos quatro níveis de log. Os níveis Padrão, Interação e Rastreamento seguem o mesmo formato em relação às informações fornecidas em cada registro.

Os registros de nível de depuração não seguem o mesmo formato. Portanto, eles não são armazenados no banco de dados de log e não estarão disponíveis para exibição no Genesys Administrator Extension.

## 7.4 Common Log Event Elements(Elementos de eventos de log comuns)

All log records (except debug-level records*) contain a common set of data elements:

Todos os registros de log (exceto registros de nível de depuração*) contêm um conjunto comum de elementos de dados:

![image](https://user-images.githubusercontent.com/52088444/158867706-62a7b343-c23d-459c-aebb-835e534ee881.png)

- Level—The log level of the log, either Alarm, Standard, Interaction, or Trace.
-  ID–The unique identifier of the log. The ID can be used to locate additional information about the Application ID of the Application that generated the log and numeric identifier of the log message.
- Description—The text of the log message.
- Host—The host on which the Application that generated the log was running.
- App—The name of the Application that generated the log.
- Date—The date and time when the log was generated.
- Interaction ID—The identifier of the interaction for which this log was generated. This attribute appears only for Interaction-level logs.

* Debug-level records do not conform to any particular standard.

- Level—O nível de log do log, seja Alarm, Standard, Interaction ou Trace.
- ID–O identificador exclusivo do log. O ID pode ser usado para localizar informações adicionais sobre o ID do Aplicativo do Aplicativo que gerou o log e o identificador numérico da mensagem de log.
- Descrição—O texto da mensagem de log.
- Host—O host no qual o Aplicativo que gerou o log estava sendo executado.
- App—O nome do aplicativo que gerou o log.
- Data—A data e hora em que o log foi gerado.
- ID da interação — O identificador da interação para a qual este log foi gerado. Esse atributo aparece apenas para logs de nível de interação.

* Os registros de nível de depuração não estão em conformidade com nenhum padrão específico.

## 7.5 Log File Name

When an application is set to save logging to a log file, a file name is configured as well. Additional characters are added to it to create the actual file name. For example, the log files in the image below are both named DBServer. The rest of the file names have automatically been added by Genesys, as follows:

Quando um aplicativo é configurado para salvar o log em um arquivo de log, um nome de arquivo também é configurado. Caracteres adicionais são adicionados a ele para criar o nome real do arquivo. Por exemplo, os arquivos de log na imagem abaixo são ambos denominados DBServer. O restante dos nomes de arquivo foram adicionados automaticamente pela Genesys, como segue:

![image](https://user-images.githubusercontent.com/52088444/158868309-cbab52f7-ba83-442e-87ff-c44400683266.png)

The date and timestamp are when the file was created. You would look for the latest date and time to find the most recent log file. The date format is YYYYMMDD. The timestamp is HHMMSS_sss with the last portion as milliseconds. 

Finally, the main extension for a log file is .log. However, when running an application, it will keep a locked file with extension .snapshot.log which is used like a buffer for writing to log files. The snapshot file is automatically opened and closed during application startup and shutdown. When viewing logs for an application, you look for the file without the word snapshot in the extension.

A data e o carimbo de data/hora são quando o arquivo foi criado. Você procuraria a data e hora mais recentes para encontrar o arquivo de log mais recente. O formato de data é AAAAMMDD. O carimbo de data/hora é HHMMSS_sss com a última parte em milissegundos.

Finalmente, a extensão principal de um arquivo de log é .log. No entanto, ao executar um aplicativo, ele manterá um arquivo bloqueado com extensão .snapshot.log que é usado como um buffer para gravação em arquivos de log. O arquivo de instantâneo é aberto e fechado automaticamente durante a inicialização e o desligamento do aplicativo. Ao visualizar os logs de um aplicativo, você procura o arquivo sem a palavra snapshot na extensão.

## 7.6 Viewing Logs in GAX

To view logs in GAX, go to GAX > Centralized Log. By default you will be viewing a list of all the logs that are organized into columns. 

Para visualizar os logs no GAX, vá para GAX > Log Centralizado. Por padrão, você verá uma lista de todos os logs organizados em colunas.


![image](https://user-images.githubusercontent.com/52088444/158868695-df111344-198b-4ae5-9291-a6ea7787f424.png)


Each log message displays the following fields:

- ID–The unique identifier of the log event.
- Generated–The date and time the log event occurred.
- Text–A description of the log event.
- Application–The name of the Application that reported the log event.
- Host–The host where the Application resides

Results can be sorted in ascending and descending order by clicking on each column name.

When viewing the Centralized Log, keep in mind there are typically multiple views of log messages which can be seen by applying different possible values in the given field as shown in the below image. There is also an icon to refresh and retrieve the most recent log records from the database.


Cada mensagem de log exibe os seguintes campos:

- ID–O identificador exclusivo do evento de log.
- Gerado – A data e hora em que o evento de log ocorreu.
- Texto–Uma descrição do evento de log.
- Aplicativo – o nome do aplicativo que relatou o evento de log.
- Host–O host onde o Aplicativo reside

Os resultados podem ser classificados em ordem crescente e decrescente clicando no nome de cada coluna.

Ao visualizar o log centralizado, lembre-se de que normalmente há várias exibições de mensagens de log que podem ser vistas aplicando diferentes valores possíveis no campo fornecido, conforme mostrado na imagem abaixo. Há também um ícone para atualizar e recuperar os registros de log mais recentes do banco de dados.

![image](https://user-images.githubusercontent.com/52088444/158869132-9aa6f1b4-6065-4dac-bd2e-800d673aec23.png)

Different Filters allow you to see logs in a particular level (Standard, Interaction, Trace), or a particular type (Alarm, Audit). Alarm logs can relate to past alarms that have been already cleared. Audit logs, if configured, track solution control and configuration activity in terms of who did what and when.

Filtros diferentes permitem que você veja logs em um nível específico (Padrão, Interação, Rastreamento) ou em um tipo específico (Alarme, Auditoria). Os logs de alarme podem estar relacionados a alarmes anteriores que já foram apagados. Os logs de auditoria, se configurados, rastreiam o controle da solução e a atividade de configuração em termos de quem fez o quê e quando.

![image](https://user-images.githubusercontent.com/52088444/158869290-1ace540b-5fbd-4ebd-a862-42bcf868323e.png)

You can click the Search button (the button on the right, shown in the following image) to turn on Filters. Filters let you reduce the logs listed to just the ones you want, such as listing only those with the word “Answer” within the Text. After changing filter values, click Search to update the list. Click Reset All Filter to return to the full list.

Você pode clicar no botão Pesquisar (o botão à direita, mostrado na imagem a seguir) para ativar os Filtros. Os filtros permitem que você reduza os logs listados apenas para aqueles que você deseja, como listar apenas aqueles com a palavra “Resposta” no Texto. Após alterar os valores do filtro, clique em Pesquisar para atualizar a lista. Clique em Redefinir todos os filtros para retornar à lista completa.

## 7.7 Log Record Maintenance(Manutenção de registro de log)

Navigate to GAX > Centralized Log. Click Trash button at the top of the page to delete records as shown in the following image. To delete logs in the Log Database from GAX, select the records you want to delete, then click the Trash Button as shown in the following image.

Navegue até GAX > Log centralizado. Clique no botão Lixeira na parte superior da página para excluir registros, conforme mostrado na imagem a seguir. Para excluir logs no banco de dados de log do GAX, selecione os registros que deseja excluir e clique no botão Trash conforme mostrado na imagem a seguir.

![image](https://user-images.githubusercontent.com/52088444/158869923-fde41c5c-82a2-4efd-93ef-c83b97f53e07.png)

Log records can be deleted based on: Log Type, Level, Time Generated, Source (Application, Host, Solution), or Extended Attribute.

Os registros de log podem ser excluídos com base em: Tipo de Log, Nível, Tempo Gerado, Origem (Aplicativo, Host, Solução) ou Atributo Estendido.

Note: Logs stored in the Log Database are not automatically purged, so the Log Maintenance Wizard must be used to purge older records, or a DBA should configure a stored procedure/job to automatically purge old records.

Observação: os logs armazenados no banco de dados de log não são limpos automaticamente, portanto, o Assistente de manutenção de log deve ser usado para limpar registros mais antigos ou um DBA deve configurar um procedimento/trabalho armazenado para limpar automaticamente os registros antigos.

## 7.8 Network Logging(Registro de Rede)

Network logging is the term for what makes logging available. If the application is configured for network logging, then logging can write to the Log Database. 

Example:

As shown in the image below, when T-Server or SIP Server is configured for network logging, it sends its log messages to the message server (write). Message Server sends the log messages to the Log Database (write), where they are made available for viewing (read) using GAX. 

7.8 Registro de Rede
O log de rede é o termo para o que torna o log disponível. Se o aplicativo estiver configurado para log de rede, o log poderá gravar no banco de dados de log.

Exemplo:

Conforme mostrado na imagem abaixo, quando o T-Server ou SIP Server é configurado para registro em rede, ele envia suas mensagens de registro para o servidor de mensagens (gravação). O Message Server envia as mensagens de log para o Log Database (gravação), onde são disponibilizadas para visualização (leitura) usando GAX.

![image](https://user-images.githubusercontent.com/52088444/158870439-61b435d2-0ac2-4c0a-9884-e7ca91e22553.png)

If network logging has not been configured, the Centralized Log in GAX will not display any log messages. 

Configuring network logging is covered in the Framework Routing & Reporting 8.5 Administration course.

Se o log de rede não tiver sido configurado, o Log Centralizado no GAX não exibirá nenhuma mensagem de log.

A configuração do log de rede é abordada no curso Framework Routing & Reporting 8.5 Administration.

## 7.9 Configuring Logging(Configurando o Logging)


In this section, you will learn to change the logging you want to be generated for the application.

To configure logging within Genesys Administrator Extension go to GAX > Configuration > Environment.

Within the list of Environment options, select Applications

Nesta seção, você aprenderá a alterar o log que deseja que seja gerado para o aplicativo.

Para configurar o log no Genesys Administrator Extension, vá para GAX > Configuration > Environment.

Na lista de opções de Ambiente, selecione Aplicativos

![image](https://user-images.githubusercontent.com/52088444/158870830-b32c1ea5-282b-4807-b15f-e459961dc8e3.png)

Select one or more application object by checking the box next to the object, and from the More menu, choose Configure Logging as shown in the following image.

Selecione um ou mais objetos de aplicativo marcando a caixa ao lado do objeto e, no menu More, escolha Configure Logging conforme mostrado na imagem a seguir.

![image](https://user-images.githubusercontent.com/52088444/158871127-eb3053db-3252-4ef0-aa73-b4dd504318a0.png)

This displays the dialogue box seen below. Here you make choices about the logging that the application will generate. The first option verifies the application you have selected. 

The second option is log level which determines the log level available for output. The interaction level you select is generated along with all levels below it. For example: If you choose Interaction, you will generate Interaction and Standard level. If you select None, there will be no logging configured. If you select All, it adds Debug—you will generate Debug, Trace, Interaction, and Standard.

Isso exibe a caixa de diálogo vista abaixo. Aqui você faz escolhas sobre o log que o aplicativo irá gerar. A primeira opção verifica o aplicativo que você selecionou.

A segunda opção é o nível de log que determina o nível de log disponível para saída. O nível de interação selecionado é gerado junto com todos os níveis abaixo dele. Por exemplo: Se você escolher Interação, você gerará Interação e nível Padrão. Se você selecionar Nenhum, não haverá registro configurado. Se você selecionar Tudo, ele adicionará Depuração — você gerará Depuração, Rastreamento, Interação e Padrão.

![image](https://user-images.githubusercontent.com/52088444/158871259-26e58265-0cd3-4a2d-9691-774b5047f2b3.png)

Next is Log Output. This is where you select the location of the log output. Network Log Server sends the log messages to the Message Server and Log Database so that it can see them using GAX. Plain Text File puts the log output into a text file or a log file. Console means it will show up in a command or DOS window. You need to select the checkbox for the output you desire. 

The selected Log Outputs determines what sections of the bottom half of the dialogue box are required (seen below). If you have selected Network Log Server, you must specify which Message Server to use. If you have selected Plain Text File, you must specify the location and name of the Log File. You can also choose to limit the number of segments and their size. 

Em seguida é a saída de log. É aqui que você seleciona o local da saída do log. O servidor de log de rede envia as mensagens de log para o servidor de mensagens e banco de dados de log para que ele possa vê-los usando o GAX. Arquivo de texto simples coloca a saída de log em um arquivo de texto ou arquivo de log. Console significa que ele aparecerá em um comando ou janela do DOS. Você precisa marcar a caixa de seleção para a saída desejada.

As saídas de registro selecionadas determinam quais seções da metade inferior da caixa de diálogo são necessárias (veja abaixo). Se você selecionou Network Log Server, você deve especificar qual Message Server usar. Se você selecionou Arquivo de Texto Simples, você deve especificar o local e o nome do Arquivo de Log. Você também pode optar por limitar o número de segmentos e seu tamanho.

![image](https://user-images.githubusercontent.com/52088444/158871536-2b04a56f-907b-485f-bd21-324f08e8e7c8.png)

More on interaction level logging and the specific messages associated with the processing of a call will be covered in the Media Layer lesson of this course.

The Framework Routing & Reporting 8.5 Administration course covers additional options for logging as part of configuring application objects. 

Mais informações sobre o registro de nível de interação e as mensagens específicas associadas ao processamento de uma chamada serão abordadas na lição Camada de mídia deste curso.

O curso Framework Routing & Reporting 8.5 Administration abrange opções adicionais para registro em log como parte da configuração de objetos de aplicativo.


## 7.10 Learning Summary(Resumo de Aprendizagem)

Now that you have completed this chapter, you should be able to do the following: 

1 - Describe log levels. 

2 - Describe log elements. 

3 - Describe where to view Genesys logs (log outputs).

4 - Use Genesys Administrator Extension to view logs.

5 - Configure logging.

Agora que você concluiu este capítulo, você deve ser capaz de fazer o seguinte:

1 - Descreva os níveis de log.

2 - Descreva os elementos do log.

3 - Descreva onde visualizar os logs do Genesys (saídas de log).

4 - Use o Genesys Administrator Extension para visualizar os logs.

5 - Configure o log.