---
title: Verificar se todos os objetos de Contato do Exchange UM foram removidos do pool herdado
TOCTitle: Verificar se todos os objetos de Contato do Exchange UM foram removidos do pool herdado
ms:assetid: 5a813169-0ed7-4f84-a242-ed2cd4ea5c43
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688068(v=OCS.15)
ms:contentKeyID: 49886232
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar se todos os objetos de Contato do Exchange UM foram removidos do pool herdado

 

_**Tópico modificado em:** 2012-09-26_

Use a ferramenta **OCSUmUtil** ou o cmdlet **Get-CsExumContact** para verificar se os objetos de contato de UM do Exchange foram removidos do pool Office Communications Server 2007 R2 antigo. **OCSUmUtil** está localizado na seguinte pasta:

%Arquivos de Programa%\\Common Files\\ Lync Server 2013\\Support\\OcsUMUtil.exe

**OCSUmUtil** precisa ser executado a partir de uma conta de usuário que tenha:

  - Associação ao grupo RTCUniversalServerAdmins e RTCUniversalUserAdmins (que inclui direitos para ler as configurações da Unificação de Mensagens do Exchange Server).

  - Direitos no domínio para criar objetos de contato no contêiner de unidade organizacional (UO) especificado

Para obter detalhes sobre como usar o cmdlet **Get-CsExumContact**, consulte [Get-CsExUmContact](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsExUmContact) na documentação do Shell de Gerenciamento do Lync Server.

