---
title: Configurações Novas e Modificadas para Lync 2013
TOCTitle: Configurações Novas e Modificadas para Lync 2013
ms:assetid: bb13789c-7eda-461c-a387-02ea8ca4dabe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205204(v=OCS.15)
ms:contentKeyID: 49307921
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurações Novas e Modificadas para Lync 2013

 

_**Tópico modificado em:** 2015-03-09_

Este tópico discute as alteração nos cmdlets do Shell de Gerenciamento do Lync Server que relatam diretamente ao gerenciamento do cliente. O Lync Server 2013 apresenta vários parâmetros novos e reprova parâmetros para recursos que podem ser configurados de outras maneiras.

## Novos parâmetros de gerenciamento de cliente


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nova</th>
<th>Cmdlet Shell de Gerenciamento do Lync Server</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TracingLevel</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>Quando configurado como Verdadeiro, o rastreamento de software estará ativado no Lync; quando configurado como Falso, o rastreamento de software estará desabilitado. O rastreamento de software envolve manter um registro detalhado de tudo o que um programa faz (incluindo monitorar chamadas de APIs). O rastreamento é útil para desenvolvedores e funcionários de suporte de aplicativo.Esta configuração é equivalente à Política de grupo do Communications Server 2007 R2 &quot;Ativar rastreamento para comunicador&quot;. As configurações são:</p>
<ul>
<li><p>Desligado = o rastreamento esta desabilitado e o usuário não consegue alterar esta configuração.</p></li>
<li><p>Leve = o rastreamento mínimo é executado e o usuário não pode alterar esta configuração.</p></li>
<li><p>Ligado = o rastreamento detalhado é executado e o usuário não consegue alterar esta configuração.</p></li>
</ul>
<p>Por padrão TracingLevel está definido como um valor nulo. Isso significa que o rastreamento mínimop é executado, mas o usuário não pode habilitar ou desabilitar este rastreamento mínimo.</p></td>
</tr>
<tr class="even">
<td><p>EnableMediaRedirection</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>Quando definido como Verdadeiro ($True) permite que fluxos de áudio e vídeo sejam separados do resto do tráfego de rede. Por outro lado, isso permite que os dispositivos do cliente executem a codificação e a decodificação de áudio e vídeo localmente. O redirecionamento de mídia resulta no uso reduzido de largura de banda, maior escalabilidade do servidor e uma experiência do usuário melhorada comparada a técnicas semelhantes como dispositivos remotos ou compressão de codec.</p></td>
</tr>
<tr class="odd">
<td><p>AllowLargeMeetings</p></td>
<td><p>CsConferencing</p></td>
<td><p>Quando definido como Verdadeiro, todas as reuniões Lync são tratadas como &quot;reuniões grandes&quot;. Com uma reunião grande, as restrições são colocadas no número de notificações que são enviadas aos participantes, além do tamanho da lista de participantes que é transmitida por padrão.</p></td>
</tr>
<tr class="even">
<td><p>DisablePowerPointAnnotations</p></td>
<td><p>CsConferencing</p></td>
<td><p>Quando definido como Verdadeiro ($True) os usuários não poderão adicionar anotações a slides do PowerPoint usando em uma conferência. No entanto, dependendo do valor da propriedade AllowAnnotations, os usuários ainda terão acesso a outros recursos de quadro branco. O valor padrão é Falso, ou seja, as anotações de PowerPoint são permitidas.</p></td>
</tr>
<tr class="odd">
<td><p>AllowSharedNotes</p></td>
<td><p>CsConferencing</p></td>
<td><p>Quando definido como Verdadeiro (o valor padrão) qualquer bloco de notas OneNote vinculado à conferência será atualizado automaticamente com informações, como participantes da conferência e detalhes sobre conteúdo compartilhado durante a conferência.</p></td>
</tr>
<tr class="even">
<td><p>EnableInviteCustomization</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>Usado juntamente com outros parâmetros novos de CsMeetingConfiguration para personalizar os convites de reunião gerados pelo Suplemento de Reunião Online para Lync 2013.</p></td>
</tr>
<tr class="odd">
<td><p>LogoURL</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>Adiciona o logotipo de sua organização a todos os convites gerados pelo Suplemento de Reunião Online para Lync 2013. Você pode especificar o URL de um GIF ou uma imagem JPG.</p></td>
</tr>
<tr class="even">
<td><p>HelpURL</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>Adiciona o URL de ajuda ou suporte de sua organização para todos os convites gerados pelo Suplemento de Reunião Online para Lync 2013.</p></td>
</tr>
<tr class="odd">
<td><p>LegalURL</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>Adiciona texto legal ou de aviso de isenção a todos os convites gerados pelo Suplemento de Reunião Online para Lync 2013. Você pode especificar o URL do local do texto.</p></td>
</tr>
<tr class="even">
<td><p>CustomFooterText</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>Adicione um rodapé personalizado para todos os convites gerados pelo Suplemento de Reunião Online para Lync 2013. Você pode especificar o URL do local do texto de rodapé personalizado.</p></td>
</tr>
<tr class="odd">
<td><p>IsPublicDisclosureAllowed</p></td>
<td><p>CsWebServiceConfiguration</p></td>
<td><p>Habilita a nova versão 2013 do Lync Web App. A nova versão do Lync Web App não está habilitada por padrão e deve ser ativada pelo administrador.</p></td>
</tr>
</tbody>
</table>


## Parâmetros de gerenciamento do cliente preteridos


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro</th>
<th>Cmdlet Shell de Gerenciamento do Lync Server</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EnableSQMData</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>O parâmetro EnableSQMData do cmdlet Set-CSClientPolicy foi removido de Lync Server 2013. Em vez disso, você pode usar a configuração de Política de grupo compartilhada para dados de SQM (Gerenciamento de qualidade de software) a fim de determinar a interface do usuário da opção de Melhoria da experiência do usuário na página de opções gerais do cliente Lync:</p>
<p>HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\Common\QMEnable</p>
<p>Valores:</p>
<p>1 = exibir e marcar a caixa de seleção (o usuário pode desmarcar a caixa de seleção)</p>
<p>0 = desativar e desabilitar a caixa de seleção (o usuário não pode substituir)</p>
<p>Nulo = o valor é determinado pela configuração do Office e a caixa de seleção é exibida para que usuários configurem como escolherem</p></td>
</tr>
<tr class="even">
<td><p>AllowExchangeContactStore</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>Este parâmetro foi removido. Em vez disso, ao implantar o Lync Server 2013 e publicar a topologia, o armazenamento unificado é ativado por padrão para todos os usuários. Isso significa que todos os contatos do usuário são mantidos no Exchange e estão disponíveis no Lync, no Outlook e no Outlook Web Access. É possível usar o cmdlet Set-CsUserServicesPolicy para personalizar quais usuários têm um repositório de contato unificado disponível. Você pode ativar usuários globalmente, por site, por inquilino ou por indivíduos ou grupos de indivíduos. Para obter detalhes, consulte <a href="lync-server-2013-enable-users-for-unified-contact-store.md">Habilitar usuários para repositório unificado de contatos no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p>MAPIPollInterval</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>Este parâmetro não é usado pelo Lync 2013. Em versões anteriores, este parâmetro especificava a frequência com que um cliente recuperava dados MAPI das pastas públicas do Exchange</p></td>
</tr>
</tbody>
</table>

