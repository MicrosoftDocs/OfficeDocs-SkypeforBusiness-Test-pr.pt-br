---
title: Resumo de Certificado - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)
TOCTitle: Resumo de Certificado - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)
ms:assetid: b059a34e-99df-40af-91fe-fe2aa52841f6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ618374(v=OCS.15)
ms:contentKeyID: 49307831
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de Certificado - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)

 

_**Tópico modificado em:** 2015-03-09_

Os requisitos de certificado para ativar e estabelecer comunicações com mensagens extensíveis e parceiros de protocolo de presença (XMPP) requerem o registro adicional dos seus domínios XMPP. O registro incluído no certificado como um nome alternativo da entidade (SAN) será o domínio que pode participar das comunicações XMPP. O domínio pode ser o domínio no nível raiz (por exemplo, contoso.com) se você deseja habilitar XMPP para o domínio inteiro ou pode ser determinados domínios filho (por exemplo, corp.contoso.com, finance.contoso.com) se estiver habilitando XMPP para um subconjunto de usuários.

## Resumo do certificado para o protocolo Extensible Messaging and Presence


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente</th>
<th>Nome da entidade</th>
<th>Nomes alternativos de entidade (SAN)/Ordem</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Atribuir ao Serviço de Borda de Acesso da Servidor de Borda ou do Pool de borda</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>webcon.contoso.com</p>
<p>sip.contoso.com</p>
<p>sip.fabrikam.com</p>
<p>contoso.com</p></td>
<td><p>As três primeiras entradas SAN são as entradas SAN normais para um Servidor de Borda completo. A contoso.com é a entrada exigida para federação com o parceiro XMPP no nível de domínio raiz. Essa entrada permitirá XMPP em todos os domínios com o sufixo contoso.com.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Tarefas

[Exemplo de configuração de XMPP no Lync Server 2013 – federação XMPP com Google Talk](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  

#### Conceitos

[Planejar certificados do Servidor de Borda no Lync Server 2013](lync-server-2013-plan-for-edge-server-certificates.md)  

#### Outros Recursos

[Configurar certificados de Borda para Lync Server 2013](lync-server-2013-set-up-edge-certificates.md)  
[Request-CsCertificate](https://docs.microsoft.com/en-us/powershell/module/skype/Request-CsCertificate)  
[Set-CsCertificate](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate)

