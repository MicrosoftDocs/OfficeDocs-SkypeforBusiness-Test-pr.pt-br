---
title: 'Lync Server 2013: Failover do pool de Borda usado para federação de XMPP'
TOCTitle: Failover do pool de Borda usado para federação de XMPP
ms:assetid: 587e7829-a26b-46f8-8aad-b78a7b325b55
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688065(v=OCS.15)
ms:contentKeyID: 49886229
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Failover do pool de Borda usado para federação de XMPP no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Na sua organização, há um pool de borda designado como o pool para uso da federação XMPP. Se esse pool parar de funcionar, você deve transferir a federação XMPP para usar um pool de borda diferente antes da federação XMPP poder funcionar novamente.

Quando você instala pools de borda e habilita a Federação XMPP, é possível simplificar o processo de recuperação de desastres configurando a criação de registros do servidor DNS externos para todos os seus pools de Borda para a federação XMPP, em vez de apenas um. Cada um destes registros SRV devem ter um conjunto de prioridade diferente. Todo o tráfego da federação XMPP atravessa o pool com o registro SRV com a mais alta prioridade. Para obter mais informações sobre como habilitar e configurar a federação XMPP, consulte [Configurando federação de XMPP no Lync Server 2013](lync-server-2013-setting-up-xmpp-federation.md).

No procedimento a seguir, o EdgePool1 é o pool no qual a federação XMPP foi originalmente hospedada e o EdgePool2 é o pool no qual a federação XMPP está hospedada agora.

## Pool de borda com falhas usado para federação XMPP

1.  Se você ainda não possuir outro pool de borda implantado (além de um não estiver funcionando no momento), implante esse pool. Para obter detalhes, consulte [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md).

2.  Em cada Servidor de Borda no novo pool de borda no qual a federação XMPP estará hospedada no momento (EdgePool2), execute o seguinte cmdlet:
    
        Stop-CsWindowsService

3.  Execute o seguinte cmdlet para redirecionar a rota da federação XMPP para o EdgePool2:
    
        Set-CsSite Site2 -XmppExternalFederationRoute EdgeServer2.contoso.com
    
    Neste exemplo, o Site2 é o site contendo o pool de borda no qual a rota da federação XMPP estará hospedada no momento e o EdgeServer2.contoso.com é o FQDN de um Servidor de Borda nesse pool.

4.  No servidor DNS externo, altere o registro DNS A para federação XMPP apontar para o EdgeServer2.contoso.com.

5.  Se você ainda não tiver um registro DNS SRV para a federação XMPP que resolve o pool de Borda que hospedará a federação XMPP, você deve adicioná-lo, conforme no exemplo a seguir. Este registro SRV deve ter um valor de porta de 5269.
    
        _xmpp-server._tcp.contoso.com

6.  Verifique se o pool de Borda irá agora hospedar federação XMPP com porta 5269 aberta externamente.

7.  Inicie os serviços em todos os Servidores de Borda no pool de borda no qual a federação XMPP estará hospedada no momento:
    
        Start-CsWindowsService

