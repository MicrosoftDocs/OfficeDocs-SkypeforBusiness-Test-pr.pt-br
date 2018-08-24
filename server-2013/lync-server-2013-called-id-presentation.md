---
title: Apresentação da ID chamada no Lync Server 2013
TOCTitle: Apresentação da ID chamada no Lync Server 2013
ms:assetid: cf6c6af5-3418-411e-a50b-7a9cf8e100d4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721892(v=OCS.15)
ms:contentKeyID: 49886420
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Apresentação da ID chamada no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Com o Lync Server 2010, o número de telefone da parte chamada (isto é, o número de telefone chamado) pode ser convertido do formato E.164 para o formato de discagem local exigido pelo *ponto de tronco* (isto é, o gateway associado, PBX ou tronco SIP). Para fazer isso, você deve definir uma ou mais regras de conversão para converter a URI de Solicitação antes de roteá-la para o ponto de tronco.

> [!IMPORTANT]  
> A capacidade de associar uma ou mais regras de conversão com uma configuração de tronco do Enterprise Voice é destinada a ser usada como uma <em>alternativa</em> para configurar regras de conversão no ponto de tronco. Não associe regras de conversão com uma configuração de tronco do Enterprise Voice se tiver regras de conversão configuradas no ponto do tronco porque as duas regras podem entrar em conflito.

Você pode usar um dos seguintes métodos para compilar ou modificar uma regra de conversão:

  - Use a ferramenta **Compilar uma Regra de Conversão** para especificar valores para os dígitos iniciais, comprimento, dígitos a serem removidos e dígitos a serem adicionados e permita que o Painel de Controle do Lync Server gere a regra de conversão e de padrão correspondente.

  - Escreva expressões regulares manualmente para definir o padrão de correspondência e a regra de conversão.

> [!NOTE]  
> Para obter informações sobre como escrever expressões regulares, consulte &quot;Expressões Regulares do .NET Framework&quot; em <a href="http://go.microsoft.com/fwlink/?linkid=140927%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=140927&amp;clcid=0x416</a>.

## Nesta seção

  - [Criar ou modificar uma regra de conversão usando a compilação de uma ferramenta de regra de conversão](lync-server-2013-create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool.md)

  - [Criar ou modificar uma regra de conversão manualmente](lync-server-2013-create-or-modify-a-translation-rule-manually.md)

## Consulte Também

#### Conceitos

[Apresentação de ID de Chamadas no Lync Server 2013](lync-server-2013-caller-id-presentation.md)

