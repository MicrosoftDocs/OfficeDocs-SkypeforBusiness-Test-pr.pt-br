---
title: Plataformas de hardware de servidor do Lync Server 2013
TOCTitle: Plataformas de hardware de servidor
ms:assetid: c964c1c0-0153-472b-88ad-a38866e0df0c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398835(v=OCS.15)
ms:contentKeyID: 49308103
ms.date: 07/21/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Plataformas de hardware de servidor para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

As funções de servidor do Lync Server 2013 e os computadores que executam as ferramentas administrativas do Lync Server requerem hardware de 64 bits.

O hardware específico usado para a implantação do Lync Server 2013 pode variar, dependendo dos requisitos de tamanho e uso. Esta seção descreve o hardware recomendado. Embora sejam apenas recomendações, e não requisitos obrigatórios, o uso de hardware não compatível com essas recomendações pode gerar problemas, inclusive de desempenho.

## Plataforma de hardware recomendada

Para melhor desempenho, recomendamos executar o Lync Server em servidores com hardware que atenda aos requisitos mostrados na tabela a seguir. Se você usar um hardware inferior, poderá enfrentar problemas de funcionalidade ou mau desempenho. Observe que esses requisitos de hardware são superiores àqueles de versões anteriores do Lync Server, principalmente porque no Lync Server 2013, todos os Servidores Front-End executam o SQL Server.

> [!NOTE]  
> O agrupamento NIC tem suporte e deve ser transparente para o Lync Server. Para obter detalhes, veja o artigo <a href="https://go.microsoft.com/fwlink/p/?linkid=389910">Communications Server or Lync Server and network adapter teaming (Communications Server ou Lync Server e agrupamento de adaptador de rede)</a>.

### Hardware recomendado para Servidores Front-End, Servidores Back-End, Servidores Standard Edition, Servidores de Chat Persistente, Repositório de Chat Persistente e Repositório de Conformidade de Chat Persistente (Funções de Servidores Back-End para Servidor de Chat Persistente)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente de hardware</th>
<th>Recomendado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>Processador duplo de 64 bits, seis núcleos, de 2,26 GHz ou superior.</p>
<p>Não há suporte para processadores Intel Itanium para funções de servidor do Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>Memória</p></td>
<td><p>32 GB</p></td>
</tr>
<tr class="odd">
<td><p>Disco</p></td>
<td><ul><li><p>Oito ou mais unidades de disco rígido de 10.000 RPM com pelo menos 72 GB de espaço livre em disco.</p>
<p>Dois discos devem ser usar RAID 1, e seis discos devem usar RAID 10.</p>
<p>- OU -</p></li><li><p>SSDs (unidades de estado sólido) com desempenho semelhante a oito unidades de disco mecânico de 10.000 RPM.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Rede</p></td>
<td><ul><li><p>1 adaptador de rede de porta dupla, 1 Gbps ou superior (recomendamos 2 Gbps, o que requer agrupamento com um único endereço MAC e um único endereço IP).</p>
<div class="alert">
> [!NOTE]  
> Não há suporte para configurações duais nem multihomed em Servidores Front-End, Servidores Back-End, Servidores Standard Edition nem Servidores de Chat Persistente.<br />Conexões ILO/DRAC/etc. não expostas ao sistema operacional e usadas para monitorar e gerenciar o hardware de servidor não constituem um servidor multihomed e, por isso, não têm suporte.
</div></li></ul></td>
</tr>
</tbody>
</table>


### Hardware recomendado para Servidores de Borda, Servidores de Mediação Autônomos e Directors

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente de hardware</th>
<th>Recomendado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><ul><li><p>Processador duplo de 64 bits, núcleo quádruplo, de 2,0 GHz ou superior.</p>
<p>- OU -</p></li><li><p>Processador de 4 vias de 64 bits, núcleo duplo, de 2,0 GHz ou superior.</p></li></ul>
<p>Não há suporte para processadores Intel Itanium para funções de servidor do Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>Memória</p></td>
<td><p>16 GB</p></td>
</tr>
<tr class="odd">
<td><p>Disco</p></td>
<td><ul><li><p>Quatro ou mais unidades de disco rígido de 10.000 RPM com pelo menos 72 GB de espaço livre em disco.</p>
<p>Os discos devem estar em uma configuração 2x RAID 1.</p>
<p>- OU -</p></li><li><p>SSDs (unidades de estado sólido) com desempenho semelhante a quatro unidades de disco mecânico de 10.000 RPM.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Rede</p></td>
<td><ul><li><p>1 adaptador de rede de porta dupla, 1 Gbps ou superior (recomenda-se usar 2 Gbps, o que requer agrupamento com um único endereço MAC e um único endereço IP). Duas interfaces de rede são necessárias em Servidores de Borda, com suporte em Servidor de Mediação autônomos.</p></li></ul>
<div class="alert">
> [!NOTE]  
> Não há suporte para configurações duplas nem multihomed para Diretores.<br />Conexões ILO/DRAC/etc. não expostas ao sistema operacional e usadas para monitorar e gerenciar o hardware de servidor não constituem um servidor multihomed e, por isso, não têm suporte.
</div>
<p>Servidores de Borda requerem duas interfaces de rede que sejam adaptadores de rede de porta dupla, 1 Gbps ou superior (ou dois adaptadores de rede emparelhados, para um total de quatro, cada par sendo agrupado com um único endereço MAC e um único endereço IP, para um total de dois pares).</p>
<p>Instalação de adaptadores de rede adicionais para permitir que a configuração de um endereço IP PSTN específico tenha suporte em Servidor de Mediação autônomos.</p></td>
</tr>
</tbody>
</table>

