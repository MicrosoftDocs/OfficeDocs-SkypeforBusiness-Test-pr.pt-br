---
title: Importando os pacotes de gerenciamento do Lync Server 2013
TOCTitle: Importando os pacotes de gerenciamento do Lync Server 2013
ms:assetid: 846287e1-660f-453f-bdba-b2137b5f0ea1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205052(v=OCS.15)
ms:contentKeyID: 49307334
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Importando os pacotes de gerenciamento do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

É possível ampliar os recursos do System Center Operations Manager com a instalação de pacotes de gerenciamento, softwares que indicam quais itens podem ser monitorados pelo System Center Operations Manager, como esses itens devem ser monitorados e como os alertas devem ser acionados e registrados. O Lync Server 2013 conta com dois pacotes de gerenciamento System Center Operations Manager que fornecem os seguintes recursos:

  - O Pacote de gerenciamento de componentes e usuários (Microsoft.LS.2013.Monitoring.ComponentAndUser.mp) monitora os problemas de Lync Server registrados em logs de evento pelos contadores de desempenho ou em registros dos bancos de dados de detalhes das chamadas (CDR) ou qualidade da experiência (QoE). Para problemas críticos, o System Center Operations Manager pode ser configurado para notificar os administradores imediatamente poe email, mensagens instantâneas ou SMSs. O SMS é a tecnlogia usada para enviar mensagens entre celulares.
    
    > [!NOTE]  
    > Para obter detalhes sobre como configurar as notificações do Operations Manager, consulte &quot;Configurando notificações&quot; na TechNet Library, em <a href="http://go.microsoft.com/fwlink/?linkid=268785%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=268785&amp;clcid=0x416</a>.

  - O Pacote de gerenciamento de monitoramento ativo (Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp) testa com proatividade os principais componentes Lync Server, como a conexão ao sistema, a troca de mensagem instantâneas ou as chamadas para telefones em redes telefônicas públicas comutadas (PSTN). Esses testes são realizados com o uso de cmdlets de transações sintéticos do Lync Server. Por exemplo, você pode usar o cmdlet **Test-CsIM**para simular conversas por mensagens instantâneas entre usuários de teste. Se a simulação de conversa falhar, um alerta é gerado.

Você deve importar os pacotes de gerenciamento. Se não importá-los, não será possível usar o Operations Manager para monitorar eventos do Lync Server nem executar transações sintéticas do Lync Server.

O Pacote de gerenciamento de componentes e usuários só é usado para monitorar o Lync Server 2013. Se você estiver em um cenário coexitente em que o Lync Server 2013 e o Lync Server 2010 estão instalados, será necessário continuar usando os pacotes de gerenciamento do Lync Server 2010 em seus computadores Lync Server 2010.

> [!NOTE]  
> Os pacotes de gerenciamento para Lync Server 2010 incluem o Pacote de gerenciamento de monitoramento do Lync Server 2010 e o Pacote de gerenciamento de monitoramento de chat em grupo do Lync Server 2010.

Você pode usar uma destas ferramentas para importar pacotes de gerenciamento:

  - **System Center Operations Manager**   Com este método, você usa o Operations Manager para adicionar o monitoramento para Lync Server.

  - **Operations Manager Shell**   Você pode usar o Operations Manager Shell para importar diretamente ou solucionar quaisquer problemas encontrados durante a importação de pacotes de gerenciamento por meio do console do System Center Operations Manager.

## Importando pacotes de gerenciamento por meio do System Center Operations Manager

1.  Baixe os arquivos Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp e Microsoft.LS.2013.Monitoring.ComponentAndUser.mp.

2.  No System Center Operations Manager, clique em **Administração**.

3.  No painel **Administração**, clique com o botão direito do mouse em **Pacotes de gerenciamento** e, em seguida, clique em **Importar pacotes de gerenciamento**.

4.  Na caixa de diálogo **Selecinar pacotes de gerenciamento**, clique em **Adicionar** e, em seguida, em **Adicionar do disco**.

5.  Na caixa de diálogo **Conexão do catálogo online**, clique em **Cancelar** para evitar que Operations Manager fique online para verificar se há dependências para os pacotes de gerenciamento do Lync Server. Se estiver usando o System Center Operations Manager 2012, clique em **Não**.

6.  Na caixa de diálogo **Selecionar pacotes de gerenciamento para importar**, localize e selecione os arquivos **Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp** e **Microsoft.LS.2013.Monitoring.ComponentAndUser.mp**. Em seguida, clique em **Abrir**. Para selecionar diversos arquivos na caixa de diálogo, mantenha a tecla Ctrl pressionada enquanto clica em outros arquivos.

7.  Na caixa de seleção **Selecionar pacotes de gerenciamento**, clique em **Instalar**. Se receber uma mensagem de erro e a instalação falhar, geralmente isso signfica que os arquivos dos pacotes de gerenciamento estão em uma pasta protegida pelo Controle de conta de usuário do Windows. Se isso ocorrer, copie os arquivos para outra pasta e reinicie o processo de intalação e importação.

8.  Na caixa de diálogo **Selecionar pacotes de gerenciamento**, clique em **Fechar**. A conclusão do processo de importação e instalação pode levar muitos minuto

## Importando pacotes de gerenciamento por meio do Operations Manager Shell

Em geral, é mais fácil importar os pacotes de gerenciamento por meio do Operations Manager. No entanto, se ocorrer um erro e a importação falhar, nm sempre o consle fornece relatórios de erro adequados. Por comparação, o Operations Manager Shell fornece informações detalhadas. Se estiver usando o Operations Manager e tiver problemas com a importação de um pacote de gerenciamento, importe o pacote por meio do Operations Manager Shell . O Operations Manager Shell fornece mais informações que podem ajudar a descobrir por que a importação falhou.

Se estiver usando o System Center Operations Manager 2007 R2, siga estas instruções:

1.  Clique em **Iniciar**, **Todos os programas**, **System Center Operations Manager 2007 R2** e em **Operations Manager Shell**.

2.  No Operations Manager Shell, insira o comando a seguir no prompt de comando usando o caminho do arquivo Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp e pressione ENTER:
    
        MPImport.exe D:\MP\Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp

3.  Depois de importar o primeiro pacote de gerenciamento, repita o processo usando o caminho do arquivo Microsoft.LS.2013.Monitoring.ComponentAndUser.mp:
    
        MPImport.exe D:\MP\Microsoft.LS.2013.Monitoring.ComponentAndUser.mp

4.  Feche o Operations Manager Shell.

Se estiver usando o System Center Operations Manager, siga estas instruções:

1.  Clique em **Iniciar**, **Todos os programas**, **Microsoft System Center 2012**, **Operations Manager** e, em seguida, em **Operations Manager Shell**.

2.  No Operations Manager Shell, insira o comando a seguir no prompt de comando usando o caminho do arquivo Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp e pressione ENTER:
    
        Import-SCOMManagementPack -FullName "D:\MP\ Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp"

3.  Depois de importar o primeiro pacote de gerenciamento, repita o processo usando o caminho até sua cópia do arquivo Microsoft.LS.2013.Monitoring.ComponentAndUser.mp:
    
        Import-SCOMManagementPack -FullName "D:\MP\ Microsoft.LS.2013.Monitoring.ComponentAndUser.mp"

