---
title: Configurando versões de cliente suportadas
TOCTitle: Configurando versões de cliente suportadas
ms:assetid: aebf7b48-9aa2-4a06-adc5-0c9d11b6358d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412832(v=OCS.15)
ms:contentKeyID: 49307819
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando versões de cliente suportadas

 

_**Tópico modificado em:** 2012-12-14_

No Lync Server 2013, você pode configurar políticas de versão do cliente para especificar as versões dos clientes que são suportadas no ambiente. Além disso, é possível usar a configuração global de versão do cliente para especificar uma ação padrão de clientes que não têm uma política de versão definida e, portanto, não são suportados ou restritos explicitamente.

Também é possível usar políticas de versão do cliente para gerenciar atualizações do cliente. Ao definir uma política de versão do cliente e usar as opções **Permitir e atualizar** e **Bloquear e atualizar**, os clientes receberão software atualizado do Windows Server Update Service (se estiver usando este serviço) ou do Microsoft Update.

## Configurações de política de versão de cliente

A a política de versão padrão do cliente exige que todos os clientes executem o Lync ou o Microsoft Office Communicator 2007 R2. Se os cliente em seu ambiente estiverem executando versões anteriores do Communicator, pode ser necessário reconfigurar as regras da Versão do cliente para impedir que clientes e dispositivos sejam bloqueados ou atualizados inesperadamente ao se conectarem com Lync Server 2013. É possível modificar a regra padrão ou você pode adicionar uma regra superior na lista de Política de versão do cliente para substituir a regra padrão. Além disso, conforme as Atualizações cumulativas (CUs) são lançadas, você deve configurar a Política de versão do cliente para exigir as atualizações mais recentes.

