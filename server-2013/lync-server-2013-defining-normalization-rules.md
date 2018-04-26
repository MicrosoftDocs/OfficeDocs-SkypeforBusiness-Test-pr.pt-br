---
title: 'Lync Server 2013: Definindo regras de normalização'
TOCTitle: Definindo regras de normalização
ms:assetid: ed31d56c-00b5-4f72-bd9f-beb4100d441f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399071(v=OCS.15)
ms:contentKeyID: 49308515
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo regras de normalização no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

As regras de normalização do Lync Server 2013 usam expressões regulares do .NET Framework para converter os números discados ao formato E.164; em outras palavras, as regras de normalização pegam o número de telefone discado por um usuário e convertem o número para o formato usado internamente pelo Lync Server. Cada plano de discagem deve ter uma ou mais regras de normalização atribuídas.

Para obter detalhes sobre as regras de normalização, consulte [Planos de discagem e regras de normalização no Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md) na documentação Planejamento.

Para obter detalhes sobre como escrever expressões regulares, consulte "Expressões Regulares do .NET Framework" em [http://go.microsoft.com/fwlink/p/?linkId=140927](http://go.microsoft.com/fwlink/p/?linkid=140927).

É possível usar um dos seguintes métodos para definir ou editar uma regra de normalização:

  - Use a ferramenta **Compilar uma Regra de Normalização** para especificar valores para os dígitos iniciais, tamanho, dígitos a serem removidos e dígitos a serem adicionados, e permita que o Painel de Controle do Lync Server gere o padrão de correspondência correspondente e a regra de conversão para você.

  - Escreva expressões regulares manualmente para definir o padrão de correspondência e a regra de conversão.

## Nesta seção

  - [Criar ou modificar uma regra de normalização usando a Regra Construir uma Normalização no Lync Server 2013](lync-server-2013-create-or-modify-a-normalization-rule-by-using-build-a-normalization-rule.md)

  - [Criar ou modificar uma regra de normalização manualmente no Lync Server 2013](lync-server-2013-create-or-modify-a-normalization-rule-manually.md)

## Consulte Também

#### Tarefas

[Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md)  
[Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md)

