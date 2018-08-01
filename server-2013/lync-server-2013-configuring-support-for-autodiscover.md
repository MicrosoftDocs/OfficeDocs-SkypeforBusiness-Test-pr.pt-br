---
title: Configurando o suporte para a descoberta automática
TOCTitle: Configurando o suporte para a descoberta automática
ms:assetid: 3a266456-69a0-4539-ba99-d388b83799a8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945622(v=OCS.15)
ms:contentKeyID: 52057581
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o suporte para a descoberta automática

 

_**Tópico modificado em:** 2016-12-08_

Os serviços da Web do Lync Server do **serviço de Descoberta Automática** apareceu pela primeira vez na Lync Server 2010 Atualização cumulativa: Novembro de 2011. Essa atualização estava acompanhada pela versão inicial dos clientes Lync Mobile. O serviço de descoberta automática expõe os serviços de mobilidade, conhecido como serviço Mcx.

O serviço de descoberta automática age como um local único para todos os clientes solicitarem informações sobre quais serviços e recursos estão disponíveis e como contatar os serviços, seja por um nome de domínio totalmente qualificado ou por referência do localizador de recurso uniforme da Web. A descoberta automática apresenta vários recursos, e cada cliente poderá fazer solicitações com base no recurso que ele pode usar. Por exemplo, um cliente Lync 2013 de área de trabalho usará a descoberta automática para determinar os serviços Web externos, mas não usará os serviços de mobilidade (Mcx). Para definir de forma adequada e permitir que os clientes usem os recursos disponíveis a eles, os cenários que permitem que um cliente encontre e use efetivamente as entradas da descoberta automática devem ser definidos. Para usar a descoberta automática, a implantação precisa que um proxy reverso publique os serviços Web do Lync Server, que os registros do DNS estejam configurados para resolver consultas de DNS para o serviço de descoberta automática do Lync Server e serviços Web do Lync Server, e que os serviços de certificado estejam configurados adequadamente para o cenário específico.


> [!TIP]  
> Para detalhes técnicos sobre quais elementos na solicitação de descoberta automática/resposta usar, consulte <A href="lync-server-2013-understanding-autodiscover.md">Noções básicas sobre a descoberta automática no Lync Server 2013</A>.



A informação a seguir e tabela definem, por cenário, quais configurações (se alguma) você precisa implementar para fornecer um uso efetivo e completo do serviço de descoberta automática. A informação nos tópicos a seguir é específica para o Microsoft Lync Server 2013. Se você estiver procurando orientação sobre como planejar Mobilidade para Lync Server 2010, consulte <http://go.microsoft.com/fwlink/?linkid=275113>. Para implantar o serviço de Mobilidade para Lync Server 2010, consulte <http://go.microsoft.com/fwlink/?linkid=275114>

## Nesta seção

  - [Configurando o DNS para a descoberta automática](lync-server-2013-configuring-dns-for-autodiscover.md)

  - [Configurando certificados para a descoberta automática](lync-server-2013-configuring-certificates-for-autodiscover.md)

  - [Configurando um proxy reverso para a descoberta automática](lync-server-2013-configuring-a-reverse-proxy-for-autodiscover.md)

  - [Configurando a descoberta automática para implantações híbridas](lync-server-2013-configuring-autodiscover-for-hybrid-deployments.md)

