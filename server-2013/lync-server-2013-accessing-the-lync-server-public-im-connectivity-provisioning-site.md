---
title: 'Lync Server 2013: Acessando o site de configuração de conectividade a redes públicas de mensagens instantâneas do Lync Server'
TOCTitle: Acessando o site de configuração de conectividade a redes públicas de mensagens instantâneas do Lync Server
ms:assetid: 77a08234-6bcf-4f59-b43b-ee5fc1926585
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn440174(v=OCS.15)
ms:contentKeyID: 59602797
ms.date: 03/09/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Acessando o site de configuração de conectividade a redes públicas de mensagens instantâneas do Lync Server a partir do Lync Server 2013

 

_**Tópico modificado em:** 2017-03-09_

O processo de provisionamento para a conectividade Lync-Skype mudou, em comparação com métodos anteriores de provisionamento de PIC. Este processo de provisionamento pode levar até trinta dias para ser concluído. Recomendamos que você inicie este processo primeiro, antes de concluir as etapas restantes deste documento. Depois que o processo de provisionamento do Lync-Skype é concluído para a sua conta, a conta é ativada e seus usuários elegíveis são habilitados para conectividade a redes públicas de mensagens instantâneas.

### Para provisionar a conectividade Lync-Skype, você precisa das seguintes informações:

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ol><li><p>Número do Contrato da Microsoft</p></li><li><p>Nome de domínio totalmente qualificado (FQDN) do serviço de Borda de Acesso</p></li><li><p>Domínios do protocolo SIP</p></li><li><p>Qualquer FQDN adicional do serviço de Borda de Acesso</p></li><li><p>Informações de contato</p></li></ol></td>
</tr>
<tr class="even">
<td><ol><li><p>Número do Contrato da Microsoft</p></li><li><p>Nome de domínio totalmente qualificado (FQDN) do serviço de Borda de Acesso</p></li><li><p>Domínios do protocolo SIP</p></li><li><p>Qualquer FQDN adicional do serviço de Borda de Acesso</p></li><li><p>Informações de contato</p></li></ol></td>
</tr>
</tbody>
</table>


### Para iniciar o processo de provisionamento para conectividade Lync-Skype:

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ol><li><p>Entre no site <strong>https://pic.lync.com</strong> com seu Microsoft Windows Live ID.</p></li><li><p>Selecione o tipo de contrato de licenciamento da Microsoft.</p></li>
> <li><p>Marque a caixa de seleção, confirmando que você leu e aceita os Direitos de Uso do Produto do Lync Server.</p></li>
> <li><p>Na página <strong>Iniciar Solicitação de Configuração</strong>, clique no link adequado para iniciar uma solicitação de configuração:</p></li>
> 
> <li><p>Na página <strong>Especificar Informações de Provisionamento</strong>, insira o <strong>FQDN do serviço de Borda de Acesso</strong>. Por exemplo, <strong>accessedge.contoso.com</strong>.</p></li>
> 
> 
> <li><p>Insira pelo menos um ou mais nomes de domínio SIP e clique em <strong>Adicionar</strong>.</p>
<div class="alert">
> [!IMPORTANT]  
> É necessário pelo menos um servidor de Borda de Acesso e um domínio SIP para concluir o processo de provisionamento. O domínio SIP e o servidor de Borda de Acesso devem estar ativos, em funcionamento e acessíveis na rede.
</div></li><li><p>Na lista de <strong>provedores de Serviços públicos de mensagens instantâneas</strong>, selecione <strong>Skype,</strong> e clique em <strong>Avançar</strong> para adicionar informações de contato e enviar a solicitação de configuração.</p></li></ol></td>
</tr>
<tr class="even">
<td><ol><li><p>Entre no site <strong>https://pic.lync.com</strong> com seu Microsoft Windows Live ID.</p></li><li><p>Selecione o tipo de contrato de licenciamento da Microsoft.</p></li>
> <li><p>Marque a caixa de seleção, confirmando que você leu e aceita os Direitos de Uso do Produto do Lync Server.</p></li>
> <li><p>Na página <strong>Iniciar Solicitação de Configuração</strong>, clique no link adequado para iniciar uma solicitação de configuração:</p></li>
> 
> <li><p>Na página <strong>Especificar Informações de Provisionamento</strong>, insira o <strong>FQDN do serviço de Borda de Acesso</strong>. Por exemplo, <strong>accessedge.contoso.com</strong>.</p></li>
> 
> 
> <li><p>Insira pelo menos um ou mais nomes de domínio SIP e clique em <strong>Adicionar</strong>.</p>
<div class="alert">
> [!IMPORTANT]  
> É necessário pelo menos um servidor de Borda de Acesso e um domínio SIP para concluir o processo de provisionamento. O domínio SIP e o servidor de Borda de Acesso devem estar ativos, em funcionamento e acessíveis na rede.
</div></li><li><p>Na lista de <strong>provedores de Serviços públicos de mensagens instantâneas</strong>, selecione <strong>Skype,</strong> e clique em <strong>Avançar</strong> para adicionar informações de contato e enviar a solicitação de configuração.</p></li></ol></td>
</tr>
</tbody>
</table>


