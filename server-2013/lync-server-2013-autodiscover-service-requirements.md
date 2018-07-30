---
title: 'Lync Server 2013: Requisitos do serviço de descoberta automática'
TOCTitle: Requisitos do serviço de descoberta automática
ms:assetid: 0ac5dbf7-9acd-4d25-b21a-932022b8b983
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690012(v=OCS.15)
ms:contentKeyID: 49305834
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos do serviço de descoberta automática para o Lync Server 2013

 

_**Tópico modificado em:** 2013-02-25_

O serviço de Descoberta Automática do Microsoft Lync Server 2013 é executado em servidores Diretor e pool de Front-Ends e, quando publicado em DNS, pode ser usado por dispositivos móveis que executem o Lync Mobile para localizar serviços de mobilidade. Antes que os dispositivos móveis que executam o Lync Mobile possam ter vantagem sobre a descoberta automática, é preciso modificar o certificado das listas de nome alternativo de entidade em todo Diretor e Servidor Front-End que execute o serviço de Descoberta Automática. Além disso, pode ser necessário modificar as listas de nomes alternativos de entidade nos certificados usados pelas regras de publicação de serviços de Web externa em proxies reversos.

Para detalhes sobre as entradas de nomes alternativos de entidade exigidas pelos Servidores Diretores e Front-Ends e pelos proxies reversos, consulte [Requisitos técnicos para mobilidade no Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md) no Planejamento de Mobilidade.

A decisão sobre usar listas de nomes alternativos de entidade em proxies reversos é fundamentada na porta em que o serviço de Descoberta Automática foi publicado, a saber, na porta 80 ou na porta 443:

  - **Publicado na porta 80**   Não são necessárias alterações de certificado se a consulta inicial ao serviço de Descoberta Automática ocorrer na porta 80. Isso é porque os dispositivos móveis que executam o Lync acessarão o proxy reverso na porta 80 externamente e depois serão redirecionados a um Diretor ou Servidor Front-End na porta 8080 internamente. Para obter detalhes, consulte a seção “Processo inicial de descoberta automática usando a porta 80” mais adiante, neste tópico.

  - **Publicado na porta 443**   A lista de nomes alternativos de entidade em certificados usados pela regra de serviços de publicação da Web externa deve conter uma entrada *lyncdiscover.\<sipdomain\>* para cada domínio SIP dentro da organização.

A reemissão de certificados usando uma autoridade de certificado interna geralmente é um processo simples, mas para os certificados públicos usados na regra de publicação do serviço da Web, adicionar várias entradas de nomes alternativos de entidade pode se tornar caro. Para contornar esse problema, damos suporte à conexão inicial da descoberta automática na porta 80, que é redirecionada, então, à porta 8080 no Diretor ou Servidor Front-End.

Por exemplo, presuma que um cliente móvel que execute o Lync Mobile esteja configurado para entrar no Lync Server 2013 usando o recurso de descoberta automática usando HTTP para a solicitação inicial.

## Processo inicial de descoberta automática para dispositivos móveis usando a porta 80

1.  O dispositivo móvel que executa o Lync Mobile busca pelo lyncdiscover.contoso.com usando o DNS, em que um registro A existe.

2.  O DNS externo devolve o endereço IP dos serviços Web externos para o cliente.

3.  O dispositivo móvel que executa o Lync Mobile envia a solicitação http://lyncdiscover.contoso.com?sipuri=lyncUser1@contoso.com ao proxy reverso

4.  A regra de publicação da Web ligará a solicitação da porta 80 externamente até a porta 8080 internamente, o que irá, então, roteá-la para um Diretor ou Servidor Front-End.
    
    Uma vez que a solicitação é em HTTP e não HTTPS, não são necessárias modificações para o certificado na regra de publicação de serviço da Web externa para suportar o serviço de descoberta automática.

5.  O serviço de Descoberta Automática retorna os URLs do serviço de Web externa (em formato HTTPS).

