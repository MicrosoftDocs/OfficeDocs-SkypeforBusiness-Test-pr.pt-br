---
title: 'Lync Server 2013: Solicitar certificados com antecedência (opcional)'
TOCTitle: Solicitar certificados com antecedência (opcional)
ms:assetid: 9d6d7de6-ff2a-46da-b1b7-a354c8e383e4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412733(v=OCS.15)
ms:contentKeyID: 49307600
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Solicitar certificados com antecedência (opcional) para Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Certificados são necessários para todos os servidores internos que estejam executando o Lync Server 2013, incluindo cada Enterprise EditionServidor Front-End, Servidor Standard Edition, Diretor, Servidor de Borda e Servidor de Mediação autônomo. Embora uma autoridade de certificação empresarial interna seja recomendada para servidores internos, você também pode usar uma autoridade de certificação pública. Para obter detalhes sobre requisitos de certificado e sobre o uso de uma autoridade de certificação pública, consulte [Requisitos de certificado para servidores internos no Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md), na documentação de Planejamento.

A instalação do Lync Server 2013 inclui o Assistente de Certificados, que facilita as tarefas de solicitação, atribuição e instalação de certificados durante a implantação. Se você deseja solicitar certificados antes de instalar servidores (por exemplo, para economizar tempo durante a implantação real de servidores), você pode fazê-lo utilizando um computador no qual as ferramentas administrativas do Lync Server 2013 estão instaladas ou utilizando um procedimento de solicitação de certificado definido na organização, contanto que você se certifique de que os certificados são exportáveis e contêm todos os nomes alternativos da entidade necessários. A solicitação antecipada de certificados é opcional. Se você não fizer a solicitação antecipada, será necessário solicitá-las como parte da instalação de cada servidor que requer um certificado.

Esta documentação de Implantação fornece procedimentos para usar o Assistente de Certificado para solicitar certificados como parte do processo de instalação, conforme descrito nas seções [Configurar certificados para servidores no Lync Server 2013](lync-server-2013-configure-certificates-for-servers.md), [Configurar certificados do Diretor no Lync Server 2013](lync-server-2013-configure-certificates-for-the-director.md) e [Instalar os arquivos para o Servidor de Mediação no Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md) desta documentação de Implantação. Se você solicitar certificados com antecedência, deve modificar os procedimentos de implantação de certificados nestas seções conforme o apropriado, para importar e atribuir os certificados em vez de solicitá-los no momento da implantação.

> [!NOTE]  
> O Lync Server 2013 inclui suporte para certificados SHA-256 para conexões de clientes executando os sistemas operacionais Windows Vista, Windows Server 2008, Windows Server 2008 R2 e Windows 7 e o Lync Phone Edition. Para oferecer suporte a acesso externo usando SHA-256,o certificado externo é emitido por uma AC pública usando SHA-256.
