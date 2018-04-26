---
title: Servidores de Borda Áudio/Vídeo (A/V) no Lync Server 2013
TOCTitle: Servidores de Borda Áudio/Vídeo (A/V) no Lync Server 2013
ms:assetid: b0cc538b-77eb-47fb-be82-5ab0631c6219
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721852(v=OCS.15)
ms:contentKeyID: 49886362
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Servidores de Borda Áudio/Vídeo (A/V) no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

O Serviço de borda A/V fornece uma maneira para que seus usuários internos (usuários conectados à sua rede organizacional) compartilhem áudio e vídeo com usuários externos (usuários que não estão conectados à rede organizacional). Além de áudio e vídeo, o serviço de borda A/V fornece suporte para o compartilhamento de área de trabalho e a transferência de arquivos.

O serviço de borda A/V é gerenciado principalmente usando a configuração de borda A/V; essas configurações permitem que você gerencie a quantidade máxima de largura de banda que será alocada por porta e usuário, bem como para especificar por quanto tempo um token de autenticação pode ser usado antes de precisar renová-lo. As definições de configuração de borda A/V podem ser aplicadas a sites ou servidores de borda A/V individuais. Ao determinar qual conjunto de configurações terá prioridade, use o seguinte guia:

  - As definições configuradas no escopo de serviço (isto é, em um servidor individual ) têm prioridade sobre tudo.

  - As definições configuradas no escopo do site têm prioridade sobre as definições configuradas no escopo global. No entanto, as definições de escopo de serviço também substituem as configurações de escopo do site.

  - As configurações no escopo global serão usadas somente se não há definições de serviço configuradas no servidor individual e se não há configurações de site para o site onde o servidor está localizado.

O serviço de borda A/V pode ser gerenciado somente usando o Lync Server PowerShell e os cmdlets CsAVEdgeConfiguration.

## Nesta seção

  - [Retornar Informações de Configuração do Servidor de Borda A/V](lync-server-2013-return-a-v-edge-server-configuration-information.md)

  - [Criar ou Modificar um Conjunto de Configurações do Servidor de Borda A/V](lync-server-2013-create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)

  - [Excluir um Conjunto Existente de Configurações do Servidor de Borda A/V](lync-server-2013-delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)

