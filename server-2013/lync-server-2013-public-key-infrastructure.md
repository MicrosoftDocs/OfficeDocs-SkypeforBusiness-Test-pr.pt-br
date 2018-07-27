---
title: Infraestrutura de Chave Pública para o Lync Server 2013
TOCTitle: Infraestrutura de Chave Pública para o Lync Server 2013
ms:assetid: 737c8a25-23e9-4494-ab76-5a7b729b44ca
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn481131(v=OCS.15)
ms:contentKeyID: 59679346
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Infraestrutura de Chave Pública para o Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Lync Server 2013 baseia-se em certificados para autenticação do servidor e para estabelecer uma cadeia de confiança entre clientes e servidores e entre diferentes funções do servidor. O R2 doWindows Server 2012 R2, do Windows Server 2012e do Windows Server 2008, e a Infraestrutura de chave pública (PKI) do Windows Server 2008 e do Windows Server 2003 proporcionam uma estrutura para o estabelecimento e validação dessa cadeia de confiança.

Certificados são identificações digitais. Eles identificam um servidor por nome e especificam suas propriedades. Para garantir que as informações em um certificado sejam válidas, o certificado deve ser emitido por uma AC confiável pelos clientes ou outros servidores que se conectam ao servidor. Se o servidor se conectar apenas com outros clientes e servidores de rede privada, a AC pode ser uma AC corporativa. Se o servidor interagir com entidades fora da rede privada, uma AC pública pode ser necessária.

Mesmo se as informações no certificado forem válidas, deve haver uma forma de verificar se o servidor que apresenta o certificado é de fato aquele representado pelo certificado. É nessa etapa que o PKI do Windows entrará.

Cada certificado é vinculado a uma chave pública. O servidor nomeado no certificado mantém uma chave privada correspondente que somente ele conhece. Um cliente ou servidor de conexão usa a chave pública para criptograr partes aleatórias das informações e as envia ao servidor. Se o servidor descriptografar as informações e retorná-las como texto sem formatação, a entidade de conexão pode se assegurar de que o servidor vincula a chave privada ao certificado e, portanto, o servidor é nomeado no certificado

> [!NOTE]  
> Nem todas as ACs públicas cumprem os requisitos dos certificados do Lync Server 2013. Recomendamos que consulte a lista de fornecedores certificados de AC pública para suas necessidades de certificados públicos. Para obter mais detalhes, consulte Parceiros de certificação de comunicação unificados em <a href="http://go.microsoft.com/fwlink/p/?linkid=140898">http://go.microsoft.com/fwlink/p/?LinkId=140898</a>

## Pontos de distribuição das listas de certificados revogados (CRLs)

O Lync Server 2013 requer que todos os certificados de servidor contenham um ou mais pontos de distribuição das Listas de Certificados Revogados (CRLs). Os pontos de distribuição (CDP) de CRL são locais dos quais as CRLs podem ser baixadas para verificar se o certificado não foi revogado desde sua emissão e se o certificado continua dentro do período de validade. Um ponto de distribuição de CRL pode ser encontrado nas propriedades do certificado como uma URL e é normalmente uma HTTP segura.

## Uso avançado da chave

O Lync Server 2013 requer que todos certificados de servidor suportem o uso avançado de chave (EKU) para fins de autenticação de servidor. A configuração do campo do EKU para autenticação do servidor significa que o certificado é válido para fins de autenticação de servidores. Esse EKU é essencial para MTLS. É possível ter mais de uma entrada no EKU, permitindo o uso do certificado para mais de uma finalidade.

> [!NOTE]  
> O EKU de autenticação do cliente é exigido para conexões de saída MTLS do Live Communications Server 2003 e Live Communications Server 2005, porém não é mais necessário. Entretanto, esse EKU deve estar presente nos Servidores de Borda que se conectam ao AOL por meio da conectividade a redes públicas de mensagens instantâneas.
