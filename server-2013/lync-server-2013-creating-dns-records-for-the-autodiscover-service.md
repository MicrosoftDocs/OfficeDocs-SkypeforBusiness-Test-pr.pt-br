---
title: 'Lync Server 2013: Criando registros de DNS para o Serviço de Autodiscover'
TOCTitle: Criando registros de DNS para o Serviço de Autodiscover
ms:assetid: 3756ffe4-c6b1-492d-850e-42a832e06567
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690010(v=OCS.15)
ms:contentKeyID: 49306383
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criando registros de DNS para o Serviço de Autodiscover no Lync Server 2013

 

_**Tópico modificado em:** 2014-06-20_

Os usuários do Lync Mobile precisarão habilitar a descoberta automática, e uma parte disso envolve a criação de alguns registros DNS (Sistema de Nomes de Domínio). Dependendo de suas necessidades, os seguintes item são necessários:

  - Um registro DNS interno para oferecer suporte a usuários móveis que se conectam a partir da rede da organização.

  - Um registro DNS externo, ou público, para oferecer suporte aos usuários móveis que se conectam a partir da Internet

Por que os dois? É necessário criar um registro DNS interno e um registro DNS externo para cada domínio SIP.

Os registros DNS criados podem ser registros (do host) A ou registros CNAME. Para ajudar, explicaremos abaixo como criar estes registros DNS internos e externos. Caso seja necessário ler mais sobre os requisitos de DNS para usuários móveis, consulte [Requisitos técnicos para mobilidade no Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md).

## Criando um registro DNS CNAME interno

1.  Para criar um registro DNS interno, é necessário fazer logon em um servidor DNS em sua rede com uma conta de domínio que seja um membro do grupo de Admins. do Domínio ou um membro do grupo DnsAdmins.

2.  Abra o snap-in administrativo do DNS: clique em **Iniciar** , depois, em **Ferramentas Administrativas** e, então, em **DNS** .

3.  Na árvore do console do servidor DNS, expanda as **Zonas de pesquisa direta** para o domínio do Active Directory em que o Lync Server 2013Pool de diretores e o Pool de Front-Ends estão instalados. (por exemplo, contoso.local).

4.  Se um registro de host A (AAAA para IPv6) existir para o Pool de diretores para um registro DNS interno, um registro de host A deve existir para o FQDN (nome de domínio totalmente qualificado) de Serviços Web internos para o Pool de diretores (por exemplo, lyncwebdir01.contoso.local). Caso não esteja aqui, não será possível usar um Pool de diretores, e você precisará usar o FQDN para o Pool de Front-Ends ou até mesmo um FQDN de um único servidor, se esta for sua configuração.

5.  Com isso em mente, se um registro de host A (AAAA para IPv6) existir para o Pool de Front-Ends para um registro DNS interno, um registro de host A (ou AAAA) deve existir para o FQDN interno de Serviços Web para o Pool de Front-Ends (por exemplo, lyncwebpool01.contoso.local). Caso contrário, será necessário anotar o FQDN para o Servidor Front-End ou Servidor Standard Edition.

6.  Depois de descobrir quais registros de host A (ou AAAA) existem, na árvore do console do servidor DNS, expanda as **Zonas de pesquisa direta** para o domínio SIP (por exemplo, contoso.com).

7.  Clique com o botão direito do mouse no nome do domínio SIP e, depois, em **Novo Alias (CNAME)** .

8.  Em **Nome de alias**, digite lyncdiscoverinternal como o nome de host para a URL interna do Serviço de Descoberta Automática.

9.  Em **FQDN (nome de domínio totalmente qualificado) para o host de destino**, digite ou procure o FQDN de Serviços Web internos para o Pool de diretores (por exemplo, lyncwebdir01.contoso.local) e clique em **OK**.

10. Você deve criar um novo registro CNAME de Descoberta Automática na zona de pesquisa direta de cada domínio SIP com suporte em seu ambiente do Lync Server 2013.

## Criando um registro DNS CNAME externo

