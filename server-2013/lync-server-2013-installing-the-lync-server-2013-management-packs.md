---
title: Instalando os pacotes de gerenciamento do Lync Server 2013
TOCTitle: Instalando os pacotes de gerenciamento do Lync Server 2013
ms:assetid: b800d4ab-fdc8-4c72-a76a-b78932779fe3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205202(v=OCS.15)
ms:contentKeyID: 49307902
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando os pacotes de gerenciamento do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Por si mesmo, o System Center Operations Manager tem a capacidade de monitorar somente uma pequena parte do sistema operacional Windows. No entanto, você pode estender os recursos do System Center Operations Manager instalando pacotes de gerenciamento, software que ditam quais itens o System Center Operations Manager pode monitorar, incluindo como esses itens devem ser monitorados e como os alertas devem ser ativados e relatados. O Microsoft Lync Server 2013 inclui dois pacotes de gerenciamento do System Center Operations Manager que fornecem os seguintes recursos:

  - O Pacote de gerenciamento de componente e usuário (Microsoft.LS.2013.Monitoring.ComponentAndUser.mp) rastreia os problemas do Lync Server registrados em logs de eventos, registrados por contadores de desempenho ou registrado nos registros de detalhes de chamada (CDR) ou os bancos de dados de QoE (Qualidade da Experiência). Para problemas críticos, é possível configurar o System Center Operations Manager para notificar os administradores imediatamente por e-mail, mensagem instantânea ou mensagens de SMS. SMS é a tecnologia usada para enviar mensagens de texto de um dispositivo móvel para outro.
    
    > [!NOTE]  
    > Para obter mais informações sobre como configurar a notificação do Operations Manager, consulte Configurando notificações na biblioteca do TechNet em <a href="http://go.microsoft.com/fwlink/?linkid=268785%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=268785&amp;clcid=0x416</a>.

  - O Pacote de monitoramento ativo (Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp) testa proativamente componentes-chave do Lync Server, como entrar no sistema, trocar mensagens instantâneas ou fazer chamadas para um telefone localizado na rede telefônica pública comutada (PSTN). Esses testes são realizados usando os cmdlets de transação sintéticos do Lync Server. Por exemplo, o cmdlet **Test-CsIM** é usado para simular uma conversa de mensagem instantânea entre um par de usuários de teste. Um alerta será gerado em caso de falha nessa conversa de mensagens simulada.

Os dois pacotes de gerenciamento incluídos com o Lync Server 2013 incluem um grande número de melhorias nos pacotes de gerenciamento usados com o Microsoft Lync Server 2010. Por exemplo, o Pacote de gerenciamento de componente do Lync Server 2013 não está limitado ao monitoramento do próprio Lync Server. Além do monitoramento de logs de eventos e contadores de desempenho para o Lync Server, o pacote de Gerenciamento de componentes também pode rastrear o desempenho de, bem como emitir alertas para itens importantes como:

  - **Serviços de Informações da Internet (IIS)**   Alertas serão emitidos se os Serviços de informações da Internet ficarem offline. Isso é importante porque os serviços Web do Lync Server dependem do IIS.

  - **Uso de processo**   Alertas serão emitidos se a capacidade dos recursos do sistema (como a memória disponível) ficar baixa. Esses alertas serão emitidos mesmo se o Lync Server não for responsável pelo alto uso do sistema.

  - **Eventos de falha do computador**   Alertas serão emitidos em caso de problemas de hardware ou software que ameacem a viabilidade de um servidor. Por exemplo, os administradores do Lync Server serão notificados se um servidor parecer prestes a sofrer uma falha de disco rígido.

Os novos pacotes de gerenciamento também dispõem de relatórios avançados. Os novos relatórios do Lync Server 2013 incluem:

  - **Relatório de disponibilidade de cenários extremidade a extremidade**   Este relatório detalha a disponibilidade/tempo de ativação para serviços-chave do Lync Server, como registro ou presença.

  - **Relatório de capacidade**   Usando informações do contador de desempenho, este relatório mostra tendência de componentes do sistema, como disponibilidade de memória e uso do processador.

  - **Relatório de componentes**   Este relatório lista os principais geradores de alerta agrupados por componentes do Lync Server.

Além desses relatórios pré-criados, os pacotes de gerenciamento para o Lync Server 2013 informam automaticamente sobre alertas de Confiabilidade de chamada (métricas medidas pela Registro de detalhes das chamadas) e estados de QoE (métricas medidas pela Qualidade da Experiência). Se o Registro de detalhes das chamadas estiver ativado, você pode analisar os alertas de Confiabilidade de chamada completando o seguinte procedimento no console do System Center Operations Manager:

  - Expanda **Monitoramento**, **Integridade do Microsoft Lync Server 2013**, **Confiabilidade de chamada e qualidade de mídia**, e clique em **Confiabilidade de chamada**.

Para exibir alertas de Qualidade da Experiência, conclua esse procedimento pelo console do System Center Operations Manager:

  - Expanda **Monitoramento**, **Integridade do Microsoft Lync Server 2013**, **Confiabilidade de chamada e qualidade de mídia**, e, em seguida, expanda **Qualidade de mídia**.

Os pacotes de gerenciamento do Lync Server 2013 usam descoberta de nível de máquina em vez do mecanismo de descoberta central usando no Microsoft Lync Server 2010. Isso significa que cada agente do System Center descobre a si mesmo e informa sua existência ao Servidor de Gerenciamento Central. O uso da descoberta de nível de máquina simplifica a administração da infraestrutura do System Center e também permite que versões diferentes dos pacotes de gerenciamento do Lync Server (por exemplo, os pacotes de gerenciamento do Lync Server 2010 e os pacotes de gerenciamento do Lync Server 2013) coexistam.

