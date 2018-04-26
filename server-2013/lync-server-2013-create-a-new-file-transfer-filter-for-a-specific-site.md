---
title: Criar um novo filtro de transferência de arquivos para um local específico
TOCTitle: Criar um novo filtro de transferência de arquivos para um local específico
ms:assetid: d0006487-5217-491c-b730-e6c551cd9825
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182589(v=OCS.15)
ms:contentKeyID: 49308185
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar um novo filtro de transferência de arquivos para um local específico

 

_**Tópico modificado em:** 2012-10-18_

Além de modificar o filtro de transferência global, é possível configurar os filtros de transferência de arquivo personalizado de locais específicos dentro da implantação do Lync Server 2013. Para obter detalhes sobre a filtragem de transferência de arquivos, consulte [Configurando a filtragem de transferência de arquivo e URL para mensagens instantâneas (IM) no Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).

## Para criar um filtro de transferência de arquivo para um site específico

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **IM e Presença** e clique em **Filtro de Arquivo** .

4.  Na página **Filtro de Arquivo**, clique em **Novo**.

5.  Na caixa de diálogo **Selecionar um Site**, clique no site para o qual você deseja criar o filtro de transferência de arquivo e clique em **OK**.

6.  Em **Novo Filtro de Arquivo**, clique na caixa de seleção **Habilitar filtro de arquivo**.

7.  Na caixa de listagem suspensa **Transferência de arquivo**, clique em **Bloquear Tudo** ou **Bloquear tipos de arquivos específicos**.

8.  Se você clicou em **Bloquear tudo**, pule para a etapa 10.

9.  Se você clicou em **Bloquear tipos de arquivos específicos**, faça o seguinte:
    
    1.  Clique em **Selecionar** para modificar a lista padrão de extensões de tipo de arquivo que você deseja bloquear.
    
    2.  Na caixa de diálogo **Selecionar Tipo de Arquivo**, selecione os tipos de arquivo que você deseja bloquear ou permitir adicionando ou removendo suas extensões das categorias sob **Extensões de tipo de arquivo**.
    
    3.  Se você não vir a extensão de um tipo de arquivo que você deseja bloquear, digite a extensão na caixa de texto sob **Adicionar extensões de tipo de arquivo à lista** e clique em **Adicionar**.
    
    4.  Clique em **OK**.

10. Clique em **Confirmar**.

## Consulte Também

#### Tarefas

[Configurando a filtragem de transferência de arquivo e URL para mensagens instantâneas (IM) no Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)  
[Criar um novo filtro de URL para tratar hiperlinks em conversas de IM](lync-server-2013-create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)  
[Modificar o filtro de transferência de arquivo padrão](lync-server-2013-modify-the-default-file-transfer-filter.md)  

#### Conceitos

[Modificar o filtro de URL padrão](lync-server-2013-modify-the-default-url-filter.md)

