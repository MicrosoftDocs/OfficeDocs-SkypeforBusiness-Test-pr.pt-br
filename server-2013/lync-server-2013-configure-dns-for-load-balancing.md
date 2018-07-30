---
title: 'Lync Server 2013: Configurar DNS para balanceamento de carga'
TOCTitle: Configurar DNS para balanceamento de carga
ms:assetid: 1b2e8414-8676-4872-8ecf-ea07196f74de
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398251(v=OCS.15)
ms:contentKeyID: 49306045
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar DNS para balanceamento de carga no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Para concluir com este procedimento com êxito, você deve estar conectado no servidor ou domínio no mínimo como um membro do grupo de Administradores de Domínio ou membro do grupo DnsAdmins.

O Balanceamento de Carga do DNS (Domain Name System) balanceia o tráfego de rede que é exclusivo ao Lync Server 2013, como tráfego SIP e de mídia. O balanceamento de carga DNS é suportado para pools de Front-Ends, pools de Borda, pools de Diretores e pools de Mediação autônomos. Um pool configurado para usar o balanceamento de carga DNS deve possuir dois FQDNs (nomes de domínio totalmente qualificados) definidos: o FQDN do pool normal que é usado pelo balanceamento de carga DNS (por exemplo, pool1.contoso.com) e que resolve aos IPs físicos dos servidores no pool, e outro FQDN para o Serviços Web do pool (por exemplo, web1.contoso.net), que resolve para o endereço IP virtual do pool. Para obter detalhes sobre Balanceamento de Carga DNS, consulte [Balanceamento de carga DNS no Lync Server 2013](lync-server-2013-dns-load-balancing.md) na documentação de Planejamento.

> [!NOTE]  
> O balanceamento de carga de hardware ainda é exigido para tráfego HTTPS de cliente para servidor.

Antes que possa usar o balanceamento de carga DNS, você deve fazer o seguinte:

1.  Substituir o pool FQDN Serviços Web interno.
    

    > [!WARNING]
    > Se você decidir substituir os serviços web internos com um FQDN definido automaticamente, cada FQDN deve ser único se comparado a outro Pool de Front-Ends, Diretor ou um Pool de diretores.



2.  Crie registros de host A DNS para resolver o pool FQDN para os endereços IP de todos os servidores no pool.

3.  Habilite randomização de Endereço IP ou, no caso do Windows Server DNS, habilite o Round robin.
    
    > [!NOTE]  
    > O Round robin deve ser habilitado por padrão.

## Substituir o FQDN de Serviços Web internos

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  A partir da árvore do console, expanda o nó dos pools do Enterprise Edition Front End.

3.  Clique com o botão direito do mouse no pool e em **Editar Propriedades** , em seguida **Serviços Web** .

4.  Em **Serviços Web internos** , selecione a caixa de seleção **Substituir o FQDN** .

5.  Digite o FQDN do pool que resolve os endereços IP físicos dos servidores no pool.

6.  Em **Serviços Web externos** , digite o FQDN de pool externo que resolve os endereços de IP virtuais e clique em **OK** .

7.  A partir da árvore de console, clique no **Lync Server 2013**, e então no painel **Actions** , clique em **Publicar topologia**.

## Para criar Registros de Host (A) DNS para os sevidores de pool internos

1.  Clique em **Iniciar**, **Todos os Programas**, **Ferramentas Administrativas** e **DNS** .

2.  No **Gerenciador DNS**, clique no servidor DNS responsável pelo gerenciamento dos registros e expanda-o.

3.  Clique em **Zona de pesquisa direta** para expandi-la.

4.  Clique com o botão direito do mouse no domínio DNS que deseja adicionar aos registros e clique em **Novo Host (A ou AAAA)...** .

5.  Na caixa **Nome** , digite o nome do registro host (o nome do domínio será atumaticamente acrescentado).

6.  Na caixa de endereço de IP, digite o endereço IP do Front End Server individual e selecione **Criar registro de ponteiro associado (PTR)** ou **Permitir que qualquer usuário autenticado atualize registros de DNS com o mesmo nome de proprietário** , se aplicável.

7.  Continue criando registros para todos os membros do Front End Servers participantes no Balanceamento de Carga DNS.
    
    Por exemplo, se você tiver um nome de pool pool1.contoso.com e três Front End Servers, você deve criar as seguintes entradas DNS:
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>FQDN</th>
    <th>Tipo</th>
    <th>Dados</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Pool1.contoso.com</p></td>
    <td><p>Host (A)</p></td>
    <td><p>192.168.1.1</p></td>
    </tr>
    <tr class="even">
    <td><p>Pool1.contoso.com</p></td>
    <td><p>Host (A)</p></td>
    <td><p>192.168.1.2</p></td>
    </tr>
    <tr class="odd">
    <td><p>Pool1.contoso.com</p></td>
    <td><p>Host (A)</p></td>
    <td><p>192.168.1.3</p></td>
    </tr>
    </tbody>
    </table>
    
    Para detalhes sobre criação de registros Host (A) DNS, consulte [Configurar registros de Host DNS para Lync Server 2013](lync-server-2013-configure-dns-host-records.md).

## Para habilitar o Round robin para o Windows Server

1.  Clique em **Iniciar**, **Todos os Programas**, **Ferramentas Administrativas** e **DNS**.

2.  Expanda **DNS** , clique com o botão direito do mouse no servidor DNS que você deseja configurar e clique em **Propriedades**.

3.  Clique na guia **Avançado** , selecione **Ativar rodízio** e **Ativar classificação de máscaras** e clique em **OK** .
    
    ![Caixa de diálogo Repetição alternada DNS](images/Gg398251.e7bf6125-8d78-4460-8401-0a8e7e21d305(OCS.15).jpg "Caixa de diálogo Repetição alternada DNS")

> [!NOTE]  
> Este recurso deve ser habilitado por padrão.

## Consulte Também

#### Conceitos

[Balanceamento de carga DNS no Lync Server 2013](lync-server-2013-dns-load-balancing.md)

