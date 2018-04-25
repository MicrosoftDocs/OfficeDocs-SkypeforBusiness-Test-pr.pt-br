---
title: Usando Opções de Linha de Comando na Configuração
TOCTitle: Usando Opções de Linha de Comando na Configuração
ms:assetid: 99878c3c-ff31-48e2-8424-580d7b07a7bf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205129(v=OCS.15)
ms:contentKeyID: 49307563
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando Opções de Linha de Comando na Configuração

 

_**Tópico modificado em:** 2016-12-08_

A linha de comando Setup.exe é usada em poucas operações na instalação do Office. Em vez de usar as opções da linha de comando Setup, você geralmente usa a Ferramenta de personalização do Office e o arquivo Config.xml file para instalação do produto e personalização de recursos.

A linha de comando Setup.exe do Office reconhece as opções de linha de comando descritas na tabela a seguir.

### Opções de linha de comando Setup do Office

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Opção de linha de comando Setup</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>/admin</p></td>
<td><p>Executa a Ferramenta de personalização do Office para criar um arquivo de personalização de Setup (arquivo .msp).</p></td>
</tr>
<tr class="even">
<td><p>/adminfile [caminho]</p></td>
<td><p>Aplica o arquivo de personalização de Setup à instalação. Você pode especificar um caminho de arquivo de personalização específico (arquivo .msp) ou a pasta onde você armazena os arquivos de personalização.</p></td>
</tr>
<tr class="odd">
<td><p>/config [caminho]</p></td>
<td><p>Especifica o arquivo Config.xml que o Setup usa durante a instalação. Use a opção /config para especificar o arquivo Config.xml personalizado para instalações do Lync 2013, por exemplo: <code>/config \\server\share\Lync15\Lync.WW\Config.xml</code></p></td>
</tr>
<tr class="even">
<td><p>/modify Lync</p></td>
<td><p>Usado com um arquivo Config.xml modificado para executar o Setup em modo de manutenção e fazer alterações à instalação existente do Office. Por exemplo, você pode usar a opção /modify para adicionar ou remover recursos do Lync.</p></td>
</tr>
<tr class="odd">
<td><p>/repair Lync</p></td>
<td><p>Executa o Setup do computador do usuário para reparar o Lync.</p></td>
</tr>
<tr class="even">
<td><p>/uninstall Lync</p></td>
<td><p>Executa o Setup para remover o Lync do computador do usuário.</p></td>
</tr>
</tbody>
</table>


Para obter detalhes sobre as opções de linha de comando setup, consulte [http://go.microsoft.com/fwlink/?linkid=267515\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=267515%26clcid=0x416).

