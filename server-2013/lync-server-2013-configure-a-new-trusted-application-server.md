---
title: Configurar um novo servidor de aplicativos confiável no Lync Server 2013
TOCTitle: Configurar um novo servidor de aplicativos confiável no Lync Server 2013
ms:assetid: a7233db7-fac3-43ff-972e-3bc29a56adb3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg617964(v=OCS.15)
ms:contentKeyID: 49307717
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar um novo servidor de aplicativos confiável no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Um aplicativo confiável é um aplicativo baseado no Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK que é confiável pelo Microsoft Lync Server 2013. Para detalhes sobre aplicativos UCMA, consulte “Documentação do Unified Communications Managed API 3.0 Core SDK” em [http://go.microsoft.com/fwlink/?linkid=210320\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=210320%26clcid=0x416).

Para informações sobre como configurar o Microsoft Outlook Web Access (OWA) e o Lync Server 2013, consulte "Configurar a integração entre o Outlook Web App e o Lync Server 2010" na documentação do Microsoft Exchange Server 2013.

Para publicar, habilitar ou desabilitar uma topologia com sucesso ao adicionar ou remover uma função de servidor, você deve estar conectado como um usuário que seja membro dos grupos RTCUniversalServerAdmins e Administradores de Domínio. Também é possível delegar as permissões e direitos de administrador adequados para adicionar funções de servidor. Para detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md) na documentação de Implantação. Para outras alterações na configuração, apenas a associação ao grupo RTCUniversalServerAdmins é necessária.

## Para configurar um servidor de aplicativos confiáveis

1.  Faça logon no computador no qual o Construtor de Topologias está instalado como um membro do grupo Admins. do Domínio ou do grupo RTCUniversalServerAdmins.

2.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

3.  Selecione **Fazer download da topologia a partir da implantação existente** e clique em **OK**.

4.  Na caixa de diálogo**Salvar Topologia Como**, clique no arquivo do Construtor de Topologias que deseja usar e clique em **Salvar**.

5.  No painel à esquerda, clique com o botão direito em **Servidores de aplicativos confiáveis** e depois em **Novo Pool de Aplicativos Confiáveis**.

6.  Insira o **FQDN do Pool** do pool de aplicativos confiáveis, selecione se este será um servidor único ou múltiplo e clique em **Avançar**.

7.  Na página **Selecionar o próximo salto**, na lista, selecione o Lync Server 2013 Pool de Front-Ends.

8.  Clique em **Concluir**.

9.  Selecione o nó superior **Lync Server 2013** e depois, no menu **Ações**, clique em **Publicar Topologia**.
    
    O **Pool de Aplicativos Confiáveis** deve ter sido criado com sucesso e associado com o Pool de Front-Ends correto.

