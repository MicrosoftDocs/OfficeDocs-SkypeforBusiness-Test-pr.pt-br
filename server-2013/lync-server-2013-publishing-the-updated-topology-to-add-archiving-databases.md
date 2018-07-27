---
title: Publicando a topologia atualizada para adicionar ao arquivamento de bancos de dados
TOCTitle: Publicando a topologia atualizada para adicionar ao arquivamento de bancos de dados
ms:assetid: 454c68df-2ef5-4b5f-a44c-4eee02635d45
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204860(v=OCS.15)
ms:contentKeyID: 49306557
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Publicando a topologia atualizada para adicionar ao arquivamento de bancos de dados

 

_**Tópico modificado em:** 2012-10-01_

Após atualizar a sua topologia em Construtor de Topologias, você deve publicá-la no repositório do Gerenciamento Central antes de configurar e utilizar Arquivamento. Cópias somente leitura dos dados são replicadas para todos os servidores da topologia para mantê-los em sincronia com as alterações da topologia e de outras configurações.

## Para publicar a topologia atualizada

1.  Em um computador executando o Lync Server 2013 ou caso as ferramentas administrativas Lync Server estão instaladas, efetue login utilizando uma conta que seja membro do grupo Usuários local (ou uma conta com direitos equivalentes).
    
    > [!NOTE]  
    > Você pode definir uma topologia utilizando uma conta que seja membro do grupo Usuários local, mas para publicar uma topologia (que é necessário para adicionar um servidor à topologia), você deve utilizar uma conta que seja membro do grupo <strong>Administradores de domínio</strong> e o grupo <strong>RTCUniversalServerAdmins</strong> e que possui permissões de controle total (isto é, ler, gravar e modificar) no compartilhamento de arquivos que você está usando para o repositório de arquivo Lync Server 2013 (isto é, de forma que Construtor de Topologias possa configurar a lista de controle de acesso condicional (DACLs) ou uma conta com direitos equivalentes.

2.  Abra a topologia que você criou na seção anterior utilizando o Construtor de Topologias.

3.  Na árvore do console, clique com o botão direito em **Lync Server 2013** e, então, clique em **Publicar topologia**.

4.  Na página **Publicar topologia**, clique em **Avançar**.

5.  Na página **Criar banco de dados**, verifique se o banco de dados está selecionado e, então, clique em **Avançar**.
    
    > [!NOTE]  
    > Se você não possuir as permissões adequadas para criar bancos de dados, você pode cancelar a seleção do banco de dados e alguém com as permissões adequadas podem criar o banco de dados. Para detalhes sobre os direitos e permissões de administrador necessários, consulte <a href="lync-server-2013-deployment-permissions-for-sql-server.md">Permissões de implantação para Servidor SQL no Lync Server 2013</a> na documentação de Implantação.<br />    Apenas bancos de dados em servidores SQL Server dedicados podem ser instalados utilizando o Construtor de Topologias. Bancos de dados nos servidores SQL Server que são alocados com outros componentes de servidor devem ser instalados ao executar a instalação local em tal computador.

6.  Na página **Assistente de publicação concluído**, verifique se a topologia foi publicada com êxito e clique em **Concluir**.
    
    > [!IMPORTANT]  
    > Após publicar a topologia, você deve configurar as opções e políticas de Arquivamento antes que qualquer conteúdo seja arquivado. Para detalhes, consulte <a href="lync-server-2013-configuring-support-for-archiving.md">Configurando o suporte para arquivamento no Lync Server 2013</a> na documentação de Implantação.
