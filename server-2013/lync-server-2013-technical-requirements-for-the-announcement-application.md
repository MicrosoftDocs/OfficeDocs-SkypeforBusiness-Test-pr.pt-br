---
title: 'Lync Server 2013: Requisitos técnicos para o aplicativo Comunicado'
TOCTitle: Requisitos técnicos para o aplicativo Comunicado
ms:assetid: fbd8c204-3765-4b22-a0c9-a781b5126366
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205413(v=OCS.15)
ms:contentKeyID: 49308697
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos técnicos para o aplicativo Comunicado no Lync Server 2013

 

_**Tópico modificado em:** 2013-11-07_

Esta seção descreve os seguintes requisitos técnicos para Aplicativo Comunicado:

  - Requisitos de hardware

  - Requisitos de software

  - Requisitos de porta

  - Requisitos do arquivo de áudio

## Requisitos de hardware

O Aplicativo Comunicado tem os mesmos requisitos de hardware de Servidores Front-End. Para detalhes sobre requisitos de hardware, consulte [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md) na documentação de Suportabilidade.

## Requisitos de software

O Aplicativo Comunicado tem os mesmos requisitos do sistema operacional e pré-requisitos de software como Servidores Front-End. Para detalhes sobre requisitos do software, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) na documentação de Suportabilidade.

Todos os servidores Servidores Front-End ou Edição Standard que executam o Aplicativo Comunicado devem ter Tempo de Execução do Windows Media Format instalado para servidores executando Windows Server 2008 R2 ou Microsoft Media Foundation para servidores executando Windows Server 2012 ou Windows Server 2012 R2. Para Windows Server 2008 R2, o Tempo de Execução do Windows Media Format é instalado como parte da Windows Desktop Experience. Tempo de Execução do Windows Media Format ou Microsoft Media Foundation são exigidos para arquivos de Windows Media Audio (.wma) que o Aplicativo Comunicado reproduz para comunicados e música.

## Requisitos de porta

O Aplicativo Comunicado usa as seguintes portas:

  - **Porta 5071**   Usada para solicitações de escuta de SIP

> [!NOTE]  
> Essa porta é a definição padrão, que você pode modificar usando o cmdlet <strong>Set-CsApplicationServer</strong>. Para detalhes sobre esse cmdlet, consulte a documentação de Shell de Gerenciamento do Lync Server.

## Requisitos do arquivo de áudio

O Aplicativo Comunicado suporta formatos de arquivo Wave (.wav) e Windows Media audio (.wma) para música e comunicados. Os requisitos para arquivo de áudio para Aplicativo Comunicado são os mesmos de Aplicativo Grupo de Resposta. Para detalhes, consulte [Requisitos técnicos do Grupo de Resposta no Lync Server 2013](lync-server-2013-technical-requirements-for-response-group.md).

