---
title: Noções básicas sobre a descoberta automática no Lync Server 2013
TOCTitle: Noções básicas sobre a descoberta automática no Lync Server 2013
ms:assetid: d70a15b7-750b-4e0f-9a7f-0254d6d486c3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945654(v=OCS.15)
ms:contentKeyID: 52057737
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Noções básicas sobre a descoberta automática no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O serviço de Descoberta Automática do Lync Server 2013 é um recurso que foi introduzido originalmente em Microsoft Lync Server 2010 como parte da atualização cumulativa de Lync Server 2010 em novembro de 2011. Além de correções, essa atualização cumulativa implementou o suporte a clientes do Lync Mobile e Lync 2013.

No Lync Server 2013, o serviço de serviço de Descoberta Automática é uma parte integral da operação de clientes móveis internos e externos, e a Descoberta Automática também se estende a novos clientes, como o recentemente introduzido Aplicativo Lync Windows Store para o Windows 8. A Descoberta Automática também é utilizada pelos clientes de desktop do Lync 2013. A Descoberta Automática é reconhecida no Lync Server pelos registros requeridos de sistema de nome de domínio (DNS) **lyncdiscover.\<domínio\>** e **lyncdiscoverinternal.\<domínio\>**. Adicionalmente, versões mais recentes do Lync 2010 e do cliente de desktop Lync 2013 preferem Descoberta Automática em relação aos registros SRV de sistema de nome de domínio (DNS), usando registros SRV de DNS somente se lyncdiscover.\<domínio\> ou lyncdiscoverinternal.\<domínio\> não responder ou não se resolver. O Aplicativo Lync Windows Store para Windows 8 e Lync Mobile utiliza exclusivamente Descoberta Automática e não fará referência aos tradicionais registros SRV de DNS.

No Lync Server 2013, a Descoberta Automática é expandida para comunicar ao cliente quais elementos, recursos e métodos de comunicação estão disponíveis a ele. As informações são comunicadas por uma requisição enviada pelo cliente e os serviços Web do Lync Server respondem com uma resposta claramente definida, que nomeia o que está disponível para o cliente e como contatar esses recursos no formato de documento de resposta de Descoberta Automática.

O melhor modo de entender o documento de resposta de Descoberta Automática, incluindo como os serviços Web informam clientes sobre recursos por meio desse documento, é analisar minuciosamentecada linha e defini-la em uma resposta comum a partir do documento de resposta de Descoberta Automática do serviço Web Lync.

> [!NOTE]  
> Nos detalhes a seguir, o usuário já realizou a autenticação com o servidor inicial ao responder uma solicitação de autenticação.

> [!NOTE]  
> O serviço Web de Descoberta Automática do Lync é definido no <strong>Microsoft Office Protocols</strong> na seção <strong>Especificações em aberto</strong> da biblioteca do <strong>Microsoft Developer Network</strong> (MSDN). Para detalhes, consulte o documento de especificação completo, &quot;Protocolo de serviço Web de Descoberta Automática do Lync&quot;, em: <a href="http://go.microsoft.com/fwlink/?linkid=273839" class="uri">http://go.microsoft.com/fwlink/?linkid=273839</a>. Para detalhes sobre autenticação, consulte &quot;Protocolo de serviço Web de autenticação OC&quot; em <a href="http://go.microsoft.com/fwlink/?linkid=279015" class="uri">http://go.microsoft.com/fwlink/?linkid=279015</a>.

## A resposta de Descoberta Automática do serviço Web do Lync Server

A resposta retornada quando a solicitação de Descoberta Automática é enviada é a mesma para um cliente interno ou externo. Alguns parâmetros capazes de reconhecer a localização podem mudar. Se uma solicitação de cliente é recebida, mas o verdadeiro pool é diferente daquele que foi contatado, o pool inicial do usuário será configurado para esse usuário. Um colega cuja conta está em um pool diferente, mas realizando login pelo mesmo escritório, obteria uma resposta sutilmente diferente. a resposta indica o Servidor Front-End ou o Pool de Front-Ends correto para esse usuário.

