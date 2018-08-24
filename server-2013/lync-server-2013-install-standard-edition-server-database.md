---
title: 'Lync Server 2013: Instalar o banco de dados do servidor Standard Edition'
TOCTitle: Instalar o banco de dados do servidor Standard Edition
ms:assetid: 0bd3a804-aad6-48cb-981b-54725af032db
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398167(v=OCS.15)
ms:contentKeyID: 49305853
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalar o banco de dados do servidor Standard Edition para o Lync Server 2013

 

_**Tópico modificado em:** 2012-10-01_

Configurar um Servidor Standard Edition como o único servidor da sua infraestrutura que hospeda usuários difere de outras instalações de servidores por haver uma seleção no **Assistente de Implantação** especificamente para a configuração do servidor inicial.

## Para instalar um servidor do Standard Edition

1.  Faça o longi no servidor no qual você quer instalar o Servidor Standard Edition como administrador local ou um domínio equivalente.

2.  Se você não houver preparado o Serviços de Domínio Active Directory, então primeiro realize esses procedimentos. Para obter detalhes, consulte [Preparando Serviços de Domínio do Active Directory para o Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md).

3.  No Assistente de Implantação do Lync Server, clique em **Preparar o primeiro servidor do Standard Edition** .

4.  Na página **Preparar primeiro servidor Standard Edition** , clique em **Avançar** .

5.  Na página **Executando comandos** , o Software de banco de dados Microsoft SQL Server 2008 Express é instalado como Repositório de Gerenciamento Central. Regras de firewall necessárias são criadas. Quando a instalação do banco de dados e do software de pré-requisito estiver completa, clique em **Finalizar** .
    
    > [!NOTE]  
    > A instalação inicial pode levar algum tempo sem nenhuma atualização visível na tela de resumo de saída do comando. Isto ocorre devido à instalação do SQL Server Express. Se você precisa monitorar a instalação do banco de dados, use o Gerenciador de Tarefas para monitorar a configuração.

6.  Na página do Assistente de Implantação do Lync Server, clique em **Instalar Construtor de Topologias** se você ainda não instalou as ferramentas administrativas. Para obter detalhes, consulte [Instalar ferramentas administrativas do Lync Server 2013](lync-server-2013-install-lync-server-administrative-tools.md).

7.  Confirme se há marcas de seleção verdes ao lado de “Preparar Active Directory,” “Preparar primeiro servidor Standard Edition” e “Instalar Construtor de Topologias”.

