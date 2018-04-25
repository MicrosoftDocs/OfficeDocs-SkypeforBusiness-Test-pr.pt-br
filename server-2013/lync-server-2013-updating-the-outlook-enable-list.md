---
title: Atualizando a opção Habilitar Lista do Outlook
TOCTitle: Atualizando a opção Habilitar Lista do Outlook
ms:assetid: 5db120dc-52f9-4dde-acb9-3824ae245086
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ215438(v=OCS.15)
ms:contentKeyID: 49306851
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atualizando a opção Habilitar Lista do Outlook

 

_**Tópico modificado em:** 2013-01-07_

Você pode garantir que o Suplemento de Reunião Online para Microsoft Lync 2013 sempre permaneça habilitado para os usuários criando uma política que o inclui na Lista de Gerenciamento de Suplementos para Outlook. A política de Lista de Gerenciamento de Suplementos está incluída nos arquivos de modelos administrativos do Office do Console de Gerenciamento de Política de Grupo. Ele cria uma chave de registro em HKCU\\Software\\Policies\\Microsoft\\Office\\15.0\\Outlook15\\Resiliency\\AddinList. Você pode adicionar um valor para ucaddin.dll dessa chave e configurar o valor ucaddin.dll, assim ele sempre esteja habilitado e que os usuários não possam desativá-lo manualmente.

## Para adicionar o ucaddin.dll à Lista de Gerenciamento de Suplementos para Outlook

  - Para a chave de registro AddinList, localizada em HKCU\\Software\\Policies\\Microsoft\\Office\\15.0\\Outlook15\\Resiliency\\AddinList, adicione o seguinte valor:
    
      - Tipo de Registro = REG\_SZ
    
      - Nome = ucaddin.dll
    
      - Valor = 1 (especifica que o suplemento sempre esteja habilitado e não possa ser gerenciado pelos usuários)