6.  O dispositivo móvel que executa o Lync Mobile, pode se reconectar ao proxy reverso na porta 443 e se redirecionado pela 4443 para o serviço móvel executando o pool base do usuário.
    
    Uma vez que a consulta do HTTPS é sobre o URL dos serviços de Web externa versus o URL do serviço de descoberta automática, ela é bem-sucedida, pois o certificado já deve conter entradas de nomes alternativos de entidade para os FQDNs (nomes de domínio totalmente qualificados) de serviços Web externos.
    
    Neste cenário, não há alterações necessárias para dar suporte à mobilidade.
    
    > [!NOTE]  
    > Se o servidor Web de destino possuir um certificado que não tenha um valor de correspondência para lyncdiscover.contoso.com como um valor de lista de nome alternativo de entidade:<br />    a.   O servidor Web responde com uma “Saudação de Servidor” e nenhum certificado.<br />    b.   O dispositivo móvel que executa o Lync Mobile encerra a sessão imediatamente.<br />    Se o servidor da Web de destino tiver um certificado que inclui lyncdiscover.contoso.com como valor de lista de nome alternativo de entidade:<br />    a.   O servidor Web responde com uma “Saudação de Servidor” e um certificado.<br />    b.   O dispositivo móvel que executa o Lync Mobile valida o certificado e completa o aperto de mãos.

Para dar suporte a uma conexão inicial ao serviço de descoberta automática usando a porta 80 no seu servidor de proxy reverso, você pode criar uma regra de publicação de http semelhante a este exemplo para uma regra de publicação de proxy reverso do Forefront Threat Management Gateway 2010:

1.  Crie uma nova regra de publicação da Web (por exemplo, **Descoberta Automática do Lync Server (HTTP)** ).

2.  Em **Nome Público** , insira lyncdiscover.contoso.com.

3.  Na guia **Ponte** , selecione apenas a opção das solicitações de ponte da Porta 80 à Porta 8080.

4.  Na guia **Autenticação** , selecione **Sem autenticação** e **Cliente não pode autenticar diretamente** .

5.  Confirme as alterações e mova a regra para o topo da listra de regras do Lync (primeira na ordem de processamento).

## Mobilidade para a Implantação de domínio dividido

Um espaço de endereço SIP compartilhado, também conhecido como *domínio dividido* ou *implantação híbrida* é uma configuração na qual os usuários são implantados em uma implantação local e um ambiente online. O resultado desejado é ter um usuário, independentemente de onde seu servidor doméstico esteja localizado (local ou online), para fazer logon na implantação e ser redirecionado ao local de seu servidor doméstico. Para conseguir isso, o recurso de Descoberta automática do Microsoft Lync Server 2013 é usado para redirecionar o usuário online para a topologia online. Isso é realizado configurando o URL de Descoberta automática usando o Shell de Gerenciamento do Lync Server e os cmdlets **Get-CsHostingProvider** e **Set-CsHostingProvider** .

Será necessário coletar e registrar os seguintes atributos implantados:

  - A partir do Shell de Gerenciamento do Lync Server, digite
    
        Get-CsHostingProvider

  - Nos resultados, encontre o provedor online com o atributo **ProxyFQDN** . Por exemplo, sipfed.online.lync.com

  - Registre o valor do ProxyFQDN

  - Habilitar federação no Painel de Controle do Lync Server local, permitindo a federação com o provedor online

  - Habilite a federação para o provedor online. Por padrão, todos os usuários online são habilitados para federação de domínio e podem se comunicar com todos os domínios

  - Se você for definir domínios bloqueados e permitidos, determine os domínios que permitirá ou bloqueará explicitamente

  - Para federação online, é necessário planejar exceções de firewall, certificados e registros de host DNS (A ou AAAA, se estiver usando IPv6). Além disso, é necessário configurar as políticas de federação. Para obter detalhes, consulte [Planejamento para Federação do Servidor Lync Server e Office Communications](lync-server-2013-planning-for-lync-server-and-office-communications-server-federation.md)

