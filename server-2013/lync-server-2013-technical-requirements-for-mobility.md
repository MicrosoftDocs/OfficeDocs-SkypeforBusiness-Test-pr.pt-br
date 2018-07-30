---
title: 'Lync Server 2013: Requisitos técnicos para mobilidade'
TOCTitle: Requisitos técnicos para mobilidade
ms:assetid: 831be681-4de0-4e42-b04f-8879ca4dcd23
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690030(v=OCS.15)
ms:contentKeyID: 49307301
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos técnicos para mobilidade no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Os usuários de dispositivos móveis encontram vários cenários de aplicativos de dispositivos móveis que requerem planejamento especial. Por exemplo, um usuário pode começar a usar um aplicativo de celular enquanto estiver fora do trabalho por meio da rede 3G, alternar para rede Wi-Fi corporativa ao chegar no trabalho e alternar para 3G novamente quando deixar o edifício. Você precisa planejar seu ambiente para suportar tais transições da rede e garantir uma experiência de usuário consistente. Esta seção descreve os requisitos de infraestrutura que você precisa atender para oferecer suporte a aplicativos de celular e a descoberta automática de recursos de dispositivos móveis.

> [!NOTE]  
> Embora os aplicativos de celular também possam conectar-se a outros serviços do Lync Server 2013, o requisito para enviar todas as solicitações Web de aplicativos de celular para o mesmo FQDN externo da Web aplica-se somente ao Mobility Service do Lync Server 2013. Outros serviços de mobilidade não exigem essa configuração.

A exigência de afinidade com cookie em balanceadores de carga de hardware é reduzida dramaticamente e você pode substituir a afinidade com TCP se estiver usando o Lync Mobile oferecido com Lync Server 2013. A afinidade com cookie ainda pode ser usada, mas os serviços Web não a requerem mais.

> [!IMPORTANT]  
> Todo o tráfego de Serviço de Mobilidade passa pelo proxy reverso, independentemente do ponto de origem - interno ou externo. Em caso de utilizar proxy reverso único, múltiplos proxies reversos ou ainda um dispositivo oferecendo a função de proxy reverso, pode surgir um problema em que o tráfego interno esteja saindo por uma interface e tentando ingressar imediatamente na mesma interface. Isso frequentemente leva a uma violação de regra de segurança conhecida como Spoof de pacote TCP ou apenas spoofing. O <em>Hairpin</em> (saída e reentrada imediata de um pacote ou série de pacotes) deve ser permitido para que a mobilidade possa funcionar. Uma solução para esse problema é usar um proxy reverso separado do firewall (a regra para prevenção de spoofing deve ser sempre obrigatória no firewall, para fins de segurança). O hairpin pode ocorrer na interface externa do proxy reverso em vez da interface externa do firewall. Você detecta o spoofing no firewall, cancela temporariamente a regra no proxy reverso permitindo assim o hairpin que a mobilidade requer.<br />Use os registros de host DNS ou CNAME para definir o proxy reverso para o comportamento de hairpin - não o firewall - se possível.

Lync Server 2013 suporta serviços de mobilidade para clientes móveis Lync 2010 Mobile e Lync 2013. Ambos os clientes utilizam o serviço de Descoberta Automática Lync Server 2013 para encontrar o seu ponto de entrada de mobilidade, mas diferem no serviço de mobilidade que cada um usa. Lync 2010 Mobile usa o Mobility Service conhecido como *Mcx* , introduzido com a atualização cumulativa de novembro de 2011 para o Lync Server 2010. Clientes móveis Lync 2013 utilizam o Unified Communications Web API, ou *UCWA* , como seu provedor de serviços de mobilidade.

## Configuração do DNA Interno e Externo

O Mobility Services Mcx (introduzido com a atualização cumulativa de novembro de 2011 para o Lync Server 2010) e o UCWA (introduzido com a atualização cumulativa de fevereiro de 2013 para o Lync Server 2013) utilizam DNS do mesmo modo.

