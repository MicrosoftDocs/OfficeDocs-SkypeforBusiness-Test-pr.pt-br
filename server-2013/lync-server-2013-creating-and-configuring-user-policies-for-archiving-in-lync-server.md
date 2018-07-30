---
title: Criando e Configurando Políticas de Usuário para Arquivamento no Lync Server
TOCTitle: Criando e Configurando Políticas de Usuário para Arquivamento no Lync Server
ms:assetid: 5af0e605-3563-4d6f-a3c6-511d204a3165
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204923(v=OCS.15)
ms:contentKeyID: 49306820
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criando e Configurando Políticas de Usuário para Arquivamento no Lync Server

 

_**Tópico modificado em:** 2012-10-09_

Para habilitar ou desabilitar o arquivamento para usuários específicos hospedados no Lync Server, primeiro você precisa criar uma política de usuário e depois aplicá-la a um ou mais usuários ou grupos de usuários. Para obter detalhes sobre como aplicar políticas de usuário a usuários específicos e a grupos de usuários, consulte [Aplicando uma política de arquivamento do Lync Server ao usuário](lync-server-2013-applying-a-lync-server-archiving-policy-to-a-user.md) na documentação de implantação.

Para obter detalhes sobre como as políticas de arquivamento funcionam, incluindo a hierarquia das políticas globais, de site e de usuário, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) nas documentações de planejamento, implantação e operações.

> [!NOTE]  
> Se você tiver habilitado a integração do Microsoft Exchange para sua implantação, as políticas de Bloqueio In-loco do Exchange controlarão se o arquivamento será habilitado para os usuários que estão hospedados no Exchange 2013 e cujas caixas de correio estão em Bloqueio In-loco. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na documentação de implantação.<br />Você deve especificar todas as opções adequadas nas configurações de arquivamento antes de habilitar o arquivamento. Para obter detalhes, consulte <a href="lync-server-2013-configuring-archiving-options.md">Configurando opções de arquivamento</a> no documentação de implantação.

## Para configurar uma política de arquivamento para usuários hospedados no Lync Server

1.  A partir de uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e digite a URL do administrador para abrir o Painel de Controle do Lync Server 2013. Para obter detalhes sobre os diferentes métodos que podem ser usados para iniciar o Painel de Controle do Lync Server 2013, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Política de Arquivamento**.

4.  Clique em **Novo** e em **Política do usuário**.

5.  Em **Nova Política de Arquivamento**, faça o seguinte:
    
      - Em **Nome**, especifique o nome da política de usuário.
    
      - Em **Descrição**, forneça informações sobre a política de usuário (por exemplo, política de usuário do departamento jurídico).
    
      - Para controlar o arquivamento das comunicações internas para a política de usuário, marque ou desmarque a caixa de seleção **Arquivar comunicações internas**.
    
      - Para controlar o arquivamento das comunicações externas para a política de usuário, marque ou desmarque a caixa de seleção **Arquivar comunicações externas**.

6.  Clique em **Confirmar**.

Uma política de usuário aplica-se somente aos usuários aos quais você a atribui. Para obter detalhes sobre como aplicar uma política de usuário a usuários específicos, consulte [Aplicando uma política de arquivamento do Lync Server ao usuário](lync-server-2013-applying-a-lync-server-archiving-policy-to-a-user.md) na documentação de implantação.

