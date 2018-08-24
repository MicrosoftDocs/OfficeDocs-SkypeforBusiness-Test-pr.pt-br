---
title: "Lync Server 2013: Configurar federação p/ um provedor de conferência de áudio"
TOCTitle: Configurar federação para um provedor de conferência de áudio
ms:assetid: 08dedcce-0d3f-45da-8282-cf2634a41665
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn510996(v=OCS.15)
ms:contentKeyID: 59954256
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar federação para um provedor de conferência de áudio no Lync Server 2013

 

_**Tópico modificado em:** 2014-07-24_

Se você pretende usar um Provedor de Conferência de Áudio (ACP) em sua implantação híbrida (Lync Server no local com Lync Online), será necessário configurar a federação entre sua implantação do Lync no local e o parceiro ACP como um Servidor Parceiro Permitido. É possível configurar a federação adicionando o domínio do parceiro ACP e o servidor de Borda (também conhecido como Proxy de Acesso) à lista de Domínios de Federação para sua implantação no local. Seu parceiro ACP precisará adicionar o FQDN de seu pool de Servidor de Borda no local à lista de domínios de federação permitidos. Entre em contato com o provedor ACP para obter detalhes adicionais. Seu parceiro ACP precisará adicionar o FQDN de seu pool de Servidor de Borda no local à lista de domínios de federação permitidos.

  - **Adição do domínio ACP e do servidor de borda como um domínio federado permitido**
    
    Para adicionar o domínio ACP como um Servidor de Parceiro Permitido (Domínio de Federação permitido), siga as etapas em [Configurar suprote para domínios externos permitidos no Lync Server 2013](lync-server-2013-configure-support-for-allowed-external-domains.md). Para o Servidor de borda, adicione o FQDN do servidor de borda do parceiro ACP. Pode ser necessário entrar em contato com seu parceiro ACP para obter o FQDN do Servidor de Borda, que também pode ser mencionado pelo ACP como Proxy de Acesso.

  - **Forneça o FQDN do seu pool do servidor de borda ao parceiro ACP**
    
    O parceiro ACP precisa configurar a federação para adicionar seu domínio no local como um Servidor Parceiro Permitido, adicionando o FQDN de seu pool de Servidor de Borda como um domínio de Federação permitido.