Quando você usa a Descoberta Automática, os dispositivos móveis usam o DNS para localizar os recursos. Durante a pesquisa de DNS, ocorre uma tentativa de conexão ao FQDN (nome de domínio totalmente qualificado) que está associado ao registro DNS interno(lyncdiscoverinternal.*\<internal domain name\>*). Se não for possível estabelecer a conexão por meio do registro DNS interno, ocorre uma tentativa de conexão por meio do registro DNS externo (lyncdiscover. *\<sipdomain\>*). Um dispositivo móvel interno à rede se conecta à URL interna do serviço Descoberta Automática e um dispositivo móvel externo à rede se conecta à URL externa do serviço de Descoberta Automática. As solicitações de Descoberta Automática externas ocorrem por meio do proxy reverso. O serviço de Descoberta Automática do Lync Server 2013 retorna todas as URLs de serviços Web para o pool inicial do usuário, incluindo URLs do Mobility Service (Mcx e UWCA). No entanto, as URLs interna e externa do Mobility Service estão associadas ao FQDN de serviços Web externos. Portanto, independentemente de um dispositivo móvel ser interno ou externo à rede, o dispositivo sempre conecta-se ao serviço de dispositivos móveis do Lync Server 2013 externamente através do proxy reverso.

> [!NOTE]  
> É importante compreender que a implantação pode ser composta por diversos namespaces diferentes para uso interno e externo. O nome de seu domínio SIP pode ser diferente do nome de domínio da implantação interna. Por exemplo, seu domínio SIP pode ser <strong>contoso.com</strong>, enquanto a implantação interna pode ser <strong>contoso.net</strong>. Os usuários que fizerem logon no Lync Server usarão o nome do domínio SIP, como <strong>john@contoso.com</strong>. Ao lidar com os serviços Web externos (definidos em Construtor de Topologias como <strong>Serviços Web externos</strong>), o nome de domínio e o nome de domínio SIP serão consistentes conforme as definições do DNS. Ao lidar com serviços Web internos (definidos em Construtor de Topologias como <strong>Serviços Web internos</strong>), o nome padrão dos serviços Web internos será o FQDN do Servidor Front-End, Pool de Front-Ends, Diretor ou Pool de diretores. É possível substituir o nome dos serviços Web internos. Use o nome de domínio interno (não o nome de domínio SIP) para os serviços Web internos e defina o registro do host DNS A (ou, para IPv6, AAAA) para refletir o nome substituído. Por exemplo, o FQDN padrão dos serviços Web internos pode ser <strong>pool01.contoso.net</strong>. O FQDN substituído dos serviços Web internos pode ser <strong>webpool.contoso.net</strong>. A definição dos serviços Web dessa forma garante que a localidade interna e externa dos serviços seja observada, em vez da localidade do usuário.<br />No entanto, como os serviços Web são definidos em Construtor de Topologias e é possível substituir o nome dos serviços Web internos, é possível definir os serviços web internos com qualquer nome de domínio, inclusive o nome de domínio SIP escolhido; isso contanto que o nome dos serviços Web resultante, o certificado que o valida e os registros DNS que o define sejam consistentes. A resolução do nome para o endereço IP é determinada pelos registros do host DNS e por um namespace consistente.<br />Para as finalidades deste tópico e dos exemplos, o nome de domínio interno é usado para ilustrar a topologia e as definições de DNS.

O diagrama a seguir ilustra o fluxo de solicitações Web de aplicativos de dispositivos móveis para o serviço de mobilidade e o serviço Descoberta Automática ao usar configuração DNS interna e externa.

**Fluxo do serviço de mobilidade usando a Descoberta Automática**

![Fluxo de solicitação de mobilidade](images/Hh690030.cdb96424-96f2-4abf-88d7-1d32d1010ffd(OCS.15).jpg "Fluxo de solicitação de mobilidade")

> [!NOTE]  
> O diagrama ilustra os serviços Web genéricos. Um diretório virtual nomeado Mobilidade representa os serviços de mobilidade Mcx e/ou UCWA. Se você não aplicou as atualizações cumulativas de fevereiro de 2013 para o Lync Server 2013, você talvez não tenha o diretório virtual Ucwa definido em seus serviços Web internos e externos. Você terá um diretório virtual Descoberta Automática, e poderá ter também um diretório virtual Mcx.<br />A Descoberta Automática e a descoberta de serviços funcionam do mesmo modo, independentemente da tecnologia de serviços de mobilidade que você tenha implantado.

