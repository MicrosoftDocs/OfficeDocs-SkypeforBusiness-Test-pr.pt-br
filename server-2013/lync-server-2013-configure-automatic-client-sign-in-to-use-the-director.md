---
title: 'Lync Server 2013: Configurar Entrada Automática de Cliente para usar o Diretor'
TOCTitle: Configurar Entrada Automática de Cliente para usar o Diretor
ms:assetid: 85369ffc-53ae-43be-8a23-84a094faecff
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398678(v=OCS.15)
ms:contentKeyID: 49307340
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar Entrada Automática de Cliente para usar o Diretor no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Quando você implanta um Lync Server 2013, o Diretor ou um pool de Diretores, é recomendável usar a Entrada Automática do Cliente como prática recomendada. Para obter detalhes sobre como configurar servidores DNS para entrada automática do cliente, consulte [Requisitos DNS para conexão automática de clientes no Lync Server 2013](lync-server-2013-dns-requirements-for-automatic-client-sign-in.md) na documentação de Planejamento.

Se você já implantou a Entrada Automática do Cliente, consulte as seções a seguir para configurá-la em seu(s) Diretor(es).

## Instância de um único Diretor

Se já tiver a entrada automática de cliente implantada e ela estiver apontando para um Servidor Front-End ou Pool de Front-Ends, será necessário alterar o registro SRV de DNS para que ele aponte ao Diretor.

## Pool de Diretor

Se já tiver a entrada automática de cliente implantada e la está apontando para um Servidor Front-End ou Pool de Front-Ends, será necessário alterar o registro SRV de DNS para que ele aponte ao pool do Diretor.

