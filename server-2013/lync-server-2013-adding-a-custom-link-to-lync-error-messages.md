---
title: "Lync Server 2013: Adicionando um link personalizado às mens. de erro do Lync"
TOCTitle: Adicionando um link personalizado às mensagens de erro do Lync
ms:assetid: de756088-fcc3-4e47-bde8-4fa4cc852fd1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398979(v=OCS.15)
ms:contentKeyID: 52057739
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionando um link personalizado às mensagens de erro do Lync no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-20_

Personalize as mensagens de erro do Lync 2013 adicionando um link às suas próprias informações de suporte técnico ou solução de problemas. Para fazer isso, use o cmdlet **New-CSClientPolicy** ou **Set-CSClientPolicy** Shell de Gerenciamento do Lync Server com o parâmetro CustomLinkInErrorMessages. O texto do link personalizado é "Clique aqui para obter tópicos de suporte do administrador" e não pode ser personalizado.

Por exemplo, o comando a seguir faz com que o link personalizado apareça na área da nota de rodapé de cada mensagem de erro do Lync 2013 e define o destino do link para http://contoso.com/help/LyncHelpDesk.aspx:

    New-CsClientPolicy -Identity LyncErrorLink -CustomLinkInErrorMessages "http://contoso/help/LyncHelpDesk.aspx"

Use o **Grant-CSClientPolicy** para atribuir essa nova política aos usuários. Para obter detalhes, consulte **New-CSClientPolicy** e **Grant-CSClientPolicy** na documentação do Shell de Gerenciamento do Lync Server.

