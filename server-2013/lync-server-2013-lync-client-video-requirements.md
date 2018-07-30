---
title: 'Lync Server 2013: Requisitos de vídeo do cliente Lync'
TOCTitle: Requisitos de vídeo do cliente Lync
ms:assetid: 8f68f4c2-3194-487c-bd2f-fbe71ba8ad70
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688132(v=OCS.15)
ms:contentKeyID: 49886311
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de vídeo do cliente Lync para o Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Esta seção descreve o suporte a hardware de vídeo para as chamadas de vídeo do Lync 2013 e descreve como determinar a qualidade de vídeo esperada para várias configurações de computador, tablet e dispositivos móveis.

## Requisitos e Recursos de Vídeo para Windows Tablets e Desktops

O Lync 2013 introduz aceleração de hardware para codificação e decodificação de vídeo baseado no padrão H.264/MPEG-4 Part 10 Advanced Video Coding. Este recurso permite que computadores com velocidades baixas de clock de CPU codifiquem e decodifiquem vídeo de maior resolução. Os requisitos de hardware de vídeo variam, dependendo da configuração do computador e a resolução de vídeo desejada.

## Requisitos de hardware de vídeo


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Recurso</th>
<th>Requisito</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Decodificação H.264 acelerada por hardware usando DirectX Video Acceleration (DXVA)</p></td>
<td><ul><li><p>A placa de vídeo deve suportar DirectX 9.0 e deve expor o modo de decodificação DXVA2_ModeH264_VLD_NoFGT.</p></li><li><p>O driver mais recente da placa de vídeo deve estar instalado.</p></li></ul>
<div class="alert">
> [!NOTE]  
> Para obter detalhes sobre modos de decodificação, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=268530">http://go.microsoft.com/fwlink/p/?LinkId=268530</a>.
</div></td>
</tr>
<tr class="even">
<td><p>Codificação H.264 acelerado por hardware: Requisitos de chipset</p></td>
<td><p>As seguintes soluções de vídeo acelerado por hardware da Intel têm suporte:</p><ul><li><p>Chipsets de segunda e terceira geração Intel HD Graphics 2000, 2500, 3000 e 4000 (ou versões mais recentes) com codificadores de vídeo de hardware integrados. A instalação do driver Intel HD Graphics 15.28.9.2884 ou driver mais recente contendo os seguintes itens é necessária:</p><ul><li><p>Driver de display 9.17.10.2884 ou driver mais recente</p></li><li><p>HMFT (Hardware media foundation transform) versão 3.12.10.31 ou HMFT mais recente</p></li></ul></li></ul>
<p>As seguintes soluções de codificação de vídeo acelerada por hardware AMD são suportadas (requer Atualizações CU1 para Lync Server 2013):</p><ul><li><p>o Mecanismo de Codec de Vídeo AMD, que está disponível em diversos cartões gráficos distintos e nas unidades de processamento aceleradas integradas do Processador Acelerado AMD A-Series. O driver do Mecanismo de Codec de Vídeo AMD 9.12.0.0 ou superior deve ser instalado.</p></li></ul></td>
</tr>
<tr class="odd">
<td><p>Codificação H.264 acelerado por hardware: Requisitos de câmera</p></td>
<td><p>Câmera de vídeo USB com codificador de hardware H.264 integrado com conformidade com a especificação USB Video Class (UVC) versão 1.5.</p>
<div class="alert">
> [!NOTE]  
> O Lync 2013 suporta câmeras UVC 1.5 com Windows 8 ou Windows 8.1, que inclui suporte para UVC 1.5. Como o Windows 7 não inclui suporte para câmeras UVC 1.5, o Lync 2013 trata as câmeras UVC 1.5 como câmeras regulares sem suporte para codificação de hardware.
</div></td>
</tr>
<tr class="even">
<td><p>Decodificação H.264 acelerada por hardware usando DirectX Video Acceleration (DXVA)</p></td>
<td><ul><li><p>A placa de vídeo deve suportar DirectX 9.0 e deve expor o modo de decodificação DXVA2_ModeH264_VLD_NoFGT.</p></li><li><p>O driver mais recente da placa de vídeo deve estar instalado.</p></li></ul>
<div class="alert">
> [!NOTE]  
> Para obter detalhes sobre modos de decodificação, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=268530">http://go.microsoft.com/fwlink/p/?LinkId=268530</a>.
</div></td>
</tr>
<tr class="odd">
<td><p>Codificação H.264 acelerado por hardware: Requisitos de chipset</p></td>
<td><p>As seguintes soluções de vídeo acelerado por hardware da Intel têm suporte:</p><ul><li><p>Chipsets de segunda e terceira geração Intel HD Graphics 2000, 2500, 3000 e 4000 (ou versões mais recentes) com codificadores de vídeo de hardware integrados. A instalação do driver Intel HD Graphics 15.28.9.2884 ou driver mais recente contendo os seguintes itens é necessária:</p><ul><li><p>Driver de display 9.17.10.2884 ou driver mais recente</p></li><li><p>HMFT (Hardware media foundation transform) versão 3.12.10.31 ou HMFT mais recente</p></li></ul></li></ul>
<p>As seguintes soluções de codificação de vídeo acelerada por hardware AMD são suportadas (requer Atualizações CU1 para Lync Server 2013):</p><ul><li><p>o Mecanismo de Codec de Vídeo AMD, que está disponível em diversos cartões gráficos distintos e nas unidades de processamento aceleradas integradas do Processador Acelerado AMD A-Series. O driver do Mecanismo de Codec de Vídeo AMD 9.12.0.0 ou superior deve ser instalado.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Codificação H.264 acelerado por hardware: Requisitos de câmera</p></td>
<td><p>Câmera de vídeo USB com codificador de hardware H.264 integrado com conformidade com a especificação USB Video Class (UVC) versão 1.5.</p>
<div class="alert">
> [!NOTE]  
> O Lync 2013 suporta câmeras UVC 1.5 com Windows 8 ou Windows 8.1, que inclui suporte para UVC 1.5. Como o Windows 7 não inclui suporte para câmeras UVC 1.5, o Lync 2013 trata as câmeras UVC 1.5 como câmeras regulares sem suporte para codificação de hardware.
</div></td>
</tr>
</tbody>
</table>


