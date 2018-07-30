---
title: 'Lync Server 2013: Determinar requisitios de DNS'
TOCTitle: Determinar requisitios de DNS
ms:assetid: 95777017-6282-44c0-a685-f246af0501b4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398758(v=OCS.15)
ms:contentKeyID: 49307504
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Determinar requisitios de DNS para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Use o fluxograma a seguir para determinar os requisitos do Sistema de Nomes de Domínio (DNS). Alterações das atualizações cumulativas do Lync Server 2013: fevereiro de 2013 são observadas onde se aplicam.

> [!IMPORTANT]  
> O Microsoft Lync Server 2013 suporta o uso de endereçamento IPv6. Para usar endereços IPv6, é necessário também fornecer suporte para DNS IPv6 e configurar os registros AAAA (conhecido como &quot;quad-A&quot;) de host DNS. Em implantações onde IPv4 e IPv6 estão sendo usados, é melhor configurar e manter ambos os registros A de host para IPv4 e AAAA de host para IPv6. Mesmo foi realizada a transição completa da sua implantação para IPv6, os registros de host DNS IPv4 ainda podem ser necessários quando usuários externos ainda estão usando IPv4.

**Fluxograma - Como determinar os requisitos do DNS**

![Fluxograma de Requisitos DNS](images/Gg398758.175782ac-363e-408a-912f-8991bf152970(OCS.15).jpg "Fluxograma de Requisitos DNS")

> [!IMPORTANT]  
> Por padrão, o nome de um computador que não está vinculado a um domínio é um nome de host, não um nome de domínio totalmente qualificado (FQDN). O Construtor de Topologias usa FQDNs, não nomes de host. Portanto, você deve configurar um sufixo DNS no nome do computador a ser implantado como um Servidor de Borda que não está vinculado a um domínio. <strong>Use somente caracteres padrão</strong> (incluindo A-Z, a-z, 0-9 e hífens) ao atribuir FQDNs dos seus Lync Servers, Servidores de Borda e pools. Não use caracteres Unicode ou sublinhados. Caracteres que não são padrão em um FQDN geralmente não são suportados por DNSs externos e CAs públicos (ou seja, quando o FQDN deve ser atribuído ao SN no certificado). Para obter mais detalhes, consulte <a href="lync-server-2013-configure-dns-host-records.md">Configurar registros de Host DNS para Lync Server 2013</a>

## Como os clientes do Lync localizam serviços

Microsoft Lync 2010, Lync 2013 e Lync Mobile são semelhantes na forma como o cliente encontra e acessa serviços no Lync Server 2013. A notável exceção é o Aplicativo Lync Windows Store que utiliza um processo de localização de serviço diferente. Esta seção detalha dois cenários de como os clientes localizam os serviços, primeiro, o método tradicional usando uma série de registros SRV e de host, segundo, usando apenas os registros do serviço de Descoberta Automática. As atualizações cumulativas para os cliente de área de trabalho alteram o processo de localização de DNS Lync Server 2010 Para todos os clientes, o processos de consultas DNS continua até uma consulta bem sucedida ser retornada ou a lista de possíveis registros DNS ser esgotada, e o erro final é retornado ao cliente.

Para todos os clientes, **exceto** durante a consulta ao DNS do Aplicativo Lync Windows Store, os registros SRV são consultados e retornados para o cliente na ordem a seguir:

1.  lyncdiscoverinternal.*\<domain\>*    Um registro (host) do serviço de Descoberta Automática nos serviços Web internos

2.  lyncdiscover.*\<domain\>*    Um registro (host) do serviço de Descoberta Automática nos serviços Web externos

3.  \_sipinternaltls.\_tcp.*\<domínio\>*    Conexões TLS internas

4.  \_sipinternal.\_tcp.*\<domínio\>*    Conexões TCS internas (executado somente se TCP for permitido)

5.  \_sip.\_tls.*\<domínio\>*     Conexões TLS externas

6.  sipinternal.*\<domain\>*    Um registro (host) do Pool de Front-Ends ou do Diretor, que somente pode ser resolvido na rede interna

7.  sip.*\<domain\>*    Um registro (host) do Pool de Front-Ends ou do Diretor na rede interna ou no Serviço de Borda de Acesso quando o cliente for externo

