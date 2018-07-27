---
title: Planejando para a descoberta automática
TOCTitle: Planejando para a descoberta automática
ms:assetid: 51f1ff94-1d64-4e6d-a878-b86fa07edc2d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945628(v=OCS.15)
ms:contentKeyID: 52057605
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejando para a descoberta automática

 

_**Tópico modificado em:** 2013-02-16_

A Descoberta Automática foi lançada para o Lync Server na atualização cumulativa para Lync Server 2010: novembro de 2011. A principal finalidade dessa implementação inicial da Descoberta Automática foi fornecer maneiras do Lync Mobile localizar o serviço de Mobilidade (Mcx). O serviço de Descoberta Automática no Lync Server 2013 agora é um serviço usado pelos clientes para localizar os servidos dos servidores e dos usuários. O serviço de Descoberta Automática do Microsoft Lync Server 2013 é executado no Diretores e no Servidores Front-End.


> [!TIP]
> Para obter mais compreensão técnica sobre a Descoberta Automática e o que é comunicado aos clientes, consulte <A href="lync-server-2013-understanding-autodiscover.md">Noções básicas sobre a descoberta automática no Lync Server 2013</A>.<BR>A Mobilidade ainda é um cenário distinto e os serviços de Mobilidade ainda necessitam de algum planejamento especial. Para obter detalhes adicionais, consulte <A href="lync-server-2013-planning-for-mobility.md">Planejamento para mobilidade no Lync Server 2013</A>.



Quando a Descoberta Automática foi lançada no Lync Server 2010, haviam compromissos que precisavam ser criados para implementar um serviço que exigia possíveis alterações de certificado para as implantações do servidor existentes. A Descoberta Automática pode ser usada por meio da porta TCP 443 para HTTPS ou da porta TCP 80 para HTTP. Se a decisão foi tomada para usar HTTPS, os certificados nos proxies reversos, Diretores e Servidores Front-End precisam ser reemitidos para acomodar os registros DNS do `lyncdiscover.<domain>` e do `lyncdiscoverinternal.<domain>` necessários. Se a decisão foi usar HTTP, a reemissão dos certificados pode ser evitada usando os registros CNAME DNS (ou alias) para usar nomes existentes nos certificados. Usar HTTP significa que as comunicações iniciais estão sem criptografia.

Como o Lync Server 2013 usa a Descoberta Automática para todos os clientes, o cenário principal é usar HTTPS exclusivamente e criar certificados com lyncdiscover.\<domain\> como parte da configuração de proxies reversos, Diretores e Servidores Front-End. Se você estiver implementando a Descoberta Automática em uma implantação atualizada do Lync Server 2010, é possível usar HTTP para evitar reemitir certificados. As orientações para ambos os cenários são fornecidas nas seguintes seções.

> [!IMPORTANT]  
> A lista de nomes alternativos de entidade nos certificados usados por meio da regra de publicação de serviços Web externos deve conter uma entrada <em>lyncdiscover.&lt;sipdomain&gt;</em> para cada domínio SIP na sua organização. Para obter detalhes sobre as entradas de nome alternativo do assunto necessários para os Diretores, Servidores Front-End e proxies reversos, consulte <a href="lync-server-2013-certificate-summary-autodiscover.md">Resumo do certificado – descoberta automática</a>.

## Nesta seção

  - [Resumo do certificado – descoberta automática](lync-server-2013-certificate-summary-autodiscover.md)

  - [Resumo da porta – descoberta automática no Lync Server 2013](lync-server-2013-port-summary-autodiscover.md)

  - [Resumo do DNS – descoberta automática no Lync Server 2013](lync-server-2013-dns-summary-autodiscover.md)

  - [Domínio híbrido e divido – descoberta automática](lync-server-2013-hybrid-and-split-domain-autodiscover.md)

