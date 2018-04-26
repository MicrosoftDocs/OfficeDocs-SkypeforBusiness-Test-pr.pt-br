---
title: Examinando o relatório de certificados
TOCTitle: Examinando o relatório de certificados
ms:assetid: 549cfc9b-3cc5-4483-a93c-fc0738c7f622
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558651(v=OCS.15)
ms:contentKeyID: 52057606
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Examinando o relatório de certificados

 

_**Tópico modificado em:** 2013-02-21_

O Relatório de Certificados contém todos os certificados que são necessários na implantação recomendada do Lync Server 2013. A Ferramenta de Planejamento leva em conta os nomes de entidades e os nomes alternativos de entidades que são inseridos. O texto padrão que é mantido sem edição pode representar um desafio potencial para a equipe responsável pela solicitação e emissão dos certificados. As informações do certificado também incluem informações sobre o local de onde o certificado pode ser normalmente emitido. Se a infraestrutura não tiver uma infraestrutura de chave pública interna (PKI), todos os certificados poderão ser solicitados por meio de um provedor de certificados público. Os campos EKU (Uso Estendido de Chave) e Atribuir a do relatório são muito úteis para ajudar a compreender quais devem ser a finalidade e a localização de cada certificado.

![Relatório do administrador de certificados](images/Gg558651.63a29335-d9e4-41ae-97ec-3c9d9fd30d8a(OCS.15).jpg "Relatório do administrador de certificados")

Leia com atenção e compreenda o uso e a finalidade de cada certificado na implantação. Se houver uma dúvida sobre o que faz um certificado, determine qual servidor ou serviço está se comunicando com o que. Os certificados no Lync Server 2013 são usados para duas finalidades principais:

  - MTLS (Mutual Transport Layer Security): cada um dos computadores envolvidos na comunicação apresenta um certificado que prova sua identidade para outro computador. Isso é conhecido como autenticação de servidor. A comunicação não pode começar até que cada computador confie na identidade de outro computador.

  - Criptografia: a criptografia (Secure Sockets Layer, ou SSL, e Transport Layer Security, ou TLS) é um meio fundamental para ajudar a proteger as comunicações, ajudar a garantir a privacidade e criar um sistema confiável de colaboração e comunicação.

## Consulte Também

#### Outros Recursos

[Revisando os Relatórios do Administrador no Lync Server 2013](lync-server-2013-reviewing-the-administrator-reports.md)

