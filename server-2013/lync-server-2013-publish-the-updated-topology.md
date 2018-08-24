---
title: 'Lync Server 2013: Postar a topologia atualizada'
TOCTitle: Postar a topologia atualizada
ms:assetid: 59455dd1-6a9e-433f-a714-d3636c068100
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204910(v=OCS.15)
ms:contentKeyID: 49306794
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Postar a topologia atualizada no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-01_

Após atualizar sua topologia no Construtor de Topologias, você deve publicar a topologia no Repositório de Gerenciamento Central para poder configurar e usar o Servidor de Chat Persistente. Cópias somente leitura dos dados serão replicadas em todos os servidores da topologia para manter todos os servidores sincronizados com a topologia e outras alterações de configuração.

## Para publicar uma topologia atualizada

Antes de publicar sua topologia, instale os bancos de dados do Servidor de Chat Persistente. Use o Construtor de Topologias para instalar os bancos de dados selecionando **Ação** e **Instalar bancos de dados** .

1.  Em um computador que executa o Lync Server 2013 ou no qual as ferramentas administrativas do Lync Server estão instaladas, faça logon usando uma conta que seja membro do grupo **Admins. do Domínio** e do grupo **RTCUniversalServerAdmins** e que tenha permissões de controle total (ou seja, leitura, gravação e modificação) no repositório de arquivos que será usado como repositório de arquivos do Servidor de Chat Persistente (para que o Construtor de Topologias possa configurar as DACLs (listas de controle de acesso discricionário)) ou uma conta com direitos de usuário equivalentes.

2.  Inicie o Construtor de Topologias. Selecione **Baixar Topologia da implantação existente** ou **Abrir Topologia de um arquivo local** se tiver salvado localmente.

3.  Na árvore do console, clique com o botão direito do mouse em **Lync Server 2013** e depois em **Publicar Topologia** .

4.  Na página **Publicar a topologia** , clique em **Avançar** .

5.  Na página **Assistente de publicação concluído** , verifique se a topologia foi publicada com êxito e clique em **Concluir** .
    
    > [!IMPORTANT]  
    > Depois que publicar a topologia, você deverá configurar o suporte ao Servidor de Chat Persistente para que seja possível arquivar conteúdo.
