---
title: "Lync Server 2013: Normaliz. de cont. de ch. remota e de número de telefone"
TOCTitle: Normalização de controle de chamada remota e de número de telefone
ms:assetid: 291d9e87-4c65-4ea2-888f-517741391de5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558630(v=OCS.15)
ms:contentKeyID: 49306215
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Normalização de controle de chamada remota e de número de telefone no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-22_

Os clientes do Lync baixam regras de normalização de número de telefone como parte do download do arquivo do ABS (Serviço de Catálogo de Endereços). Em cenários de controle de chamada remota, as regras de normalização de número de telefone do Serviço de Catálogo de Endereços são aplicadas a chamadas recebidas e realizadas de controle de chamada remota. Para as chamadas recebidas para um usuário com o controle de chamada remota habilitado, primeiro o número de telefone do chamador é normalizado no formato E.164 pelo gateway SIP/CSTA ou PBX (Central Privada de Comutação Telefônica). Quando o Lync Server 2013 recebe a chamada do gateway, executa uma RNL (pesquisa de número reversa) do número de telefone do chamador em relação ao número normalizado na lista de Contatos do Microsoft Office Outlook ou na GAL (lista de endereços global) do receptor da chamada, que está armazenada no Serviço de Catálogo de Endereços. Se a pesquisa de número reversa encontrar uma correspondência, o chamador será identificado pelo nome na notificação de chamada recebida.

Para chamadas de saída do controle de chamada remota, o Lync aplica as regras de normalização de número de telefone do Serviço Catálogo de Endereços ao número discado antes de rotear a chamada ao gateway SIP/CSTA.

Para obter detalhes sobre a criação de regras de normalização do número de telefone para controle de chamada remota, consulte [Planos de discagem e regras de normalização no Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md) na documentação de Planejamento.

## Migrando as regras de normalização do número de telefone

Se você estiver migrando os usuários que antes estavam habilitados para controle de chamada remota, consulte os seguintes tópicos na documentação Migração:

  - Para Lync Server 2010, consulte [Migrar catálogo de endereços](migrate-address-book.md) na documentação de Migração.

  - Para Communications Server 2007 R2, consulte [Migrar catálogo de endereços](migrate-address-book_1.md) na documentação de Migração.

