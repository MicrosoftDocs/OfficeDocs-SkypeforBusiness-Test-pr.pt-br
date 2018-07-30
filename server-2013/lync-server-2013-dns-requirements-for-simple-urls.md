---
title: 'Lync Server 2013: Requisitos de DNS para URLs simples'
TOCTitle: Requisitos de DNS para URLs simples
ms:assetid: 3a3c9b22-892f-45a7-b05c-539d358a1a86
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425874(v=OCS.15)
ms:contentKeyID: 49306424
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de DNS para URLs simples no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Lync Server 2013 dá suporte a URLs simples, que facilitam para os usuários o ingresso em reuniões e para os administradores o acesso às ferramentas administrativas do Lync Server. Para obter detalhes sobre URLs simples, consulte [Planejamento de URLs simples no Lync Server 2013](lync-server-2013-planning-for-simple-urls.md).

O Lync Server dá suporte às seguinte três URLs simples: Meet, Dial-In e Admin. É preciso definir as URLs simples como Meet ou Dial-In, e a URL simples Admin é opcional. Os registros de DNS (Sistema de Nomes de Domínio) necessários para dar suporte às URLs simples dependem de como elas foram definidas e de você deseja dar suporte à recuperação de desastre para URLs simples.

## Opção 1 de URL simples

Na Opção 1, você cria uma nova URL de base para cada URL simples.

> [!NOTE]  
> Quando um usuário clica no link de reunião de uma URL simples, o servidor que o registro do DNS A resolve determina o software do cliente correto para iniciar. Depois que o software de cliente é iniciado, ele se comunica automaticamente com o pool em que a conferência está hospedada. Assim, os usuários são encaminhados ao servidor apropriado para o conteúdo da reunião, independente do servidor ou pool para o qual os registros de DNS A da URL resolvem.

### Opção 1 de URL simples

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>URL simples</strong></p></td>
<td><p><strong>Exemplo</strong></p></td>
</tr>
<tr class="even">
<td><p>Reunir</p></td>
<td><p>https://meet.contoso.com, https://meet.fabrikam.com e assim por diante (um para cada domínio SIP em sua organização)</p></td>
</tr>
<tr class="odd">
<td><p>Discar</p></td>
<td><p>https://dialin.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Admin</p></td>
<td><p>https://admin.contoso.com</p></td>
</tr>
</tbody>
</table>


Se você usar a Opção 1, defina o seguinte:

  - Para cada URL simples Reunir, você precisa de um registro DNS A que resolva a URL para o endereço IP do Diretor, se estiver implantado. Do contrário, ele deve resolver para o endereço IP do balanceador de carga ou do pool de Front-End. Se você não implantou um pool e está usando a implantação de servidor do Standard Edition, o registro de DNS A deve resolver para o endereço IP do servidor do Standard Edition na sua organização.
    
    Se você tiver mais de um domínio SIP em sua organização e usar essa opção, crie URLs simples Reunir para cada domínio SIP; um registro de DNS A é necessário para cada uma dessas URLs. Por exemplo, se você tem contoso.com e fabrikam.com, crie registros de DNS A para https://meet.contoso.com e https://meet.fabrikam.com.
    
    Ou então, se você tiver vários domínios SIP e deseja minimizar os registros de DNS e requisitos de certificado para essas URLs simples, use a Opção 3 descrita adiante neste tópico.

  - Para a URL simples Discar, você precisa de um registro DNS A que resolva a URL para o endereço IP do Diretor, se estiver implantado. Do contrário, ele deve resolver para o endereço IP do balanceador de carga ou do pool de Front-End. Se você não implantou um pool e está usando a implantação de servidor do Standard Edition, o registro de DNS A deve resolver para o endereço IP do servidor do Standard Edition na sua organização.

  - A URL simples Admin é apenas interna. Ela exige um registro DNS A que resolva a URL para o endereço IP do Diretor, se estiver implantado. Do contrário, ele deve resolver para o endereço IP do balanceador de carga ou do pool de Front-End. Se você não implantou um pool e está usando a implantação de servidor do Standard Edition, o registro de DNS A deve resolver para o endereço IP do servidor do Standard Edition na sua organização.

## Opção 2 de URL simples

Na Opção 2, as URLs simples Reunir, Discar e Admin têm uma URL de base comum, como lync.contoso.com. Portanto, você só precisa de um registro de DNS A para essas URLs simples, que resolve lync.contoso.com para o endereço IP de um pool do Diretor ou pool de Front-End. Se você não implantou um pool e está usando a implantação de servidor do Standard Edition, o registro de DNS A deve resolver para o endereço IP do servidor do Standard Edition na sua organização.

Observe que se você tiver mais de um domínio SIP em sua organização, deve criar URLs simples Reunir para cada domínio SIP; um registro de DNS A é necessário para cada uma dessas URLs. Neste exemplo, embora três URLs simples sejam baseadas no lync.contoso.com, uma URL simples Reunir adicional para fabrikam.com é configurada com uma URL de base diferente. Neste exemplo, você deve criar registros de DNS A para https://lync.contoso.com e https://lync.fabrikam.com. A Opção 3 de URL Simples mostra outra maneira de manipular a nomeação e os registros de DNS A, se você tiver vários domínios SIP.