8.  sipexternal.*\<domain\>*    Um registro (host) do Serviço de Borda de Acesso quando o cliente for externo

O Aplicativo Lync Windows Store altera o processo completamente, pois usa dois registros:

1.  lyncdiscoverinternal.*\<domain\>*    Um registro (host) do serviço de Descoberta Automática nos serviços Web internos

2.  lyncdiscover.*\<domain\>*    Um registro (host) do serviço de Descoberta Automática nos serviços Web externos

Não há fallback para outros tipos de registro.

A diferença entre os métodos usados pelos clientes mais recentes em comparação aos clientes mais antigos é que o serviço de Descoberta Automática está se tornando o método preferido para localizar todos os serviços.

Quando uma conexão é bem sucedida, o Serviço de Descoberta Automática retorna todas as URLs dos Serviços Web para o pool base do usuário, incluindo os URLs do Serviço de Mobilidade (conhecido como Mcx pelo diretório virtual criado para o serviço no IIS), Microsoft Lync Web App e Agendador da Web. No entanto, o URL do Serviço de Mobilidade e o URL do Serviço de Mobilidade externo estão associados com o FQDN dos serviços web. Desta maneira, independentemente do dispositivo móvel ser interno ou externo à rede, o dispositivo sempre se conecta ao Serviço de Mobilidade externamente através do proxy reverso.

Se as atualizações cumulativas do Lync Server 2013: fevereiro de 2013 tiverem sido instaladas, o Serviço de Descoberta Automática também retorna referências a Interno/UCWA, Externo/UCWA e UCWA. Essas entradas se referem ao componente Web Unified Communications Web API (UCWA). Atualmente, apenas a entrada UCWA é usada e fornece uma referência a uma URL do componente Web. UCWA é usado por clientes móveis do Lync 2013 em vez do Serviço de Mobilidade Mcx usado pelos clientes do Lync 2010 Mobile.

> [!NOTE]  
> Ao criar registros SRV, é importante lembrar que eles devem apontar para um registro A ou AAAA (se você estiver usando endereçamento IPv6) de DNS no mesmo domínio em que o registro SRV do DNS for criado. Por exemplo, se o registro SRV está em contoso.com, o registro A ou AAAA (se você estiver usando endereçamento IPv6) para o qual aponta não pode estar em fabrikam.com.


> [!TIP]
> A configuração padrão serve para direcionar todo o tráfego do cliente móvel para o site externo. É possível modificar as configurações para retornar apenas a URL interna, se isso for preferível para as suas necessidades. Com esta configuração, os usuários podem usar aplicativos móveis do Lync em seus dispositivos móveis apenas quando estiverem dentro da rede corporativa. Para definir esta configuração, use o cmdlet <STRONG>Set-CsMcxConfiguration</STRONG>.



> [!NOTE]  
> Embora aplicativos móveis também possam se conectar a outros serviços do Lync Server 2013, como o Serviço de Catálogo de Endereços, solicitações web de aplicativos móveis internos vão para o FQDN externo da web somente para o Serviço de Mobilidade. Outras solicitações de serviços, como solicitações do Catálogo de Endereços, não exigem esta configuração.

Os dispositivos móveis são compatíveis com a descoberta manual de serviços. Neste caso, cada usuário deve configurar as definições do dispositivo móvel com as URIs do Serviço de Descoberta Automática interna e externa completas, incluindo o protocolo e o caminho, da seguinte forma:

  - https:// *\<ExtPoolFQDN\>* /Autodiscover/autodiscoverservice.svc/Root para acesso externo

  - https:// *\<IntPoolFQDN\>* /AutoDiscover/AutoDiscover.svc/Root para acesso interno

Recomendamos utilizar a descoberta automática, em vez da descoberta manual. No entanto, ar configurações manuais podem ser úteis para solucionar problemas de conectividade dos dispositivos móveis.

## Configurando Split-Brain DNS com Lync Server

O split-brain DNS é conhecido por vários nomes, por exemplo, DNS dividido ou DNS de horizonte dividido. Ele descreve simplesmente uma configuração de DNS onde há duas zonas DNS com o mesmo namespace - mas uma zona de DNS serve apenas solicitações internas e a outra DNS serve apenas solicitações externas. No entanto, muitos dos DNS SRV e registros A contidos no DNS interno não serão contidos no DNS externo, e o inverso é também verdadeiro. Nos casos onde o mesmo registro DNS existe tanto no DNS interno quanto externo (p.ex., www.contoso.com), o endereço IP retornado será diferente baseado em onde (interno ou externo) a consulta iniciou.

