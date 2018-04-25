---
title: 'Lync Server 2013: Reduzindo as IMs não solicitadas'
TOCTitle: Reduzindo as IMs não solicitadas para Lync Server 2013
ms:assetid: d2998708-e699-4465-a918-e1d9ea4c49c3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn518335(v=OCS.15)
ms:contentKeyID: 60505940
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Reduzindo as IMs não solicitadas para Lync Server 2013

 

_**Tópico modificado em:** 2013-12-05_

O aplicativo Filtro de IM Inteligente protege a implantação do Microsoft Lync Server 2013 contra os vírus mais comuns com prejuízo mínimo para a experiência do usuário. O Filtro de IM Inteligente oferece:

  - Filtragem avançada de URL

  - Filtragem avançada de transferência de arquivos

Use o Filtro de IM Inteligente para configurar filtros que bloqueiem mensagens instantâneas não solicitadas ou potencialmente prejudiciais de pontos de extremidade desconhecidos fora do firewall da empresa. Para configurar filtros, especifique os critérios a serem utilizados para determinar o que deve ser bloqueado, como mensagens instantâneas contendo hiperlinks e arquivos com extensões específicas.

Antes de implantar o Filtro de IM Inteligente, você deve compreender como as opções de filtragem são aplicadas quando as mensagens são roteadas de um servidor Lync Server 2013 para outro. O modo como essas opções de filtragem são aplicadas é consistente, quer os servidores estejam em uma única organização ou ultrapasse os limites organizacionais. Essa consistência se aplica ao modo como o aviso personalizado e os textos de aviso são inseridos nas mensagens e enviados entre os servidores.

A opção de filtragem recomendada é permitir mensagens instantâneas com hiperlinks, mas exigir que o Filtro de IM Inteligente desabilite o link, inserindo um sublinhado antes dele. Se você escolher essa opção, terá a opção adicional de redigir um aviso para os usuários que aparecem no início de cada mensagem instantânea que contém um hiperlink.

A segunda opção de filtragem é permitir mensagens instantâneas com hiperlinks não modificados. Se você escolher essa opção, terá a opção adicional (recomendada) de redigir um aviso para os usuários que estão inseridos em cada mensagem.

A terceira opção é bloquear todas as mensagens instantâneas que contêm hiperlinks. Se você escolher essa opção, o servidor enviará um aviso ao usuário, Você deverá escrever esse aviso.

