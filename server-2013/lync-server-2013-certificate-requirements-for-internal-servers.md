---
title: 'Lync Server 2013: Requisitos de certificado para servidores internos'
TOCTitle: Requisitos de certificado para servidores internos
ms:assetid: 0444cdbd-538c-43b1-b9a1-9d7d6cf818d6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398094(v=OCS.15)
ms:contentKeyID: 49305716
ms.date: 02/18/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de certificado para servidores internos no Lync Server 2013

 

_**Tópico modificado em:** 2017-02-17_

Entre os servidores internos que executam o Lync Server e exigem certificados estão o servidor Standard Edition, o Servidor Front-End Enterprise Edition, o Servidor de Mediação e o Diretor. A tabela abaixo mostra os requisitos de certificado desses servidores. Você pode usar o Assistente de Certificado do Lync Server para solicitar esses certificados.


> [!TIP]
> Certificados curinga têm o suporte de nomes alternativos de entidade associados com os URLs simples em Pool de Front-Ends, Servidor Front-End ou Diretor. Para obter detalhes sobre suporte de certificado curinga, consulte <A href="lync-server-2013-wildcard-certificate-support.md">Suporte a certificado curinga no Lync Server 2013</A>.



Embora uma autoridade de certificação (CA) corporativa interna seja recomenda para servidores internos, também é possível usar uma CA pública. Para obter uma lista das CAs públicas que oferecem certificados que cumprem com requisitos específicos de certificados de comunicações unificadas (UC) e que trabalhem junto à Microsoft para certificar-se que elas trabalham com o Assistente de certificado do Lync Server, consulte o artigo da base de dados de conhecimento da Microsoft (ID 929395), "Parceiros de certificado de comunicações unificados," no endereço [http://go.microsoft.com/fwlink/?linkid=202834\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=202834%26clcid=0x416).

A comunicação com outros aplicativos e servidores, como um Exchange 2013, requer um certificado que é suportado por outros aplicativos e produtos. Para a versão 2013, o Lync Server 2013 e outros produtos de servidor da Microsoft, incluindo Exchange 2013 e SharePoint Server, suportam o protocolo de Autorização Aberta para autenticação e autorização de servidor para servidor. Para detalhes, consulte [Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) na documentação de Implantação ou Operações.

Para conexões de clientes executando o Sistema operacional Windows 7, Sistema operacional Windows Server 2008, Sistema operacional Windows Server 2008 R2, Sistema operacional Windows Vista e o Microsoft Lync Phone Edition, o Lync Server 2013 inclui suporte (mas não exige) para certificados assinados utilizando a função de hash de criptografia SHA-256. Para oferecer suporte ao acesso externo utilizando o SHA-256, o certificado externo é emitido por uma CA pública utilizando o SHA-256.

As tabelas a seguir mostram os requisitos de certificado por função de servidor para pools de Front-Ends e servidores Standard Edition. Todos são certificados padrão de servidores da web com chave privada e não exportáveis.

Observe que o Uso Avançado de Chave (EKU) é automaticamente configurado quando o assistente de certificado é usado para solicitar certificados.

> [!NOTE]  
> Cada nome amigável do certificado deve ser exclusivo no armazenamento do computador.

> [!NOTE]  
> Se você tiver configurado sipinternal.contoso.com ou sipexternal.contoso.com no seu DNS, será necessário adicioná-los no Nome Alternativo da Entidade do certificado.

### Certificados para o servidor Standard Edition

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificado</th>
<th>Nome da entidade/ Nome comum</th>
<th>Nome alternativo de entidade</th>
<th>Exemplo</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Padrão</p></td>
<td><p>Nome de domínio totalmente qualificado (FQDN) do pool</p></td>
<td><p>FQDN do pool e FQDN do servidor</p>
<p>Se você tiver vários domínios SIP e tiver habilitado a configuração automática do cliente, o assistente de certificados detectará e adicionará os FQDNs de cada domínio SIP aceito.</p>
<p>Se esse pool é o servidor de logon automático para clientes, e a combinação estrita do Sistema de Nome de Domínio (DNS) é exigida na política do grupo, também é preciso de entradas para o sip.sipdomain (para cada domínio de SIP que você tiver).</p></td>
<td><p>SN=se01.contoso.com; SAN=se01.contoso.com</p>
<p>Se esse pool é o servidor de logon automático para clientes, e se a combinação estrita de DNS for exigida na política do grupo, também serão precisos: SAN=sip.contoso.com; SAN=sip.fabrikam.com</p></td>
<td><p>No servidor Standard Edition, o servidor FQDN é o mesmo que o pool FQDN.</p>
<p>O assistente detecta quaisquer domínios SIP especificados durante a instalação e os adiciona automaticamente ao nome alternativo para a entidade.</p>
<p>Você também utiliza este certificado para Autenticação de Servidor para Servidor.</p></td>
</tr>
<tr class="even">
<td><p>Web interna</p></td>
<td><p>FQDN do servidor</p></td>
<td><p>Cada um dos seguintes:</p><ul><li><p>FQDN de web interna (que é o mesmo que o FQDN do servidor)</p></li><li><p>Atender a URLs simples</p></li><li><p>URL simples de discagem</p></li><li><p>Administrar URL simples</p>
<p></p></li><li><p>Ou, uma entrada curinga para os URLs simples</p></li></ul>
<p></p></td>
<td><p>SN=se01.contoso.com; SAN=se01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com; SAN=admin.contoso.com</p>
<p>Como usar um certificado curinga:</p>
<p>SN=se01.contoso.com; SAN=se01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>O FQDN da Web interna não pode ser substituído no Construtor de Topologias.</p>
<p>Se possuir vários Atender a URLs simples, devem-se incluir todos eles como nomes alternativos de entidade.</p>
<p>As entradas curinga são suportadas pelas entradas de URL simples.</p></td>
</tr>
<tr class="odd">
<td><p>Web externa</p></td>
<td><p>FQDN do servidor</p></td>
<td><p>Cada um dos seguintes:</p><ul><li><p>FQDN da web externa</p></li><li><p>URL simples de discagem</p></li><li><p>Encontre URLs simples por domínio SIP</p></li><li><p>Ou, uma entrada curinga para os URLs simples</p></li></ul></td>
<td><p>SN=se01.contoso.com; SAN=webcon01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com</p>
<p>Como usar um certificado curinga:</p>
<p>SN=se01.contoso.com; SAN=webcon01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>Se possuir vários Atender a URLs simples, devem-se incluir todos eles como nomes alternativos de entidade.</p>
<p>As entradas curinga são suportadas pelas entradas de URL simples.</p></td>
</tr>
</tbody>
</table>


### Certificados de servidor Front-End eu um pool de Front-Ends

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificado</th>
<th>Nome da entidade/ Nome comum</th>
<th>Nome alternativo de entidade</th>
<th>Exemplo</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Padrão</p></td>
<td><p>FQDN do pool</p></td>
<td><p>FQDN do pool e FQDN do servidor.</p>
<p>Se você tiver vários domínios SIP e tiver habilitado a configuração automática do cliente, o assistente de certificados detectará e adicionará os FQDNs de cada domínio SIP aceito.</p>
<p>Se esse pool for o servidor de logon automático para clientes, e a combinação estrita do DNS é exigida na política do grupo, também é preciso de entradas para o sip.sipdomain (para cada domínio de SIP que você tiver).</p></td>
<td><p>SN=eepool.contoso.com; SAN=eepool.contoso.com; SAN=ee01.contoso.com</p>
<p>Se esse pool é o servidor de logon automático para clientes, e se a combinação estrita de DNS for exigida na política do grupo, também serão precisos: SAN=sip.contoso.com; SAN=sip.fabrikam.com</p></td>
<td><p>O assistente detecta quaisquer domínios SIP especificados durante a instalação e os adiciona automaticamente ao nome alternativo para a entidade.</p>
<p>Você também utiliza este certificado para Autenticação de Servidor para Servidor.</p></td>
</tr>
<tr class="even">
<td><p>Web interna</p></td>
<td><p>FQDN do pool</p></td>
<td><p>Cada um dos seguintes:</p><ul><li><p>FQDN da Web interna (que NÃO é igual ao FQDN do servidor)</p></li><li><p>FQDN do servidor</p></li><li><p>FQDN do pool do Lync</p></li><li><p>Atender a URLs simples</p></li><li><p>URL simples de discagem</p></li><li><p>Administrar URL simples</p></li><li><p>Ou, uma entrada curinga para os URLs simples</p></li></ul>
<p></p></td>
<td><p>SN=ee01.contoso.com; SAN=ee01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com; SAN=admin.contoso.com</p>
<p>Como usar um certificado curinga:</p>
<p>SN=ee01.contoso.com; SAN=ee01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>Se possuir vários Atender a URLs simples, devem-se incluir todos eles como nomes alternativos de entidade.</p>
<p>As entradas curinga são suportadas pelas entradas de URL simples.</p></td>
</tr>
<tr class="odd">
<td><p>Web externa</p></td>
<td><p>FQDN do pool</p></td>
<td><p>Cada um dos seguintes:</p><ul><li><p>FQDN da web externa</p></li><li><p>URL simples de discagem</p></li><li><p>Administrar URL simples</p></li><li><p>Ou, uma entrada curinga para os URLs simples</p></li></ul></td>
<td><p>SN=ee01.contoso.com; SAN=webcon01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com</p>
<p>Como usar um certificado curinga:</p>
<p>SN=ee01.contoso.com; SAN=webcon01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>Se possuir vários Atender a URLs simples, devem-se incluir todos eles como nomes alternativos de entidade.</p>
<p>As entradas curinga são suportadas pelas entradas de URL simples.</p></td>
</tr>
</tbody>
</table>


### Certificados do diretor

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificado</th>
<th>Nome da entidade/ Nome comum</th>
<th>Nome alternativo de entidade</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Padrão</p></td>
<td><p>FQDN do pool de Diretores</p></td>
<td><p>FQDN do Diretor, FQDN do pool de Diretores</p>
<p>Se esse pool for o servidor de logon automático para clientes, e a combinação estrita do DNS é exigida na política do grupo, também é preciso de entradas para o sip.sipdomain (para cada domínio de SIP que você tiver).</p></td>
<td><p>SN=dir-pool.contoso.com; SAN=dir-pool.contoso.com; SAN=dir01.contoso.com</p>
<p>Se esse pool de Diretor for o servidor de logon automático para clientes, e se a combinação estrita de DNS for exigida na política do grupo, também serão precisos: SAN=sip.contoso.com; SAN=sip.fabrikam.com</p></td>
</tr>
<tr class="even">
<td><p>Web interna</p></td>
<td><p>FQDN do servidor</p></td>
<td><p>Cada um dos seguintes:</p><ul><li><p>FQDN de web interna (que é o mesmo que o FQDN do servidor)</p></li><li><p>Atender a URLs simples</p></li><li><p>URL simples de discagem</p></li><li><p>Administrar URL simples</p></li><li><p>Ou, uma entrada curinga para os URLs simples</p></li></ul>
<p></p></td>
<td><p>SN=dir01.contoso.com; SAN=dir01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com; SAN=admin.contoso.com</p>
<p>SN=dir01.contoso.com; SAN=dir01.contoso.com SAN=*.contoso.com</p></td>
</tr>
<tr class="odd">
<td><p>Web externa</p></td>
<td><p>FQDN do servidor</p></td>
<td><p>Cada um dos seguintes:</p><ul><li><p>FQDN da web externa</p></li><li><p>URL simples de discagem</p></li><li><p>Administrar URL simples</p></li><li><p>Ou, uma entrada curinga para os URLs simples</p></li></ul></td>
<td><p>O FQDN de web externa de Diretores deve ser diferente do Pool de Front-Ends ou do Servidor Front-End.</p>
<p>SN=dir01.contoso.com; SAN=directorwebcon01.contoso.com SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com</p>
<p>SN=dir01.contoso.com; SAN=directorwebcon01.contoso.com SAN=*.contoso.com</p></td>
</tr>
</tbody>
</table>


Se possuir um pool do Servidor de Mediação autônomo, os servidores presentes em cada um precisam dos certificados listados na tabela a seguir. Se um Servidor de Mediação for colocado junto aos Servidores Front-End, são suficientes os certificados listados na tabela “Certificados para Servidor Front-End no Pool do Front-End”, já apresentada neste tópico.

### Certificados para um Servidor de Mediação Autônomo

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificado</th>
<th>Nome da entidade/ Nome comum</th>
<th>Nome alternativo de entidade</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Padrão</p></td>
<td><p>FQDN do pool</p></td>
<td><p>FQDN do pool</p>
<p>FQDN do servidor membro do pool</p></td>
<td><p>SN=medsvr-pool.contoso.net; SAN=medsvr-pool.contoso.net; SAN=medsvr01.contoso.net</p></td>
</tr>
</tbody>
</table>


### Certificados para Aparelho de Filial Persistente

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificado</th>
<th>Nome da entidade/ Nome comum</th>
<th>Nome alternativo de entidade</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Padrão</p></td>
<td><p>FQDN do aplicativo</p></td>
<td><p>SIP.&lt;sipdomain&gt; (precisa de uma entrada por domínio SIP)</p></td>
<td><p>SN=sba01.contoso.net; SAN=sip.contoso.com; SAN=sip.fabrikam.com</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[Suporte a certificado curinga no Lync Server 2013](lync-server-2013-wildcard-certificate-support.md)

