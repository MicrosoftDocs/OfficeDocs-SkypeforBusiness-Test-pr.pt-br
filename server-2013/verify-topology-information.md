---
title: Verificar informações da topologia
TOCTitle: Verificar informações da topologia
ms:assetid: aa4c424e-f87c-4be6-8df6-a0cd193b11fc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205151(v=OCS.15)
ms:contentKeyID: 49307753
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar informações da topologia

 

_**Tópico modificado em:** 2012-09-26_

A primeira etapa na verificação da conclusão da mesclagem é exibir as informações de topologia do Office Communications Server 2007 R2 que você mesclou com o Lync Server 2013. No Construtor de Topologias, o nó **BackCompatSite** exibe o FQDN (nome de domínio totalmente qualificado) de cada pool e servidor do Office Communications Server 2007 R2 que você mesclou.

## Para ver BackCompatSite no Construtor de Topologia

1.  Em seu ambiente do Office Communications Server 2007 R2, abra a ferramenta administrativa do Office Communications Server 2007 R2 e anote os FQDNs dos pools e servidores antigos.

2.  Em seu ambiente do Lync Server 2013, abra o Construtor de Topologias e expanda o nó **BackCompatSite** .

3.  Verifique se os FQDNs dos pools e servidores mesclados são exibidos.
    
    > [!NOTE]  
    > Você não vê nenhuma informação no <strong>BackCompatSite</strong> para servidores colocados em um servidor de Front End ou Standard Edition. Somente funções de servidor necessárias para interoperabilidade entre o Office Communications Server 2007 R2 e Lync Server 2013 são exibidas.

![Caixa de diálogo BackCompatSite do Construtor de Topologia](images/JJ205243.62751c76-f018-4c6d-bb48-c61ef8974d31(OCS.15).jpg "Caixa de diálogo BackCompatSite do Construtor de Topologia")

Também é possível usar o Painel de Controle do Lync Server 2013 para exibir sua topologia mesclada. No Painel de Controle do Lync Server 2013, é possível ver cada FQDN de servidor, FQDN de pool e nome de site de sua topologia mesclada. Os servidores mesclados têm um nome de **Site** de **BackCompatSite** .

## Para exibir a topologia mesclada no Painel de Controle do Lync Server 2013

1.  Abrir o Painel de Controle do Lync Server 2013.

2.  Clique em **Topologia** .

3.  Na guia **Status** , verifique se os servidores e pools mesclados aparecem procurando por **BackCompatSite** na coluna **Site** .

![Painel de Controle do Lync Server mostrando a topologia mesclada](images/JJ205151.f986ddd4-2040-454d-9389-7f6154b59cc9(OCS.15).jpg "Painel de Controle do Lync Server mostrando a topologia mesclada")

Para ver mais detalhes sobre um pool mesclado, use o cmdlet **Get-CsPool** . Além das informações disponíveis no Construtor de Topologias e Painel de Controle do Lync Server 2013, esse cmdlet exibe os serviços que são executados no pool Lync Server 2013.

> [!NOTE]  
> Quando você pública a topologia após a execução do Assistente de mesclagem no Construtor de Topologias, os diretórios de conferência são mesclados no Lync Server 2013. Os diretórios de conferência podem ser verificados executando o cmdlet <strong>Get-CsConferenceDirectory</strong>.

## Para ver serviços em um pool mesclado

1.  Abra o Shell de Gerenciamento do Lync Server 2013.

2.  Na linha de comando, digite o seguinte:
    
        Get-CsPool [-Identity <FQDN of the pool>]
    
    Por exemplo:
    
        Get-CsPool -Identity pool02.contoso.net

## Para verificar os diretórios de conferência mesclados

1.  Abra o Shell de Gerenciamento do Lync Server 2013.

2.  Na linha de comando, digite o seguinte:
    
        Get-CsConferenceDirectory

3.  Verifique se todos os diretórios de conferência para o pool ou servidor que você está mesclando estão no Lync Server 2013.

