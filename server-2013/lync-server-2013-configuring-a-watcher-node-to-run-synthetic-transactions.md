---
title: Configurando um nó inspetor para executar transações sintéticas
TOCTitle: Configurando um nó inspetor para executar transações sintéticas
ms:assetid: cedda508-8881-4079-88d5-49798f342ddf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205314(v=OCS.15)
ms:contentKeyID: 49308165
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando um nó inspetor para executar transações sintéticas

 

_**Tópico modificado em:** 2015-03-09_

Após os arquivos do agente do Centro do Sistema terem sido instalados, você deve configurar o nó do observador sozinho. As etapas realizadas para configurar um nó do observador irá variar dependendo se seu computador do nó do observador está dentro da sua rede de perímetro ou fora.

Ao configurar um nó do observador, você também deve escolher o tipo de método de autenticação a ser implantado neste nó. O Lync Server 2013 permite escolher um dos dois métodos de autenticação: Autenticação de Credencial ou Servidor Confiável. As diferenças entre estes dois métodos são destacadas na tabela a seguir:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuração</th>
<th>Descrição</th>
<th>Locais suportados</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servidor confiável</p></td>
<td><p>Usa uma certificação para personificar um servidor interno e desafios de autenticação de bypass.</p>
<p>Isto é útil para os administradores que preferem gerenciar um único certificado ao invés de várias senhas do usuário no nó do observador.</p></td>
<td><p>Dentro da empresa.</p>
<p>Observe que, com este método, o nó do observador deve estar no mesmo domínio que os pools sendo monitorados. Se o nó do observador e os pools monitorados estão em domínios diferentes, use a Autenticação de Credencial.</p></td>
</tr>
<tr class="even">
<td><p>Autenticação de Credencial</p></td>
<td><p>Armazena os nomes de usuário e senhas com segurança no Gerenciador de Credencial do Windows no nó do observador.</p>
<p>Este modo exige mais gerenciamento de senha, mas é a única opção para nós do observador fora da empresa. Estes nós do observador não podem ser tratados como um ponto de extremidade confiável para autenticação.</p></td>
<td><p>Fora da empresa.</p>
<p>Dentro da empresa.</p></td>
</tr>
</tbody>
</table>


Verifique também se o firewall tem regras de entrada para MonitoringHost.exe e PowerShell.exe. Se esses processos forem bloqueados pelo firewall, suas transações sintéticas falharão com um erro 504 (tempo limite do servidor).

