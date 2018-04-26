---
title: Atualizar registros de DNS SRV
TOCTitle: Atualizar registros de DNS SRV
ms:assetid: 9542b91a-108c-4980-89ec-634905cbbf26
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688139(v=OCS.15)
ms:contentKeyID: 49886320
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atualizar registros de DNS SRV

 

_**Tópico modificado em:** 2012-09-29_

Para realizar este procedimento com sucesso, é necessário fazer login no servidor ou domínio como membro do grupo Admins. de Domínio ou do grupo DnsAdmins.

Este tópico descreve como atualizar os registros de DNS (Domain Name System) após migrar para o Lync Server 2013. Depois que todos os usuário forem movidos para Lync Server 2013, mas antes que o pool ou Diretor antigo do Lync Server 2010 seja descomissionado, é necessário atualizar os registros DNS SRV em seu DNS interno para cada domínio SIP. Este procedimento supõe que o DNS interno tem zonas para os domínios de usuário do SIP.

**Para configurar um registro SRV de DNS**

1.  No servidor DNS, clique em **Iniciar** , clique em **Ferramentas Administrativas** e em **DNS** .

2.  Na árvore do console para o seu domínio SIP, expanda **Zonas de Pesquisa Direta** , expanda o domínio SIP em que o Lync Server 2013 será instalado e navegue para a configuração **\_tcp**.

3.  No painel direito, clique com o botão direito em **\_sipinternaltls** e selecione **Propriedades**.

4.  Em **Host que oferece este serviço** , atualize o FQDN do host para apontar para o pool Lync Server 2013.

5.  Clique em **OK** .

**Para verificar se o FQDN do servidor Standard Edition ou pool de Front-Ends pode ser resolvido**

1.  Faça logon em um computador cliente no domínio.

2.  Clique em **Iniciar** e em **Executar** .

3.  Na caixa **Abrir** , digite **cmd** e clique em **OK** .

4.  No prompt de comando, digite **nslookup** *\<FQDN do pool de Front End\>* ou *\<FQDN do servidor Standard Edition\>* e pressione ENTER.

5.  Verifique se recebeu uma resposta que resolve para o endereço IP apropriado para o FQDN.