Para oferecer suporte aos usuários de dispositivos móveis de dentro e fora da rede corporativa, os FQDNs de web interno e externo devem atender a alguns pré-requisitos. Além disso, talvez você precise atender a outros requisitos, dependendo dos recursos escolhidos para implementar:

  - Novos registros DNS CNAME ou A (host, se IPv6, AAAA) para descoberta automática.

  - Nova regra de firewall, se você quiser dar suporte a notificações de envio pela sua rede Wi-Fi.

  - Nomes alternativos da entidade em certificados de servidor interno e certificados de proxy reverso para descoberta automática.

  - Afinidade da fonte das alterações na configuração do balanceador de carga de hardware Servidor Front-End.

A sua topologia deve atender aos seguintes requisitos para dar suporte ao Serviço de Mobility e ao Serviço de Descoberta Automática:

  - O FQDN interno da web do Pool de Front-Ends deve ser diferente do FQDN externo da web do Pool de Front-Ends.

  - O FQDN interno da web somente deve resolver à rede corporativa e ser acessível a partir dela .

  - O FQDN interno da web somente deve resolver à Internet e ser acessível nela.

  - Para um usuário que está dentro da rede corporativa, a URL do Serviço de Mobility deverá ser direcionada ao FQDN externo da web. Este requisito é para o Serviço de Mobility e se aplica somente a esta URL.

  - Para um usuário que está fora da rede corporativa, a solicitação deve ir ao FQDN externo da web do Pool de Front-Ends ou da Diretor.

Se você oferecer suporte à descoberta automática, será necessário criar os seguintes registros DNS para cada domínio SIP:

  - Um registro DNS interno para suportar usuários móveis que se conectam de dentro da rede da organização.

  - Um registro DNS externo ou público para suportar usuários móveis que se conectam pela Internet.

A URL de descoberta automática interna não deve ser endereçável a partir de fora da rede. A URL de descoberta automática externa não deve ser endereçável de dentro da rede. No entanto, se você não puder atender este requisito para a URL externa, a funcionalidade do cliente móvel provavelmente não será afetada, porque a primeira tentativa sempre é com a URL interna.

Os registros DNS podem ser registros CNAME ou registros A (host, se IPv6, AAAA).

> [!NOTE]  
> Os clientes de dispositivo móvel não suportam vários certificados de SSL (Secure Sockets Layer) de domínios diferentes. Portanto, não há redirecionamento CNAME para diferentes domínios por HTTPS. Por exemplo, um registro DNS CNAME para lyncdiscover.contoso.com que redireciona a um endereço de director.contoso.net não é suportado por HTTPS. Na topologia, um cliente de dispositivo móvel precisa usar HTTP para a primeira solicitação, para que o redirecionamento de CNAME seja resolvido por HTTP. As solicitações subseqüentes usam HTTPS. Para oferecer suporte a esse cenário, você precisará configurar o proxy inverso com uma regra de publicação na web para a porta 80 (HTTP). Para obter detalhes, consulte &quot;Para criar uma regra de publicação na web para a porta 80&quot; in <a href="lync-server-2013-configuring-the-reverse-proxy-for-mobility.md">Configurando o proxy reverso para mobilidade no Lync Server 2013</a>.<br />O redirecionamento de CNAME ao mesmo domínio é suportado por HTTPS. Nesse caso, o certificado do domínio de destino cobre o domínio de origem.

Para detalhes sobre os registros de DNS requeridos para o seu cenário, consulte [Resumo do DNS – descoberta automática no Lync Server 2013](lync-server-2013-dns-summary-autodiscover.md).

## Requisitos de Firewall e de Porta