1.  Para criar um registro DNS CNAME externo, conecte-se ao provedor público de DNS e siga nossas etapas. Não é possível descrever exatamente aonde você está indo no ambiente do provedor de DNS, pois pode haver maneiras diferentes de gerenciar o DNS externo, mas esperamos que estas etapas ajudem.

2.  Faça logon no provedor de DNS externo com uma conta que pode criar registros DNS naquele ambiente.

3.  Você já deve ter um domínio SIP criado para este ambiente. Expanda as **Zonas de pesquisa direta** para este domínio SIP ou, de outra forma, selecione-o dependendo da interface DNS externa sendo usada.

4.  Você já deve ver um registro de host A (AAAA para IPv6) para o Pool de diretores (como lyncwebexdir01.contoso.com), portanto confirme se está lá. Caso contrário, pode ser que você não esteja usando um Pool de diretores. Se for esse o caso, será necessário usar o FQDN de seu Pool de Front-Ends ou, caso você esteja fazendo isso para um único servidor, para o servidor Front-End ou servidor Standard Edition.

5.  Também é necessário confirmar se um registro de host A (AAAA para IPv6) existe para o FQDN (nome de domínio totalmente qualificado) de Serviços Web externos para o pool de Front-Ends (como lyncwebextpool01.contoso.com), ou um FQDN para o FQDN de servidor único caso você não tenha um pool de Front-Ends. Conforme observado na etapa anterior, os itens abaixo serão necessários se você não tiver um pool de Diretores.

6.  Agora, no formato adequado para o provedor DNS externo, escolha a opção para criar um **Novo Alias (CNAME)** (pode ser uma opção de menu ou um link, dependendo do formato do provedor DNS).

7.  Na caixa de texto de **Nome do alias**, assim como no DNS interno, digite lyncdiscover como o nome de host para a URL de serviço externo de descoberta automática.

8.  Na caixa de texto de **Nome de domínio totalmente qualificado (FQDN) para o host de destino**, digite o FQDN dos serviços Web externos para Pool de diretores (por exemplo, lyncwebexdir01.contoso.com) e clique em OK ou tome a ação necessária no DNS externo para aceitar a criação desta entrada. Conforme observado na Etapa 4 acima, se você não tiver um Pool de diretores, precisará usar o FQDN do pool de Front-Ends ou FQDN de servidor único que você configurou, conforma apropriado.

9.  Será necessário criar um novo registro CNAME de descoberta automática na zona de pesquisa direta de cada domínio SIP compatível no ambiente do Lync 2013.

## Criando um registro A DNS interno

1.  Para criar um registro DNS interno, faça logon em um servidor DNS na rede com a conta de domínio que seja membro do grupo de Admins. de Domínio ou um membro do grupo DnsAdmins.

2.  Abra o snap-in administrativo do DNS: clique em **Iniciar** , depois, em **Ferramentas Administrativas** e, então, em **DNS** .

3.  Para um registro DNS interno, na árvore de console do servidor de DNS, expanda as **Zonas de Pesquisa Direta** para seu domínio do Active Directory (por exemplo, contoso.local) onde o pool do Lync Server 2013Diretor e Pool de Front-Ends estão instalados.

4.  Se um registro de host A (AAAA para IPv6) existir para o Pool de diretores para um registro DNS interno, um registro de host A deve existir para o FQDN (nome de domínio totalmente qualificado) de Serviços Web internos para o Pool de diretores (por exemplo, lyncwebdir01.contoso.local). Caso não esteja aqui, não será possível usar um Pool de diretores, e você precisará usar o endereço IP para seu pool de Front-Ends ou até mesmo um endereço IP de servidor único, caso seja sua configuração.

5.  Com isso em mente, se um registro de host A (AAAA para IPv6) existir para o Pool de Front-Ends para um registro DNS interno, um registro de host A (ou AAAA) deve existir para o FQDN de Serviços Web internos para o Pool de Front-Ends (por exemplo, lyncwebpool01.contoso.local). Caso contrário, será necessário anotar o endereço IP para o Servidor Front-End ou Servidor Standard Edition.

6.  Depois de descobrir quais registros de host A (ou AAAA) existem, na árvore do console do servidor DNS, expanda as **Zonas de pesquisa direta** para o domínio SIP (por exemplo, contoso.com).

