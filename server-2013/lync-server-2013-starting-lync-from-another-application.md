---
title: Iniciando o Lync a partir de outro aplicativo
TOCTitle: Iniciando o Lync a partir de outro aplicativo
ms:assetid: 573b30b1-6590-4b24-8e96-a41be57cb0ef
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398376(v=OCS.15)
ms:contentKeyID: 52057608
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Iniciando o Lync a partir de outro aplicativo

 

_**Tópico modificado em:** 2015-03-09_

É possível usar parâmetros de linha de comando para iniciar o Lync 2013 rapidamente. Por exemplo, se um usuário clicar no número de telefone em outro aplicativo, o aplicativo iniciará uma instância do Lync 2013 e uma chamada para esse número.

O Lync 2013 também pode reconhecer uma lista delimitada por ponto-e-vírgula de nomes de contato para a conferência de grupo.

Se o Lync 2013 estiver configurado para entrar automaticamente quando é iniciado, inicie o Lync 2013 com os parâmetros de linha de comando para abrir a janela principal do Lync. Se o Lync não estiver configurado para entrar automaticamente quando for iniciado, a janela será aberta.

A tabela a seguir mostra os parâmetros disponíveis.

### Parâmetros de linha de comando do Lync 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Extensão</th>
<th>Formato de dados</th>
<th>Ação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>tel:</p></td>
<td><p>tel URI</p></td>
<td><p>Abre a janela de conversação para uma chamada de áudio mas não disca o número especificado.</p></td>
</tr>
<tr class="even">
<td><p>callto:</p></td>
<td><p>tel:, sip:, ou tel URI digitável</p></td>
<td><p>Abre a janela de conversação para uma chamada de áudio mas não disca o número especificado.</p></td>
</tr>
<tr class="odd">
<td><p>sip:</p></td>
<td><p>URI do SIP</p></td>
<td><p>Abre a janela de conversação com o URI (Uniform Resource Identifier) do SIP na lista de participantes.</p></td>
</tr>
<tr class="even">
<td><p>Sips:</p></td>
<td><p>URI do SIP</p></td>
<td><p>Se o Lync 2013 estiver configurado para usar o protocolo TLS, ele funcionará exatamente como o sip:. Se o TLS não estiver sendo usado, uma caixa de diálogo será exibida informando ao usuário que um nível maior de segurança é necessário.</p></td>
</tr>
<tr class="odd">
<td><p>conf:</p></td>
<td><p>URI do SIP da conferência para ingresso</p></td>
<td><p>Quando o URI é self, ele cria uma instância do foco e exibe somente a lista de participantes. Caso contrário, ele exibe a lista de participantes, mas não envia INVITE.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>im:</p></td>
<td><p>URI do SIP</p></td>
<td><p>Exibe uma janela de conversação de somente mensagens instantâneas com o URI do SIP. Aceita vários URIs de SIP especificados dentro de colchetes angulares (&lt;&gt;) sem nenhum separador.</p>
<pre><code>im:&lt;sip:user1@host&gt;&lt;sip:user2@host&gt;</code></pre></td>
</tr>
</tbody>
</table>


A tabela a seguir fornece exemplos destes parâmetros de linha de comando.

### Exemplos de parâmetros de linha de comando

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Instância</th>
<th>Resultados</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Tel:+14255550101</p></td>
<td><p>Abre uma exibição somente de telefone com +14255550101.</p></td>
</tr>
<tr class="even">
<td><p>Callto:tel:+ 14255550101</p></td>
<td><p>Abre uma exibição somente de telefone com +14255550101.</p></td>
</tr>
<tr class="odd">
<td><p>Callto:sip:kazuto@litwareinc.com</p></td>
<td><p>Abre uma exibição somente de telefone com kazuto@litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p>sip:kazuto@litwareinc.com</p></td>
<td><p>Abre uma janela de conversação com kazuto@litwareinc.com.</p></td>
</tr>
<tr class="odd">
<td><p>conf:sip:https://meet.contoso.com/kazuto/7322994</p></td>
<td><p>Abre uma janela de conversação e exibe as opções para ingressar em áudio de reunião.</p></td>
</tr>
</tbody>
</table>