> [!IMPORTANT]  
> No momento o Split-Brain DNS não é suportado pela mobilidade, ou mais especificamente, os registros de DNS LyncDiscover e LyncDiscoverInternal. O LyncDiscover deve ser definido em um servidor de DNS externo e o LyncDiscoverInternal deve ser definido em um servidor de DNS interno.

Nestes tópicos, o termo split-brain DNS será usado.

Se você estiver configurando um split-brain DNS, as zonas interna e externa contêm um resumo dos tipos de registros DNS necessários em cada zona. Para detalhes, consulte [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).

**DNA Interno:**

  - Contém uma zona de DNS chamada contoso.com, para a qual é autoritativo

  - A zona contoso.com interna contém:
    
      - Registros A e AAAA de DNS (se você estiver usando endereçamento IPv6) e SRV para configuração automática do cliente do Lync Server 2013 interno (opcional)
    
      - Registros A e AAAA (se você estiver usando endereçamento IPv6) ou CNAME para descoberta automática dos Serviços Web do Lync Server 2013 (opcional)
    
      - Registros A e AAAA (se você estiver usando endereçamento IPv6) para nome de pool de front end, Diretor ou nome de pool de Diretor, e todos os servidores internos executando o Lync Server 2013 na rede corporativa
    
      - Registros A e AAAA (se você estiver usando endereçamento IPv6) para a interface interna de borda de cada Lync Server 2013 e Servidor de Borda no perímetro de rede
    
      - Registros A e AAAA (se você estiver usando endereçamento IPv6) para a interface interna de cada servidor de proxy reverso no perímetro de rede (opcional para gerenciamento de proxy reverso)
    
      - Todas as interfaces de borda internas do Lync Server 2013  Servidor de Bordano perímetro de rede usam zona DNS interna para resolver consultas para contoso.com
    
      - Todos os servidores executando Lync Server 2013 e clientes executando Lync 2013 no ponto de rede corporativa para servidores DNS internos para resolver consultas para contoso.com, ou usar arquivos HOSTS para cada servidor de borda e listar registros A e AAAA (se você estiver usando endereçamento IPv6) para o servidor de próximo salto, especificamente o Diretor ou VIP Diretor, VIP do pool de front end ou servidor Standard Edition.

**DNS Externo:**

  - Contém uma zona de DNS chamada contoso.com, para a qual é autoritativo

  - A zona contoso.com externa contém:
    
      - Registros A e AAAA de DNS (se você estiver usando endereçamento IPv6) e SRV para configuração automática do cliente do Lync Server 2013 (opcional)
    
      - Registros A e AAAA (se você estiver usando endereçamento IPv6) ou CNAME para descoberta automática dos Serviços Web do Lync Server 2013 para usar com mobilidade (opcional)
    
      - Registros A e AAAA (se você estiver usando endereçamento IPv6) e SRV para a interface externa de borda de cada Lync Server 2013, Servidor de Borda ou IP virtual (VIP) de balanceador de carga de hardware no perímetro de rede
    
      - Registros A e AAAA (se você estiver usando endereçamento IPv6) para a interface externa do servidor de proxy reverso ou VIP de um pool de servidores de proxy reverso no perímetro de rede

## Configuração automática sem Split-Brain DNS

Usando o split-brain DNS for utilizado, um usuário do Lync Server 2013 que entrar internamente pode tirar vantagem da configuração automática se a zona do DNS interno contiver um registro SRV \_sipinternaltls.\_tcp para cada domínio SIP em uso. No entanto, se você não usa split-brain DNS, a configuração automática interna de clientes executando o Lync não funcionará, a menos que uma das soluções alternativas descritas posteriormente neste seção seja implementada. Isso acontece porque o Lync Server 2013 exige que o URI do SIP do usuário corresponda ao domínio do pool de Front End designado para a configuração automática. Este também era o caso com versões anteriores do Communicator.

