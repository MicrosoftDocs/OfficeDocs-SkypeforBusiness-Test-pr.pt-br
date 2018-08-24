---
title: Resumo do certificado – descoberta automática
TOCTitle: Resumo do certificado – descoberta automática
ms:assetid: 16ac96bb-882a-4141-b75c-9530637548d9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945616(v=OCS.15)
ms:contentKeyID: 52057559
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo do certificado – descoberta automática

 

_**Tópico modificado em:** 2015-03-09_

O serviço de Descoberta Automática do Lync Server 2013 é executado em servidores Diretor e pool de Front-End, e, quando publicado em DNS, pode ser usado por clientes Lync para localizar servidores e serviços de usuário. Se você estiver atualizando do Lync Server 2010 e não implantou a Mobilidade, antes de os clientes poderem usar a descoberta automática, será preciso modificar o certificado das listas de nome alternativo de assunto em qualquer Diretor e Servidor Front-End que execute o serviço de Descoberta Automática. Além disso, pode ser necessário modificar as listas de nomes alternativos de assunto nos certificados usados pelas regras de publicação de serviços de Web externa em proxies reversos.

A decisão sobre usar as listas de nomes alternativos de entidade em proxies reversos é baseada em se o serviço de Descoberta Automática foi publicado na porta 80 ou na porta 443:

  - **Publicado na porta 80**   Não são necessárias alterações de certificado se a consulta inicial ao serviço de Descoberta Automática ocorrer na porta 80. Isso porque os serviços móveis executados no Lync executarão o proxy reverso na porta 80 externamente e, então, farão a ponte a um Diretor ou Servidor Front-End na porta 8080 internamente. Para detalhes, consulte a seção "Processo de Descoberta automática inicial usando a porta 80" [Requisitos técnicos para mobilidade no Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md).

  - **Publicado na porta 443**   A lista de nomes alternativos de entidade em certificados usados pela regra de serviços de publicação da Web externa deve conter uma entrada *lyncdiscover.\<sipdomain\>* para cada domínio SIP dentro da organização.
    
    > [!IMPORTANT]  
    > Nos recomendamos fortemente usar HTTPS em vez de HTTP. O HTTPS usa certificados para criptografar dados. O HTTP não fornece criptografia e qualquer dado enviado será em texto simples.

A reemissão de certificados usando uma autoridade de certificado interna geralmente é um processo simples, mas, para os certificados públicos usados na regra de publicação do serviço da Web, adicionar várias entradas de nomes alternativos de assunto pode se tornar caro. Para contornar esse problema, damos suporte à conexão inicial da descoberta automática na porta 80, que é redirecionada, então, à porta 8080 no Diretor ou Servidor Front-End.

> [!NOTE]  
> Se a infra-estrutura do Lync Server 2013 usa certificados internos que são emitidos por uma CA (autoridade de certificação interna) e você planeja oferecer suporte a dispositivos móveis com conexão sem fio, a cadeia do certificado raiz da autoridade de certificação interna deve ser instalada nos dispositivos móveis ou você deve alterar para um certificado público na infra-estrutura do Lync Server 2013.

Este tópico descreve os nomes alernativos de assunto necessários para o Diretor, Servidor Front-End e pproxy reverso. Apenas os nomes alternativos de assunto (SAN) adicionados são referenciados. Consulte as seções de planejamento para orientação em outras entradas em certificados. Para detalhes, consulte [Cenários para o Diretor no Lync Server 2013](lync-server-2013-scenarios-for-the-director.md), [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md) e [Cenários de proxy reverso no Lync Server 2013](lync-server-2013-scenarios-for-reverse-proxy.md).

As tabelas a seguir definem as entradas SAN de Descobrimento automático para o Pool de diretores, o Pool de Front-Ends e o proxy reverso:

### Requisitos de certificado do Pool de Diretores

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Descrição</th>
<th>Entrada de nome de entidade alternativo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>URL interna do serviço de Descoberta Automática</p></td>
<td><p>SAN=lyncdiscoverinternal.<em>&lt;nome de domínio interno&gt;</em></p></td>
</tr>
<tr class="even">
<td><p>URL externa do serviço de Descoberta Automática</p></td>
<td><p>SAN=lyncdiscover.<em>&lt;sipdomain&gt;</em></p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Você designa o certificado recém atualizado com a nova entrada de SAN ao certificado padrão. Como alternativa, é possível usar SAN=*.<em>&lt;sipdomain&gt;</em>

### Requisitos de certificado do pool Front-End

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Descrição</th>
<th>Entrada de nome de entidade alternativo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>URL interna do serviço de Descoberta Automática</p></td>
<td><p>SAN=lyncdiscoverinternal.<em>&lt;nome de domínio interno&gt;</em></p></td>
</tr>
<tr class="even">
<td><p>URL externa do serviço de Descoberta Automática</p></td>
<td><p>SAN=lyncdiscover.<em>&lt;sipdomain&gt;</em></p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Você deve designar o certificado atualizado com a nova entrada de SAN ao certificado padrão. Como alternativa, é possível usar SAN=*.<em>&lt;sipdomain&gt;</em>

### Requisitos de certificado de proxy reverso (CA pública)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Descrição</th>
<th>Entrada de nome de entidade alternativo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>URL externa do serviço de Descoberta Automática</p></td>
<td><p>SAN=lyncdiscover.<em>&lt;sipdomain&gt;</em></p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Designe o certificado atualizado com a nova entrada de SAN para o Ouvinte SSL no proxy reverso.
