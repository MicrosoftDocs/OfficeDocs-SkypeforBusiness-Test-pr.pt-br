---
title: 'Lync Server 2013: Requisitos de hardware e de software para o Diretor'
TOCTitle: Requisitos de hardware e de software para o Diretor
ms:assetid: 747b701e-7f97-46fe-91c5-1e8d9addf9f7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398560(v=OCS.15)
ms:contentKeyID: 49307123
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de hardware e de software para o Diretor no Lync Server 2013

 

_**Tópico modificado em:** 2016-05-19_

Esta seção detalha os requisitos de hardware e software do Diretor e os cenários de colocação com suporte para o Diretor.

## Requisitos de hardware por Diretor

A tabela a seguir lista os requisitos de hardware para o Diretor:

### Requisitos de hardware por Diretor

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente de hardware</th>
<th>Requisitos mínimos</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><ul>
<li><p>Processador de 64 bits, quad-core, 2.0 GHz ou superior</p></li>
<li><p>Processador 64 bits dual, dual-core, 2.0 GHz ou superior</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Memória</p></td>
<td><p>4 GB</p></td>
</tr>
<tr class="odd">
<td><p>Disco</p></td>
<td><ul>
<li><p>Disco rígido (HDD) de 10K de RPM</p></li>
<li><p>Drive de estado sólido (SSD) de alto desempenho com desempenho igual ou superior a 10K RPM HDD</p></li>
<li><p>Discos para arquivos de dados do banco de dados de 2 x RAID 10 (distribuídos e espelhados), 15.000 de RPM</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Rede</p></td>
<td><ul>
<li><p>Adaptadores de rede Dual 1 Gbps (recomendado)</p></li>
<li><p>Adaptador de rede de 1 Gbps único (suportado)</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Requisitos de software para o Diretor

A função Diretor pode ser implantada somente em servidores que executem o Lync Server 2013 Enterprise Edition.

Um dos seguintes sistemas operacionais de 64 bits é necessário para todos os Diretores:

  - O sistema operacional Windows Server 2008 R2 Standard com Service Pack 1

  - O sistema operacional Windows Server 2008 R2 Enterprise com Service Pack 1

  - O sistema operacional Windows Server 2008 R2 Datacenter com Service Pack 1

  - O sistema operacional Windows Server 2012 Standard

  - O sistema operacional Windows Server 2012 Datacenter

O Lync Server 2013 também exige a instalação dos seguintes programas e atualizações, detalhados no tópico [Suporte adicional e requisitos de servidor no Lync Server 2013](lync-server-2013-additional-server-support-and-requirements.md).

## Colocação com suporte

A função de servidor Diretor não pode ser colocada com outras funções de servidor no Lync Server 2013. Porém, se você não implantar um Diretor, os Servidores Front-End assumirão a função.

