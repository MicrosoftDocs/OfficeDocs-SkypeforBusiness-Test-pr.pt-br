---
title: Verificar coexistência de pool piloto com pool herdado
TOCTitle: Verificar coexistência de pool piloto com pool herdado
ms:assetid: fe7e14bb-c7eb-4719-b154-009e99360520
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205420(v=OCS.15)
ms:contentKeyID: 49308718
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar coexistência de pool piloto com pool herdado

 

_**Tópico modificado em:** 2012-09-29_

Depois de implantar o pool piloto, você deve verificar a coexistência de dois pools usando ferramentas administrativas para exibir as informações dos pools. Para os pools Lync Server 2013 e pools herdados, você deve usar as ferramentas Painel de Controle do Lync Server 2013 e Construtor de Topologias.

## Verifique se os serviços do Lync Server 2013 foram iniciados

1.  No servidor Front End Lync Server 2013, navegue em Ferramentas Administrativas\\Serviços applet.

2.  Verifique se os serviços a seguir estão sendo executados no servidor Front End:

**Serviços do Lync Server 2013**

![Lista de serviços do Lync Server iniciados](images/JJ205420.cfff9385-6bf6-461c-982c-e727c9f20b70(OCS.15).png "Lista de serviços do Lync Server iniciados")

## Abra o Painel de Controle do Lync Server 2013

No servidor Front End em sua implantação de Lync Server 2013, abra o Painel de Controle do Lync Server 2013 e selecione o pool Lync Server 2010. Repita o procedimento para abrir o pool Lync Server 2013.

**Abre o Painel de controle do Lync Server 2013**

![Caixa de diálogo Selecionar URL](images/JJ205420.b1f8e650-9c3c-4563-a403-5069f198342f(OCS.15).png "Caixa de diálogo Selecionar URL")

> [!IMPORTANT]  
> Em Lync Server 2013, você atualizar Silverlight para Silverlight versão 5 antes de usar o Painel de Controle do Lync Server.

Essa topologia agora inclui as funções de servidor Lync Server 2010 e Lync Server 2013.

**Página de Topologia do Painel de Controle do Lync Server 2013**

![Painel de Controle do Lync Server - página Topologia](images/JJ205420.4ed1cc7a-cb3e-42f6-82e2-6d4d71d19352(OCS.15).jpg "Painel de Controle do Lync Server - página Topologia")

## Não tente abrir a topologia no Construtor de Topologias Lync Server 2010

Se tentar abrir a topologia usando o Lync Server 2010 Construtor de Topologias, você receberá o erro abaixo. A topologia pode ser visualizada somente usando o Lync Server 2013 Construtor de Topologias. O Lync Server 2013 Construtor de Topologias deve ser usado para criar pools para Lync Server 2013 e Lync Server 2010.

**Mensagem de erro do Construtor de Topologia do Lync Server 2010**

![Erro de Ajuste MMC do Construtor de Topologias do Lync Server](images/JJ205420.f6666343-c348-4d81-ae0e-6ba5a44e16c4(OCS.15).png "Erro de Ajuste MMC do Construtor de Topologias do Lync Server")

