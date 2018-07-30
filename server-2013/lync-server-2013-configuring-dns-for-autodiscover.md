---
title: Configurando o DNS para a descoberta automática
TOCTitle: Configurando o DNS para a descoberta automática
ms:assetid: f07a634c-3cf3-4958-8556-84596319ef54
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945656(v=OCS.15)
ms:contentKeyID: 52057765
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o DNS para a descoberta automática

 

_**Tópico modificado em:** 2012-12-12_

Para dar suporte à descoberta automática dos clientes do Lync, você precisa criar os seguintes registros DNS (Sistema de Nomes de Domínio):

  - Um registro DNS interno para dar suporte aos clientes do Lync que se conectam a partir da rede de sua organização.

  - Um registro DNS externo ou público para dar suporte aos clientes do Lync que se conectam pela Internet

Você deve criar um registro DNS interno e outro externo para cada domínio SIP.

Os registros DNS podem ser registros A (host) ou CNAME, com base em sua capacidade de criar novos certificados com o SAN (nome alternativo da entidade) adicional. Se você não puder solicitar e implantar um novo certificado externo (público) com o SAN lyncdiscover.\<domain name\>, use o procedimento para a utilização de HTTP/TCP na porta 80. Os procedimentos a seguir descrevem como criar registros DNS internos e externos.

## Para criar registros DNS CNAME

1.  Faça logon em um servidor DNS conforme segue:
    
      - Para criar um registro DNS interno, faça logon em um servidor DNS de sua rede como membro do grupo Admins. do Domínio ou DnsAdmins.
    
      - Para criar um registro DNS externo, conecte-se com seu provedor de DNS público.

2.  Abra o snap-in administrativo do DNS: clique em **Iniciar**, depois, em **Ferramentas Administrativas** e, então, em **DNS**.

3.  Realize uma das seguintes ações:
    
      - Para um DNS interno, na árvore de console do servidor DNS, expanda **Zonas de pesquisa direta** de seu domínio do Active Directory (por exemplo, contoso.local).
        
        > [!NOTE]  
        > Este é o domínio do Active Directory no qual seu pool do Lync Server 2013 Diretor e Pool de Front-Ends estão instalados.    
      - Para um registro DNS externo, na árvore de console do servidor DNS, expanda **Zonas de pesquisa direta** de seu domínio SIM (por exemplo, contoso.com).

4.  Verifique se o registro de host A existe para seu Pool de diretores da seguinte forma:
    
      - Para um registro DNS interno, um registro de host A deve existir para o FQDN (nome de domínio totalmente qualificado) dos serviços Web internos de seu Pool de diretores (por exemplo, lyncwebdir01.contoso.local).
    
      - Para um registro de DNS externo, um registro de host A deve existir para o FQDN de Serviços Web externos do Pool de diretores (por exemplo, lyncwebextdir.contoso.com).

5.  Verifique se existe um registro de host A para o Pool de Front-Ends da seguinte forma:
    
      - Para um registro de DNS interno, um registro de host A deve existir para o FQDN de Serviços Web internos para o Pool de Front-Ends (por exemplo, lyncwebpool01.contoso.local).
    
      - Para um registro de DNS externo, um registro de host A deve existir para o FQDN de Serviços Web externos para o Pool de Front-Ends (por exemplo, lyncwebextpool01.contoso.com).

6.  Para um registro DNS interno, na árvore de console do servidor de DNS, expanda **Zonas de pesquisa direta** de seu domínio SIP (por exemplo, contoso.com).
    
    > [!NOTE]  
    > Se você estiver criando um registro DNS externo, <strong>Zonas de pesquisa direta</strong> já estará expandido para o domínio SIP da etapa 3.

7.  Clique com o botão direito do mouse no nome do domínio SIP e, depois, em **Novo Alias (CNAME)**.

8.  Em **Nome do alias**, digite uma das seguintes opções:
    
      - Para um registro DNS interno, digite lyncdiscoverinternal como o nome do host da URL interna do serviço Descoberta Automática.
    
      - Para um registro DNS externo, digite lyncdiscover como o nome do host da URL externa do serviço Descoberta Automática.

9.  Em **Nome de domínio totalmente qualificado (FQDN) para o host de destino**, realize uma das seguintes ações:
    
      - Para um registro DNS interno, digite ou procure o FQDN dos serviços Web internos de seu Pool de diretores (por exemplo, lyncwebdir01.contoso.local) e clique em **OK**.
    
      - Para um registro DNS externo, digite ou procure o FQDN dos serviços Web externos de seu Pool de diretores (por exemplo, lyncwebextdir.contoso.com) e clique em **OK**.
    
    > [!NOTE]  
    > Se você não usar uma Diretor, use o FQDN dos serviços Web internos e externos do Pool de Front-Ends ou, para um único servidor, o FQDN da Servidor Front-End ou Servidor Standard Edition.    
    > [!IMPORTANT]  
    > Você deve criar um novo registro CNAME de Descoberta Automática na zona de pesquisa direta de cada domínio SIP com suporte em seu ambiente do Lync Server 2013.

