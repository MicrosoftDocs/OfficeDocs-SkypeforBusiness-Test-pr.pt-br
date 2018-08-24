---
title: Configurar o Servidor de Mediação
TOCTitle: Configurar o Servidor de Mediação
ms:assetid: 583236fd-33cd-4045-81df-baa58ed07779
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204913(v=OCS.15)
ms:contentKeyID: 49306777
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar o Servidor de Mediação

 

_**Tópico modificado em:** 2016-12-08_

Este procedimento detalha as etapas para configurar o pool do Lync Server 2013 para usar o Servidor de Mediação do Lync Server 2013, em vez do Servidor de Mediação Office Communications Server 2007 R2 herdado.

Para publicar com sucesso, habilite ou desabilite uma topologia ao adicionar ou remover uma função do servidor, você deve estar conectado como um usuário que é um membro do RTCUniversalServerAdmins e dos grupos Administradores do Domínio. Também é possível delegar os direitos e as permissões de administrador corretos para adicionar funções do do servidor. Para obter detalhes, consulte Permissões de configuração delegadas na Documentação de implantação do servidor Standard Edition ou servidor Enterprise Edition. Para obter as alterações de configuração, somente a associação no grupo RTCUniversalServerAdmins é exigida.

> [!NOTE]  
> Para obter as informações mais recentes sobre localizar gateways PSTN qualificados, IP-PBXs, e serviços de tronco SIP que funcionem com Lync Server 2013, consulte &quot;Abrir Programa de Interoperabilidade do Microsoft Unified Communications&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=206015">http://go.microsoft.com/fwlink/p/?linkId=206015</a>.

## Para configurar o Servidor de Mediação usando o Construtor de Topologias

1.  Abrir uma topologia existente do Topology Builder.

2.  No painel esquerdo, navegue até **Gateways PSTN**.

3.  Clique com o botão direito do mouse em **Gateways PSTN** e clique em **Novo gateway IP/PSTN**.

4.  Complete a página **Definir Novo Gateway IP/PSTN** com as seguintes informações:
    
      - Insira o FQDN do gateway ou endereço IP. O FQDN do gateway é exigido se o gateway utiliza o protocolo TLS.
    
      - Aceite o valor padrão do **Porta de Escuta do Gateway IP/PSTN** ou insira a nova porta de escuta se ela for modificada.
    
      - Defina o **Protocolo de Transporte SIP**.

5.  No painel esquerdo, navegue até o **Pool de Front-Ends Enterprise Edition** ou o **Servidor Standard Edition**.

6.  Clique com o botão direito no pool e clique em **Editar propriedades**.

7.  Em **Servidor de Mediação**, defina as **Portas de Escuta**.

8.  Em seguida, associe o gateway PSTN mais recente criado, o selecionando e clicando em **Adicionar**.

9.  Em **Construtor de Topologias**, selecione o nó superior do **Lync Server**.

10. No menu **Ação**, selecione **Publicar Topologia** e clique em **Avançar**.

11. Quando o **Assistente de publicação** é concluído, clique em **Finalizar** para fechar o assistente.

> [!NOTE]  
> É importante que você conclua o próximo tópico, <a href="change-voice-routes-to-use-the-new-lync-server-2013-mediation-server.md">Alterar rotas de voz para usar o novo Servidor de Mediação do Lync Server 2013</a> para garantir que as rotas de voz estejam apontando para o Servidor de Mediação correto.
