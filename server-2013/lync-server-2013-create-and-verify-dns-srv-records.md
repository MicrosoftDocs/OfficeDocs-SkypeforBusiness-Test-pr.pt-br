---
title: 'Lync Server 2013: Criar e verificar registros DNS SRV'
TOCTitle: Criar e verificar registros DNS SRV
ms:assetid: 86888c7e-1401-458f-9a7b-08ac726deeec
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398680(v=OCS.15)
ms:contentKeyID: 49307349
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar e verificar registros DNS SRV no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Para concluir com êxito este procedimento, você deve estar conectado no servidor ou domínio no mínimo como um membro do grupo de Administradores de Domínio ou membro do grupo DnsAdmins.

Este tópico descreve como configurar os registros do DNS (Sistema de Nomes de Domínio) que são necessários que você crie na implantação do Lync Server 2013 e os exigidos para a entrada automática de clientes. Quando você cria um Pool de Front-Ends, a Configuração cria objetos e configurações do Active Directory para o pool, incluindo o FQDN (nome de domínio totalmente qualificado). Configurações e objetos similares são criados para Servidor Standard Edition. Para que os clientes possam se conectar ao pool ou Servidor Standard Edition, o FQDN do pool ou Servidor Standard Edition deve estar registrado no DNS. Você deve criar registros SRV de DNS no DNS interno para cada domínio SIP. Este procedimento supõe que o DNS interno tem zonas para os domínios de usuário do SIP.

## Para configurar um registro SRV de DNS

1.  No servidor DNS, clique em **Iniciar**, clique em **Ferramentas Administrativas** e em **DNS**.

2.  Na árvore de console do domínio SIP, expanda **Zonas de Pesquisa Direta** e clique com o botão direito do mouse no domínio SIP no qual o Lync Server 2013 será instalado.

3.  Clique em **Outros Registros Novos**.

4.  Em **Selecione um tipo de registro de recurso**, clique em **Local do Serviço (SRV)** e, em seguida, clique em **Criar Registro**.

5.  Clique em **Serviço** e digite **\_sipinternaltls** .

6.  Clique em **Protocolo** e digite **\_tcp** .

7.  Clique em **Número da Porta** e digite **5061** .

8.  Clique em **Host que oferece este serviço** e digite o FQDN do pool.ou Servidor Standard Edition.

9.  Clique em **OK** e em **Concluído**.

## Para verificar a criação de um registro SRV de DNS

1.  Faça logon em um computador cliente do domínio com uma conta que seja membro do grupo Usuários autenticados ou que tenha permissões equivalentes.

2.  Clique em **Iniciar** e em **Executar**.

3.  Na caixa **Abrir**, digite **cmd** e clique em **OK**.

4.  No prompt de comando, digite **nslookup** e pressione ENTER.

5.  Digite **set type=srv** e pressione ENTER.

6.  Digite **\_sipinternaltls.\_tcp.contoso.com** e pressione ENTER. A saída exibida para o registro de TLS (segurança de camada de transporte) é a seguinte:
    
    Servidor: *\<servidor dns\>* .contoso.com
    
    Endereço: *\<endereço IP do servidor DNS\>*
    
    Resposta não-autorizada:
    
    \_sipinternaltls.\_tcp.contoso.com SRV service location:
    
    priority = 0
    
    weight = 0
    
    port = 5061
    
    svr hostname = poolname.contoso.com (ou um registro A do servidor Standard Edition)
    
    poolname.contoso.com internet address = *\<endereço IP virtual do balanceador de carga\>* ou *\<endereço IP de um único servidor Enterprise Edition para pools com um só servidor Enterprise Edition\>* ou *\<endereço IP do servidor Standard Edition\>*

7.  Quando terminar, no prompt de comando, digite **exit** e pressione ENTER.

## Para verificar se o FQDN do servidor Standard Edition ou pool de Front-Ends pode ser resolvido

1.  Faça logon em um computador cliente no domínio.

2.  Clique em **Iniciar** e em **Executar**.

3.  Na caixa **Abrir**, digite **cmd** e clique em **OK**.

4.  No prompt de comando, digite **nslookup** *\<FQDN do pool de Front End\>* ou *\<FQDN do servidor Standard Edition\>* e pressione ENTER.

5.  Verifique se recebeu uma resposta que resolve para o endereço IP apropriado para o FQDN.

