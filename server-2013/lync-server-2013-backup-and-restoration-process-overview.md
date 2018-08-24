---
title: Visão geral do processo de restauração e backup
TOCTitle: Visão geral do processo de restauração e backup
ms:assetid: e0f23b21-070f-4df5-b795-cea2f5338d85
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202192(v=OCS.15)
ms:contentKeyID: 52057746
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral do processo de restauração e backup

 

_**Tópico modificado em:** 2013-03-26_

Esta seção fornece uma visão geral de como funciona o processo de backup e restauração para o Lync Server 2013. O mesmo processo é usado para todos os servidores Standard Edition e Enterprise Edition, independentemente de seus locais.

Em geral, o processo de backup funciona da seguinte maneira:

  - Você cria um local de backup como uma pasta compartilhada em um computador autônomo que não faz parte de qualquer pool. O local do backup é citado em **$Backup**.

  - De forma regular e agendada, você faz o backup de todos os bancos de dados do Lync Server e de todos os repositórios de arquivo descritos em [Requisitos de backup e restauração: dados](lync-server-2013-backup-and-restoration-requirements-data.md) seguindo os procedimentos descritos em [Fazendo backup do Lync Server](lync-server-2013-backing-up-lync-server.md). O Repositório de Gerenciamento Central inclui todas as configurações de servidor.

  - Sempre que você executa um backup subsequente, cria uma nova pasta compartilhada e muda o caminho consultado pelo **$Backup**.

Em geral, o processo de restauração funciona da seguinte maneira:

  - Quando uma falha ou interrupção ocorre, você restaura os dados no local referenciado pelo **$Backup** para computadores novos ou limpos.
    
    > [!IMPORTANT]  
    > Este processo de restauração não restaura os dados para um estado de servidor existente. Ou seja, esse processo exige que o servidor seja limpo ou novo.

  - Para permitir que as informações de conferência e de usuário sejam recuperáveis após uma falha, você pode implementar uma topologia de recuperação pós-desastre com pools de Front-End emparelhados, como descrito em [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md). Além dessa opção, o Lync Server suporta somente o modelo de recuperação simples para seus bancos de dados. Com o modelo de recuperação simples, bancos de dados são recuperados até o ponto do último backup completo, o que significa que você não poderá restaurar um banco de dados até o ponto onde ocorreu a falha ou até um ponto específico no tempo. Para muitas organizações, o modelo de recuperação simples é ideal, porque o banco de dados back-end do Lync Server (RTCXDS.mdf) é na verdade menor que os arquivos de log de transação, e é significativamente menor que os arquivos de aplicativos de bancos de dados típicos de certas linhas de atuação comercial.

  - Toda configuração de DNS (Sistema de Nomes de Domínio), configuração DHCP (Dynamic Host Configuration Protocol), nomes de domínio, FQDNs (nomes de domínio totalmente qualificados), caminhos de repositório de arquivo e assim por diante, precisam ser no momento da restauração iguais as do momento do backup.

Se um servidor que estiver executando o Lync Server falhar, a recuperação incluirá as seguintes etapas:

  - Instale o sistema operacional em um computador novo ou limpo com o mesmo FQDN que o computador com falha.

  - Reinstale os certificados.

  - Se o servidor hospedar um banco de dados, instale o Microsoft SQL Server 2012 ou o Microsoft SQL Server 2008 R2.

  - Em geral, se o servidor hospedar um banco de dados, execute o Construtor de Topologias para criar e instalar o banco de dados e configurar as ACLs (Listas de controle de acesso).

  - Em geral, se o servidor hospedar uma função de servidor, execute a Etapa 1 a 4 do Assistente de Implantação do Lync Server para instalar os arquivos de configuração local, instalar os componentes da função do servidor, atribuir certificados e iniciar os serviços.
    
    > [!NOTE]  
    > Se o servidor hospedar um banco de dados alinhado com a função de servidor, a execução da etapa 2 do Assistente de Implantação do Lync Server recriará o banco de dados.

  - Se o servidor hospedou um banco de dados, restaure os dados do backup.

