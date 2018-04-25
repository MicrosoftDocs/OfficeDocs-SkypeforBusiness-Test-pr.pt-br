---
title: Criar um novo filtro de URL para tratar hiperlinks em conversas de IM
TOCTitle: Criar um novo filtro de URL para tratar hiperlinks em conversas de IM
ms:assetid: d0ee01e5-f039-4a34-ac9d-659fe4e9e879
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182590(v=OCS.15)
ms:contentKeyID: 49308193
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar um novo filtro de URL para tratar hiperlinks em conversas de IM

 

_**Tópico modificado em:** 2012-09-26_

Além de modificar o filtro de URL global, é possível configurar filtros de URL personalizados de locais específicos dentro da sua implantação do Lync Server 2013. Para obter detalhes sobre a filtragem de URLs, consulte [Configurando a filtragem de transferência de arquivo e URL para mensagens instantâneas (IM) no Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).

## Para criar um novo filtro de URL

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **IM e Presença** e clique em **Filtro de URL**.

4.  Na página **Filtro de URL**, clique em **Novo**.

5.  Em **Selecionar um Site**, clique no site para o qual você deseja criar o filtro de URL e clique em **OK**.

6.  Na caixa de diálogo **Novo Filtro de URL**, marque a caixa de seleção **Habilitar Filtro de URL** para habilitar a filtragem de URL para o site.

7.  Para bloquear qualquer URL ativa que contenha um arquivo com uma extensão listada sob **Extensões de tipos de arquivos a serem bloqueadas** em **Editar Filtro de Arquivo**, marque a caixa de seleção **Bloquear URLs com extensão de arquivo**.

8.  Na caixa de listagem suspensa **Prefixo de hiperlink**, clique na opção que corresponde à forma como você deseja lidar com URLs em conversas de mensagem instantânea.
    
    A caixa **Permitir mensagem** permite que uma mensagem de aviso seja enviada ao usuário ao enviar hiperlinks que têm permissão para serem enviados.

9.  Clique em **Confirmar**.

## Consulte Também

#### Tarefas

[Configurando a filtragem de transferência de arquivo e URL para mensagens instantâneas (IM) no Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)  
[Criar um novo filtro de transferência de arquivos para um local específico](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)  
[Modificar o filtro de transferência de arquivo padrão](lync-server-2013-modify-the-default-file-transfer-filter.md)  

#### Conceitos

[Modificar o filtro de URL padrão](lync-server-2013-modify-the-default-url-filter.md)

