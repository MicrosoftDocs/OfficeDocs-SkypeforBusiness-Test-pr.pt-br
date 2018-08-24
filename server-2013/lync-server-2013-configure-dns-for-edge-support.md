---
title: 'Lync Server 2013: Configurar DNS para suporte à borda'
TOCTitle: Configurar DNS para suporte à borda
ms:assetid: 955493e6-aa29-424d-bb81-1ef87b3b15e3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398756(v=OCS.15)
ms:contentKeyID: 49307501
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar DNS para suporte à borda no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-15_

Você deve configurar os registros de DNS (Sistema de Nomes de Domínio) para interfaces de borda internas e externas, incluindo ambas as interfaces do Servidor de Borda e do proxy reverso. Como padrão, os Servidores de Borda não são reunidos em um domínio e não têm um nome de domínio totalmente qualificado. O Servidor de Borda é referenciado apenas pelo nome (de máquina) curto, não um nome de domínio totalmente qualificado. No entanto, a Construtor de Topologias usa FQDNs, não nomes curtos. O nome do Servidor de Borda deve corresponder ao FQDN usado pelo Construtor de Topologias. Para isso, você define um sufixo DNS que, ao ser combinado como nome de máquina, resulta no FQDN esperado. Use o seguinte procedimento em "Para adicionar o sufixo DNS do nome do computador em um Servidor de Borda que não está associado a um domínio" para adicionar o sufixo DNS ao nome do computador.

> [!NOTE]  
> Por padrão, o DNS usa um algoritmo round-robin para alternar a ordem dos dados de registro de recursos retornados nas perguntas de consulta, quando vários registros de recurso do mesmo tipo existem para um nome de domínio DNS consultado. O balanceamento de carga de DNS do Lync Server 2013 depende do round-robin de DNS como parte do mecanismo do balanceamento de carga de DNS. Verifique se essa configuração de round-robin não foi desativada. Se estiver usando um servidor DNS que não executa um sistema operacional Windows, verifique se a solicitação do registro de recurso round-robin está ativada.

Use os procedimentos a seguir em “ **Para criar um registro DNS SRV** ” para criar e verificar cada registro DNS SRV. Use o procedimento em “ **Para criar um registro A de DNS** ” para definir os registros A de DNS necessários para acesso do usuário externo. Para confirmar que os registros estão configurados e funcionando corretamente, consulte “ **Para verificar um registro DNS** ” neste tópico. Para obter detalhes sobre cada registro necessário para suportar acesso do usuário externo, consulte [Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

## Para adicionar o sufixo DNS do nome do computador em um Servidor de Borda que não está associado a um domínio

1.  No computador, clique em **Iniciar** , clique com o botão direito do mouse em **Computador** e clique em **Propriedades** .

2.  Em **Nome do computador, domínio e configurações de grupo de trabalho** , clique em **Alterar configurações** .

3.  Na guia **Nome do Computador** , clique em **Alterar** .

4.  Em **Alterações de Nome/Domínio do Computador** , clique em **Mais** .

5.  Em **Sufixo DNS e nome NetBIOS do computador** , no **Sufixo DNS primário deste computador** , digite o nome de seu domínio interno (por exemplo, corp.contoso.com) e clique em **OK** três vezes.

6.  Reinicie o computador.

## Para criar um registro SRV de DNS

1.  No servidor DNS apropriado, clique em **Iniciar** , clique em **Painel de Controle** , clique em **Ferramentas Administrativas** e, em seguida, clique em **DNS** .
    
    > [!IMPORTANT]  
    > Você precisa configurar o DNS de forma que existam: 1) entradas de DNS externas para pesquisas de DNS externo pelos usuários remotos e parceiros federados; 2) entradas para pesquisas de DNS para uso pelos Servidores de Borda dentro da rede de perímetro (também conhecida como sub-rede com triagem), incluindo registros A para os servidores internos que executam o Lync Server 2013; e 3) entradas de DNS internas para pesquisas pelos clientes internos e servidores que executam o Lync Server 2013.

2.  Na árvore de console para seu domínio SIP, expanda **Zonas de Pesquisa Direta** e clique com o botão direito no domínio onde o Lync Server 2013 está instalado.

3.  Clique em **Outros Registros Novos** .

4.  Em **Selecione um tipo de registro de recurso** , digite o **Local do Serviço (SRV)** e, em seguida, clique em **Criar Registro** .

5.  Forneça todas as informações exigidas para o registro SRV de DNS.

## Para criar um registro A de DNS

1.  No servidor DNS, clique em **Iniciar** , clique em **Painel de Controle** , clique em **Ferramentas Administrativas** e, em seguida, clique em **DNS** .

2.  Na árvore de console do domínio SIP, expanda **Zonas de Pesquisa Direta** e clique com o botão direito no domínio em que o Lync Server 2013 está instalado.

3.  Clique em **Novo Host (A)** .

4.  Forneça todas as informações exigidas para o registro SRV de DNS.

## Para verificar um registro DNS

1.  Faça logon em um computador cliente no domínio.

2.  Clique em **Iniciar** e em **Executar** .

3.  No prompt de comando, execute o seguinte comando:
    
        nslookup <FQDN edge interface>

4.  Verifique se recebeu uma resposta que resolve para o endereço IP apropriado para o FQDN.

## Consulte Também

#### Tarefas

[Criar um registro DNS SRV para integração com Exchange UM hospedado](lync-server-2013-create-a-dns-srv-record-for-integration-with-hosted-exchange-um.md)  

#### Conceitos

[Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md)

