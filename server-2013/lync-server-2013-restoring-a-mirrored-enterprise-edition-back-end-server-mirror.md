---
title: Restaurando um servidor back-end Enterprise Edition espelhado – espelho
TOCTitle: Restaurando um servidor back-end Enterprise Edition espelhado – espelho
ms:assetid: 4b3c8eae-6f1f-4377-b39b-6699e725c517
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945626(v=OCS.15)
ms:contentKeyID: 52057624
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurando um servidor back-end Enterprise Edition espelhado – espelho

 

_**Tópico modificado em:** 2013-02-19_

Se você tiver um servidor de back-end Enterprise Edition em uma configuração em espelho e somente o banco de dados de espelho falhar, siga os procedimentos nesta seção. Se ambos o banco de dados primário e o de espelho falharem, consulte [Restaurando um servidor de back-end do Enterprise Edition](lync-server-2013-restoring-an-enterprise-edition-back-end-server.md). Se somente o banco de dados primário falhar, consulte [Restaurando um servidor back-end Enterprise Edition espelhado – primário](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-primary.md). Se o banco de dados hospedando o repositório de Gerenciamento Central falhar, consulte [Restaurar o servidor que hospeda o Repositório de Gerenciamento Central](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md). Se um servidor membro do Enterprise Edition que não for o servidor de back-end falhar, consulte [Restaurando um servidor membro do Enterprise Edition](lync-server-2013-restoring-an-enterprise-edition-member-server.md).

Recomendamos que você faça uma cópia da imagem do sistema antes de iniciar a restauração. Você pode utilizar essa imagem como ponto de reversão caso ocorra algo errado durante a restauração. Convém usar a cópia da imagem depois de instalar o sistema operacional e o SQL Server e restaurar ou registrar novamente os certificados.

## Para restaurar um banco de dados de espelho de servidor de back-end Enterprise Edition

1.  A partir de uma conta de usuário membro do grupo RTCUniversalServerAdmins, faça logon em um servidor front-end.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Desinstale o espelhamento. Primeiro, digite o cmdlet a seguir:
    
        Uninstall -CsMirrorDatabase -DatabaseType User -SqlServerFqdn <PrimaryServerFqdn> -SqlInstanceName <SQLInstance> -verbose
    
    Por exemplo:
    
        Uninstall -CsMirrorDatabase -DatabaseType User -SqlServerFqdn server4.contoso.com -SqlInstanceName archinst -verbose
    
    Faça isso para todos os tipos de bancos de dados em seu sistema.

4.  Crie um servidor novo ou limpo que tenha o mesmo nome de domínio totalmente qualificado (FQDN, neste exemplo DB1.contoso.com) que o computador com falha, instale o sistema operacional e então restaure ou atribua os certificados. Esse servidor funcionará como o novo espelho.

5.  A partir de uma conta de usuário membro do grupo RTCUniversalServerAdmins, faça logon no novo servidor.

6.  Instale o servidor SQL 2012 ou servidor SQL 2008 R2, mantendo os nomes das instâncias idênticos àqueles prévios à falha.

7.  A partir de uma conta de usuário membro do grupo RTCUniversalServerAdmins, faça logon em um servidor front-end.

8.  Use o Construtor de Topologia para instalar o banco de dados do espelho. Realize as etapas a seguir:
    
      - Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.
    
      - Clique com o botão direito no nó do Lync Server 2013, clique em **Topologia** e então em **Instalar Banco de Dados**.
    
      - Siga o procedimento do assistente para **Instalar Banco de Dados**. Na página **Criar bancos de dados**, selecione os bancos de dados que você deseja recriar.
    
      - Siga o assistente até que o prompt **Criar Banco de Dados de Espelho** apareça. Selecione o banco de dados que você deseja instalar e complete o processo.
        

        > [!TIP]  
        > Em vez de executar o Construtor de Topologia, você pode utilizar o cmdlet <STRONG>Install-CsMirrorDatabase</STRONG> para configurar o espelhamento. Para mais detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server.


