---
title: 'Lync Server 2013: Integrando com Microsoft Exchange Server 2013'
TOCTitle: Integrando Lync Server 2013 e Exchange Server 2013
ms:assetid: 795dc1c6-524f-4012-8b66-103b55198044
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688098(v=OCS.15)
ms:contentKeyID: 49886270
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Integrar Microsoft Lync Server 2013 e Microsoft Exchange Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Exchange e o Lync Server têm um longo histórico de integração e compatibilidade. Essa integração é notável principalmente nos respectivos aplicativos clientes. Por exemplo, as informações de presença do Lync podem ser registradas no Microsoft Outlook; de modo semelhante, o Lync pode usar o calendário do Outlook para atualizar as informações de presença automaticamente (por exemplo, o Lync pode alterar seu status para Ocupado a qualquer hora que o calendário mostrar uma reunião agendada). Embora não seja necessário executar o Exchange para executar o Lync Server (ou vice-versa), é quase certo que o uso simultâneo dos dois produtos sintetiza a definição do termo "melhores juntos".

Isso se mostra verdadeiro principalmente com o lançamento do Microsoft Lync Server 2013 e do Microsoft Exchange Server 2013. Além de recursos como mensagens unificadas, IM e presença, encontrados no Microsoft Exchange Server 2010 e no Microsoft Lync Server 2010, as versões 2013 dos produtos de servidor incluem diversos novos recursos. Eles incluem:

  - **Integração com arquivamento do Lync** . No Lync Server 2013, os administradores ainda têm a opção de arquivar transcrições de Webconferências e mensagens instantâneas no SQL Server (do mesmo modo que eram arquivadas no Lync Server 2010). Porém, como alternativa, os administradores podem arquivar as transcrições no Exchange 2013, armazenando-as em caixas de correio de usuários individuais do mesmo modo que o Exchange arquiva comunicações. Com isso, você obtém um único repositório para todas as comunicações eletrônicas (do Exchange e do Lync Server), o que facilita muito a pesquisa e recuperação das comunicações arquivadas em caso de necessidade.

  - **Repositório de contatos unificado** . No Lync Server 2010, os usuários tinham que manter listas de contatos separadas no Outlook e no Lync; na verdade, para garantir a disponibilidade dos mesmos contatos nos dois produtos, era preciso manter duas listas de contatos, uma para o Outlook e outra para o Lync. Porém, com o Lync Server 2013, os contatos dos usuários podem ser armazenados no Exchange 2013 e no repositório de contatos unificado. O uso de um único repositório de contatos permite que os usuários mantenham apenas um conjunto de contatos, sendo que ele fica disponível no Lync 2013, Outlook 2013 e Outlook Web Access 2013.

  - **Agendamento de reunião do Lync usando o OWA** . Com a integração do Lync Server 2013 e do Exchange 2013, os usuários podem agendar reuniões do Lync usando o Outlook Web Access 2013.

  - **Fotos em alta resolução** . O Lync 2010 era capaz de exibir apenas pequenas fotos dos contatos. Isso ocorria porque elas eram armazenadas no Active Directory, que impõe um limite de tamanho de 48 x 48 pixels para as fotos armazenadas. Porém, com o Lync Server 2013, as fotos podem ser armazenadas no Microsoft Exchange, que permite utilizar fotos em alta resolução, de até 648 x 648 pixels. Como você pode imaginar, o Lync 2013 passou por um upgrade para permitir a exibição de fotografias em alta resolução.

Lembre-se de que esses novos recursos exigem a utilização do Lync Server 2013 e do Exchange 2013. Além disso, os usuários que planejam aproveitar esses novos recursos ao máximo devem ter contas no Lync Server 2013 e no Exchange 2013, e devem ter as versões mais recentes dos softwares clientes (por exemplo, Lync 2013). Por exemplo, o repositório de contatos unificado não está disponível para usuários hospedados no Lync Server 2010; de modo semelhante, as fotos em alta resolução não podem ser exibidas no Lync 2010.

Esta documentação fornece informações sobre a integração entre o Lync Server 2013 e o Exchange 2013. inclusive informações passo a passo sobre como habilitar novos recursos, como a integração do arquivamento e do repositório de contatos unificado. Esta documentação não aborda a instalação e configuração iniciais desses dois produtos. Para obter detalhes de implantação do Lync Server 2013, consulte o Tech Center do Lync Server 2013, em [http://go.microsoft.com/fwlink/?linkid=246127\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=246127%26clcid=0x416). Para obter detalhes sobre a implantação do Exchange 2013, consulte o Tech Center do Exchange 2013, em [http://go.microsoft.com/fwlink/?linkid=268528\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268528%26clcid=0x416).

## Nesta seção

[Pré-requisitos para integrar Microsoft Lync Server 2013 e Microsoft Exchange Server 2013](lync-server-2013-prerequisites-for-integrating-with-exchange-server-2013.md)

[Configurando Inscrição de Parceiro no Microsoft Lync Server 2013 e Microsoft Exchange Server 2013](lync-server-2013-configuring-partner-applications-in-lync-server-2013-and-exchange-server-2013.md)

[Configurando o Microsoft Lync Server 2013 para usar arquivamento do Microsoft Exchange Server 2013](configuring-lync-server-2013-to-use-microsoft-exchange-server-2013-archiving.md)

[Configurando Microsoft SharePoint Server 2013 para buscar dados arquivados no Microsoft Lync Server 2013](lync-server-2013-configuring-microsoft-sharepoint-server-2013-to-search-for-archived-lync-server-2013-data.md)

[Configurando Microsoft Lync Server 2013 para usar o repositório de contato unificado](lync-server-2013-configuring-lync-server-to-use-the-unified-contact-store.md)

[Configurando o Uso de Fotos de Alta Resolução no Microsoft Lync Server 2013](lync-server-2013-configuring-the-use-of-high-resolution-photos.md)

[Configurando Unified Messaging do Microsoft Exchange Server 2013 para caixa postal de Microsoft Lync Server 2013](lync-server-2013-configuring-microsoft-exchange-server-2013-unified-messaging-for-lync-server-2013-voice-mail.md)

[Integrando o Microsoft Lync Server 2013 e o Microsoft Outlook Web App 2013](lync-server-2013-integrating-lync-server-and-outlook-web-app-2013.md)

