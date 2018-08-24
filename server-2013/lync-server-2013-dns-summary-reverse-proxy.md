---
title: 'Lync Server 2013: Resumo de DNS - Proxy reverso'
TOCTitle: Resumo de DNS - Proxy reverso
ms:assetid: 3073affa-4d92-4453-9974-3a82ca0c6445
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204781(v=OCS.15)
ms:contentKeyID: 49306284
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de DNS - Proxy reverso no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Você configura dois adaptadores de rede em seu proxy reverso como a seguir:

## Requisitos do Adaptador de Rede do Proxy Reverso

  - Exemplo do **Adaptador de rede 1 (interface interna)**
    
    Interface interna com 172.25.33.40 atribuído.
    
    Nenhum gateway padrão é definido.
    
    Certifique-se de que há uma rota para a rede contendo a interface interna do proxy reverso para qualquer rede que contém os servidores do Lync Server  Pool de Front-Ends (por exemplo, de 172.25.33.0 para 192.168.10.0).

  - Exemplo do **Adaptador de rede 2 (interface externa)**
    
    Um mínimo de um endereço IP público é atribuído a este adaptador de rede.
    
    O gateway é definido para o ponto do roteador ou firewall integrado em seu perímetro externo. (10.45.16.1 nos exemplos de cenário)

### Registros DNS necessários para proxy inverso

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local/TIPO/Porta</th>
<th>FQDN</th>
<th>Endereço IP</th>
<th>Mapear para/comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS/A externo</p></td>
<td><p>webext.contoso.com</p></td>
<td><p>Ouvidor atribuído para recursos publicados externamente</p></td>
<td><p>Serviços da Web externos da implantação interna. Registros adicionais podem ser definidos e criados para todos os pools e servidores únicos para qualquer domínio SIP que usará este proxy reverso e tenha os serviços da Web externos definidos.</p></td>
</tr>
<tr class="even">
<td><p>DNS/A externo</p></td>
<td><p>webdirext.contoso.com</p></td>
<td><p>Ouvidor atribuído para recursos publicados externamente</p></td>
<td><p>Serviços da Web externos para o Diretores ou pools do Diretor em sua implantação. É possível definir o máximo de Diretores possível que sejam Diretoresdistintos, nos quais podem ser associados com outros domínios SIP.</p>

> [!IMPORTANT]  
> Definindo os registros DNS e publicando o Diretores não é o pool de Front-End ou a decisão do Diretor. Você deve definir e publicar o Diretor e os serviços da Web externos do Pool de Front-Ends se estiver usando o Diretores. Tipos de tráfego específicos (para autenticação e outras utilizações) serão enviados para o Diretor primeiro, se estiver definido na topologia.

</td>
</tr>
<tr class="odd">
<td><p>DNS/A externo</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>Ouvidor atribuído para recursos publicados externamente</p></td>
<td><p>Conferência discada publicada externamente</p></td>
</tr>
<tr class="even">
<td><p>DNS/A externo</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>Ouvidor atribuído para recursos publicados externamente</p></td>
<td><p>Conferências publicadas externamente</p></td>
</tr>
<tr class="odd">
<td><p>DNS/A externo</p></td>
<td><p>officewebapps01.contoso.com</p></td>
<td><p>Assigned listener for Servidor Office Web Apps</p></td>
<td><p>Servidor Office Web Apps deployed internally or in the perimeter, and published for external client access</p></td>
</tr>
<tr class="even">
<td><p>DNS/A externo</p></td>
<td><p>lyncdiscover.contoso.com</p></td>
<td><p>Ouvidor atribuído para recursos publicados externamente</p></td>
<td><p>Registro de Descoberta do Lync Externo para Descoberta Automática publicada externamente e inclui Mobilidade, Microsoft Lync Web App e aplicativo da Web do programador</p></td>
</tr>
</tbody>
</table>

