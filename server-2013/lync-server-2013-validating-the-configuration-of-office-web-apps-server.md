---
title: Validando a Configuração do servidor do Office Web Apps no Lync Server 2013
TOCTitle: Validando a Configuração do servidor do Office Web Apps
ms:assetid: f6e8ecbf-305d-4a13-92d0-b61dbd82b0ea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205393(v=OCS.15)
ms:contentKeyID: 49308632
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Validando a Configuração do servidor do Office Web Apps no Lync Server 2013

 

_**Tópico modificado em:** 2014-04-22_

Após a adição do Office Web Apps Server à topologia, e após a publicação da topologia, você deverá ver dois novos eventos no log de eventos do Lync Server. Primeiro, um evento LS Data MCU (ID 41032) deve ser adicionado; esse evento relatará que o Office Web Apps Server foi descoberto:

**O WAC do servidor de webconferência foi descoberto, o conteúdo do PowerPoint está habilitado.**

Além disso, você deve ver outro evento LS Data MCU (ID 41032) que relata as URLs do Office Web Apps Server. Por exemplo, você deve ver algo semelhante a isso:

**Descoberta bem sucedida do WAC do Servidor de Webconferência.**

**Página interna do apresentador WAC: https://atl-officewebapps-001.litwareinc.com/m/Presenter.aspx?a=0\&embed=**

**Página interna do participante WAC: https://atl-officewebapps-001.litwareinc.com/m/ParticipantFrame.aspx?a=0\&embed=true&=**

**Página externa do apresentador WAC: https://atl-officewebapps-001.litwareinc.com/m/Presenter.aspx?a=0\&embed**

**Página externa do participante WAC: https://atl-officewebapps-001.litwareinc.com/m/ParticipantFrame.aspx?a=0\&embed=true&**

Se você ver um evento LS Data MCU com o ID 41033, significa que a descoberta do Office Web Apps Server falhou. Neste caso, o Microsoft Lync Server 2013 tentará quantas vezes for necessário descobrir o Office Web Apps Server recém configurado. Se o processo de descoberta falhar repetidamente, você deve remover o Office Web Apps Server do seu documento de topologia, publicar a topologia atualizada e tentar adicionar o Office Web Apps Server novamente à topologia depois que os problemas de conectividade tiverem sido resolvidos.

Se o Office Web Apps Server parecer estar configurado corretamente e tiver sido reconhecido pelo processo de descoberta, é possível verificar se o Office Web Apps Server está funcionando conforme o esperado compartilhando uma apresentação do PowerPoint entre um par de clientes do Microsoft Lync 2013. Se o Usuário A puder carregar e exibir a apresentação do PowerPoint e se o Usuário B puder participar da reunião e ver a apresentação, então o Office Web Apps Server está funcionando.

Mesmo que o Office Web Apps Server pareça estar configurado corretamente, é possível receber a mensagem de erro “Alguns recursos de compartilhamento não estão disponíveis devido a problemas de conectividade do servidor” ao tentar compartilhar uma apresentação do PowerPoint. Se você receber essa mensagem de erro, você deve reiniciar o servidor (ou servidores) de Front End associados ao novo Office Web Apps Server.

