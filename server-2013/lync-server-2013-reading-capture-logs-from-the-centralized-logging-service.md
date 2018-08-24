---
title: Lendo Registros de Captura do Serviço de Registro em Log
TOCTitle: Lendo Registros de Captura do Serviço de Registro em Log
ms:assetid: c86ccf61-d86f-4ebd-b8d1-984a1b73005d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721879(v=OCS.15)
ms:contentKeyID: 49886407
ms.date: 12/29/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lendo Registros de Captura do Serviço de Registro em Log

 

_**Tópico modificado em:** 2016-12-28_

Você percebe o benefício real do Serviço de Log Centralizado após executar a pesquisa e possui um arquivo que pode usar para rastrear um problema relatado. Existe um número de formas que você pode ler o arquivo. O arquivo de resultado está em um formato de texto padrão e você pode usar Notepad.exe ou qualquer outro programa que permitirá abrir e ler um arquivo de texto. Para arquivos maiores e problemas mais complexos, você pode usar uma ferramenta como Snooper.exe projetado para ler e analisar o resultado do registro em log do Serviço de Log Centralizado. O Snooper é incluído com as Ferramentas de Depuração do Lync Server 2013 disponíveis como um download separado. Não há atalhos ou itens de menu criados para as Ferramentas de Depuração do Lync Server 2013. Após instalar as Ferramentas de Depuração Lync Server 2013, abra o Windows Explorer, uma janela da linha de comando ou o Shell de Gerenciamento do Lync Server e vá para o diretório (local padrão) C:\\Program Files\\Microsoft Lync Server 2013\\Ferramentas de Depuração. Clique duas vezes em Snooper.exe ou digite Snooper.exe e pressione ENTER se estiver usando a linha de comando ou o Shell de Gerenciamento do Lync Server.

> [!IMPORTANT]  
> A intenção deste tópico não é detalhar e discutir técnicas de resolução de problemas. A resolução de problemas e os processos relacionados é um assunto complexo. Para obter detalhes sobre os fundamentos da resolução de problemas e cargas de trabalho específicas da resolução de problemas, consulte o livro do Kit de recursos do Microsoft Lync Server 2010 em <a href="http://go.microsoft.com/fwlink/?linkid=211003%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=211003&amp;clcid=0x416</a>. Os processos e procedimentos ainda se aplicam ao Lync Server 2013.

O Lync Server 2013 introduz a versão atualizada do Snooper incluindo alguns novos recursos. A tela a seguir mostra a versão do Snooper do Office Communications Server 2007.

![Versão do Snooper do Office Communications 2007.](images/JJ721879.129503a8-8edd-4bb0-a68f-c43f9a548b93(OCS.15).jpg "Versão do Snooper do Office Communications 2007.")

A tela a seguir mostra a nova versão do Snooper incluída nas Ferramentas de Depuração do Lync Server 2013.

![Versão do Snooper do Lync Server 2013.](images/JJ721879.131495dd-8220-4ae4-af37-0ac5c318fd45(OCS.15).jpg "Versão do Snooper do Lync Server 2013.")

A tela a seguir mostra a barra de ferramentas com funções usadas frequentemente.

![Barra de ferramentas do Snooper 2013.](images/JJ721879.989249c5-a33e-4251-b8b4-411019cc12b2(OCS.15).jpg "Barra de ferramentas do Snooper 2013.")

E, o novo recurso que adiciona valor é a exibição do Fluxograma (fluxo de chamadas). Você seleciona um fluxo de mensagens na guia **Mensagem** e clica no botão **Fluxo de chamada**. Conforme você passa pelas mensagens, o fluxograma de chamada é atualizado com novos dados.

![Diagrama do fluxo de chamadas do Snooper 2013.](images/JJ721879.bb8be45d-a842-48fe-86f8-380207d70bab(OCS.15).jpg "Diagrama do fluxo de chamadas do Snooper 2013.")

É possível passar sobre a exibição do diagrama e obter detalhes sobre a mensagem e o conteúdo de fluxos e mensagens, assim como os elementos do servidor. Clique em qualquer seta do fluxo de chamadas para ir para a mensagem na exibição de Mensagens.

![Detalhes da mensagem do diagrama do fluxo de chamadas.](images/JJ721879.1147d720-38a9-4bda-8361-78f27ecde3d1(OCS.15).jpg "Detalhes da mensagem do diagrama do fluxo de chamadas.")

## Para abrir um arquivo de log no Snooper

1.  Para usar o Snooper e abrir arquivos de log, você precisará de acesso de leitura aos arquivos de log. Para usar o Snooper e acessar os arquivos de log, você deve ser membro dos grupos de segurança RBAC CsAdministrator ou CsServerAdministrator ou uma função RBAC personalizada que contém um destes dois grupos.

2.  Após a instalação das Ferramentas de Depuração do Lync Server (LyncDebugTools.msi), mude o diretório para o local do Snooper.exe usando o Windows Explorer ou na linha de comando. Por padrão, as ferramentas de depuração estão localizadas em C:\\Program Files\\Microsoft Lync Server 2013\\Ferramentas de Depuração. Clique duas vezes ou execute Snooper.exe.

3.  Após o Snooper estar aberto, clique com o botão direito em **Arquivo**, clique em **Abrir arquivo**, encontre seus arquivos de log, selecione um arquivo na caixa de diálogo **Abrir** e clique em **Abrir**.

4.  As mensagens de **Rastreamento** do arquivo de log são exibidas na guia **Rastreamento**. Clique na guia **Mensagens** para exibir o conteúdo da mensagem dos rastreamentos coletados.

## Para exibir um fluxograma da chamada

1.  Para usar o Snooper e abrir arquivos de log, você precisa de acesso de leitura dos arquivos de log. Para usar o Snooper e acessar os arquivos de log, você precisará ser um membro dos grupos de segurança RBAC CsAdministrator ou CsServerAdministrator ou uma função RBAC personalizada que contém um destes dois grupos.

2.  Abra um arquivo de log e clique na guia **Mensagens**, selecione uma conversa na exibição de mensagens ou selecione um componente de rastreamento na guia **Rastreamento**.

3.  Clique em **Fluxo de chamadas**.
    
    > [!NOTE]  
    > Se você clicar em uma mensagem ou rastreamento que não faz parte do fluxo de chamadas, o diagrama não aparecerá e uma mensagem de status aparece na parte inferior do Snooper dizendo “Esta mensagem não é elegível para fluxo de chamadas”. Escolha outra mensagem ou rastreamento e o fluxo de chamadas aparecerá se a mensagem ou o rastreamento faz parte de um fluxo de chamadas.

4.  Mova pelas Mensagens ou linhas de Rastreamento e observe se o fluxograma de chamada atualiza ou muda para exibir um novo diagrama.

5.  Passe sobre os elementos para obter informações sobre mensagens de chamada, pontos de extremidade e outros componentes.

