---
title: 'Lync Server 2013: Criar um registro DNS SRV para integração com Exchange UM hospedado'
TOCTitle: Criar um registro DNS SRV para integração com Exchange UM hospedado
ms:assetid: 8ea590ae-58ea-4ca5-9853-e0708b3ea760
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh500728(v=OCS.15)
ms:contentKeyID: 49307421
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar um registro DNS SRV para integração com Exchange UM hospedado

 

_**Tópico modificado em:** 2016-12-08_

Este tópico descreve como configurar o registro SRV do Sistema de Nome de Domínio (DNS) requerido por um Lync Server 2013Servidor de Borda para rotear para um serviço do Exchange hospedado como o Microsoft Exchange Online.

## Para criar um registro SRV de DNS para o serviço do Exchange hospedado

1.  Faça logon no servidor de DNS externo como membro do grupo DnsAdmins.

2.  Clique em **Iniciar**, **Ferramentas Administrativas** e em **DNS**.

3.  Na árvore do console para o seu domínio SIP, expanda **Zonas de Pesquisa Direta** e selecione o domínio SIP em que o Lync Server 2013 será instalado.
    
    > [!IMPORTANT]  
    > Você deve criar o registro SRV de DNS no domínio SIP em que o Lync Server está ou será instalado. Ao criar o registro SRV, o FQDN usado para o Host que está oferecendo este campo de serviço deve ser o FQDN externo do pool de Borda. Por exemplo, se o FQDN externo do seu pool de Borda for edge01.contoso.net, insira este valor. Este também deve ser o mesmo domínio do registro (A) dos Hosts DNS.

4.  Clique com o botão direito no domínio selecionado e clique em **Outros Registros Novos**.

5.  Em **Tipo de Registro de Recurso**, clique em **Local do Serviço (SRV)** e em **Criar Registro**.

6.  Em **Novo Registro de Recurso**, clique em **Serviço** e digite **\_sipfederationtls** .

7.  Clique em **Protocolo** e digite **\_tcp**.

8.  Clique em **Número da Porta** e digite **5061**.

9.  Clique em **Host que oferece este serviço** e digite o nome de domínio totalmente qualificado (FQDN) do Lync Server 2013  Pool de borda que fornece acesso ao seu sistema do Lync Server 2013 para clientes externos confiáveis.
    
    > [!NOTE]  
    > O domínio também deve ser configurado como domínio autoritativo, aceito em suas configurações do Exchange Online. Para obter detalhes, consulte Criar domínios aceitos em <a href="http://go.microsoft.com/fwlink/p/?linkid=229762">http://go.microsoft.com/fwlink/p/?linkId=229762</a>.

10. Clique em **OK** e em **Concluído**.

## Para verificar se o registro SRV do DNS foi criado com sucesso

1.  Faça logon em um computador cliente no domínio.

2.  Clique em **Iniciar** e em **Executar**.

3.  No prompt de comando, execute o seguinte comando:
    
        nslookup <FQDN Lync Edge Pool>

4.  Verifique se recebeu uma resposta que resolve para o endereço IP apropriado para o FQDN.

## Consulte Também

#### Conceitos

[Criar registros de DNS para servidores de proxy reverso no Lync Server 2013](lync-server-2013-create-dns-records-for-reverse-proxy-servers.md)

