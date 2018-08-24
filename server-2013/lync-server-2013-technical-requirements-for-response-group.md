---
title: 'Lync Server 2013: Requisitos técnicos do Grupo de Resposta'
TOCTitle: Requisitos técnicos do Grupo de Resposta
ms:assetid: 477488bd-124f-437b-9327-732a0d7271ca
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204863(v=OCS.15)
ms:contentKeyID: 49306587
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos técnicos do Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Esta seção descreve os seguintes requisitos técnicos para Aplicativo Grupo de Resposta:

  - Requisitos de hardware

  - Requisitos de software

  - Requisitos de porta

  - Requisitos do arquivo de áudio

  - Requisitos de ferramenta de configuração do Grupo de Resposta

## Requisitos de hardware

O Aplicativo Grupo de Resposta tem os mesmos requisitos de hardware de Servidores Front-End. Para detalhes sobre requisitos de hardware, consulte [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md) na documentação de Suportabilidade.

## Requisitos de software

O Aplicativo Grupo de Resposta tem os mesmos requisitos do sistema operacional e pré-requisitos de software como Servidores Front-End. Para detalhes sobre requisitos do software, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) na documentação de Suportabilidade.

Se você utiliza arquivos Windows Media Audio (.wma) para músicas e anúncios Grupo de Resposta, todos os Servidores Front-End ou servidores Standard Edition que executam Aplicativo Grupo de Resposta deverão ter o Windows Media Format Runtime instalado para servidores que executam Windows Server 2008 R2 ou Microsoft Media Foundation para servidores que executam Windows Server 2012 ou Windows Server 2012 R2. Para Windows Server 2008 R2, o Windows Media Format Runtime está instalado como parte da Experiência de Desktop do Windows.

Para mais detalhes sobre requisitos de áudio, consulte "Requisitos de arquivo de áudio" mais adiante nesta seção.

## Requisitos de porta

O Aplicativo Grupo de Resposta utiliza as seguintes portas:

  - **Porta 5071**   Usada para solicitações de escuta de SIP

  - **Porta 8404**   Utilizado para comunicações entre servidores
    
    > [!NOTE]  
    > Esta porta é utilizada pra o serviço de Correspondência e é obrigatório quando o Aplicativo Grupo de Resposta é implantado em um pool que possua mais de um Servidor Front-End.

> [!NOTE]  
> Essas portas são configurações padrão que você pode alterar utilizando o cmdlet <strong>Set-CsApplicationServer</strong>. Para detalhes sobre este cmdlet, consulte a documentação do Shell de Gerenciamento do Lync Server.

## Requisitos do arquivo de áudio

O Aplicativo Grupo de Resposta suporta formato de arquivo wave (.wav) e Windows Media audio (.wma) para mensagens do Grupo de resposta, música de espera ou perguntas de resposta resposta de voz interativa (IVR).

O formato de arquivo de áudio Windows Media requer que o Windows Media Format Runtime esteja instalado no Servidores Front-End executando o Windows Server 2008 R2 e Windows Server 2008. Para mais detalhes, consulte "Requisitos de software", anteriormente nesta seção.

## Formatos de arquivo wave suportados

Os arquivos wave devem atender os seguintes requisitos:

  - Arquivo 8 bits ou 16 bits

  - Formato de Modulação de código de pulso linear (LPCM), A-Law ou mu-Law

  - Mono ou estéreo

  - 4 MB ou menos

Para melhor desempenho de arquivos wave, um arquivo Wave 16 kHz, mono e de 16 bits é recomendado.

## Formatos de arquivo de áudio Windows Media

Se você utilizar um arquivo de áudio Windows Media, considere utilizar taxas de bit baixos e verifique o desempenho do sistema sob carga.

Você pode utilizar o Microsoft Expression Encoder 4 para converter um arquivo para o formato Windows Media Audio. Para baixar o Expression Encoder 4, consulte [http://go.microsoft.com/fwlink/?linkid=202843\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=202843%26clcid=0x416).

## Requisitos de ferramenta de configuração de Grupo de resposta

O Ferramenta de Configuração de Grupo de Resposta suporta as combinações de sistemas operacionais e navegadores da web descritos na tabela a seguir.

> [!NOTE]  
> Versões 32 bits ou 64 bits do sistema operacional são suportadas. Apenas versões 32 bits do Internet Explorer são suportadas.

### Sistemas operacionais e navegadores da web suportados

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Sistema operacional</th>
<th>Navegador da Web</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Vista com Service Pack (SP) 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (modo nativo)</p>
<p>Internet Explorer 9 (modo nativo)</p></td>
</tr>
<tr class="even">
<td><p>Windows 7</p>
<p>Windows 7 com Service Pack 1</p></td>
<td><p>Internet Explorer 8 (modo nativo)</p>
<p>Internet Explorer 9 (modo nativo)</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 com Service Pack 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (modo nativo)</p>
<p>Internet Explorer 9 (modo nativo)</p></td>
</tr>
<tr class="even">
<td><p></p>
<p></p>
<p></p>
<p>Windows Server 2008 R2</p>
<p>Windows Server 2008 R2 com Service Pack 1</p></td>
<td><p>Internet Explorer 8 (modo nativo)</p>
<p>Internet Explorer 9 (modo nativo)</p></td>
</tr>
</tbody>
</table>


## Console de agente do Grupo de resposta

O console de agente suporta as combinações de sistemas operacionais e navegadores da web descritas na tabela a seguir.

> [!NOTE]  
> Versões 32 bits ou 64 bits do sistema operacional são suportadas. Apenas versões 32 bits do Internet Explorer são suportadas.

### Sistemas operacionais e navegadores da web suportados

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Sistema operacional</th>
<th>Navegador da Web</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Vista com Service Pack (SP) 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (modo nativo)</p>
<p>Internet Explorer 9 (modo nativo)</p></td>
</tr>
<tr class="even">
<td><p>Windows 7</p>
<p>Windows 7 com Service Pack 1</p></td>
<td><p>Internet Explorer 8 (modo nativo)</p>
<p>Internet Explorer 9 (modo nativo)</p>
<p>Firefox 10.0</p>
<p>Chrome 18.0</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 com Service Pack 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (modo nativo)</p>
<p>Internet Explorer 9 (modo nativo)</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 R2</p>
<p>Windows Server 2008 R2 com Service Pack 1</p></td>
<td><p>Internet Explorer 8 (modo nativo)</p>
<p>Internet Explorer 9 (modo nativo)</p>
<p>Firefox 10.0</p>
<p>Chrome 18.0</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td></td>
</tr>
</tbody>
</table>