7.  Clique com o botão direito do mouse no nome do domínio SIP e, então, em **Novo Host (A ou AAAA)** .

8.  Em **Nome**, digite lyncdiscoverinternal como o nome de host para a URL de serviço interno de descoberta automática.

9.  Em **Endereço IP**, digite o endereço IP de Serviços Web internos do Diretor (ou, se você usar um balanceador de carga, digite o IP virtual (VIP) do balanceador de carga do Diretor). Conforme observado na Etapa 4 acima, se você não estiver usando um Diretor, será necessário inserir o endereço IP do Servidor Front-End ou Servidor Standard Edition ou, se você usar um balanceador de carga, digite o VIP do balanceador de carga do Pool de Front-Ends.

10. Clique em **Adicionar Host** e, depois, em **OK** .

11. Para criar um registro A ou AAAA, repita as etapas de 8 a 10, lembrando-se de que será necessário criar novos registros A ou AAAA de descoberta automática na zona de pesquisa direta de cada domínio SIP compatível no ambiente do Lync Server 2013.

12. Quando terminar de criar os registros A (para IPv6, AAAA), clique em **Concluído** .

## Criando um registro DNS externo

1.  Para criar um registro DNS CNAME externo, conecte-se ao provedor público de DNS e siga nossas etapas. Não é possível descrever exatamente aonde você está indo no ambiente do provedor de DNS, pois pode haver maneiras diferentes de gerenciar o DNS externo, mas esperamos que estas etapas ajudem.

2.  Faça logon assim como em uma conta que pode criar registros DNS naquele ambiente.

3.  Para um registro DNS externo, na árvore de console do servidor DNS, expanda as **Zonas de pesquisa direta** para seu domínio SIP (por exemplo, contoso.com). Para um registro DNS externo, na árvore de console do servidor DNS, expanda as **Zonas de pesquisa direta** para seu domínio SIM (por exemplo, contoso.com).

4.  Você já deve ver um registro de host A (AAAA para IPv6) para o Pool de diretores (como lyncwebexdir01.contoso.com), portanto confirme se está lá e qual é o endereço IP. Caso contrário, pode ser que você não esteja usando um Pool de diretores. Se for esse o caso, será necessário usar o endereço IP de seu Pool de Front-Ends ou, caso você esteja fazendo isso para um único servidor, para o servidor Front-End ou servidor Standard Edition. Lembre-se de que os servidores também podem estar atrás de um balanceador de carga, ou utilizando um proxy reverso. Anote também os endereços IP para as etapas a seguir.

5.  Também é necessário confirmar se um registro de host A (AAAA para IPv6) existe para o FQDN (nome de domínio totalmente qualificado) de Serviços Web externos para o pool de Front-Ends (como lyncwebextpool01.contoso.com), ou um endereço IP para a instalação do Lync de servidor único caso você não tenha um pool de Front-Ends. Conforme observado na etapa anterior, os itens abaixo serão necessários se você não tiver um pool de Diretores.

6.  Agora, no formato adequado para o provedor DNS externo, escolha a opção para criar um **Novo Host A ou AAAA** (pode ser uma opção de menu ou um link, dependendo do formato do provedor DNS).

7.  Em um local para digitar um **Nome**, digite lyncdiscover como o nome de host para a URL de serviço externo de descoberta automática.

8.  Em uma caixa de texto de **Endereço IP** digite o IP para seu Pool de diretores (por exemplo, lyncwebexdir01.contoso.com) ou possivelmente o IP do balanceador de carga do seu pool (ou um IP de proxy reverso que leva a ele) e clique em OK ou tome qualquer ação no DNS externo para aceitar a criação desta entrada. Conforme observado na Etapa 4 acima, se você não tiver um Pool de diretores, será necessário utilizar o endereço IP do pool de Front-Ends ou o endereço IP do servidor único que você configurou, conforme adequado.

9.  Será necessário criar um novo registro A ou AAAA de descoberta automática na zona de pesquisa direta de cada domínio SIP compatível com seu ambiente do Lync 2013.

