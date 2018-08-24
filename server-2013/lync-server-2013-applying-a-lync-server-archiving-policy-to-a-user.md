---
title: Aplicando uma política de arquivamento do Lync Server ao usuário
TOCTitle: Aplicando uma política de arquivamento do Lync Server ao usuário
ms:assetid: a23e4876-aa8d-4f49-a3bd-3696616e8290
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205143(v=OCS.15)
ms:contentKeyID: 49307661
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Aplicando uma política de arquivamento do Lync Server ao usuário

 

_**Tópico modificado em:** 2012-10-10_

Após criar uma política de usuário do Lync Server, é necessário aplicá-la aos usuários ou grupos de usuários específicos que estão hospedados no Lync Server 2013, antes que entre em vigor. Para obter detalhes sobre a criação de políticas de usuário para usuários específicos, consulte [Criando e Configurando Políticas de Usuário para Arquivamento no Lync Server](lync-server-2013-creating-and-configuring-user-policies-for-archiving-in-lync-server.md) na documentação de Implantação.

Para obter detalhes sobre como as políticas de Arquivamento funcionam, incluindo a hierarquia para políticas globais, locais e de usuários, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, documentação de Implantação, ou documentação de Operações.

> [!NOTE]  
> Para configurar e usar arquivamento, você deve primeiro implantar o arquivamento. Para maiores detalhes, consulte <a href="lync-server-2013-deploying-archiving.md">Implantando Arquivamento no Lync Server 2013</a> na documentação de Implantação.<br />Se você ativar a integração do Microsoft Exchange em sua implantação, as políticas de Espera no Local do Exchange controlarão se o arquivamento está ativado para os usuários que estão hospedados no Exchange 2013 e terão suas caixas de correio colocadas em Espera no Local. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na documentação de Implantação.<br />Você deve especificar todas as opções apropriadas nas configurações de arquivamento antes de ativar o Arquivamento. Para obter detalhes, consulte <a href="lync-server-2013-configuring-archiving-options.md">Configurando opções de arquivamento</a> na documentação de Implantação.

## Para aplicar uma política de arquivamento Lync Server a um usuário

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server 2013. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server 2013, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários** e procure a conta de usuário que deseja configurar.

4.  Na tabela que lista os resultados da pesquisa, clique na conta do usuário, em **Editar** e em **Exibir detalhes**.

5.  Em **Editar usuário do Lync Server** em **Política de arquivamento**, selecione a política de usuário de arquivamento que você deseja aplicar.
    
    > [!NOTE]  
    > As configurações <strong>&lt;Automáticas&gt;</strong> são aplicadas nas configurações da instalação do servidor padrão. Essas configurações são aplicadas automaticamente pelo servidor.

6.  Clique em **Confirmar**.