Um exemplo de documento de resposta de Descoberta Automática:

    <AutodiscoverResponse xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" AccessLocation="External">
       <User>
          <SipServerInternalAccess fqdn="pool01.contoso.com" port="5061"/>
          <SipClientInternalAccess fqdn=" pool01.contoso.com" port="443"/>
          <SipServerExternalAccess fqdn="sip.contoso.com" port="5061"/>
          <SipClientExternalAccess fqdn="sip.contoso.com " port="443"/>
          <Link token ="External/Autodiscover" href="https://webexternal.contoso.com/Autodiscover/AutodiscoverService.svc/root"/>
          <Link token="Internal/Autodiscover" href="https://webinternal.contoso.net/Autodiscover/AutodiscoverService.svc/root"/>
          <Link token="External/AuthBroker" href="https://webexternal.contoso.com/Reach/sip.svc"/>
          <Link token="Internal/AuthBroker" href="https://webinternal.contoso.net/Reach/sip.svc"/>
          <Link token="External/WebScheduler" href="https://webexternal.contoso.com/Scheduler"/>
          <Link token="Internal/WebScheduler" href="https://webinternal.contoso.net/Scheduler"/>
          <Link token="External/Mcx" href="https://webexternal.contoso.com/Mcx/McxService.svc"/>
          <Link token="Internal/Mcx" href="https://webexternal.contoso.net/Mcx/McxService.svc"/>
          <Link token="External/Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>
          <Link token="Internal/Ucwa" href="https://webinternal.contoso.net/ucwa/v1/applications"/>
          <Link token="Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>
          <Link token="External/XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>
          <Link token="Internal/XFrame" href="https://webinternal.contoso.net/Autodiscover/XFrame/XFrame.html"/>
          <Link token="XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>
          <Link token="Self" href="https://webexternal.contoso.net/Autodiscover/AutodiscoverService.svc/root/user"/>
       </User>
    </AutodiscoverResponse>

## Detalhes do documento de resposta de Descoberta Automática

O documento de resposta de Descoberta Automática pode permanecer em qualquer um de dois formatos. O formato padrão é uma Notação de Objeto JavaScript (JSON). O outro formato é um documento de linguagem de marcação extensível (XML). O XML é usado para este exemplo. A solicitação e resposta são previsíveis porque o documento tem um esquema definido que determina o formato. A linha no documento que descreve o esquema usado é a primeira linha na solicitação ou resposta:

    <AutodiscoverResponse xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" AccessLocation="External">

A definição de **AccessLocation=”External”** indica que a solicitação foi feita por um usuário externo.

```
    <SipServerInternalAccess fqdn="pool01.contoso.com" port="5061"/>
```
```
    <SipServerExternalAccess fqdn="sip.contoso.com" port="5061"/>
```

SipServerInternalAccess e SipServerExternalAccess atualmente não estão sendo usadas. Essas entradas estão reservadas para uso futuro.

```
    <SipClientInternalAccess fqdn=" pool01.contoso.com" port="443"/>
```
```
    <SipClientExternalAccess fqdn="sip.contoso.com " port="443"/>
```

SipClientInternalAccess e SipClientExternalAccess descrevem o nome de domínio totalmente qualificado e porta que um cliente interno ou externo utilizará para acessar o servidor SIP definido. O cliente desktop Lync e o Aplicativo Lync Windows Store utilizam essas entradas, segundo sua localização (interna ou externa) para encontrar o Diretor ou Servidor Front-End.

```
    <Link token="Internal/Autodiscover" href="https://webinternal.contoso.net/Autodiscover/AutodiscoverService.svc/root"/>
```
```
    <Link token ="External/Autodiscover" href="https://webexternal.contoso.com/Autodiscover/AutodiscoverService.svc/root"/>
```

As referências de `Autodiscover` contêm os pontos de entrada de serviço para o serviço de Descoberta Automática. O atributo de token contém o nome do serviço, e a href é uma URL que define para o cliente onde o serviço pode ser encontrado. Clientes em uma rede externa utilizam o `External/Autodiscover`. O serviço de Descoberta Automática está instalado como parte do processo de implantação. O `Internal/Autodiscover` não é usado atualmente, e está reservado para uso futuro.

