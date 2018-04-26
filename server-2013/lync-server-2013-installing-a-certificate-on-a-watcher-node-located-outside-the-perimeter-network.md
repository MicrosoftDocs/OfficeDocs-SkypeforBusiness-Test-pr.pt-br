---
title: Instalando um Certificado no Nó Inspetor Localizado Fora da Rede do Perímetro
TOCTitle: Instalando um Certificado no Nó Inspetor Localizado Fora da Rede do Perímetro
ms:assetid: 825c9c02-1951-4d7a-a25e-a313a85333f8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688113(v=OCS.15)
ms:contentKeyID: 49886286
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando um Certificado no Nó Inspetor Localizado Fora da Rede do Perímetro

 

_**Tópico modificado em:** 2016-12-08_

Agentes do System Center Operations Manager executando em uma rede de perímetro (como um servidor de borda Lync Server), fora da empresa (como um nó watcher externo de transação resumida) ou entre uma inicialização confiável Serviços de Domínio Active Directory, podem exigir a configuração de um Servidor de Gateway do System Center Operations Manager. Essa função do servidor permite que os agentes não tenham uma relação confiável com o Servidor de Gerenciamento Raiz para gerar alertas. Para mais detalhes, consulte "Gerenciar Servidores de Gateway em Operations Manager 2007" no System Center Operations Manager TechNet Library em [http://go.microsoft.com/fwlink/?linkid=268703\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268703%26clcid=0x416).

Se implantar um agente em um desses locais, você também deverá solicitar e configurar um certificado que habilite o nó watcher para enviar alertas a System Center Operations Manager. Para simplificar esse processo, a equipe do Operations Manager criou um conjunto de utilitários que permitem que você solicite e instale o tipo certo de certificado no computador nó watcher. Para detalhes e para saber como baixar esses utilitários, consulte o artigo de blog "Obtaining Certificates for Non-Domain Joined Agents Made Easy With Certificate Generation Wizard" (Obtendo certificados para agentes não ingressados e que não são de domínio com o Assistente de geração de certificado) em [http://go.microsoft.com/fwlink/?linkid=267421\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=267421%26clcid=0x416).

