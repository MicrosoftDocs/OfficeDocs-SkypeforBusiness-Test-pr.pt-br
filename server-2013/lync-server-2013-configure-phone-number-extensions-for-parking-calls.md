---
title: Configurar extensões de números de telefone para estacionamento de chamadas
TOCTitle: Configurar extensões de números de telefone para estacionamento de chamadas
ms:assetid: fbf97624-9587-42a6-b276-1b69c574a74d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182611(v=OCS.15)
ms:contentKeyID: 49308700
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar extensões de números de telefone para estacionamento de chamadas

 

_**Tópico modificado em:** 2012-09-10_

Aplicativo de Estacionamento de Chamada usa números de extensão na tabela de órbita de Estacionamento de Chamada para estacionamento de chamada. É necessário configurar a tabela de órbita Estacionamento de Chamada com intervalos de números de extensão reservados pela organização para chamadas estacionadas. Essas extensões precisam ser extensões virtuais (ou seja, extensões com nenhum usuário ou telefone atribuído a eles). Cada pool do Lync Server onde um aplicativo de Aplicativo de Estacionamento de Chamada é implantado e configurado pode ter um ou mais intervalos de órbita. Os intervalos de órbita devem ser exclusivos globalmente entre as implantações do Lync Server.

> [!IMPORTANT]  
> Marque a caixa de seleção <strong>Habilitar estacionamento de chamada</strong> na sua política de voz antes de usar o Estacionamento de Chamada. Por padrão, essa opção não está selecionada.

## Nesta seção

  - [Criar ou modificar o intervalo de órbita de Estacionamento de Chamadas no Lync Server 2013](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)

  - [Excluir um intervalo de órbita de estacionamento de chamada no Lync Server 2013](lync-server-2013-delete-a-call-park-orbit-range.md)

