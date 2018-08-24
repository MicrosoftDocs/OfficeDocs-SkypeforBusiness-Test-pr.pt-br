---
title: Criptografia do Lync Server 2013
TOCTitle: Criptografia do Lync Server 2013
ms:assetid: d18c74a6-385b-407b-98eb-0d525fa38fea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn481135(v=OCS.15)
ms:contentKeyID: 59679350
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criptografia do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Lync Server 2013 utiliza o TLS e MTLS para criptografar mensagens instantâneas. Todo o tráfego de servidor para servidor necessita do MTLS, independentemente de se o tráfego está restrito à rede interna ou se ultrapassa seu perímetro. O TLS é opcional, porém é fortemente recomendado entre o Servidor de Mediação e o gateway de mídia. Se o TLS for configurado neste link, o MTLS será necessário. Portanto, o gateway deve ser configurado com um certificado de uma AC considerada confiável pelo Servidor de Mediação.

Os requisitos para tráfego de cliente para cliente dependem de se o tráfego excede o firewall corporativo interno. Tráfego estritamente interno pode utilizar o TLS, caso em que mensagens instantâneas são criptografadas, ou TCP, caso em que não serão criptografadas.

A seguinte tabela resume os requisitos de protocolo para cada tipo de tráfego.

### Proteção de Tráfego

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de Tráfego</th>
<th>Protegido por</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servidor para Servidor</p></td>
<td><p>MTLS</p></td>
</tr>
<tr class="even">
<td><p>De cliente para servidor</p></td>
<td><p>TLS</p></td>
</tr>
<tr class="odd">
<td><p>Mensagens instantâneas e presença</p></td>
<td><p>TLS (se configurado para TLS)</p></td>
</tr>
<tr class="even">
<td><p>Compartilhamento de mídia de áudio, vídeo e de área de trabalho</p></td>
<td><p>SRTP</p></td>
</tr>
<tr class="odd">
<td><p>Compartilhamento de área de trabalho (sinalização)</p></td>
<td><p>TLS</p></td>
</tr>
<tr class="even">
<td><p>Webconferência</p></td>
<td><p>TLS</p></td>
</tr>
<tr class="odd">
<td><p>Download de conteúdo de reunião, download do catálogo de endereços, expansão de grupo de distribuição</p></td>
<td><p>HTTPS</p></td>
</tr>
</tbody>
</table>


## Criptografia de mídia

O tráfego de mídia é criptografado usando Secure RTP (SRTP), um perfil de protocolo de transporte em tempo real (RTP) que proporciona confidencialidade, autenticação e proteção contra ataques no tráfego do RTP. O SRTP usa uma chave de sessão criada pelo serviço de autenticação de media relay em resposta a uma autenticação bem-sucedida da solicitação do servidor (em nome dos participantes da mídia). A chave de sessão está protegida pelo nome de usuário e senha negociados apresentados ao serviço de autenticação de media relay pelo Servidores Front-End e enviados aos participantes pelo canal SIP protegido pelo TLS. A descriptografia da chave de sessão protegida com nome de usuário e senha que o serviço de media relay usou e fornecidos de maneira segura por meio de um certificado TLS do participante e do canal SIP protegido permite que os participantes façam a descriptografia do fluxo do SRTP. Além disso, o fluxo da mídia em ambas as direções entre o Servidor de Mediação e seu próximo salto interno também é criptografado usando SRTP. O fluxo de mídia em ambas as direções entre o Servidor de Mediação e o gateway de mídia não é criptografado. O Servidor de Mediação pode oferecer suporte à criptografia de um gateway de mídia, mas o gateway deve oferecer suporte ao MTLS e ao armazenamento de um certificado.

> [!NOTE]  
> Áudio/Vídeo (A/V) é suportado na nova versão do Windows Live Messenger. Se você estiver implantando uma federação A/V no Windows Live Messenger, você também deve modificar o nível de criptografia do Lync Server. Por padrão, o nível de criptografia é Exigido. Você deve alterar essa configuração para Suportado usando o Shell de Gerenciamento do Lync Server. Para obter mais informações, consulte <a href="lync-server-2013-deploying-external-user-access.md">Implantação de acesso do usuário externo no Lync Server 2013</a> na Documentação de implantação.

O tráfego de mídia de áudio e vídeo não é criptografado entre os clientes Microsoft Lync 2013 e Windows Live.

## FIPS

O Lync Server 2013 e Microsoft Exchange Server 2013 operam com suporte dos algoritmos do Federal Information Processing Standard (FIPS) 140-2 se os sistemas operacionais do Windows Server forem configurados para utilizar os algoritmos do FIPS 140-2 na criptografia do sistema. Para implantar o suporte do FIPS, você deve configurar cada servidor que executa o Lync Server 2013 para suportá-lo. Para obter detalhes sobre o uso de algoritmos em conformidade com o FIPS e sobre como implementar o suporte do FIPS, consulte o artigo 811833 da Base de dados de conhecimento da Microsoft, Efeitos de habilitar a configuração de segurança “System cryptography: Use FIPS compliant algorithms for encryption, hashing, and signing" no Windows XP e em versões posteriores do Windows em [http://go.microsoft.com/fwlink/p/?linkid=3052\&kbid=811833](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=811833). Para obter mais detalhes sobre o suporte e restrições do FIPS 140-2 do Exchange 2010, consulte SP1 do Exchange 2010 e Suporte para Algoritmos em Conformidade com o FIPS em [http://go.microsoft.com/fwlink/p/?LinkId=205335](http://go.microsoft.com/fwlink/p/?linkid=205335).

