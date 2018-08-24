---
title: Verificar configurações
TOCTitle: Verificar configurações
ms:assetid: 41dbf91c-f2e1-4b9a-88cf-959575558cf2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204848(v=OCS.15)
ms:contentKeyID: 49306520
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar configurações

 

_**Tópico modificado em:** 2015-03-09_

Após mesclar a topologia e executar o cmdlet **Import-CsLegacyConfiguration** , verifique se suas políticas e configurações do Office Communications Server 2007 R2 foram importadas para o Lync Server 2013. A tabela a seguir lista as políticas e configurações que você deve verificar.

## Políticas e configurações a serem verificadas após a migração


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Se você utiliza esta carga de trabalho:</th>
<th>Verifique essas políticas e configurações:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mensagem instantânea (IM) e conferência</p></td>
<td><p>Política de presença</p>
<p>Política de conferência</p></td>
</tr>
<tr class="even">
<td><p>Conferência Discada</p></td>
<td><p>Números de acesso de discagem</p>
<p>Planos de discagem</p></td>
</tr>
<tr class="odd">
<td><p>Enterprise Voice</p></td>
<td><p>Política de voz</p>
<p>Rotas de voz</p>
<p>Planos de discagem</p>
<p>Configurações de uso do PSTN</p></td>
</tr>
<tr class="even">
<td><p>Communicator Web Access</p></td>
<td><p>URLs simples</p></td>
</tr>
<tr class="odd">
<td><p>Usuários externos</p></td>
<td><p>Políticas de acesso externo</p></td>
</tr>
<tr class="even">
<td><p>Arquivamento</p></td>
<td><p>Política de arquivamento</p></td>
</tr>
</tbody>
</table>


## Para verificar as políticas e configurações

1.  No seu ambiente Office Communications Server 2007 R2, anote os nomes dos planos de discagem (conhecido anteriormente como perfis de localização), números de acesso de discagem (números e regiões de telefone para acesso do Atendedor de Conferência), rotas de voz e as políticas listadas na tabela anterior, além de URLs utilizadas para o Communicator Web Access.

2.  No servidor de Front End Lync Server 2013, abra Painel de Controle do Lync Server.

3.  Para verificar as políticas de conferência importadas, no painel à esquerda, clique em **Conferência** , clique em **Política de conferência** e, então, verifique se todas as políticas de conferência do seu ambiente Office Communications Server 2007 R2 foram incluídas na lista.
    
    > [!NOTE]  
    > A política de <strong>Reunião</strong> de versões anteriores do Office Communications Server agora é conhecido como a política de conferência no Lync Server 2013. Além disso, a configuração <strong>Participantes anônimos</strong> de versões anteriores do Office Communications Server agora é uma configuração na política de conferência do Lync Server 2013.    
    > [!NOTE]  
    > Em Office Communications Server 2007 R2, se a política de conferência não for definida para <strong>uso por usuário</strong> , apenas configurações de política global são importadas. Nenhuma outra política de conferência é importada neste caso.    
    > [!NOTE]  
    > O <strong>Participantes anônimos</strong> está definido para <strong>Impor por usuário</strong> na sua Office Communications Server 2007 R2 política de conferência, duas políticas de conferência são criadas durante a migração: uma com <strong>AllowAnonymousParticipantsInMeetings</strong> definida como <strong>Verdadeira</strong> e uma com <strong>AllowAnonymousParticipantsInMeetings</strong> definida como <strong>Falso</strong> .

4.  Para verificar planos importados, clique em **Roteamento de voz** , clique em **Plano de discagem** e, então, verifique se todos os planos de discagem no seu ambiente Office Communicator 2007 R2 estão incluídos na lista.
    
    > [!NOTE]  
    > Em Lync Server 2013, <strong>perfis de localização</strong> agora estão referenciados como <strong>dial-plans</strong> .

5.  Para verificar políticas de voz importadas, clique em **Roteamento de voz** , clique em **Política de voz** e, então, verifique se todas as suas políticas de voz do ambiente Office Communicator 2007 R2 estão incluídas na lista.
    
    > [!NOTE]  
    > Se a política não estiver definida como <strong>uso por usuário</strong> no seu ambiente Office Communications Server 2007 R2, apenas configurações de políticas globais são importadas. Nenhuma outra política de voz é importada nesta situação.

6.  Para verificar rotas de voz importadas, clique em **Rota de voz** , clique em **Rota** e, então, verifique se todas as rotas de voz no seu ambiente Office Communicator 2007 R2 estão incluídas na lista.

7.  Para verificar configurações de uso do PSTN, clique em **Roteamento de voz** , clique em **Uso do PSTN** e, então, verifique se as configurações de Uso do PSTN do seu ambiente Office Communicator 2007 R2 foram incluídas na lista.

8.  Para verificar políticas de acesso externo importadas, clique em **Federação e acesso externo** , clique em **Política de acesso externo** e, então, verifique se todas as políticas de acesso externo no seu ambiente Office Communicator 2007 R2 estão incluídas na lista.

9.  Para verificar as políticas de arquivamento, clique em **Monitoramento e arquivamento** , clique em **Política de arquivamento** e, então, verifique se todas as políticas de arquivamento no seu ambiente Office Communications Server 2007 R2 estão incluídas na lista.

10. Abra o Shell de Gerenciamento do Lync Server.

11. Para verificar as políticas de presença, na linha de comando, digite o seguinte:
    
        Get-CsPresencePolicy
    
    Ao olhar para o nome no parâmetro **Identidade** , verifique se todas as políticas de presença no seu ambiente Office Communications Server 2007 R2 foram importadas.

## Para verificar políticas e configurações utilizando cmdlets

1.  Abra o Shell de Gerenciamento do Lync Server.

2.  Execute os cmdlets na tabela a seguir para verificar políticas e configurações.
    
    A sintaxe desses cmdlets são como o exemplo a seguir:
    
        Get-CsConferencingPolicy
    
    Para detalhes sobre esses cmdlets, execute:
    
        Get-Help <cmdlet name> -Detailed


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Para essa política ou configuração:</th>
<th>Utilize este :</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Política de presença</p></td>
<td><p><strong>Get-CsPresencePolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>Política de conferência</p></td>
<td><p><strong>Get-CsConferencingPolicy</strong></p></td>
</tr>
<tr class="odd">
<td><p>Números de acesso de discagem</p></td>
<td><p><strong>Get-CsDialInConferencingAccessNumber</strong></p></td>
</tr>
<tr class="even">
<td><p>Planos de discagem</p></td>
<td><p><strong>Get-CsDialPlan</strong></p></td>
</tr>
<tr class="odd">
<td><p>Política de voz</p></td>
<td><p><strong>Get-CsVoicePolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>Rotas de voz</p></td>
<td><p><strong>Get-CsVoiceRoute</strong></p></td>
</tr>
<tr class="odd">
<td><p>Uso de PSTN</p></td>
<td><p><strong>Get-CsPstnUsage</strong></p></td>
</tr>
<tr class="even">
<td><p>URLs</p></td>
<td><p><strong>Get-CsSimpleUrlConfiguration</strong></p></td>
</tr>
<tr class="odd">
<td><p>Políticas de acesso externo</p></td>
<td><p><strong>Get-CsExternalAccessPolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>Política de arquivamento</p></td>
<td><p><strong>Get-CsArchivingPolicy</strong></p></td>
</tr>
</tbody>
</table>

