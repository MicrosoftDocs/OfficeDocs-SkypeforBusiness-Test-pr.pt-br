---
title: Restaurando um servidor back-end Enterprise Edition espelhado – primário
TOCTitle: Restaurando um servidor back-end Enterprise Edition espelhado – primário
ms:assetid: bc555b46-70c5-4eee-ae91-e195df238293
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945648(v=OCS.15)
ms:contentKeyID: 52057701
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurando um servidor back-end Enterprise Edition espelhado – primário

 

_**Tópico modificado em:** 2013-02-17_

Se você tiver um Servidor de Back End Enterprise Edition em uma configuração em espelho e somente o banco de dados primário falhar, siga os procedimentos nesta seção. Se ambos o banco de dados primário e o de espelho falharem, consulte [Restaurando um servidor de back-end do Enterprise Edition](lync-server-2013-restoring-an-enterprise-edition-back-end-server.md). Se somente o espelho falhar, consulte [Restaurando um servidor back-end Enterprise Edition espelhado – espelho](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md). Se o banco de dados hospedando o repositório de Gerenciamento Central falhar, consulte [Restaurar o servidor que hospeda o Repositório de Gerenciamento Central](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md). Se um servidor membro do Enterprise Edition que não for o Back End Server falhar, consulte [Restaurando um servidor membro do Enterprise Edition](lync-server-2013-restoring-an-enterprise-edition-member-server.md).

Recomendamos que você realize uma imagem de backup do sistema antes de dar início à restauração. Você pode utilizar essa imagem como um ponto de retorno, caso algo dê errado durante a restauração. Você pode desejar utilizar a imagem de backup após a instalação do sistema operacional e servidor SQL, e restaurar ou reinscrever os certificados.

Neste tópico, o banco de dados primário usado como exemplo terá um nome de domínio totalmente qualificado (FQDN) de BE1.contoso.com, e o banco de dados de espelho terá um FQDN de BE2.contoso.com.

## Para restaurar um banco de dados primário de Servidor de Back End Enterprise Edition

1.  A partir de uma conta de usuário membro do grupo RTCUniversalServerAdmins, faça logon em um Servidor Front End.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Force todos os bancos de dados configurados a realizarem failover para o espelho. Para cada um dos tipos de bancos de dados que você tiver configurado neste servidor, digite o cmdlet a seguir:
    
        Invoke-CsDataBaseFailover -PoolFqdn <Pool FQDN> -DatabaseType <Configured Database Type> -NewPrincipal Mirror -Force -Verbose
    
    Por exemplo:
    
        Invoke-CsDataBaseFailover -PoolFqdn pool0.vdomain.com -DatabaseType User -NewPrincipal Mirror -Force -Verbose
    

    > [!WARNING]  
    > Caso tenha configurado o banco de dados back-end para usar espelhamento sincronizado com uma testemunha, o failover será automático.



4.  Após completar o failover, faça o seguinte:
    
      - Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.
    
      - Desabilite o espelhamento no Servidor de Back End: clique com o botão direito no pool sob **pools de Front-End Enterprise Edition** e selecione **Editar Propriedades**. Na guia **Geral**, sob **Associações**, limpe a caixa de marcar **Habilitar espelhamento do SQL Server store**. Faça isso para Arquivamento e Monitoramento conforme necessário. Em seguida, clique em **OK**.
    
      - Clique com o botão direito sobre o nó do Lync Server 2013, clique em **Topologia** e então em **Publicar**.
    
      - Selecione o backend ainda operante (BE2.contoso.com) como o novo SQL store. Para fazer isso, clique com o botão direito no pool sob **pools de Front End Enterprise Edition** e selecione **Editar Propriedades**. Na guia **Geral**, sob **Associações**, digite o FQDN do backend operante no campo **SQL Server store** (no exemplo dado a você, BE2.contoso.com).
    
      - Clique com o botão direito sobre o nó do Lync Server 2013, clique em **Topologia** e então em **Publicar**.
    
      - Reinicie os serviços de modo que cada servidor possa ler a nova topologia. A partir de um Shell de Gerenciamento do Lync Server, execute os cmdlets a seguir em cada Servidor de Front End que pertença a esse pool:
        
            Stop-CsWindowsService
            Start-CsWindowsService

5.  Desinstale o espelhamento. A partir de um Shell de Gerenciamento do Lync Server, execute o cmdlet a seguir:
    
        Uninstall-CsMirrorDatabase -DatabaseType User -SqlServerFqdn <MirrorServerFqdn> -SqlInstanceName <SQLInstance> -verbose
    
    Por exemplo:
    
        Uninstall-CsMirrorDatabase -DatabaseType User -SqlServerFqdn DB2.contoso.com -SqlInstanceName rtc -verbose
    
    Faça isso para todos os tipos de bancos de dados em seu sistema.

6.  Crie um servidor novo ou limpo que tenha o mesmo FQDN (neste exemplo, DB1.contoso.com) como o computador com falha, instale o sistema operacional e então restaure ou atribua os certificados. Esse servidor funcionará como o novo espelho.

7.  A partir de uma conta de usuário membro do grupo RTCUniversalServerAdmins, faça logon no novo servidor.

8.  Instale o servidor SQL 2012 ou servidor SQL 2008 R2, mantendo os nomes das instâncias idênticos àqueles prévios à falha.

9.  A partir de uma conta de usuário membro do grupo RTCUniversalServerAdmins, faça logon em um Servidor Front End.

10. Use o Construtor de Topologia para instalar o banco de dados do espelho. Realize as etapas a seguir:
    
      - Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.
    
      - Habilite o espelhamento no Servidor de Back End. Para isso, clique com o botão direito no pool sob **pools de Front-End Enterprise Edition** e selecione **Editar Propriedades**. Na guia **Geral**, sob **Associações**, selecione a caixa de marcar **Habilitar espelhamento do SQL Server store**. Faça isso também para Arquivamento e Monitoramento, se necessário.
        
        Então, no campo **Espelhando o SQL Server store**, digite o FQDN do novo servidor (neste exemplo, BE1.contoso.com). Em seguida, clique em **OK**.
    
      - Clique com o botão direito no nó do Lync Server 2013, clique em **Topologia** e então em **Instalar Banco de Dados**.
    
      - Siga o procedimento do assistente para **Instalar Banco de Dados**. Na página **Criar bancos de dados**, selecione os bancos de dados que você deseja recriar.
    
      - Siga o assistente até que você chegue ao prompt **Criar Banco de Dados de Espelho**. Selecione o banco de dados que você deseja instalar e complete o processo.

