---
title: Configurando políticas de site para arquivamento
TOCTitle: Configurando políticas de site para arquivamento
ms:assetid: dc2ea206-8b9c-44dd-a479-efb217593c89
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205325(v=OCS.15)
ms:contentKeyID: 49308326
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando políticas de site para arquivamento

 

_**Tópico modificado em:** 2012-10-09_

É possível habilitar ou desabilitar o Arquivamento para sites específicos criando e configurando uma política de Arquivamento para cada um destes sites. Uma política de site substitui a política global, mas as políticas de usuário substituem as políticas de site. As políticas de arquivamento se aplicam apenas se você não usar a integração do Microsoft Exchange ou se você usar a integração Microsoft Exchange, mas possuir alguns usuários não hospedados no Exchange 2013 e suas caixas de correio em Retenção Local.

Para obter detalhes sobre como as políticas de Arquivamento funcionam, incluindo a hierarquia para políticas globais, de site e de usuário, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Implantação, Planejamento ou Operações.

> [!NOTE]  
> Se você habilitar a integração do Microsoft Exchange em sua implantação, as políticas de Retenção Local do Exchange controlam se o arquivamento é habilitado para os usuários hospedados no Exchange 2013 e possuem caixas de correio em Retenção Local. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na documentação de Implantação.<br />Você deve especificar todas as opções adequadas nas configurações de Arquivamento antes de habilitar o Arquivamento de comunicações internas ou externas nas políticas de Arquivamento. Para obter detalhes, consulte <a href="lync-server-2013-configuring-archiving-options.md">Configurando opções de arquivamento</a> na documentação de Implantação.

## Para criar uma política de arquivamento para um site

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server 2013.

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Política de Arquivamento**.
    
    Para obter detalhes sobre como as políticas de Arquivamento funcionam, incluindo a hierarquia de políticas globais, de site e de usuário, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, Implantação ou Operações.

4.  Clique em **Nova** e em **Política de site**.

5.  Em **Selecionar um site**, clique no site ao qual a política é aplicada.

6.  Em **Nova Política de Arquivamento**, faça o seguinte:
    
      - Em **Nome**, especifique um nome para a política do site.
    
      - Em **Descrição**, forneça as informações sobre a política de site (por exemplo, a política de de site para Redmond).
    
      - Para controlar o arquivamento das comunicações internas do site especificado, marque ou desmarque a caixa de seleção **Arquivar comunicações internas**.
    
      - Para controlar o arquivamento das comunicações externas do site especificado, marque ou desmarque a caixa de seleção **Arquivar comunicações externas**.

7.  Clique em **Confirmar**.

