---
title: (Recomendado) Criar diretórios de conferência
TOCTitle: (Recomendado) Criar diretórios de conferência
ms:assetid: 787f4c94-1c96-468a-a74d-e06b7bd4b8a3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn832056(v=OCS.15)
ms:contentKeyID: 63257627
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (Recomendado) Criar diretórios de conferência

 

_**Tópico modificado em:** 2014-10-03_

Diretórios de conferência mantêm um mapeamento entre o ID alfanumérico da reunião que o participante usa para entrar em uma conferência quando estiver usando o Lync 2013 e o ID exclusivamente numérico da conferência que o participante da conferência discada usa para entrar nela. O formato do ID de conferência é como segue:

    <housekeeping digit (1 digit)><conference directory (usually 1-2 digits)><conference number (variable number of digits><check digit (1 digit)>

Criar vários diretórios de conferência garantirá que os IDs de conferência sejam curtos até que uma quantidade significativa de conferências seja criada. Em uma organização com um número comum de conferências por usuário, é recomendável criar um diretório de conferência para cada 999 usuários no pool. Usando essa diretriz, os IDs podem ser geralmente mantidos pequenos. No entanto, assim que o número de diretórios de conferência (em todos os pools) ultrapassar 9, o tamanho do ID de conferência aumentará para suportar conferências adicionais.

## Criando um diretório de conferência

1.  Em Shell de Gerenciamento do Lync Server, digite o seguinte cmdlet:
    
        New-CsConferenceDirectory -Identity <XdsGlobalRelativeIdentity> -HomePool <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
    
    Por exemplo, o seguinte cria um diretório de conferência com a identidade 42, hospedado no pool atl-cs-001.litwareinc.com:
    
        New-CsConferenceDirectory -Identity 42 -HomePool "atl-cs-001.litwareinc.com"

## Consulte Também

#### Conceitos

[Exigências da conferência discada no Lync Server 2013](lync-server-2013-dial-in-conferencing-requirements.md)  

#### Outros Recursos

[New-CsConferenceDirectory](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsConferenceDirectory)