```
    <Link token="Internal/AuthBroker" href="https://webinternal.contoso.net/Reach/sip.svc"/>
```
```

    <Link token="External/AuthBroker" href="https://webexternal.contoso.com/Reach/sip.svc"/>
```

As referências de `AuthBroker` contêm os pontos de entrada de serviço para o serviço de corretor de autenticação interno e externo, neste caso, sip.svc. O atributo de token contém o nome do serviço, e a href é uma URL que define para o cliente onde o serviço pode ser encontrado. Clientes em uma rede interna utilizam o `Internal/AuthBroker`. Clientes em uma rede externa utilizam o `External/AuthBroker`. O serviço AuthBroker está instalado como parte do processo de implantação dos seus serviços Web de implantação Lync Server 2013 internos.

```
    <Link token="Internal/WebScheduler" href="https://webinternal.contoso.net/Scheduler"/>
```
```
    <Link token="External/WebScheduler" href="https://webexternal.contoso.com/Scheduler"/>
```

O token `WebScheduler` faz referência às URLs para acesso pelo cliente ao agendamento via Web para conferências Lync Server. Atualmente, o `External/WebScheduler` é utilizado. O WebScheduler é instalado como parte do processo de implantação dos seus serviços Web de implantação internos Lync Server 2013.

```
    <Link token="Internal/Mcx" href="https://webexternal.contoso.net/Mcx/McxService.svc"/>
```
```
    <Link token="External/Mcx" href="https://webexternal.contoso.com/Mcx/McxService.svc"/>
```

`Internal/Mcx` e `External/Mcx` são as localizações dos Mobility services, introduzidos na atualização cumulativa para Lync Server 2010 em novembro de 2011. Essas referências continuarão a ser usadas por Lync 2010 Mobile em todos os dispositivos suportados. O serviço Mcx é instalado como parte do processo de implantação dos seus serviços Web de implantação Lync Server 2013 internos.

```
    <Link token="Internal/Ucwa" href="https://webinternal.contoso.net/ucwa/v1/applications"/>
```
```
    <Link token="External/Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>

    <Link token="Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>
```

**Interno/Ucwa**, **Externo/Ucwa** e **Ucwa** oferecem um meio para que os clientes acessem a Unified Communications Web Application Programming Interface (UCWA API, ou simplesmente UCWA). Os diretórios virtuais `Internal/Ucwa` e `External/Ucwa` são pontos de acesso reservados para aprimoramentos futuros, e não são utilizados. O diretório virtual `Ucwa` é utilizado para Microsoft Lync Mobile (introduzido com o Lync Server 2013) em todos os dispositivos suportados. O serviço UCWA é instalado como parte do processo de implantação dos seus serviços Web de implantação Lync Server 2013 internos.

```
    <Link token="Internal/XFrame" href="https://webinternal.contoso.net/Autodiscover/XFrame/XFrame.html"/>
```
```
    <Link token="External/XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>
```
```
    <Link token="XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>
```

`Internal/XFrame`, **External/XFrame** e **XFrame** fornecem acesso a aplicativos de servidor baseados em UCWA. O XFrame é instalado como parte do processo de implantação dos seus serviços Web de implantação Lync Server 2013 internos.

    <Link token="Self" href="https://webexternal.contoso.net/Autodiscover/AutodiscoverService.svc/root/user"/>

O token `Self` faz referência a informações específicas do cliente (tipo de resposta do usuário) que está fazendo a solicitação. O cliente que fez essa solicitação era externo e essa referência de Descoberta Automática é para a porção de usuário do serviço de Descoberta Automática.

## Consulte Também

#### Outros Recursos

[Requisitos do sistema para componentes de acesso de usuário externo para Lync Server 2013](lync-server-2013-system-requirements-for-external-user-access-components.md)  
[Planejando para a descoberta automática](lync-server-2013-planning-for-autodiscover.md)