Por exemplo, se você tem dois domínios SIP em uso, os registros de serviço (SRV) do DNS a seguir serão necessários:

  - Se um usuário entrar como bob@contoso.com, o registro SRV a seguir funcionará para a configuração automática, porque o domínio SIP do usuário (contoso.com) corresponde ao domínio do pool de Front End da configuração automática:
    
     \_sipinternaltls.\_tcp.contoso.com. 86400 IN SRV 0 0 5061 pool01.contoso.com

  - Se um usuário entrar como alice@fabrikam.com, o registro SRV do DNS a seguir funcionará para a configuração automática do segundo domínio SIP.
    
     \_sipinternaltls.\_tcp.fabrikam.com. 86400 IN SRV 0 0 5061 pool01.fabrikam.com

Se um usuário entrar como tim@litwareinc.com, o registro SRV a seguir funcionará para a configuração automática, porque o domínio SIP do usuário (contoso.com) corresponde ao domínio do pool de Front End da configuração automática:

 \_sipinternaltls.\_tcp.litwareinc.com. 86400 IN SRV 0 0 5061 pool01.fabrikam.com

Se a configuração automática for necessária para clientes executando o Lync, selecione uma das seguintes opções:

  - **Objetos de Política de Grupo**   Use objetos de Política de Grupo (GPOs) para popular os valores de servidor corretos.
    
    > [!NOTE]  
    > Esta opção não habilita a configuração automática, mas automatiza o processo de configuração manual; assim, se esta abordagem for utilizada, os registros SRV associados à configuração automática não são necessários.

  - **Comparação da zona interna**   Crie uma zona no DNS interno que corresponda à zona do DNS externo (por exemplo, contoso.com) e crie registros A ou AAAA (se você estiver usando endereçamento IPv6) de DNS correspondentes ao pool do Lync Server 2013 usado para a configuração automática. Por exemplo, se um usuário está hospedado em pool01.contoso.net mas entra no Lync como bob@contoso.com, crie uma zona do DNS interno chamada contoso.com e, dentro dela, crie um registro A ou AAAA (se você estiver usando endereçamento IPv6) de DNS para pool01.contoso.com.

  - **Zona interna exata**   Se criar uma zona inteira no DNS interno não for uma opção, você poderá criar zonas exatas (ou seja, dedicadas) que correspondam aos registros SRV necessários para a configuração automática e popular estas zonas usando o dnscmd.exe. O dnscmd.exe é necessário porque a interface do usuário do DNS não é compatível com a criação de zonas exatas. Por exemplo, se o domínio SIP for contoso.com e você tiver um pool de Front End chamado pool01 que contém dois Servidores Front End, serão necessárias as seguintes zonas exatas e registros A em seu DNS interno:
    
        dnscmd . /zoneadd _sipinternaltls._tcp.contoso.com. /dsprimary
        dnscmd . /recordadd _sipinternaltls._tcp.contoso.com. @ SRV 0 0 5061 pool01.contoso.com.
        dnscmd . /zoneadd pool01.contoso.com. /dsprimary
        dnscmd . /recordadd pool01.contoso.com. @ A 192.168.10.90
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
        dnscmd . /recordadd pool01.contoso.com. @ A 192.168.10.91 
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
    
    Se seu ambiente possui um segundo domínio SIP (por exemplo, fabrikam.com), as seguintes zonas exatas e registros A são necessários em seu DNS interno:
    
        dnscmd . /zoneadd _sipinternaltls._tcp.fabrikam.com. /dsprimary
        dnscmd . /recordadd _sipinternaltls._tcp.fabrikam.com. @ SRV 0 0 5061 pool01.fabrikam.com.
        dnscmd . /zoneadd pool01.fabrikam.com. /dsprimary
        dnscmd . /recordadd pool01.fabrikam.com. @ A 192.168.10.90
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
        dnscmd . /recordadd pool01.fabrikam.com. @ A 192.168.10.91
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>

> [!NOTE]  
> O FQDN do pool de Front End aparece duas vezes, mas com dois endereços IP diferentes. Isso acontece porque o balanceamento de carga do DNS é usado, mas se o balanceamento de carga do hardware for utilizado, existirá apenas uma única entrada do pool de Front End. Além disso, os valores do FQDN do pool de Front End mudam entre os exemplos contoso.com e fabrikam.com, mas os endereços IP permanecem os mesmos. Isso acontece porque usuários entrando a partir do domínio SIP usam o mesmo pool de Front End para a configuração automática.