## Determinação de capacidades de codificação e decodificação de vídeo H.264

Geralmente, há quatro fatores principais que determinam a capacidade de codificação e decodificação de uma configuração específica de computador:

  - Suporte para decodificação acelerada por hardware usando DXVA

  - Suporte para codificação acelerada por hardware

  - Número de núcleos físicos

  - Índice de Experiência do Windows (WEI)

A Ferramenta de Apuração do Sistema do Windows (WinSAT) determina o WEI. Ao executar a ferramenta WinSAT, ela gera um documento XML Formal.Assessment no computador no diretório %windir%\\Performance\\WinSAT\\DataStore. Esse arquivo XML contém as duas pontuações a seguir que são particularmente importantes para determinar as capacidades de codificação e decodificação:

  - O VideoEncodeScore indica a capacidade de codificação de vídeo com base em software de computador.

  - O valor GraphicsScore indica a capacidade de codificação acelerada por hardware do computador.

As três tabelas a seguir explicam a capacidade máxima de codificação e decodificação de diferentes tipos de PC, dependendo da aceleração de hardware que eles suportam. Para resoluções iguais ou maiores que 640x360, a taxa de quadros máxima suportada é de 30 quadros por segundo (fps). Para resoluções menores que 640x360, a taxa de quadros máxima suportada é de 15 fps.

### Computador sem DXVA e codificação acelerada por hardware

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Resolução do codificador compatível</th>
<th>Resolução do decodificador compatível</th>
<th>Requisito</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>424x240</p></td>
<td><p>424x240 (640x360 a 15fps para casos apenas de recepção)</p></td>
<td><p>1 núcleo e VideoEncodeScore = 4,0</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>640x360</p></td>
<td><p>2 núcleos e VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="odd">
<td><p>640x360</p></td>
<td><p>1280x720</p></td>
<td><p>2 núcleos e VideoEncodeScore ≥ 4,5</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 4,5</p></td>
</tr>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1280x720</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 7,3</p></td>
</tr>
<tr class="even">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 7,3</p></td>
</tr>
<tr class="odd">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>N/D</p></td>
</tr>
<tr class="even">
<td><p>424x240</p></td>
<td><p>424x240 (640x360 a 15fps para casos apenas de recepção)</p></td>
<td><p>1 núcleo e VideoEncodeScore = 4,0</p></td>
</tr>
<tr class="odd">
<td><p>640x360</p></td>
<td><p>640x360</p></td>
<td><p>2 núcleos e VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>1280x720</p></td>
<td><p>2 núcleos e VideoEncodeScore ≥ 4,5</p></td>
</tr>
<tr class="odd">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 4,5</p></td>
</tr>
<tr class="even">
<td><p>1280x720</p></td>
<td><p>1280x720</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 7,3</p></td>
</tr>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 7,3</p></td>
</tr>
<tr class="even">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>N/D</p></td>
</tr>
</tbody>
</table>


