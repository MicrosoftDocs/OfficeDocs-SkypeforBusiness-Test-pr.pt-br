---
title: Criar ou modificar rotas da região de rede
TOCTitle: Criar ou modificar rotas da região de rede
ms:assetid: 76993daa-76c2-4cec-8363-de8aebef0145
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521016(v=OCS.15)
ms:contentKeyID: 49307153
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar rotas da região de rede

 

_**Tópico modificado em:** 2012-10-08_

Cada região de uma configuração do serviço de controle de admissão de chamadas (CAC) deve ter alguma maneira de acessar todas as outras regiões. Enquanto os links de regiões definem limitações de largura de banda nas conexões entre regiões e também representam os links físicos, uma rota determina qual caminho vinculado a conexão vai percorrer de uma região para a outra. Você pode usar o Painel de Controle do Lync Server para configurar as rotas de região de rede. No Painel de Controle do Lync Server, você pode criar, modificar ou excluir uma rota de região de rede. Use este tópico para criar ou modificar uma rota de região de rede. Para obter mais detalhes sobre a exclusão de rotas de região de rede existentes, consulte [Excluindo rotas da região de rede existentes](lync-server-2013-deleting-existing-network-region-routes.md).

## Para criar uma rota de região de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração de Rede** e em **Rota de Região**.

4.  Na página **Rota de Região**, clique em **Novo**.

5.  Em **Nova Rota de Região**, digite um valor no campo **Nome**.
    
    > [!NOTE]  
    > Este valor deve ser exclusivo na sua implantação do Microsoft Lync Server 2013.

6.  Na lista suspensa **Região de rede 1**, selecione uma das duas regiões que deve ser conectada por esta rota.

7.  Na lista suspensa **Região de rede 2**, selecione a região para esta rota. Esta região deve ser diferente da região selecionada para a região de rede 1.

8.  Use a caixa de listagem **Links de região de rede** para adicionar os links de região para a rota. Clique no botão **Adicionar** para exibir a página **Link de Região**. Clique em um link de região para adicionar a esta rota e clique em **OK**.
    
    > [!NOTE]  
    > Continue a clicar no botão <strong>Adicionar</strong> para adicionar mais links, ou selecione um link e clique em <strong>Remover</strong> para remover um link.

9.  Clique em **Confirmar**.

## Para modificar uma rota de região de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração de Rede** e em **Rota de Região**.

4.  Na página **Rota de Região**, clique no roteiro de região que você deseja alterar.

5.  No menu **Editar**, clique em **Exibir detalhes**.

6.  Em **Editar rota de região**, você pode alterar as regiões associadas por essa rota e os links de região associados ao roteiro.

7.  Clique em **Confirmar**.

## Consulte Também

#### Tarefas

[Excluindo rotas da região de rede existentes](lync-server-2013-deleting-existing-network-region-routes.md)

