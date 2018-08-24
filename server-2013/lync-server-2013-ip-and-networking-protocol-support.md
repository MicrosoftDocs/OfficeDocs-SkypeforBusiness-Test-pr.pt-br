---
title: 'Lync Server 2013: Suporte a protocolo IP e de rede'
TOCTitle: Suporte a protocolo IP e de rede
ms:assetid: b0cffb10-3478-445c-89c7-8cb8b5027424
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412848(v=OCS.15)
ms:contentKeyID: 49307814
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a protocolo IP e de rede no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 oferece suporte aos seguintes protocolos IP e de rede:

  - **Protocolos IP.**   O Lync Server 2013 oferece suporte para a versão IP 4 (IPv4) ou 6 (IPv6) da rede do servidor.
    
    > [!NOTE]  
    > O Lync Server 2013 pode funcionar em uma rede com pilha IP dupla habilitada.

  - **Protocolos de transporte SIP.**   Normalmente, o SIP pode usar pelo menos três tipos de transporte: o protocolo UDP (User Datagram Protocol), o protocolo TCP (Transmission Control Protocol) e o protocolo TLS (Transport Layer Security). Na configuração de transporte SIP padrão, o TLS ignora o TCP. O TLS é usado na rede do Lync Server 2013. Na borda da rede, o Lync Server 2013 pode interoperar sobre o TCP. O Lync Server 2013 não oferece suporte a UDP para transporte SIP porque não atende aos padrões mínimos de segurança, confiabilidade e escalabilidade de comunicações empresarial. Para obter mais detalhes, consulte o artigo do blog NextHop, "To UDP, or not to UDP, that is the question," em [http://go.microsoft.com/fwlink/p/?linkId=185369](http://go.microsoft.com/fwlink/p/?linkid=185369).
    
    > [!NOTE]  
    > O conteúdo de cada blog e sua URL estão sujeitos a alterações sem aviso prévio.