Para obter detalhes, consulte o artigo do blog DMTF, "Configuração Automática do Comunicador e Split-Brain DNS," em [http://go.microsoft.com/fwlink/p/?linkId=200707](http://go.microsoft.com/fwlink/p/?linkid=200707).

> [!NOTE]  
> O conteúdo de cada blog e sua URL estão sujeitos a alterações sem aviso prévio.

## Configurar o Sistema de nomes de domínios (DNS) para Recuperação de Desastres

Para configurar o DNS para redirecionar o tráfego web do Lync Server 2013 para seus sites de recuperação de desastres e failover, é necessário usar um provedor de DNS que suporte GeoDNS. Você pode definir seus registros DNS para Web para suportar recuperação de desastres, de forma que os recursos que usam os serviços web prosseguirão mesmo se um Pool de Front-Ends inteiro cair. Esse recurso de recuperação de desastres suporta URLs simples de Descoberta Automática (URL do Lyncdiscover), de reunião e discado.

Você define e configura registros adicionais de host de DNS (A e AAAA se estiver usando IPv6) para resolução de serviços web interna e externa em seu provedor GeoDNS. Os detalhes a seguir supõem pools pareados, geograficamente dispersos e GeoDNS suportado por seu provedor com DNS round-robin ou configurado para usar o Pool1 como primário, e failover para o Pool2, em caso de perda de comunicações ou falha de hardware.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Registro GeoDNS (exemplo)</th>
<th>Registros de pool (exemplo)</th>
<th>Registros CNAME (exemplo)</th>
<th>Registros DNS (selecione uma opção)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Meet-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Alias Meet.contoso.com para Pool1InternalWebFQDN.contoso.com</p>
<p>Alias Meet.contoso.com para Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin entre pools</p>
<p>Use o primário, conecte-se ao secundário em caso de falha</p></td>
</tr>
<tr class="even">
<td><p>Meet-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Alias Meet.contoso.com para Pool1ExternalWebFQDN.contoso.com</p>
<p>Alias Meet.contoso.com para Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin entre pools</p>
<p>Use o primário, conecte-se ao secundário em caso de falha</p></td>
</tr>
<tr class="odd">
<td><p>Dialin-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Alias Dialin.contoso.com para Pool1InternalWebFQDN.contoso.com</p>
<p>Alias Dialin.contoso.com para Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin entre pools</p>
<p>Use o primário, conecte-se ao secundário em caso de falha</p></td>
</tr>
<tr class="even">
<td><p>Dialin-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Alias Dialin.contoso.com para Pool1ExternalWebFQDN.contoso.com</p>
<p>Alias Dialin.contoso.com para Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin entre pools</p>
<p>Use o primário, conecte-se ao secundário em caso de falha</p></td>
</tr>
<tr class="odd">
<td><p>Lyncdiscoverint-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Alias Lyncdiscoverinternal.contoso.com para Pool1InternalWebFQDN.contoso.com</p>
<p>Alias Lyncdiscoverinternal.contoso.com para Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin entre pools</p>
<p>Use o primário, conecte-se ao secundário em caso de falha</p></td>
</tr>
<tr class="even">
<td><p>Lyncdiscover-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Alias Lyncdiscover.contoso.com para Pool1ExternalWebFQDN.contoso.com</p>
<p>Alias Lyncdiscover.contoso.com para Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin entre pools</p>
<p>Use o primário, conecte-se ao secundário em caso de falha</p></td>
</tr>
<tr class="odd">
<td><p>Scheduler-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Alias Scheduler.contoso.com para Pool1InternalWebFQDN.contoso.com</p>
<p>Alias Scheduler.contoso.com para Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin entre pools</p>
<p>Use o primário, conecte-se ao secundário em caso de falha</p></td>
</tr>
<tr class="even">
<td><p>Scheduler-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Alias Scheduler.contoso.com para Pool1ExternalWebFQDN.contoso.com</p>
<p>Alias Scheduler.contoso.com para Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin entre pools</p>
<p>Use o primário, conecte-se ao secundário em caso de falha</p></td>
</tr>
</tbody>
</table>


## Balanceamento de carga DNS

O balanceamento de carga do DNS normalmente é implementado no nível do aplicativo. O aplicativo (por exemplo, um cliente executando o Lync), tenta se conectar a um servidor em um pool estabelecendo conexão com um dos três endereços IP resultantes da consulta do registro A e AAAA (se o endereçamento IPv6 estiver sendo usado) de DNS para o nome de domínio totalmente (FQDN) do pool.

Por exemplo, se houver três servidores front end em um pool chamado pool01.contoso.com, acontecerá o seguinte:

  - Clientes executando o DNS de consulta do Lync para pool01.contoso.com. A consulta resulta em três endereços de IP e os armazena em cache da seguinte maneira (não necessariamente nesta ordem):
    
    pool01.contoso.com      192.168.10.90
    
    pool01.contoso.com      192.168.10.91
    
    pool01.contoso.com      192.168.10.92

  - O cliente tenta estabelecer uma conexão TCP com um dos endereços IP. Em caso de falha, o cliente tenta o próximo endereço IP em cache.

  - Se a conexão TCP for bem sucedida, o cliente negocia o TLS para se conectar ao registrador principal em pool01.contoso.com.

  - Se o cliente experimenta todas as entradas em cache sem uma conexão bem sucedida, o usuário é notificado de que nenhum servidor executando o Lync Server 2013 está disponível no momento.

> [!NOTE]  
> O balanceamento de carga baseado em DNS é diferente do round robin de DNS (DNS RR), que normalmente faz referência ao balanceamento de carga confiando no DNS para fornecer uma ordem diferente de endereços IP correspondentes aos servidores em um pool. Normalmente o DNS RR só habilita a distribuição de carga, mas não habilita o failover. Por exemplo, se a conexão com um endereço IP retornado pela consulta DNS A e AAAA (se estiver usando o endereçamento IPv6), a conexão falha. Portanto, o round robin de DNS por si só é menos confiável do que o balanceamento de carga baseado em DNS. O round robin de DNS pode ser usado em conjunto com o balanceamento de carga do DNS.

O balanceamento de carga do DNS é usado para:

  - SIP entre servidores de balanceamento de carga para servidores de borda

  - Balanceamento de carga de aplicativos de Serviços de Aplicativos de Comunicações Unificadas (UCAS), como o Atendedor Automático de Conferências, Grupo de Resposta e Estacionamento de Chamada

  - Evitar novas conexões a aplicativos UCAS (também conhecido como "drenagem")

  - Balanceamento de carga de todo o tráfego cliente-para-servidor entre clientes e Servidores de Borda

O balanceamento de carga do DNS não pode ser usado para:

  - Tráfego web cliente-para-servidor para Diretor ou Servidores de Front End

Balanceamento de carga do DNS e tráfego federado:

Se vários uma consulta ao servidor DNS retornar vários registros, o serviço de Borda de Acesso sempre escolhe o registro SRV de DNS com a prioridade numérica mais baixa e peso numérico mais alto. O documento Internet Engineering Task Force "A DNS RR for specifying the location of services (DNS SRV)" <http://www.ietf.org/rfc/rfc2782.txt> especifica se existem vários registros SRV de DNS definidos, a prioridade é usada primeiro, depois o peso. Por exemplo o registro SRV de DNS A possui um peso de 20 e uma prioridade de 40 e o registro SRV de DNS B possui um peso de 10 e uma prioridade de 50. O registro SRV de DNS A com prioridade 40 será selecionado. As regras a seguir se aplicam à seleção de registros SRV de DNS:

  - A prioridade é considerada primeiro. O cliente DEVE tentar entrar em contato com o host de destino definido pelo registro SRV de DNS com a prioridade numérica mais baixa que ele puder atingir. Os destinos com a mesma prioridade DEVEM ser examinados em uma ordem definida pelo campo de peso.

  - O campo de peso especifica um peso relativo para as entradas com a mesma prioridade. Pesos superiores DEVEM ser informados com uma probabilidade maior de ser proporcionalmente selecionada. Os administradores DNS DEVEM usar Peso 0 quando não houver nenhuma seleção de servidor para fazer. Na presença de registros contendo pesos maiores que 0, os registros com peso de 0 devem ter uma chance muito pequena de serem selecionados.

Se vários registros SRV de DNS com prioridade e peso iguais forem retornados, o serviço de Borda de Acesso escolherá o primeiro registro SRV que for recebido do servidor DNS.