### Opção 2 de URL simples

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>URL simples</strong></p></td>
<td><p><strong>Exemplo</strong></p></td>
</tr>
<tr class="even">
<td><p>Reunir</p></td>
<td><p>https://lync.contoso.com/Meet, https://lync.fabrikam.com/Meet e assim por diante (um para cada domínio SIP em sua organização)</p></td>
</tr>
<tr class="odd">
<td><p>Discar</p></td>
<td><p>https://lync.contoso.com/Dialin</p></td>
</tr>
<tr class="even">
<td><p>Admin</p></td>
<td><p>https://lync.contoso.com/Admin</p></td>
</tr>
</tbody>
</table>


## Opção 3 de URL simples

A Opção 3 é muito útil se você tem diversos domínios SIP, e deseja que eles tenham URLs simples separadas, mas deseja minimizar os registros de DNS e requisitos de certificado para essas URLs simples. Neste exemplo, você só precisa de um registro de DNS A que resolve lync.contoso.com para o endereço IP de um pool do Diretor ou pool de Front-End.

### Opção 3 de URL simples

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>URL simples</strong></p></td>
<td><p><strong>Exemplo</strong></p></td>
</tr>
<tr class="even">
<td><p>Reunir</p></td>
<td><p>https://lync.contoso.com/contosoSIPdomain/Meet</p>
<p>https://lync.contoso.com/fabrikamSIPdomain/Meet</p></td>
</tr>
<tr class="odd">
<td><p>Discar</p></td>
<td><p>https://lync.contoso.com/contosoSIPdomain/Dialin</p></td>
</tr>
<tr class="even">
<td><p>Admin</p></td>
<td><p>https://lync.contoso.com/contosoSIPdomain/Admin</p></td>
</tr>
</tbody>
</table>


## Opção de recuperação de desastres para URLs simples

Se você tiver múltiplos sites que contenham Pools de Front-Ends e seu provedor de DNS der suporte a GeoDNS, será possível configurar os registros DNS de URLs simples para que ofereçam suporte à recuperação de desastres, de modo que a funcionalidade das URLs simples continuem mesmo que um Pool de Front-Ends inteiro deixe de funcionar. Este recurso de recuperação de desastres dá suporte às URLs simples Meet e Dial-In.

Para fazer essa configuração, crie dois endereços de GeoDNS. Cada endereço contém dois registros DNS A ou CNAME que são decompostos em dois pools que são unidos para fins de recuperação de desastres. Um endereço de GeoDNS é usado para acesso interno e é decomposto no FQDN da Web interno ou endereço IP do balanceador de carga dos dois pools. O outro endereço GeoDNS é usado para acesso externo e é decomposto no FQDN da Web externo ou endereço IP do balanceador de carga dos dois pools. Veja a seguir um exemplo da URL simples Meet, usando os FQDNs dos pools:

```
    Meet-int.geolb.contoso.com
         Pool1InternalWebFQDN.contoso.com
         Pool2InternalWebFQDN.contoso.com
```
```
    Meet-ext.geolb.contoso.com
         Pool1ExternalWebFQDN.contoso.com
         Pool2ExternalWebFQDN.contoso.com
```

Em seguida, crie registros CNAME que decomponham sua URL simples Meet (como meet.contoso.com) nos dois endereços de GeoDNS.

> [!NOTE]  
> Se sua rede usar <em>grampeamento</em> (roteamento de todo o tráfego de URLs simples pelos links externos, inclusive o tráfego que vem de dentro de sua organização), será possível simplesmente configurar os endereços de GeoDNS externos e decompor sua URL simples Meet apenas nesses endereços externos.

Quando esse método é usado, é possível configurar cada endereço de GeoDNS para usar um método de round robin e distribuir solicitações nos dois pools ou para fazer a conexão principalmente com um pool (como o pool localizado geograficamente mais perto) e usar o outro pool apenas em caso de falhas de conectividade.

Você pode definir a mesma configuração para a URL simples Dial-In. Para isso, crie registros adicionais como os do exemplo anterior, substituindo `dialin` por `meet` nos registros DNS. Para a URL simples Admin, use uma das três opções listadas anteriormente nesta seção.

Depois que esta configuração é definida, é preciso usar um aplicativo de monitoramento para definir o monitoramento de HTTP para rastrear as falhas. Para acesso externo, monitore para ter certeza de que as solicitações de autodetecção HTTPS GET para o FQDN da Web externo ou endereço IP do balanceador de carga dos dois pools sejam bem-sucedidas. Por exemplo, as solicitações a seguir não devem conter nenhum cabeçalho **ACCEPT** e devem retornar **200 OK**.

```
    HTTPS GET Pool1ExternalWebFQDN.contoso.com/autodiscover/autodiscoverservice.svc/root
```
```    
    HTTPS GET Pool2ExternalWebFQDN.contoso.com/autodiscover/autodiscoverservice.svc/root
```

Para acesso interno, é preciso monitorar a porta 5061 no FQDN da Web interno ou endereço IP do balanceador de carga dos dois pools. Se alguma falha de conectividade for detectada, o VIP desses pools deverão fechar as portas 80, 443 e 444.

