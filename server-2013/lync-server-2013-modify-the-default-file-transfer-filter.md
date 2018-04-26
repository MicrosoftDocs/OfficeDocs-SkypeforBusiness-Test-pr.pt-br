---
title: Modificar o filtro de transferência de arquivo padrão
TOCTitle: Modificar o filtro de transferência de arquivo padrão
ms:assetid: 791774a2-0bb6-4b5b-aeb0-ff69abb170f4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521017(v=OCS.15)
ms:contentKeyID: 49307192
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar o filtro de transferência de arquivo padrão

 

_**Tópico modificado em:** 2012-11-01_

O Lync Server 2013 oferece um filtro de transferência de arquivos que bloqueia tipos específicos de arquivos durante as seguintes atividades relacionadas a arquivos na sua implantação do Lync Server 2013:

  - Solicitações de transferência de arquivo durante conversas de mensagens instantâneas (IM)

  - Carregamentos de arquivo e downloads durante o uso do recurso do folheto do cliente do Office Live Meeting 2007

  - Reprodução de multimídia durante conferências

Dependendo dos tipos de arquivos que deseja bloquear ou permitir, você pode usar Painel de Controle do Lync Server para modificar o filtro global. Para obter detalhes sobre a filtragem de transferência de arquivo, consulte [Configurando a filtragem de transferência de arquivo e URL para mensagens instantâneas (IM) no Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).

## Para modificar o filtro de transferência de arquivo padrão

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **IM e Presença** e em **Filtro de Arquivos**.

4.  Na página **Filtro de Arquivo**, clique duas vezes no filtro **Global**.

5.  Em **Editar Filtro de Arquivo**, marque a caixa de seleção **Habilitar filtro de arquivo**.

6.  Na caixa de listagem suspensa **Transferência de arquivos**, clique em **Bloquear tudo** ou em **Bloquear tipos de arquivo específicos**.

7.  Se você clicou em **Bloquear Tudo**, pule para a etapa 9.

8.  Se você clicou em **Bloquear tipos de arquivos específicos**, faça o seguinte:
    
    1.  Clique em **Selecionar** para modificar a lista padrão de extensões do tipo de arquivo que você deseja bloquear.
    
    2.  Em **Selecionar Tipo de Arquivo**, selecione os tipos de arquivo que você deseja bloquear ou permitir adicionando ou removendo suas extensões das categorias em **Extensões do tipo de arquivo**.
    
    3.  Se você não ver a extensão para um tipo de arquivo que deseja bloquear, digite a extensão na caixa de texto em **Adicionar extensões do tipo de arquivo à lista** e clique em **Adicionar**.
    
    4.  Clique em **OK**.

9.  Clique em **Confirmar**.

## Consulte Também

#### Tarefas

[Configurando a filtragem de transferência de arquivo e URL para mensagens instantâneas (IM) no Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)  
[Criar um novo filtro de transferência de arquivos para um local específico](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)  
[Criar um novo filtro de URL para tratar hiperlinks em conversas de IM](lync-server-2013-create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)  

#### Conceitos

[Modificar o filtro de URL padrão](lync-server-2013-modify-the-default-url-filter.md)

