---
title: 'Lync Server 2013: Planejar certificados do Servidor de Borda'
TOCTitle: Planejar certificados do Servidor de Borda
ms:assetid: f1dfe220-2398-4ac8-ba4c-206c8c0cbc50
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413010(v=OCS.15)
ms:contentKeyID: 49308561
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejar certificados do Servidor de Borda no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-05_

A criação de certificados para Borda é simplificada no Lync Server 2013.

**Fluxograma de Certificados para Servidor de Borda**

![Fluxograma de Certificados](images/Gg413010.a5fc20db-7ced-4364-b577-6a709a8367cd(OCS.15).jpg "Fluxograma de Certificados")

Criar um certificado público único, certificar-se de ter uma chave privada de exportação definida para o certificado e atribui-lo às seguintes interfaces externas do Servidor de Borda usando o assistente de certificado:

> [!IMPORTANT]  
> Os certificados curinga não têm suporte no Lync Server, exceto quando usados para resumir as URLs simples por meio do proxy reverso. Você deve definir os SANs (nome alternativo da entidade) distintos de cada nome de domínio SIP, Serviço de Borda de Webconferência, Serviço de Borda A/V e domínio XMPP oferecidos por sua implantação.

> [!NOTE]  
> Introduzidos no Lync Server 2013, os certificados de teste de Autenticação de Áudio/Vídeo anteriores ao tempo de expiração do certificado atual exigem planejamento adicional. Em vez de um certificado com várias finalidades para a interface externa da Borda, será necessário dois certificados: um atribuído ao Serviço de Borda de Acesso e ao Serviço de Borda de Webconferência e um para o Serviço de Borda A/V. Para obter informações adicionais, consulte <a href="lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate">Adaptando Certificados AV e OAuth Usando no Lync Server 2013 -Roll in Set-CsCertificate</a>

> [!IMPORTANT]  
> No caso de um pool de Servidores de Borda, você exporta o certificado com a chave privada para cada Servidor de Borda e atribui o certificado a cada serviço do Servidor de Borda. Faça o mesmo para o certificado do Servidor de Borda interno, exportando o certificado com a chave privada e o atribuindo a cada interface interna da Borda.

  - Certificar-se de ter uma chave privada de exportação atribuída ao certificado

  - Serviço de Borda de Acesso (referida como **Borda de acesso SIP externa** no assistente de certificado)

  - Serviço de Borda de Webconferência (referida como **Borda de conferência da Web externa** no assistente de certificado)

  - Serviço de Autenticação A/V (referido como **Borda A/V externa** no assistente de certificado)

Criar um certificado interno único com chave privada de exportação, copiá-lo e atribui-lo a cada uma das interfaces internas do Servidor de Borda:

  - Servidor de Borda (referido como **Borda interna** no assistente de certificado)

> [!IMPORTANT]  
> É possível usar certificados separados e distintos para cada serviço do Servidor de Borda. Um bom motivo para escolher certificados separados é se deseja usar o novo recurso de certificados do Serviço de Borda A/V. No caso deste recurso, é recomendado dissociar o certificado do Serviço de Borda A/V do Serviço de Borda de Acesso e do Serviço de Borda de Webconferência. Se optar por solicitar, adquirir e atribuir certificados separados para cada serviço, você deve solicitar que a chave privada possa ser exportada para o Serviço de Borda A/V (novamente, este é o serviço de Autenticação A/V atual) e atribuir o mesmo certificado à interface externa da Borda A/V em cada Servidor de Borda.

## Consulte Também

#### Tarefas

[Adaptando Certificados AV e OAuth Usando no Lync Server 2013 -Roll in Set-CsCertificate](lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate)  

#### Conceitos

[Alterações no Lync Server 2013 que afetam o planejamento do Servidor de Borda](lync-server-2013-changes-in-lync-server-that-affect-edge-server-planning.md)

