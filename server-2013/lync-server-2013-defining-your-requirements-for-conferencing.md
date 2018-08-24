---
title: 'Lync Server 2013: Definindo seus requisitos para conferência'
TOCTitle: Definindo seus requisitos para conferência
ms:assetid: 5c83e268-22bf-42b2-bac3-3237b5e02e03
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204935(v=OCS.15)
ms:contentKeyID: 49306838
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo seus requisitos para conferência no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-30_

Ao determinar quais funcionalidades de conferência serão implantadas, você precisa considerar os recursos que deseja disponibilizar para seus usuários, bem como seus recursos de largura de banda de rede. A lista de perguntas a seguir o guiará durante o processo de planejamento de conferências para determinar quais recursos de conferência você deve implantar de acordo com as necessidades de sua organização.

  - **Você deseja habilitar a webconferência, que inclui a colaboração em documentos e o compartilhamento de aplicativos?**
    
    Se sim, precisará habilitar a conferência para seu Pool de Front-Ends no Microsoft Lync Server 2013, Ferramenta de Planejamento ou no Construtor de Topologias. Ao habilitar a conferência, tanto a webconferência como a conferência A/V são habilitadas.
    
    O compartilhamento de aplicativo requer e usa mais largura de banda do que a colaboração em documentos. O Lync Server 2013 fornece um mecanismo de regulagem para controlar cada sessão de compartilhamento de aplicativo. Por padrão, isso é definido como 1,5 KB por segundo para cada sessão.
    
    Se você não desejar habilitar o compartilhamento de aplicativo, mas desejar a colaboração em documentos, poderá habilitar a conferência e usar políticas de reunião para desabilitar o compartilhamento de aplicativo. Para obter detalhes sobre a configuração de políticas de reunião, consulte [Políticas de conferência no Lync Server 2013](lync-server-2013-conferencing-policies.md).
    
    Para permitir que os usuários compartilhem apresentações do PowerPoint, você precisa configurar o Servidor Office Web Apps. Para obter detalhes sobre como configurar o Servidor Office Web Apps, consulte [Configurando a integração com servidor de Office Web Apps e Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

  - **Deseja habilitar a conferência A/V?**
    
    Se sim, precisará habilitar a conferência para seu Pool de Front-Ends no Lync Server 2013, Ferramenta de Planejamento ou no Construtor de Topologias. Ao habilitar a conferência, tanto a webconferência como a conferência A/V são habilitadas.
    
    A conferência A/V exige e usa mais largura de banda que a webconferência (que inclui a colaboração em documentos e o compartilhamento de aplicativo). Se você desejar habilitar a webconferência, mas não a conferência A/V, poderá habilitar a conferência e usar as políticas de reunião para desabilitar a conferência A/V.
    
    Se você desejar habilitar a conferência de áudio, mas não a conferência de vídeo, poderá habilitar a conferência A/V e usar políticas de reunião para impedir as conferências de vídeo. Como alternativa, você pode habilitar a conferência A/V e permitir que somente determinados usuários iniciem ou participem de conferências A/V.
    
    > [!NOTE]  
    > O Enterprise Voice não é necessário para você usar a conferência A/V. Se você habilitar a conferência A/V, seus usuários poderão adicionar áudio a suas conferências se tiverem dispositivos de áudio, mesmo que você use um sistema PBX como sua solução de telefone.

  - **Deseja permitir que os usuários ingressem na parte de áudio de conferências quando usam um telefone PSTN?**
    
    Em caso afirmativo, implante e habilite a conferência de discagem. Em seguida, os usuários convidados (dentro e fora da sua organização) poderão ingressar na parte de áudio de conferências usando um telefone PSTN.

  - **Deseja permitir que usuários externos com clientes do Lync Server 2013 ingressem nos tipos de conferências que você habilitou?**
    
    Em caso afirmativo, você deve implantar Servidores de Borda. Ao permitir a participação externa em reuniões, você aproveita ao máximo seu investimento no Lync Server 2013. Por exemplo, usuários que têm laptops com o Lync Server 2013 podem ingressar em conferências de onde estiverem: em casa, no aeroporto ou nas instalações de clientes.
    
    Além disso, com os Servidores de Borda implantados, você pode criar relações federadas com outras organizações, como seus clientes ou fornecedores, e os usuários dessas organizações poderão colaborar mais facilmente com seus usuários.
    
    Para obter detalhes sobre a implantação de Servidores de Borda, consulte [Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) e [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md). Para obter detalhes sobre como habilitar o acesso externo para o Servidor Office Web Apps, consulte [Publicando o servidor do Office Web Apps no Lync Server 2013 usando um servidor de proxy reverso](lync-server-2013-publishing-office-web-apps-server-using-a-reverse-proxy-server.md).

  - **Deseja controlar os clientes que podem ingressar em reuniões do Lync Server 2013?**
    
    Em caso afirmativo, você deve configurar a página de ingresso em reunião para que apenas as opções do cliente que você deseja oferecer fiquem disponíveis. Sempre que um usuário clicar em um link para ingressar em uma reunião agendada, o Lync Server 2013 detectará se um cliente já está instalado no computador. Em seguida, ele iniciará o cliente padrão e abrirá a página de ingresso em reunião, que contém links para clientes alternativos. A página de ingresso em reunião sempre contém a opção de usar o Microsoft Lync Web App. Além dessa opção, você pode decidir se deseja incluir links do Participante e das versões anteriores do Communicator. Para obter detalhes, consulte [Configurando a página de ingresso na reunião no Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md).

## Nesta seção

  - [Requisitos de webconferência no Lync Server 2013](lync-server-2013-web-conferencing-requirements.md)

  - [Requisitos para Conferência A/V no Lync Server 2013](lync-server-2013-a-v-conferencing-requirements.md)

  - [Exigências da conferência discada no Lync Server 2013](lync-server-2013-dial-in-conferencing-requirements.md)

## Consulte Também

#### Outros Recursos

[Planejamento de conferência no Lync Server 2013](lync-server-2013-planning-for-conferencing.md)  
[Lista de verificação de implantação para conferência no Lync Server 2013](lync-server-2013-deployment-checklist-for-conferencing.md)

