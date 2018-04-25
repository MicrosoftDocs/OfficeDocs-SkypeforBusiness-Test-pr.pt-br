---
title: 'Lync Server 2013: Configurar armazenamento de arquivo'
TOCTitle: Configurar armazenamento de arquivo
ms:assetid: a985be20-5a00-4f38-b45b-83dc82de3827
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205150(v=OCS.15)
ms:contentKeyID: 49307741
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar armazenamento de arquivo para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 suporta usando compartilhamento de arquivos em um Sistema de Arquivos Distribuído (DFS). Para obter detalhes do DFS para Windows Server 2008, consulte o Guia Passo a Passo de DFS para Windows Server 2008 em [http://go.microsoft.com/fwlink/p/?linkId=202835](http://go.microsoft.com/fwlink/p/?linkid=202835). Para usar um DFS, o Lync Server 2013 exige o seguinte:

  - Namespaces sejam baseados em domínio

  - Todos os servidores de namespace estejam executando um mínimo de Windows 2008

A configuração do Lync Server 2013 exige que as permissões na pasta compartilhada permita acesso total ao Administrador. O Lync Server 2013 usará então permissões de arquivo NTFS para ACL das pastas. Permissões de compartilhamento DFS herdadas não serão usadas para acesso restrito.

Para obter detalhes sobre exigências de compartilhamento de arquivos, consulte [Suporte a armazenamento de arquivo no Lync Server 2013](lync-server-2013-file-storage-support.md) na documentação de Suporte.

O procedimento a seguir descreve como configurar corretamente permissões de pastas compartilhas usando o Assistente de Namespace DFS (como descrito no guia de instalação do DFS)

## Para configurar permissões de pastas compartilhadas

1.  clique em **Iniciar** , aponte para **Todos os Programas** , aponte para **Ferramentas Administrativas** e clique em **Gerenciamento DFS** .

2.  Na árvore de console do snap-in do Gerenciamento DFS, clique com o botão direito no servidor de namespace (por exemplo, filesrv1.contoso.com) e depois clique em **Editar Configurações** .

3.  Selecione **Permissões de pastas compartilhadas** .

4.  Selecione **Usar permissões personalizadas** .

5.  Para o grupo Administrador, selecione o seguinte sob **Permitir** :
    
      - **Controle total**
    
      - **Alterar**
    
      - **Ler**

6.  Clique em **Aplicar** e em **OK** .