## Para criar registros DNS A

1.  Faça logon em um servidor DNS conforme segue:
    
      - Para criar um registro DNS interno, faça logon em um servidor DNS de sua rede como membro do grupo Admins. do Domínio ou DnsAdmins.
    
      - Para criar um registro DNS externo, conecte-se com seu provedor de DNS público ou servidor DNS externo.

2.  Abra o snap-in administrativo do DNS: clique em **Iniciar**, depois, em **Ferramentas Administrativas** e, então, em **DNS**.

3.  Realize uma das seguintes ações:
    
      - Para um DNS interno, na árvore de console do servidor DNS, expanda **Zonas de pesquisa direta** de seu domínio do Active Directory (por exemplo, contoso.local).
        
        > [!NOTE]  
        > Este é o domínio do Active Directory no qual seu pool do Lync Server 2013 Diretor e Pool de Front-Ends estão instalados.    
      - Para um registro DNS externo, na árvore de console do servidor DNS, expanda **Zonas de pesquisa direta** de seu domínio SIM (por exemplo, contoso.com).

4.  Verifique se existe um registro de host A (para IPv6, AAAA) do Pool de diretores conforme segue:
    
      - Para um registro DNS interno, um registro de host A (para IPv6, AAAA) deve existir para o FQDN de serviços Web internos do Pool de diretores (por exemplo, lyncwebdir01.contoso.local).
    
      - Para um registro DNS externo, um registro de host A (para IPv6, AAAA) deve existir para o FQDN de serviços Web externos do Pool de diretores (por exemplo, lyncwebextdir.contoso.com).

5.  Verifique se existe um registro de host A (para IPv6, AAAA) do Pool de Front-Ends conforme segue:
    
      - Para um registro DNS interno, um registro de host A (para IPv6, AAAA) deve existir para o FQDN de serviços Web internos do Pool de Front-Ends (por exemplo, lyncwebpool01.contoso.local).
    
      - Para um registro DNS externo, um registro de host A (para IPv6, AAAA) deve existir para o FQDN de serviços Web externos do Pool de Front-Ends (por exemplo, lyncwebextpool01.contoso.com).

6.  Para um registro DNS interno, na árvore de console do servidor DNS, expanda **Zonas de pesquisa direta** de seu domínio SIP (por exemplo, contoso.com).
    
    > [!NOTE]  
    > Se você estiver criando um registro DNS externo, <strong>Zonas de pesquisa direta</strong> já estará expandido para o domínio SIP da etapa 3.

7.  Clique com o botão direito do mouse no nome do domínio SIP e, então, em **Novo Host (A ou AAAA)**.

8.  Em **Nome**, digite o nome do host conforme segue:
    
      - Para um registro DNS interno, digite lyncdiscoverinternal como o nome do host da URL interna do serviço Descoberta Automática.
    
      - Para um registro DNS externo, digite lyncdiscover como o nome do host da URL externa do serviço Descoberta Automática.
    
    > [!NOTE]  
    > O nome de domínio é presumido pela zona em que o registro está definido e, portanto, não precisa ser inserido como parte do registro A.

9.  Em **Endereço IP**, digite o endereço IP conforme segue:
    
      - Para um registro DNS interno, digite o endereço IP dos serviços Web internos da Diretor (ou, se você usa um balanceador de carga, digite o VIP (IP virtual) do balanceador de carga da Diretor).
        
        > [!NOTE]  
        > Se você não usar um Diretor, digite o endereço IP do Servidor Front-End ou Servidor Standard Edition, ou se usar um balanceador de carga, digite VIP do balanceador do Pool de Front-Ends.    
      - Para um registro DNS externo, digite o endereço IP externo ou público do proxy reverso.

10. Clique em **Adicionar Host** e, depois, em **OK**.

11. Para criar um registro A adicional, repita as etapas de 8 a 10.
    
    > [!IMPORTANT]  
    > Você deve criar novos registros A lyncdiscover e lyncdiscoverinternal na zona de pesquisa direta de cada domínio SIP com suporte no ambiente do Lync Server 2013.

12. Quando terminar de criar os registros A (para IPv6, AAAA), clique em **Concluído**.

