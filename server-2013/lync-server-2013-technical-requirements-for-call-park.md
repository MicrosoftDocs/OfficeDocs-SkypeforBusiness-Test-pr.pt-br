---
title: 'Lync Server 2013: Requisitos técnicos para Estacionamento de Chamadas'
TOCTitle: Requisitos técnicos para Estacionamento de Chamadas
ms:assetid: 38bcf302-2b72-4492-9266-f6dc31b566e1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204818(v=OCS.15)
ms:contentKeyID: 49306419
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos técnicos para Estacionamento de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Esta seção descreve os seguintes requisitos técnicos do Estacionamento de Chamada:

  - Requisitos de hardware

  - Requisitos de software

  - Requisitos de porta

  - Requisitos do arquivo de áudio

## Requisitos de hardware

O Aplicativo de Estacionamento de Chamada tem os mesmos requisitos de hardware de Servidores Front-End. Para detalhes sobre requisitos de hardware, consulte [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md) na documentação de Suportabilidade.

## Requisitos de software

O Aplicativo de Estacionamento de Chamada tem os mesmos requisitos do sistema operacional e pré-requisitos de software como Servidores Front-End. Para detalhes sobre requisitos do software, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) na documentação de Suportabilidade.

Todos os Servidores Front-End e servidores Standard Edition em que o Aplicativo de Estacionamento de Chamada está implantado devem ter o Tempo de execução do Windows Media Format instalado para os servidores que executam o Windows Server 2008 R2 ou o Microsoft Media Foundation para servidores que executam o Windows Server 2012 ou Windows Server 2012 R2. Para o Windows Server 2008 R2, o Tempo de execução do Windows Media Format é instalado como parte da Experiência de Desktop do Windows. O Tempo de execução do Windows Media Format ou o Microsoft Media Foundation são exigidos para arquivos .wma (Windows Media Audio) que o Estacionamento de Chamada toca para músicas em espera.

## Requisitos de porta

O Aplicativo de Estacionamento de Chamada usa as seguintes portas:

  - **Porta 5075**   Usada para solicitações de escuta de SIP.

> [!NOTE]  
> Esta porta é uma configuração padrão, que pode ser alterado usando o cmdlet <strong>Set-CsApplicationServer</strong>. Para obter detalhes sobre esse cmdlet, consulte a documentação do Shell de Gerenciamento do Lync Server.

## Requisitos do arquivo de áudio

O Aplicativo de Estacionamento de Chamada dá suporte a arquivos .wma (Windows Media Audio) de músicas em espera. É possível usar o Microsoft Expression Encoder 4 para personalizar arquivos de música em espera. Para baixar o Expression Encoder 4, consulte "Expression Encoder 4" em [http://go.microsoft.com/fwlink/p/?linkId=202843](http://go.microsoft.com/fwlink/p/?linkid=202843). Use a ferramenta parra converter o arquivo para o formato .wma. O formato recomendado para arquivos de música em espera do Estacionamento de Chamada é o Media Audio 9, 44 kHz, 16 bits, mono, CBR, 32 kbps.

> [!NOTE]  
> O arquivo convertido é reproduzido no telefone apenas em 16 kHz, mesmo que tenha sido gravado em 44 kHz.
