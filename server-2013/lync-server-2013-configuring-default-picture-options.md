---
title: Configurando opções de imagem padrão
TOCTitle: Configurando opções de imagem padrão
ms:assetid: b1c986f0-6400-447a-9e36-78c1c3a4f793
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn205074(v=OCS.15)
ms:contentKeyID: 53901666
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando opções de imagem padrão

 

_**Tópico modificado em:** 2013-03-22_

Por padrão, as imagens dos usuários são exibidas automaticamente. Se o usuário deseja ocultar suas imagens, eles podem selecionar a opção **Ocultar minha imagem** no cliente do Lync. No entanto, essa configuração é ignorada por outros aplicativos do Office.

Se a possibilidade de exibir imagens mesmo quando desligado pelo usuário é uma preocupação, você pode alterar as configurações de exibição de imagem do Lync globalmente ou para um local ou serviço para que as imagens do usuário não sejam exibidas por padrão. Use o seguinte cmdlet do Shell de Gerenciamento do Lync Serverpara que as imagens do usuários não sejam exibidas, a menos que eles optem explicitamente pela opção **Exibir minha imagem** no cliente:

    Set-CsPrivacyConfiguration -DisplayPublishedPhotoDefault $False

Para obter mais informações sobre esse cmdlet, consulte o [Set-CsPrivacyConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsPrivacyConfiguration) na documentação do Shell de Gerenciamento do Lync Server.

