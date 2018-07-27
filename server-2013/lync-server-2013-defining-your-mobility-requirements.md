---
title: 'Lync Server 2013: Definindo seus requisitos de mobilidade'
TOCTitle: Definindo seus requisitos de mobilidade
ms:assetid: b7608335-cdeb-4aae-8e4b-d80c55f0d62b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690039(v=OCS.15)
ms:contentKeyID: 49307892
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo seus requisitos de mobilidade para Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Durante a fase de planejamento para o recurso de mobilidade do Lync Server 2013, quando você utiliza os clientes móveis Lync 2010 Mobile e Lync 2013, precisa tomar algumas decisões que determinam as etapas de sua implantação.

A seguir estão as decisões que você precisa considerar:

  - **Você deseja usar a descoberta automática para clientes móveis do Lync?**
    
    Se você quiser oferecer suporte para a descoberta automática, será necessário criar novos registros DNS (Sistema de Nomes de Domínio) internos e externos, adicionar nomes de entidade alternativos aos certificados no Servidores Front-End, no Diretores e no proxy reverso e modificar as regras de publicação existentes no proxy reverso. Para obter detalhes, consulte [Requisitos técnicos para mobilidade no Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md). Com a descoberta automática, os usuários podem localizar automaticamente os serviços Web do Lync Server 2013 a partir de qualquer lugar de dentro e fora da rede corporativa, sem inserir as URLs nas configurações de seus dispositivos móveis.
    
    Se você usar as configurações manuais em vez da descoberta automática, os usuários móveis precisarão inserir manualmente as URLs a seguir em seus dispositivos móveis:
    
      - https://\<ExtPoolFQDN\>/Autodiscover/autodiscoverservice.svc/Root para acesso externo
    
      - https://\<IntPoolFQDN\>/AutoDiscover/autodiscoverservice.svc/Root para acesso interno
    
    Recomendamos o uso da descoberta automática. O uso principal das configurações manuais é para solução de problemas.

  - **Se você decidir oferecer suporte à descoberta automática, estará disposto a atualizar os certificados no proxy reverso com nomes de entidade alternativos para cada domínio SIP?**
    
    Se você tiver muitos domínios SIP, a atualização de certificados públicos no proxy reverso pode se tornar muito cara. Se esse for o caso, você poderá escolher implementar a descoberta automática de uma maneira que a solicitação inicial do Serviço de descoberta automática use HTTP na porta 80, em vez de usar HTTPS na porta 443. Porém, essa não é a abordagem recomendada. Se você selecionar essa alternativa, não será necessário atualizar os certificados no proxy reverso, mas será necessário criar uma regra de publicação na web para HTTP na porta 80. Para obter mais detalhes, consulte [Requisitos técnicos para mobilidade no Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md).

  - **Você deseja oferecer suporte aos clientes móveis do Lync de dentro e fora da rede corporativa, ou deseja oferecer suporte somente dentro da rede corporativa?**
    
    Se você quiser oferecer suporte aos clientes móveis de dentro e fora de sua rede, os dispositivos móveis poderão acessar os recursos de mobilidade a partir de qualquer local. A configuração padrão é oferecer suporte aos clientes de dentro e fora da rede corporativa.
    
    Embora a configuração padrão permita que o tráfego do cliente móvel passe pelo site externo, é possível restringir o tráfego do cliente móvel à rede corporativa interna. Quando você restringe o tráfego para a rede interna, os usuários podem usar os aplicativos móveis do Lync em seus dispositivos móveis somente quando estão dentro da rede.
    
    Para implantações com suporte a mobilidade com uso do serviço de mobilidade Mcx e do Lync 2010 Mobile, você executa o cmdlet **Set-CsMcxConfiguration**. Para definir a mobilidade como apenas para uso interno, você precisaria utilizar um comando similar a esse a seguir:
    
        Set-CsMcxConfiguration -Identity site:Redmond -ExposedWebURL Internal
    
    > [!NOTE]  
    > Não há requisitos adicionais de configurações para UCWA. O UCWA não tem uma configuração exclusivamente interna que seja equivalente.    
    > [!IMPORTANT]  
    > Se estiver usando um Lync Server 2013Servidor Front-End ou Pools de Front-Ends e <strong>você não tem</strong> qualquer Lync Server 2010Servidores Front-End ou Pools de Front-Ends, <strong>não há requisitos para persistência com base em cookies</strong>. Se precisar reter qualquer Lync Server 2010Servidores Front-End ou Pools de Front-Ends, as mesmas regras se aplicam assim como na persistência com base em cookie do Lync Server 2010.

  - **Você deseja oferecer suporte às notificações por push para dispositivos Apple iOS e Windows Phones?**
    
    Se você oferecer suporte às notificações por push, os dispositivos Apple iOS suportados e os Windows Phones receberão uma notificação sobre os eventos que ocorrem quando o aplicativo móvel está inativo. É necessário configurar seu Servidor de Borda para ter um relacionamento federado com o Serviço de notificação por push do Lync Server baseado em nuvem, que está localizado no datacenter do Lync Online, e executar um cmdlet para habilitar as notificações por push.
    
    Se você quiser oferecer suporte às notificações por push sobre sua rede Wi-Fi, além de suportar as notificações por push pelas redes 3G ou redes de dados dos provedores de serviço móveis, será necessário abrir a porta 5223 de saída em sua rede Wi-Fi empresarial. O suporte às notificações por push por rede Wi-Fi oferece suporte aos dispositivos móveis que usam apenas Wi-Fi e a dispositivos móveis que possuem uma recepção interna ruim.
    
    > [!IMPORTANT]  
    > Abrir a porta TCP 5223 é necessário somente ao suportar dispositivos Apple executando o cliente Lync 2010 Mobile.    
    Se você não quiser oferecer suporte às notificações por push, os usuários de dispositivos móveis da Apple e de Windows Phones não serão notificados sobre eventos, como convites de mensagem instantânea ou mensagens perdidas, que ocorrem quando o aplicativo móvel está inativo.
    
    > [!NOTE]  
    > Clientes móveis do Lync 2013 em dispositivos Apple não requerem notificações por push. Os clientes móveis do Lync 2013 em Windows Phone utilizam notificações por push. O planejamento para as notificações por push e o centro de roteamento dessas notificações permanece o mesmo para Lync Mobile em Windows Phone e dispositivos Apple que não podem executar o cliente móvel Lync 2013.

  - **Você quer que todos os usuários tenham acesso aos recursos de mobilidade ou quer ser capaz de especificar quais usuários terão acesso a esses recursos?**
    
    A tabela descreve recursos disponíveis para usuários no Lync Server 2013. Os padrões permitem Chamada via Trabalho, Voz por IP (VoIP), e permitem mobilidade. A seguir o conjunto completo de opções disponíveis:
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Recurso/Nome do parâmetro/Escopo (nomes de parâmetro para políticas podem não ser idênticos)</th>
    <th>Descrição</th>
    <th>Introduzido</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Habilitar mobilidade</p>
    <p>Nome do parâmetro: <code>EnableMobility</code></p>
    <p>Escopo: global/site/usuário</p></td>
    <td><p>Configuração administrativa para controlar usuários em um determinado escopo que tenham o Lync Mobile instalado, se a política estiver definida como False, o usuário não seria capaz de realizar sua entrada no cliente.</p>
    <p>A configuração padrão é True.</p></td>
    <td><p>Atualização cumulativa para Lync Server 2010: novembro de 2011</p></td>
    </tr>
    <tr class="even">
    <td><p>Habilitar voz externa</p>
    <p>Nome do parâmetro: <code>EnableOutsideVoice</code></p>
    <p>Escopo: global/site/usuário</p></td>
    <td><p>Controla a habilidade de um usuário de utilizar Chamada via Trabalho, um recurso que permite que usuários façam e recebam chamadas com seu número de trabalho em vez de seu número móvel. Se configurado como False, o usuário não poderá realizar nem receber chamadas utilizando seu número de trabalho a partir de seu dispositivo móvel.</p>
    <p>A configuração padrão é True</p></td>
    <td><p>Atualização cumulativa para Lync Server 2010: novembro de 2011</p></td>
    </tr>
    <tr class="odd">
    <td><p>Habilitar áudio e vídeo por IP</p>
    <p>Nome do parâmetro: <code>EnableIPAudioVideo</code></p>
    <p>Escopo: global/site/usuário</p></td>
    <td><p>Controla a possibilidade ou não de um usuário utilizar VoIP para realizar ou receber chamadas de voz ou vídeo em seu dispositivo móvel. Se estiver definido como False, o usuário não poderá realizar nem receber chamadas VoIP nem de vídeo em seu dispositivo móvel.</p>
    <p>A configuração padrão é True.</p></td>
    <td><p>Microsoft Lync Server 2013</p></td>
    </tr>
    <tr class="even">
    <td><p>Requer WiFi para áudio por IP</p>
    <p>Nome do parâmetro: <code>RequireWiFiForIPAudio</code></p>
    <p>Escopo: global/site/usuário</p></td>
    <td><p>Essa configuração define se será exigido que o cliente faça e receba chamadas via VoIP por WiFi em vez da rede de dados celular. Se definida como true, o usuário poderá realizar chamadas VoIP somente quando conectado a uma rede Wi-Fi.</p>
    <p>A configuração padrão é False.</p></td>
    <td><p>Microsoft Lync Server 2013</p></td>
    </tr>
    <tr class="odd">
    <td><p>Requer WiFi para vídeo por IP</p>
    <p>Nome do parâmetro: <code>RequireWiFiForIPVideo</code></p>
    <p>Escopo: global/site/usuário</p></td>
    <td><p>Essa configuração define se será exigido que o cliente faça e receba chamadas via WiFi em vez da rede de dados celular. Se definida como True, o usuário poderá realizar chamadas de vídeo somente quando conectado a uma rede Wi-Fi.</p>
    <p>A configuração padrão é False.</p></td>
    <td><p>Microsoft Lync Server 2013</p></td>
    </tr>
    </tbody>
    </table>
    
    Para uma descrição das definições de políticas que você pode configurar e como gerenciar essas políticas, consulte [New-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMobilityPolicy), [Set-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMobilityPolicy), [Get-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMobilityPolicy), [Grant-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsMobilityPolicy) e [Remove-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsMobilityPolicy).

  - **Você deseja que os usuários não habilitados para Enterprise Voice possam usar o recurso Clique para ingressar a fim de entrar em conferências?**
    
    Para que os usuários tenham acesso aos recursos de mobilidade e Chamada via Trabalho, eles precisam ser habilitados para o Enterprise Voice. No entanto, os usuários que não estão habilitados para o Enterprise Voice podem ingressar em conferências clicando no link em seu dispositivo móvel, caso tenham uma política de voz apropriada atribuída a eles. É possível atribuir uma política de voz específica a esses usuários ou se certificar de que exista uma política de nível global ou de site que se aplique a eles. A política de voz atribuída precisa ter registros de uso de PSTN (Rede Telefônica Pública Comutada) e rotas que definam as áreas para as quais os usuários possam discar a fim de ingressar em uma conferência. Para obter detalhes sobre como configurar a política de voz, registros de uso de PSTN e rotas, consulte [Configurando políticas de voz, registros de uso de PSTN e rotas de voz no Lync Server 2013](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md).
    
    > [!NOTE]  
    > Os usuários móveis que desejam usar Clique para ingressar precisam de uma política de voz, junto com os registros de uso de PSTN e rotas de voz, pois clicar no link no dispositivo móvel resulta em uma chamada de saída de Lync Server 2013.

## Consulte Também

#### Conceitos

[Requisitos técnicos para mobilidade no Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md)  

#### Outros Recursos

[Configurando políticas de voz, registros de uso de PSTN e rotas de voz no Lync Server 2013](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)

