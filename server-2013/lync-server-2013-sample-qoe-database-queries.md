---
title: 'Lync Server 2013: Exemplo de consultas ao banco de dados de QoE'
TOCTitle: Exemplo de consultas ao banco de dados de QoE
ms:assetid: 04e6bdd3-bbd1-47ca-8114-94a3db6beeeb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398100(v=OCS.15)
ms:contentKeyID: 49305722
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exemplo de consultas ao banco de dados de QoE no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-17_

Esta seção contém exemplos de consultas do banco de dados da Qualidade da Experiência (QoE).

Use o exemplo a seguir para obter a média de tremulação e perda de pacote para todos os fluxos de áudio.

    select avg(cast(JitterInterArrival as bigint)) as JitterAvg, avg(PacketLossRate) as PacketLossRateAvg from AudioStream

Use o exemplo a seguir para descobrir o número total de conferências que usaram o Console de Reunião.

    select avg(ConversationalMOS)
    from SessionView s
    inner join MediaLineView m
    on s.ConferenceDateTime = m.ConferenceDateTime
       and s.SessionSeq = m.SessionSeq
       and m.MediaLineLabel = 0 -- audio media line
       and s.CallerUserAgentType = 4 -- Lync
       and s.CalleeUserAgentType = 4 -- Lync

Use o exemplo a seguir para obter ConversstionalMOS, SendingMOS e ListendingMOS por dispositivo de captura.

    select t.DeviceName as Device, count(*) as SampleNum, avg(ConversationalMOS) as ConversationalMOS, avg(SendListenMOS) SendingMOS, avg(RecvListenMOS) as ListendingMOS
    from
    (
       select m.CallerCaptureDev as DeviceName, m.ConferenceDateTime, m.SessionSeq, a.StreamID, m.ConversationalMOS,a.SendListenMOS, a.RecvListenMOS
       from MediaLineView m
       inner join AudioStream a
       on m.ConferenceDateTime = a.ConferenceDateTime
          and m.SessionSeq = a.SessionSeq
          and m.MediaLineLabel = 0
    
       union
    
       select m.CalleeCaptureDev as DeviceName, m.ConferenceDateTime, m.SessionSeq, a.StreamID, m.ConversationalMOS,a.SendListenMOS, a.RecvListenMOS
       from MediaLineView m
       inner join AudioStream a
       on m.ConferenceDateTime = a.ConferenceDateTime
          and m.SessionSeq = a.SessionSeq
          and m.MediaLineLabel = 0
    
    )as t
    group by t.DeviceName
    order by SampleNum desc

