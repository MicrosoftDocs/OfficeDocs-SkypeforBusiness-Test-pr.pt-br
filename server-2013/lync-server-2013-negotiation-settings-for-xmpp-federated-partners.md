---
title: 'Lync Server 2013: Configurações de negociação para parceiros de XMPP federados'
TOCTitle: Configurações de negociação para parceiros de XMPP federados
ms:assetid: ef773942-ef92-4f71-85a1-738dfebdfa00
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ552456(v=OCS.15)
ms:contentKeyID: 49308533
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurações de negociação para parceiros de XMPP federados no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

As configurações dos tipos de negociação na configuração de um Parceiro XMPP têm uma ampla variedade de combinações possíveis. Nem todas essas combinações são válidas. A tabela descrita neste tópico definirá as configurações válidas e não válidas. As configurações comuns são apresentadas na primeira tabela; a segunda tabela descreve todas as combinações possíveis. Observe que você não pode ter a *Camada de Segurança e Autenticação Simples* (SASL) **a não ser que a***Segurança na Camada de Transporte* (TLS) também esteja disponível. A SASL é enviada em um formato sem criptografia (que pode ser lido) e nunca deve ser transmitida, a não ser que seja protegida de outro modo, como por TLS.

### Métodos comuns de negociação de federação XMPP

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
<th>Segurança na Camada de Transporte (TLS)</th>
<th>Camada de Segurança e Autenticação Simples (SASL)</th>
<th>Autenticação Dialback</th>
<th>Método(s) de autenticação esperado(s)</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Obrigatório</p></td>
<td><p>Obrigatório</p></td>
<td><p>Falso</p></td>
<td><p>SASL por TLS</p></td>
<td><p>TLS e SASL obrigatórios ajuda a garantir que o stream de mensagem da SASL seja seguro. O dialback não está disponível e não pode ser usado para um método de fallback se o parceiro XMPP federado não definiu a TLS como obrigatória ou opcional.</p></td>
</tr>
<tr class="even">
<td><p>Obrigatório</p></td>
<td><p>Opcional</p></td>
<td><p>Verdadeiro</p></td>
<td><p>SASL por TLS, TLS Dialback, TCP Dialback</p></td>
<td><p>Ao exigir TLS, se o parceiro XMPP federado definiu a SASL como opcional ou obrigatória, a SASL é usada. Se a SASL não está disponível, é usado Dialback por TLS.</p></td>
</tr>
<tr class="odd">
<td><p>Opcional</p></td>
<td><p>Opcional</p></td>
<td><p>Verdadeiro</p></td>
<td><p>SASL por TLS, TLS Dialback, TCP Dialback</p></td>
<td><p>Embora sejam muito flexíveis nos métodos de negociação oferecidos, essas configurações dependem das configurações do parceiro XMPP federado. Se o parceiro tem TLS como opcional ou obrigatória, mas a SASL não é suportada, o TLS Dialback estará disponível. Se o parceiro tem TLS e SASL definidas como opcional ou obrigatórias, a seleção ideal de TLS por SASL é usada.</p></td>
</tr>
<tr class="even">
<td><p>Sem suporte</p></td>
<td><p>Sem suporte</p></td>
<td><p>Verdadeiro</p></td>
<td><p>TCP Dialback</p></td>
<td><p>Na maioria dos casos, o TCP Dialback é a única solução possível. Embora menos desejável que outras opções, ela fornece algum nível de confiança.</p></td>
</tr>
</tbody>
</table>


### Matriz de métodos de negociação de federação XMPP - Completo

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
<th>Segurança na Camada de Transporte (TLS)</th>
<th>Camada de Segurança e Autenticação Simples (SASL)</th>
<th>Autenticação Dialback</th>
<th>Método de autenticação esperado</th>
<th>Observações, avisos ou erros de configurações não válidas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Obrigatório</p></td>
<td><p>Obrigatório</p></td>
<td><p>Verdadeiro</p></td>
<td><p>SASL por TLS</p></td>
<td>

> [!WARNING]  
> O dialback não funcionará se ambas SASL e TLS forem obrigatórias.


</div></td>
</tr>
<tr class="even">
<td><p>Obrigatório</p></td>
<td><p>Obrigatório</p></td>
<td><p>Falso</p></td>
<td><p>SASL por TLS</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Opcional</p></td>
<td><p>Obrigatório</p></td>
<td><p>Verdadeiro</p></td>
<td><p>SASL por TLS, TLS Dialback, TCP Dialback</p></td>
<td>

> [!WARNING]  
> SASL requer TLS. Permitir que o TLS seja opcional pode resultar em negociações de sessão com falhas.