### Computador com DXVA, mas sem codificação acelerada por hardware

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Resolução do codificador compatível</th>
<th>Resolução do decodificador compatível</th>
<th>Requisito</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>424x240</p></td>
<td><p>1920x1080</p></td>
<td><p>1 núcleo e VideoEncodeScore ≥ 3.0</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>2 núcleos e VideoEncodeScore ≥ 4,5</p></td>
</tr>
<tr class="odd">
<td><p>960x540</p></td>
<td><p>1920x1080</p></td>
<td><p>2 núcleos e VideoEncodeScore ≥ 6,0</p></td>
</tr>
<tr class="even">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 6,7</p></td>
</tr>
<tr class="odd">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 8.2</p></td>
</tr>
<tr class="even">
<td><p>424x240</p></td>
<td><p>1920x1080</p></td>
<td><p>1 núcleo e VideoEncodeScore ≥ 3.0</p></td>
</tr>
<tr class="odd">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>2 núcleos e VideoEncodeScore ≥ 4,5</p></td>
</tr>
<tr class="even">
<td><p>960x540</p></td>
<td><p>1920x1080</p></td>
<td><p>2 núcleos e VideoEncodeScore ≥ 6,0</p></td>
</tr>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 6,7</p></td>
</tr>
<tr class="even">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>4 núcleos e VideoEncodeScore ≥ 8.2</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> A pontuação WinSAT no Windows 7 está limitada a um máximo de 7,9. Desta forma, a capacidade de codificação de um computador sem um codificador acelerado por hardware pode ser atingida somente no Windows 8 ou Windows 8.1, onde a pontuação WinSAT é 9,9.

### Computador com DXVA e com codificador acelerado por hardware Intel HD Graphics

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Resolução do codificador compatível</th>
<th>Resolução do decodificador compatível</th>
<th>Requisito</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>Toda a segunda e terceira geração Intel HD Graphics</p></td>
</tr>
<tr class="even">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>Segunda e terceira geração Intel HD Graphics e GraphicsScore = 5.0</p></td>
</tr>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>Toda a segunda e terceira geração Intel HD Graphics</p></td>
</tr>
<tr class="even">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>Segunda e terceira geração Intel HD Graphics e GraphicsScore = 5.0</p></td>
</tr>
</tbody>
</table>


## Recursos de Vídeo do Dispositivo Móvel

A tabela a seguir descreve os recursos máximos de vídeo para os dispositivos móveis compatíveis. Para obter mais informações sobre o suporte a dispositivos móveis, consulte [Planejamento para clientes móveis no Lync Server 2013](lync-server-2013-planning-for-mobile-clients.md).


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Recurso</th>
<th>Windows Phone</th>
<th>iPhone e iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Resolução máxima de codificação H.264</p></td>
<td><p>640x480</p></td>
<td><p>iPhone 4: 192x144</p>
<p>iPad e todos os outros modelos do iPhone compatíveis: 352x288</p></td>
<td><p>320x2401</p></td>
</tr>
<tr class="even">
<td><p>Resolução máxima de decodificação H.264</p></td>
<td><p>640x480</p></td>
<td><p>iPhone e iPad: 352x288</p></td>
<td><p>320x2401</p></td>
</tr>
<tr class="odd">
<td><p>Resolução máxima de codificação H.264</p></td>
<td><p>640x480</p></td>
<td><p>iPhone 4: 192x144</p>
<p>iPad e todos os outros modelos do iPhone compatíveis: 352x288</p></td>
<td><p>320x2401</p></td>
</tr>
<tr class="even">
<td><p>Resolução máxima de decodificação H.264</p></td>
<td><p>640x480</p></td>
<td><p>iPhone e iPad: 352x288</p></td>
<td><p>320x2401</p></td>
</tr>
</tbody>
</table>


1Para dispositivos Android com processador Qualcomm Snapdragon S3 ou S4 que utilizam qualquer chipset 8x60, há suporte para envio e recebimento na resolução 640x480.

