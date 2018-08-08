---
title: "Subst. XmlAdapter p. Adap. Conform. do Serv. Chat Persis. Person. no Lync Server 2013"
TOCTitle: "Subst. XmlAdapter p. Adap. Conform. do Serv. Chat Persis. Person. no Lync Server 2013"
ms:assetid: 2cb70db2-663f-40a6-abcf-89ea7d4a8b65
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ680106(v=OCS.15)
ms:contentKeyID: 49886153
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Substituindo o XmlAdapter por um Adaptador de Conformidade do Servidor do Chat Persistente Personalizado no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

É possível gravar um adaptador personalizado ao invés de usar o XmlAdapter instalado com o Servidor de Chat Persistente. Para realizar isso, você deve oferecer um assembly .NET Framework que contém uma classe pública que implementa a interface do **IComplianceAdapter**. Você deve colocar este assembly na pasta de instalação do Servidor de Chat Persistente de cada servidor em seu Pool de Servidor de Chat Persistente. Qualquer um dos servidores de Conformidade podem oferecer dados de conformidade para seu adaptador, mas os servidores de conformidade não oferecerão dados de conformidade duplicados para várias instâncias do seu adaptador.

## Implementando a interface do IComplianceAdapter

A interface é definida no assembly Compliance.dll no namespace `Microsoft.Rtc.Internal.Chat.Server.Compliance`. A interface define dois métodos que seu adaptador personalizado deve implementar.

    void SetConfig(AdapterConfig config)

O servidor de Conformidade do Chat Persistente irá chamar este método quando o adaptador carregar pela primeira vez. O `AdapterConfig` contém a configuração de conformidade do Chat Persistente relevante para o adaptador de conformidade.

    void Translate(ConversationCollection conversations)

O servidor de Conformidade do Chat Persistente chama este método em intervalos periódicos enquanto não há novos dados para traduzir. Este intervalo de tempo é igual ao `RunInterval` conforme definido na configuração de Conformidade do Chat Persistente.

O `ConversationCollection` contém a informação de conversação coletada da última vez que este método foi chamado.

