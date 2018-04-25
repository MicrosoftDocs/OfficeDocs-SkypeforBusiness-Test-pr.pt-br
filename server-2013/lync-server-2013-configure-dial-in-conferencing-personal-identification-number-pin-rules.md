---
title: Configurar regras de PIN da conferência discada no Lync Server 2013
TOCTitle: Configurar regras de PIN da conferência discada no Lync Server 2013
ms:assetid: 27b79fb1-e2dc-4f71-bc82-b6eb61be2b16
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520967(v=OCS.15)
ms:contentKeyID: 49306181
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar regras de PIN da conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2012-06-19_

Os usuários do Lync Server 2013 que têm credenciais do AD DS (Serviços de Domínio Active Directory) em sua organização podem ingressar em conferências de discagem como usuários autenticados usando um PIN (número de identificação pessoal). A política de PIN define as regras de funcionamento dos PINs de conferências de discagem.

É possível criar uma nova política de PIN se você quiser que uma política específica seja aplicada a um site ou a determinado grupo de usuários. Se você quiser usar a mesma política de PIN para toda sua organização, poderá usar a política de PIN global e modificá-la conforme o necessário. As políticas de PIN se aplicam aos usuários a partir do escopo mais estreito para o mais amplo. Se você atribuir uma política de PIN no nível de usuário a um usuário, essas configurações terão precedência. Se você não atribuir uma política de usuário, a política de PIN no nível de site será aplicada, se existir. Se nenhuma política de usuário ou site se aplicar, a política de PIN global fornecerá as configurações padrão.

## Nesta seção

  - [Modificar as configurações de PIN de conferência discada no Lync Server 2013](lync-server-2013-modify-the-default-dial-in-conferencing-pin-settings.md)

  - [Criar ou modificar as configurações de PIN de conferência discada no Lync Server 2013 para um site ou grupo de usuários](lync-server-2013-create-or-modify-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md)

  - [Excluir configurações de PIN de conferência discada para um local ou grupo de usuários](lync-server-2013-delete-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md)