Se você oferece suporte a notificações de envio e deseja que os dispositivos móveis da Apple recebam notificações de envio pela rede Wi-Fi, é preciso abrir a porta 5223 em sua rede corporativa Wi-Fi. A porta 5223 é uma porta TCP de saída usada pelo APNS (Apple Push Notification Service). O dispositivo móvel inicia a conexão. Para obter mais detalhes, consulte [http://support.apple.com/kb/TS1629](http://support.apple.com/kb/ts1629?viewlocale=pt_br).


> [!WARNING]
> Um dispositivo Apple utilizando o cliente móvel Lync 2013 não requer notificações push.



Observe que se um usuário estiver hospedado em um SBA (Aparelho de Filial Persistente), as seguintes portas são necessárias:

  - UcwaSipExternalListeningPort requer a porta 5088

  - UcwaSipPrimaryListeningPort requer a portar 5089

Para detalhes e orientações adicionais sobre requisitos de porta e protocolo para Descoberta Automática, consulte [Resumo da porta – descoberta automática no Lync Server 2013](lync-server-2013-port-summary-autodiscover.md).

## Requisitos de Certificação

Se oferecer suporte à descoberta automática para clientes móveis Lync, será necessário modificar as listas de nome alternativo da entidade em certificados para oferecer suporte a conexões seguras de clientes móveis. Você precisa solicitar e atribuir novos certificados, adicionando as entradas de nome alternativo da entidade descritas nesta seção para cada Servidor Front-End e Diretor que executa o serviço Descoberta automática. Recomendamos também modificar as listas de nomes alternativos da entidade de certificados para os proxies reversos. Será necessário adicionar entradas de nome alternativo da entidade para cada domínio SIP na organização.

Reemitir certificados usando uma autoridade de certificação interna é normalmente um processo simples, mas a adição de várias entradas de nome alternativo da entidade a certificados públicos usados pelo proxy reverso pode ser cara. Se você tiver muitos domínios SIP, tornando a adição de nomes alternativos da entidade muito cara, é possível configurar o proxy reverso para fazer a solicitação inicial do Serviço de Descoberta Automática pela porta 80 usando HTTP, em vez da porta 443 usando HTTPS (configuração padrão). A solicitação é redirecionada para a porta 8080 no Diretor ou Pool de Front-Ends. Quando você publicar a solicitação inicial do Serviço de Descoberta Automática na porta 80, você não precisará alterar certificados de proxy reverso, pois a solicitação usa HTTP em vez de HTTPS. Essa abordagem é aceita, mas não recomendada.

## Requisitos de IIS (Serviços de Informações da Internet)

Recomendamos o uso do IIS 7.5, IIS 8.0 ou IIS 8.5 para mobilidade. O instalador do serviço de mobilidade define sinalizadores em ASP.NET para melhorar o desempenho. O IIS 7.5 é instalado por padrão no Windows Server 2008 R2, enquanto o IIS 8.0 é instalado no Windows Server 2012 e o and IIS 8.5 é instalado no Windows Server 2012 R2. O instalador do serviço de mobilidade altera automaticamente as configurações do ASP.NET.

## Requisitos do Balanceador de Carga de Hardware

No balanceador de carga por hardware que suporta o Pool de Front-Ends, os IPs virtuais (VIPs) dos serviços Web para o tráfego de serviços Web devem ser configurados para origem. A afinidade com a origem ajuda a garantir que várias conexões de um único cliente sejam enviadas a um servidor para manter o estado da sessão. Para obter detalhes sobre os requisitos de afinidade, consulte [Requisitos de balanceamento de carga para Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

Se planeja oferecer suporte a clientes móveis do Lync através da rede Wi-Fi interna, é necessário configurar VIPS de serviços web internos para origem conforme descrito para os VIPs de serviços web externos. Nessa situação, você não deve usar a afinidade source\_addr (ou TCP) para os VIPs de serviços web internos no balanceador de carga de hardware. Para obter mais detalhes, consulte [Requisitos de balanceamento de carga para Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

## Requisitos de Proxy reverso

Se oferecer suporte à descoberta automática para clientes de dispositivos móveis Lync, será necessário atualizar a regra de publicação da seguinte maneira:

  - Se decidir atualizar as listas de nomes alternativos da entidade em certificados de proxy reverso e usar HTTPS na solicitação inicial do serviço Descoberta Automática, será necessário atualizar a regra de publicação na Web para lyncdiscover. *\<sipdomain\>*. Geralmente, essa regra é combinada à regra de publicação para a URL externa de serviços Web no Pool de Front-Ends.

  - Se decidir usar HTTP na solicitação inicial do serviço de Descoberta Automática, para que não seja necessário atualizar a lista de nomes alternativos da entidade em certificados de proxy reverso, será necessário criar uma nova regra de publicação na Web para a porta HTTP/TCP 80, caso ainda não exista nenhuma regra. Se a regra para HTTP/TCP 80 já existir, atualize-a para incluir a entrada *\<sipdomain\>*.

