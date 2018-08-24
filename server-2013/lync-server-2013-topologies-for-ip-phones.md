---
title: Topologias de telefones IP
TOCTitle: Topologias de telefones IP
ms:assetid: 26ebffcf-43ff-4e70-847d-0fbc90e94e57
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425740(v=OCS.15)
ms:contentKeyID: 49306176
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Topologias de telefones IP

 

_**Tópico modificado em:** 2012-06-21_

Esta seção fornece uma visão geral do processo de conectividade e explica as diferenças entre como um telefone IP se conecta em uma rede interna e externa.

> [!NOTE]  
> O Lync Server oferece suporte para os seguintes telefones IP: o telefone de área comum Aastra 6721ip, o telefone de mesa Aastra 6725ip, o telefone HP 4110 IP (telefone de área comum), o telefone HP 4120 IP (telefone de mesa), o telefone de mesa Polycom CX600 IP, o telefone de mesa Polycom CX700 IP, o telefone de área comum Polycom CX500 IP e o telefone de conferência Polycom CX3000 IP. Destes telefones, todos menos o Polycom CX700 pode executar o Lync Phone Edition.

O diagrama a seguir descreve todos os componentes envolvidos na conectividade do dispositivo dentro do ambiente empresarial.

**Topologia Interna**

![Dispositivo na rede](images/Gg425740.3d88893e-df57-46e3-855a-a1d24589030a(OCS.15).jpg "Dispositivo na rede")

> [!NOTE]  
> A figura anterior é uma representação local, não visão geral física. Por exemplo, os Serviços de Domínio do Active Directory (AD DS) está raramente localizado na mesma máquina que qualquer componente do Lync Server. O repositório de usuários pode estar localizado no Servidor de Back-End ou nos Servidores de Arquivamento e Monitoramento. O Shell de Gerenciamento do Lync Server, servidor da Web e serviços de atualização fazem parte da função do Servidor de Front-End.

O diagrama a seguir fornece uma visão geral dos componentes envolvidos quando o dispositivo está localizado fora da rede corporativa.

**Topologia Externa**

![Dispositivos fora da rede](images/Gg425740.8ce6bb8e-b89c-4c4e-ac6d-41ac6c68f6f3(OCS.15).jpg "Dispositivos fora da rede")

> [!NOTE]  
> O serviço da Web de Atualização de Dispositivo oferece um site externo e interno, mas apenas o externo é mostrado aqui.<br />O local do Registrador e a URL do Web Service de atualização de dispositivos para a organização devem ser publicados no DNS se o acesso externo deve ser habilitado. Além disso, o Servidor de Borda deve implantado e configurado corretamente para permitir comunicações externas do dispositivo para o ambiente corporativo e vice-versa. Isto é omitido no diagrama anterior porque a implantação de Borda não é específica para conectividade do dispositivo.