</div></td>
</tr>
<tr class="even">
<td><p>Opcional</p></td>
<td><p>Obrigatório</p></td>
<td><p>Falso</p></td>
<td><p>SASL por TLS</p></td>
<td>

> [!WARNING]  
> SASL requer TLS. Permitir que o TLS seja opcional pode resultar em negociações de sessão com falhas.


</div></td>
</tr>
<tr class="odd">
<td><p>Sem suporte</p></td>
<td><p>Obrigatório</p></td>
<td><p>Verdadeiro</p></td>
<td><p>TCP Dialback</p></td>
<td>

> [!WARNING]  
> SASL requer TLS. Permitir que o TLS seja opcional pode resultar em negociações de sessão com falhas.


</div></td>
</tr>
<tr class="even">
<td><p>Sem suporte</p></td>
<td><p>Obrigatório</p></td>
<td><p>Falso</p></td>
<td>

> [!WARNING]  
> Configuração não válida


</div></td>
<td>

> [!WARNING]  
> Como a SASL requer TLS, e a TLS não está disponível, a combinação SASL/TLS não é possível. O TCP Dialback é definido como falso e não pode ser usado.


</div></td>
</tr>
<tr class="odd">
<td><p>Obrigatório</p></td>
<td><p>Opcional</p></td>
<td><p>Verdadeiro</p></td>
<td><p>SASL por TLS, TLS Dialback</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Obrigatório</p></td>
<td><p>Opcional</p></td>
<td><p>Falso</p></td>
<td><p>SASL por TLS</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Opcional</p></td>
<td><p>Opcional</p></td>
<td><p>Verdadeiro</p></td>
<td><p>SASL por TLS, TLS Dialback, TCP Dialback</p></td>
<td>

> [!WARNING]  
> SASL requer TLS. Permitir que o TLS seja opcional pode resultar em negociações de sessão com falhas.


</div></td>
</tr>
<tr class="even">
<td><p>Opcional</p></td>
<td><p>Opcional</p></td>
<td><p>Falso</p></td>
<td><p>SASL por TLS</p></td>
<td>

> [!WARNING]  
> SASL requer TLS. Permitir que o TLS seja opcional pode resultar em negociações de sessão com falhas.


</div></td>
</tr>
<tr class="odd">
<td><p>Sem suporte</p></td>
<td><p>Opcional</p></td>
<td><p>Verdadeiro</p></td>
<td><p>TCP Dialback</p></td>
<td>

> [!WARNING]  
> SASL requer TLS. Permitir que o TLS seja opcional pode resultar em negociações de sessão com falhas.


</div></td>
</tr>
<tr class="even">
<td><p>Sem suporte</p></td>
<td><p>Opcional</p></td>
<td><p>Falso</p></td>
<td>

> [!WARNING]  
> Configuração não válida


</div></td>
<td>

> [!WARNING]  
> SASL requer TLS. Permitir que o TLS seja opcional pode resultar em negociações de sessão com falhas.


</div></td>
</tr>
<tr class="odd">
<td><p>Obrigatório</p></td>
<td><p>Sem suporte</p></td>
<td><p>Verdadeiro</p></td>
<td><p>TLS Dialback</p></td>
<td><p>A configuração permite TLS Dialback.</p></td>
</tr>
<tr class="even">
<td><p>Obrigatório</p></td>
<td><p>Sem suporte</p></td>
<td><p>Falso</p></td>
<td><p>Configuração não válida</p></td>
<td>

> [!WARNING]  
> SASL ou Dialback devem estar ativados.


</div></td>
</tr>
<tr class="odd">
<td><p>Opcional</p></td>
<td><p>Sem suporte</p></td>
<td><p>Verdadeiro</p></td>
<td><p>TLS Dialback, TCP Dialback</p></td>
<td><p>Dependendo das opções de negociação do outro ponto de extremidade, TCP ou TLS Dialback serão aceitos.</p></td>
</tr>
<tr class="even">
<td><p>Opcional</p></td>
<td><p>Sem suporte</p></td>
<td><p>Falso</p></td>
<td><p>Configuração não válida</p></td>
<td>

> [!WARNING]  
> SASL ou Dialback devem estar ativados.


</div></td>
</tr>
<tr class="odd">
<td><p>Sem suporte</p></td>
<td><p>Sem suporte</p></td>
<td><p>Verdadeiro</p></td>
<td><p>TCP Dialback</p></td>
<td><p>TCP Dialback é o único método de negociação disponível</p></td>
</tr>
<tr class="even">
<td><p>Sem suporte</p></td>
<td><p>Sem suporte</p></td>
<td><p>Falso</p></td>
<td><p>Configuração não válida</p></td>
<td>

> [!WARNING]  
> SASL ou Dialback devem estar ativados.


</div></td>
</tr>
</tbody>
</table>

