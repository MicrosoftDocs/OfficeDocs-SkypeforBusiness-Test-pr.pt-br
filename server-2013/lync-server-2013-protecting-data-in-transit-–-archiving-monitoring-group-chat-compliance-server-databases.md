---
title: "Proteg. dados em tr. – b. de dados do serv.de conform. de arq., monit., chat em grupo"
TOCTitle: Protegendo dados em trânsito – bancos de dados do servidor de conformidade de arquivamento, monitoramento, chat em grupo no Lync Server 2013
ms:assetid: ea219705-1015-43a7-890b-e7e67b451e7c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn518336(v=OCS.15)
ms:contentKeyID: 60505941
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Protegendo dados em trânsito – bancos de dados do servidor de conformidade de arquivamento, monitoramento, chat em grupo no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Monitoring Server e o Servidor de Arquivamento do Microsoft Lync Server 2013 usam o serviço de enfileiramento de mensagens (também conhecido como MSMQ) para coletar e mover mensagens de dados com confiança do ponto de coleção até os servidores de repositório. O serviço de conformidade coleta dados em conjunto com o Servidor de Chat de Grupo, que também usa o serviço de enfileiramento de mensagens.

No Lync Server 2013, não há proteção interna para dados durante a transmissão; no entanto, se houver algum requisito de proteção desse tráfego, o serviço de enfileiramento de mensagens poderá fornecer criptografia em um nível de mensagem na fila de envio de mensagens. Isso é feito por meio de certificados gerenciados pelo Serviços de Domínio Active Directory. Para obter informações detalhadas, consulte o Apêndice D: Enfileiramento de mensagens e comunicação da Internet no Windows Server 2008 em [http://go.microsoft.com/fwlink/p/?LinkId=145238](http://go.microsoft.com/fwlink/p/?linkid=145238) or Appendix I: Message Queuing and Internet Communication in Windows Server 2008 R2 at [http://go.microsoft.com/fwlink/p/?LinkId=211883](http://go.microsoft.com/fwlink/p/?linkid=211883) para Windows Server 2008 R2.

