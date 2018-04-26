---
title: Verificar as comunicações com um cliente Lync Online
TOCTitle: Verificar as comunicações com um cliente Lync Online
ms:assetid: c8287b15-e1bb-4b26-8354-0ec90b2fcfe7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202189(v=OCS.15)
ms:contentKeyID: 49308066
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar as comunicações com um cliente Lync Online

 

_**Tópico modificado em:** 2016-12-08_

Para permitir que os usuários do Lync em sua organização se comuniquem com os usuários de um cliente do Microsoft Lync Online 2010, é necessário completar as seguintes etapas:

  - Atender a todos os pré-requisitos. Isso incluir a implantação de seus servidores internos e de borda, habilitação do suporte á federação para sua organização e configuração das contas de usuário. Para obter detalhes, consulte [Pré-requisitos para federação com um cliente do Lync Online](lync-server-2013-prerequisites-for-federating-with-a-lync-online-customer.md).

  - Configurar o suporte ao acesso de domínio em sua implantação interna. Isso inclui a criação de uma entrada de provedor de host e configuração de sua implantação para permitir o acesso a partir do domínio do cliente do Lync Online. Para obter detalhes, consulte [Configurar o suporte de federação para um domínio do Lync Online](lync-server-2013-configure-federation-support-for-a-lync-online-domain.md).

  - Configurar suas contas de usuário para suportar a federação. Para obter detalhes, consulte [Configurar o acesso de usuário para federação com um cliente do Lync Online](lync-server-2013-configure-user-access-for-federation-with-a-lync-online-customer.md).

Após a conclusão de todas estas etapas e o administrador do cliente do Lync Online 2010 concluir toda a configuração de seu serviço online para suporte de federação com sua organização, verifique as comunicações testando as comunicações entre um usuário interno na sua organização e um usuário do cliente do Lync Online. Se a comunicação não tiver êxito, use a Ferramenta de Registro em Log do seu Servidor de Borda para capturar log e rastrear arquivos de forma a resolver o problema. Para obter detalhes sobre o uso da Ferramenta de Registro em Log, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md) na documentação de Operações. Para obter detalhes sobre a Ferramenta de Registro em Log, consulte a documentação da Ferramenta de Registro em Log do Lync Server 2010 na Biblioteca TechNet em [http://go.microsoft.com/fwlink/?linkid=199265\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=199265%26clcid=0x416).

