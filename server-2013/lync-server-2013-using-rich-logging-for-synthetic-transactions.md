---
title: Usando Registro em Log Sofisticado para Transações Sintéticas
TOCTitle: Usando Registro em Log Sofisticado para Transações Sintéticas
ms:assetid: 32714a71-9f42-4d5b-a508-e176d8f08bbf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204798(v=OCS.15)
ms:contentKeyID: 49306319
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando Registro em Log Sofisticado para Transações Sintéticas

 

_**Tópico modificado em:** 2012-10-22_

As transações sintéticas (introduzidas no Microsoft Lync Server 2010) oferecem uma forma para que os administradores verifiquem se os usuários conseguem concluir tarefas comuns, como fazer logon no sistema, trocar mensagens instantâneas ou fazer chamadas a um telefone localizado na rede telefônica pública comutada (PSTN). Esses testes (que são embalados como um conjunto de cmdlets do Lync ServerWindows PowerShell) podem ser conduzidos manualmente por um administrador ou executados automaticamente por um aplicativo, como o System Center Operations Manager.

No Lync Server 2010, as transações sintéticas foram comprovadamente bastante úteis para ajudar os administradores a identificar problemas com o sistema. Por exemplo, o cmdlet **Test-CsRegistration** pôde alertar os administradores para o fato de que alguns usuários estavam enfrentando dificuldades para registrar o Lync Server. No entanto, as transações sintéticas foram, de certa forma, menos úteis para ajudar os administradores a determinar porque esses usuários estavam enfrentando dificuldades para registrar o Lync Server. Isso se deve ao fato de que as transações sintéticas não forneceram informações detalhadas de registro em log que poderiam ajudar os administradores a solucionar problemas do Lync Server. Na melhor das hipóteses, a saída detalhada de uma transação sintética oferecia informações passo a passo que poderiam habilitar um administrador a fazer um palpite fundamentado sobre onde era provável que tivesse ocorrido o problema.

No Microsoft Lync Server 2013, as transações sintéticas foram rearquitetadas para oferecer registro avançado em log. "Registro avançado em log" significa que, para cada atividade assumida por uma transação sintética, informações como estas serão registradas:

  - A hora em que a atividade foi iniciada

  - A hora em que a atividade foi concluída

  - A ação que foi executada (por exemplo, criar, ingressar ou sair de uma conferência; fazer logon no Lync Server; enviar uma mensagem instantânea e assim por diante)

  - Mensagens informativas, detalhadas, de advertência ou de erro geradas quando a atividade foi executada

  - Mensagens de registro de SIP

  - Registros de exceção ou códigos de diagnóstico gerados quando a atividade foi executada

  - O resultado líquido da execução da atividade

Essas informações são geradas automaticamente sempre que uma transação sintética é executada. No entanto, as informações não são exibidas automaticamente ou salvas em um arquivo de log. Em vez disso, os administradores que estão executando manualmente uma transação sintética podem usar o parâmetro OutLoggerVariable para especificar uma variável do Windows PowerShell na qual as informações serão armazenadas. A partir daqui, os administradores podem usar um par de métodos que permitem a gravação e/ou exibição do log avançado em formato XML ou HTML.

Por exemplo, os administradores do Lync Server 2010 podem executar o cmdlet **Test-CsRegistration** usando um comando semelhante ao seguinte:

    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com

Os administradores têm a opção de incluir o parâmetro OutLoggerVariable seguido pelo nome de uma variável à escolha deles:

    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com -OutLoggerVariable RegistrationTest

> [!NOTE]  
> Não use o caractere $ como prefixo do nome da variável. Use um nome de variável como RegistrationTest e não $RegistrationTest.

O comando precedente produz um conteúdo semelhante ao seguinte:

    Target Fqdn   : atl-cs-001.litwareinc.com
    Result        : Failure
    Latency       : 00:00:00
    Error Message : This machine does not have any assigned certificates.
    Diagnosis     :

No entanto, informações muito mais detalhadas do que a mensagem de erro mostrada acima estão disponíveis para essa falha. Para acessar essas informações em formato HTML, use um comando semelhante a este para salvar as informações armazenadas na variável RegistrationTest em um arquivo HTML:

    $RegistrationTest.ToHTML() | Out-File C:\Logs\Registration.html

Como alternativa, é possível usar o método ToXML() para salvar os dados em um arquivo XML:

    $RegistrationTest.ToXML() | Out-File C:\Logs\Registration.xml

Esses arquivos podem ser exibidos usando o Internet Explorer, o Visual Studio ou qualquer outro aplicativo capaz de abrir arquivos HTML/XML.

As transações sintéticas que são executadas de dentro do System Center Operations Manager gerarão automaticamente esses arquivos de log de falhas. No entanto, esses logs não serão gerados se a execução falhar antes que o Windows PowerShell possa carregar e executar a transação assimétrica.

> [!IMPORTANT]  
> Por padrão, o Lync Server 2013 salva arquivos de log em uma pasta que não é compartilhada. Para tornar esse logs prontamente acessíveis, é preciso compartilhar essa pasta (por exemplo, \\atl-watcher-001.litwareinc.com\WatcherNode).
