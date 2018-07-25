---
title: Referência das configurações da política de conferência para Lync Server 2013
TOCTitle: Referência das configurações da política de conferência para Lync Server 2013
ms:assetid: ec8125f7-ef78-4a2b-8db0-4dd3cf5a4065
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429724(v=OCS.15)
ms:contentKeyID: 49308509
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Referência das configurações da política de conferência para Lync Server 2013

 

_**Tópico modificado em:** 2014-04-22_

As tabelas deste tópico listam todas as configurações de política de conferência que você pode especificar usando o Painel de Controle do Lync Server 2013.

## Configurações da política de organizador

A tabela a seguir lista todas as configurações de política de conferência que você pode aplicar aos organizadores de conferências. Para obter a lista mais atualizada de configurações de política de conferência, consulte o tópico de ajuda do cmdlet [Set-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy).

### Configurações da política de organizador

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuração</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Tamanho máximo das reuniões</p></td>
<td><p>Define o número máximo de participantes permitidos em uma reunião.</p></td>
</tr>
<tr class="even">
<td><p>Permitir que os participantes convidem usuários anônimos</p></td>
<td><p>Permite que os organizadores da reunião convidem usuários não autenticados para as reuniões.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar a gravação</p></td>
<td><p>Permite que os apresentadores ou participantes gravem a reunião.</p></td>
</tr>
<tr class="even">
<td><p>Permitir que os participantes federados ou anônimos gravem</p></td>
<td><p>Permite que os participantes externos e não autenticados gravem a reunião.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar áudio IP</p></td>
<td><p>Permite o uso de áudio em uma reunião.</p></td>
</tr>
<tr class="even">
<td><p>Habilitar áudio/vídeo IP</p></td>
<td><p>Permite o uso de áudio e vídeo em uma reunião.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar conferência discada PSTN</p></td>
<td><p>Permite que o usuário participe de uma reunião discando a partir do PSTN (Rede telefônica pública comutada).</p></td>
</tr>
<tr class="even">
<td><p>Permitir que os participantes anônimos façam chamadas</p></td>
<td><p>Permite que usuários não autenticados ingressem em uma reunião usando telefonia discada. Com a telefonia discada, o servidor de conferência chama o usuário e o usuário atende ao telefone para ingressar na reunião.</p></td>
</tr>
<tr class="odd">
<td><p>Resolução de vídeo máxima permitida para conferências</p></td>
<td><p>Define a resolução máxima para conferência de vídeo. Os valores válidos são <strong>640*480(VGA)</strong> e <strong>352*288(CIF)</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Habilitar colaboração de dados</p></td>
<td><p>Permite a conferência de colaboração de dados ou webconferência.</p></td>
</tr>
<tr class="odd">
<td><p>Permitir que os participantes federados ou anônimos baixem conteúdo</p></td>
<td><p>Permite que os participantes externos ou não autenticados baixem conteúdo da reunião.</p></td>
</tr>
<tr class="even">
<td><p>Permitir que os participantes transfiram arquivos</p></td>
<td><p>Permite que os participantes da reunião transfiram os arquivos durante uma reunião.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar anotações</p></td>
<td><p>Permite que os participantes criem anotações no conteúdo.</p></td>
</tr>
<tr class="even">
<td><p>Habiltar sondagens</p></td>
<td><p>Permite que os participantes da reunião realizem uma sondagem durante uma reunião.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar compartilhamento de aplicativos</p></td>
<td><p>Permite que os usuários agendem reuniões que suportam o compartilhamento de aplicativo.</p></td>
</tr>
<tr class="even">
<td><p>Permitir que os participantes assumam o controle</p></td>
<td><p>Permite que os participantes assumam o controle do aplicativo compartilhado de outro usuário.</p></td>
</tr>
<tr class="odd">
<td><p>Permitir que os participantes federados e anônimos assumam o controle</p></td>
<td><p>Permite que os participantes externos e anônimos assumam o controle do aplicativo compartilhado de outro usuário.</p>

> [!IMPORTANT]  
> Se essa configuração estiver definida como Verdadeiro e <strong>Permitir que os participantes assumam o controle</strong> estiver definida como Falso, essa configuração será substituída.

</td>
</tr>
</tbody>
</table>


## Configurações da política de participantes

A tabela a seguir lista todas as configurações de política de conferência que podem ser aplicadas aos participantes de conferência.

### Configurações da política de participantes

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuração</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Habilitar compartilhamento de aplicativos</p></td>
<td><p>Permite que os usuários agendem reuniões que suportam o compartilhamento de aplicativo.</p></td>
</tr>
<tr class="even">
<td><p>Habilitar compartilhamento de aplicativo e da área de trabalho</p></td>
<td><p>Permite aos usuários participar de reuniões que suportam o compartilhamento de aplicativos e desktop. Em uma conferência, o valor dessa configuração que se aplica ao organizador da conferência será aplicado a todos os pontos de extremidade anônimos que também participarem.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar a transferência de arquivos ponto a ponto</p></td>
<td><p>Permite que os participantes realizem transferências de arquivo ponto a ponto durante uma reunião. Uma transferência de arquivo ponto a ponto não envolve todos os participantes da reunião.</p></td>
</tr>
<tr class="even">
<td><p>Habilitar a gravação ponto a ponto</p></td>
<td><p>Permite que os participantes gravem sessões de conferência ponto a ponto.</p></td>
</tr>
</tbody>
</table>

