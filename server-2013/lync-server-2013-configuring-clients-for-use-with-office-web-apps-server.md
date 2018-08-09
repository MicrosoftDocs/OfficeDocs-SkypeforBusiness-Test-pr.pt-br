---
title: "Config. Clientes do Lync Server 2013 p/ Uso com o Servidor Office Web Apps"
TOCTitle: Configurando Clientes para Uso com o Servidor Office Web Apps
ms:assetid: e5eaead7-0b32-42fb-97eb-ca203af59a9d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205339(v=OCS.15)
ms:contentKeyID: 49308426
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Clientes do Lync Server 2013 para Uso com o Servidor Office Web Apps

 

_**Tópico modificado em:** 2013-02-25_

Caso queira que os usuários experimentem todos os recursos do servidor do Office Web App, então você deve atualizar estes usuários ao Microsoft Lync 2013; apenas os usuários de Lync 2013 serão capazes de fazer coisas como rolar por slides do PowerPoint independentemente da apresentação PowerPoint (isto é, esses usuários podem visualizar qualquer slide na apresentação a qualquer momento, sem interferir de qualquer maneira com a apresentação no momento). Usuários que não estão usando o Lync 2013 ainda serão capazes de ingressar em conferências online e visualizar a apresentação de PowerPoint; no entanto, eles não serão capazes de rolar pelos slides independentemente, nem serão capazes de ver transições de slide ou vídeos integrados.

Observe que estes recursos sempre estarão disponíveis para usuários do Lync 2013; isso acontece mesmo que o apresentador do PowerPoint esteja executando o Microsoft Lync 2010. Caso uma apresentação de PowerPoint esteja sendo hospedada por um usuário executando o Lync 2010, o Lync Server 2013 será coordenado com o servidor do Office Web Apps para assegurar que os usuários do Lync 2013 exibirão a versão do servidor do Office Web Apps da apresentação. O servidor do Office Web Apps não oferece serviços do PowerPoint para usuários executando clientes que não sejam o Lync 2013. Em vez disso, estes usuários se conectam ao serviço de servidor de Conferência e visualizam apresentações do PowerPoint da mesma maneira que faziam no Microsoft Lync Server 2010. Isso também significa que estes usuários só terão acesso aos recursos mais limitados oferecidos pelo Lync Server 2010.

Embora não seja necessária configuração de cliente para o servidor do Office Web Apps (fora a atualização dos usuários ao Lync 2013), é recomendável que os participantes da conferência sejam atualizados ao Internet Explorer 9. Embora as conferências possam ser acessadas usando o Internet Explorer 8, existem algumas limitações ao usar esse navegador. Por exemplo, usuários do Internet Explorer 8 não serão capazes de redimensionar a tela do PowerPoint a um tamanho personalizado; ao invés disso, eles estarão limitados a usar um dos três tamanhos de tela predefinidos. Do mesmo modo, usuários do Internet Explorer 8 não serão capazes de reproduzir arquivos de mídia.