Após a solicitação de provisionamento ter sido enviada, pode levar até 30 dias para a conta ser ativada e os usuários serem habilitados para conectividade de redes públicas de mensagens instantâneas.

## Habilitando a federação e a Conectividade de Redes Públicas de Mensagens instantâneas

Após ter enviado a solicitação de provisionamento, você pode se concentrar no ambiente do Lync Server e nas tarefas administrativas necessárias para configurar a conectividade Lync-Skype. Nesta seção, pressupomos que o administrador do Lync Server implantou o Lync Server e configurou o acesso externo. Para obter informações adicionais sobre como configurar o acesso externo para o Lync Server, consulte "Planejando o acesso de usuário externo" em [http://go.microsoft.com/fwlink/p/?LinkID=273772](http://go.microsoft.com/fwlink/p/?linkid=273772) e "Implantando o acesso de usuário externo" em [http://go.microsoft.com/fwlink/p/?LinkID=27378](http://go.microsoft.com/fwlink/p/?linkid=27378).

Para preparar o ambiente do Lync Server para conectividade Lync-Skype, o administrador do Lync Server deve concluir estas três tarefas:

## 1\. Configurar a federação e o PIC

A federação é necessária para permitir que os usuários do Skype se comuniquem com os usuários do Lync em sua organização. A Conectividade a Redes Públicas de Mensagens Instantâneas (PIC) é uma classe de federação e deve ser configurada para permitir que seus usuários do Lync se comuniquem com os usuários do Skype. A federação e o PIC são configurados usando o Painel de Controle do Lync Server, mostrado abaixo.

> [!IMPORTANT]  
> A federação de PIC não tem mais suporte no Live Communication Server 2005 SP1 ou no Office Communications Server 2007. As plataformas que dão suporte à federação de PIC incluem o Lync Server 2013, o Lync Server 2010 e o Office Communications Server 2007 R2.

## 2\. Configurar pelo menos uma política para dar suporte ao acesso de usuário federado

Usando o Painel de Controle do Lync Server, um administrador deve configurar uma ou mais políticas de usuário externo para controlar se os usuários do Skype podem colaborar com usuários internos do Lync Server.

## 3\. Configurar a configuração do provedor de PIC do Skype para o Lync

Usando o Shell de Gerenciamento do Lync Server, um administrador deve configurar a política de cliente do Lync para exibir o Skype como um provedor de PIC adicional.

> [!NOTE]  
> Os usuários dos provedores de serviços de Conectividade a Redes Públicas de Mensagens Instantâneas (PIC) não podem participar em mensagens instantâneas ou conferências em sua organização até que você também configure pelo menos uma política (etapa 2, anteriormente neste procedimento) para dar suporte à conectividade a redes públicas de mensagens instantâneas.<br />Para configurar a federação e o PIC, consulte &quot;Habilitar ou desabilitar a federação e a Conectividade a Redes Públicas de Mensagens Instantâneas&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=306063">http://go.microsoft.com/fwlink/p/?LinkId=306063</a>.<br />Para configurar pelo menos uma política para dar suporte ao acesso de usuário federado, consulte &quot;Configurar políticas para controlar o acesso de usuário público&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=306064">http://go.microsoft.com/fwlink/p/?LinkId=306064</a>.

1.  De um Servidor Front-End do Lync Server, abra o Shell de Gerenciamento do Lync Server.

2.  Execute estes dois comandos:
    
      - Remove-CsPublicProvider -Identity Messenger
    
      - New-CsPublicProvider -Identity Skype -ProxyFqdn federation.messenger.msn.com -IconUrl "https://images.edge.messenger.live.com/Messenger\_16x16.png" -VerificationLevel 2 -Enabled 1

3.  De um cliente Lync, agora você pode selecionar Skype como provedor PIC e adicionar um cliente Skype ao especificar a conta da Microsoft deles. Além disso, um usuário do Skype que mesclou e entrou com uma conta da Microsoft pode enviar solicitação de contato a usuários do Lync. Para mais informações sobre contas da Microsoft, consulte [O que é uma conta da Microsoft?](https://support.skype.com/pt-br/faq/fa12059/what-is-a-microsoft-account). Para mais informações sobre como adicionar clientes no Lync, veja [Usando a conectividade Lync-Skype no Lync Server 2013 como usuário final](lync-server-2013-using-lync-skype-connectivity-as-an-end-user.md).

4.  Para obter informações detalhadas sobre como modificar provedores hospedados, consulte "Criar ou editar provedores federados SIP hospedados" em [http://go.microsoft.com/fwlink/p/?LinkId=306065](http://go.microsoft.com/fwlink/p/?linkid=306065).

Isso conclui as tarefas administrativas que devem ser executadas no servidor. Agora você está pronto para a conectividade Lync-Skype.

## Recursos adicionais

[Usando a conectividade Lync-Skype no Lync Server 2013 como usuário final](lync-server-2013-using-lync-skype-connectivity-as-an-end-user.md)

[Provisioning guide for Lync-Skype connectivity in Lync Server 2013](lync-server-2013-provisioning-guide-for-lync-skype-connectivity.md)

