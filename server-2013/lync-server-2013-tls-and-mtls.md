---
title: TLS e MTLS para o Lync Server 2013
TOCTitle: TLS e MTLS para o Lync Server 2013
ms:assetid: b32a5b85-fc82-42dc-a9b2-96400f8cd2b8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn481133(v=OCS.15)
ms:contentKeyID: 59679348
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# TLS e MTLS para o Lync Server 2013

 

_**Tópico modificado em:** 2013-11-07_

Os protocolos Transport Layer Security (TLS) e Mutual Transport Layer Security (MTLS) fornecem comunicações criptografadas e autenticação de ponto de extremidade na Internet. O Microsoft Lync Server 2013 usa esses dois protocolos para criar uma rede de servidores confiáveis e para garantir que todas as comunicações nessa rede sejam criptografadas. Todas as comunicações SIP entre servidores ocorrem no MTLS. As comunicações SIP entre o cliente e o servidor ocorrem no TLS.

O TLS permite que os usuários, por meio de seu software cliente, autentiquem os servidores do Lync Server 2013 aos quais se conectam. Em uma conexão TLS, o cliente solicita um certificado válido do servidor. Para ser válido, o certificado deve ser emitido por uma AC considerada confiável pelo cliente, e o nome DNS do servidor deve corresponder ao nome DNS no certificado. Se o certificado for válido, o cliente usa a chave pública no certificado para criptografar as chaves de criptografia simétricas a serem utilizadas na comunicação, assim, apenas o proprietário original do certificado pode utilizar sua chave privada para descriptografar os conteúdos de comunicação. A conexão resultante é confiável e, a partir desse momento, não será desafiada por nenhum outro servidor ou cliente confiável. Nesse contexto, a Secure Sockets Layer (SSL), conforme utilizada com serviços os Web, pode ser associada ao protocolo baseado em TLS.

Conexões de servidor para servidor baseiam-se em MTLS para autenticação mútua. Em uma conexão MTLS, o servidor que cria a mensagem e o servidor que a recebe trocam certificados mutuamente a partir de uma AC confiável. Os certificados comprovam a identidade de cada servidor ao outro. Nas implantações do Lync Server 2013, os certificados emitidos pela AC corporativa que estão dentro do período de validade e não foram revogados pela AC emissora são automaticamente considerados válidos por todos os clientes e servidores internos, pois todos os membros de um domínio do Active Directory confiam em uma AC Corporativa naquele domínio. Em cenários federados, a AC emissora deve ser confiável por ambos os parceiros federados. Cada parceiro pode usar uma AC diferente, se desejado, contanto que a AC também seja considerada confiável pelo outro parceiro. Essa confiabilidade é mais facilmente assegurada pelos Servidores de Borda que possuem o certificado da AC raiz dos parceiros em suas ACs raiz confiáveis ou pelo uso de uma AC de terceiro que seja considerada confiável pelas duas partes.

O TLS e MTLS ajudam a evitar a espionagem e ataques a intermediários. Em um ataque a intermediários, o invasor redireciona as comunicações entre duas entidades de rede por meio do computador do invasor, sem o conhecimento das partes. O TLS e a especificação do Lync Server 2013 de servidores confiáveis (apenas aqueles especificados no Construtor de Topologias) diminuem parcialmente o risco de um ataque a intermediários na camada de aplicação, utilizando uma criptografia fim a fim juntamente com a criptografia de chave pública entre dois pontos de extremidade, e um invasor terá que possuir um certificado válido e confiável com a chave privada correspondente, emitida no nome do serviço com o qual o cliente está comunicando, para descriptograr a comunicação. Em última análise, entretanto, você deve cumprir as práticas recomendadas de segurança em sua infraestrutura de rede (no caso de um DNS corporativo). O Lync Server 2013 supõe que o servidor DNS seja confiável, da mesma forma que os controladores de domínio e catálogos globais, porém o DNS não proporciona um nível de proteção contra ataques ao servidor DNS impedindo que o servidor invasor responda com êxito a uma solicitação por meio do nome falsificado.

A seguinte imagem mostra em alto nível como o Lync Server 2013 utiliza o MTLS para criar uma rede de servidores confiáveis.

**Conexões confiáveis em uma rede do Lync Server**

![Uso do MTLS](images/Dn481133.437749da-c372-4f0d-ac72-ccfd5191696b(OCS.15).jpg "Uso do MTLS")

