---
title: 'Lync Server 2013: Usando a conectividade Lync-Skype como usuário final'
TOCTitle: Usando a conectividade Lync-Skype como usuário final
ms:assetid: ad22f731-118c-4349-8790-b1a72941cbdd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn440175(v=OCS.15)
ms:contentKeyID: 59602788
ms.date: 12/29/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando a conectividade Lync-Skype no Lync Server 2013 como usuário final

 

_**Tópico modificado em:** 2016-12-27_

Conectividade Lync-Skype permite que usuários do Skype e usuários do Lync adicionem um ao outro como contatos, conversem por mensagens instantâneas e façam chamadas de vídeo e de áudio. Quando um usuário do Skype adicionar um usuário do Lync, um usuário do Skype criará um contato no Skype que contém o URI (uniform resource identifier) SIP (session initiation protocol) do usuário Lync. Por outro lado, quando um usuário do Lync adicionar um contato do Skype, o usuário Lync criará um contato no Lync que conterá a MSA (Microsoft Account) do usuário do Skype e não o nome do usuário do Skype.

**O que é um MSA?** Os usuários do Skype devem se conectar com uma conta da Microsoft (anteriormente chamada Windows Live ID) para poderem se comunicar com os contatos do Lync. Uma conta da Microsoft é uma combinação de um endereço de email e um senha, que você também pode usar para entrar em serviços como a tecnologia de armazenamento Microsoft OneDrive, o Windows Phone, o serviço de jogos online Microsoft Xbox LIVE e o cliente de colaboração e mensagens Microsoft Outlook (e, anteriormente, o serviço de email baseado em Web Microsoft Hotmail ou Windows Live Messenger). Se você usa um endereço de email e senha para logar nesses ou outros serviços, você já tem uma conta da Microsoft. Para detalhes sobre criação de conta da Microsoft, veja a página de login de conta da Microsoft em [http://go.microsoft.com/fwlink/p/?LinkId=306061](http://go.microsoft.com/fwlink/p/?linkid=306061). Você pode mesclar a sua conta do Skype atual com a sua conta da Microsoft para simples login através de uma variedade de aplicativos e serviços. Assim que a conta for mesclada, um usuário do Skype pode enviar uma solicitação de contato a usuários do Lync.

> [!IMPORTANT]  
> Para que usuários do Lync e do Skype possam se comunicar apropriadamente entre si, os seguintes requisitos devem ser cumpridos:<ul><li><p>Usuários do Skype devem estar logados no seu cliente Skype com uma conta da Microsoft (MSA).</p></li>
> <li><p>Usuários Lync devem habilitar a conectividade de rede pública para o seu administrador Lync.</p></li>
> <li><p>Quando um usuário do Skype adicionar um contato do Lync contact, verifique se a palavra Lync está aparecendo sob o nome de contato. Isso indica que o URI do Lync foi encontrado.</p></li>
> 
> <li><p>Quando um usuário do Skype adiciona um contato do Lync e o resultado da pesquisa retornar zero como valor para o domínio do Lync, o processo de provisionamento do PIC pode não ter sido concluído ou o domínio do Lync ainda não foi configurado.</p></li>
> 
> 
> <li><p>Dependendo das configurações de privacidade dos usuários do Lync e do Skype, mensagens instantâneas, vídeo e presença podem não funcionar até que os novos contatos sejam aceitos por cada usuário.</p></li></ul>


**Adicionar um contato do Skype ao Lync 2013**

1.  Em Lync, clique em **Adicionar um contato, Adicionar um Contato Externo**.

2.  Na lista de provedores de contato disponíveis, selecione **Skype**, como mostrado abaixo
    
    ![Cliente do Lync que mostra como adicionar um contato do Skype](images/Dn440175.ac4e2f21-c1d9-47d8-b99e-d49fe4eb36d7(OCS.15).jpg "Cliente do Lync que mostra como adicionar um contato do Skype")

3.  No campo **Endereço de IM**, insira a conta da Microsoft (MSA) do usuário de Skype.

4.  Na caixa suspensa **Adicionar ao grupo de contato**, selecione um grupo de contatos ao qual deseja adicionar o usuário.

5.  Na caixa suspensa **Configurar Relação de Privacidade**, selecione as configurações de contato apropriadas e clique em **OK**.

6.  O usuário não aparecerá como um contato do Lync. Selecione o usuário, clique com o botão direito do mouse no nome de usuário, e clique em **Ver Cartão de Visita** para exibir as propriedades do usuário. Conforme mostrado abaixo, você também pode clicar em **Chamada** e em **Chamada do Lync** para fazer uma chamada de áudio ou de vídeo com o usuário do Skype adicionado recentemente.
    
    ![Cliente do Lync iniciando uma chamada do Lync para um contato](images/Dn440175.cd7cb21a-87f7-4bfa-b30c-980d4098d226(OCS.15).jpg "Cliente do Lync iniciando uma chamada do Lync para um contato")

Para informações de suporte para contatos adicionais, veja [Adicionar um contato no Lync em](http://office.microsoft.com/pt-br/office365-lync-online-help/add-a-contact-in-lync-ha102828922.aspx) e [Adicionar um contato externo no Lync em](http://office.microsoft.com/pt-br/office365-lync-online-help/add-an-external-contact-in-lync-ha104038998.aspx?ctt=5%26origin=ha102828922)

Quando um usuário do Skype com conta da Microsoft usa um nome de domínio, como **bob@contoso.com**, o usuário Lync pode adicionar esta conta da Microsoft de duas maneiras:

1.  Usando o ícone **Adicionar um Contato** ou

2.  Através do campo **Encontrar alguém ou uma sala, ou discar um número**.

Em cada instância, o usuário do Lync deve inserir o email do usuário de Skype no seguinte formato: **usuário(nome de domínio)@msn.com**.

> [!IMPORTANT]  
> Essa etapa não requer uma conta da Microsoft que use os seguintes nomes de domínio: <strong>@live.com, @hotmail.com ou @outlook.com</strong>. Para mais informações sobre suporte de nomes de domínio personalizado, veja <a href="http://support.microsoft.com/kb/897567">Domínios públicos IM suportados em</a>.

**Para adicionar um contato Skype no Lync ao usar um nome de domínio personalizado.**

1.  Em Lync, clique em **Adicionar um contato, Adicionar um Contato Externo**.

2.  Na lista de provedores de contato disponíveis, selecione **Skype**, como mostrado abaixo
    
    ![Cliente do Lync que mostra como adicionar um contato do Skype](images/Dn440175.ac4e2f21-c1d9-47d8-b99e-d49fe4eb36d7(OCS.15).jpg "Cliente do Lync que mostra como adicionar um contato do Skype")

3.  No campo **Endereços IM** , insira a Conta da Microsoft (MSA) do usuário Skype no formato **usuário(nome do domínio)@msn.com**. Portanto, para o usuário bob@contoso.com, o valor inserido será **bob(contoso.com)@msn.com**, como mostrado abaixo.
    
    ![Configurações de Novo Contato de cliente do Lync](images/Dn440175.422e69b5-2c0c-4260-858f-f10309af772f(OCS.15).jpg "Configurações de Novo Contato de cliente do Lync")

4.  Na lista suspensa **Adicionar ao grupo de contatos**, selecione um grupo de contatos na qual adicionar o usuário.

5.  Na lista suspensa **Configurar Relação de Privacidade**, selecione as configurações de contato apropriadas e clique em **OK**.

6.  Um usuário Lync também pode usar o campo **Encontrar alguém ou uma sala ou discar um número** no Lync, e adicionar um endereço de email semelhante a **usuário(nome de domínio)@msn.com**. Portanto, para a conta da Microsoft bob@contoso.com, o valor de entrada será **bob(contoso.com)@msn.com**, como mostrado abaixo.
    
    ![Procurando um contato no cliente do Lync](images/Dn440175.69787db8-f9b9-49e5-b197-b90b10393301(OCS.15).jpg "Procurando um contato no cliente do Lync")

7.  Siga as etapas 4 e 5 anteriores deste procedimento para adicionar o contato a um grupo e selecionar as configurações de privacidade adequadas.

**Para adicionar um contato Lync ao Skype**

1.  Entre no Skype. O usuário de Skype deve estar logado como cliente Skype com uma conta da Microsoft (MSA).
    
    ![Página Entrada de cliente do Skype](images/Dn440175.b4fd7c5a-be35-4205-80c7-872863b7a91d(OCS.15).jpg "Página Entrada de cliente do Skype")

2.  Selecione o ícone Adicionar Contatos

3.  Insira a SIP ou o URI do usuário de Skype. Por exemplo, bob@contoso.com.

4.  Quando o Skype encontrar os resultados correspondentes, procure pela palavra **Lync** sob o nome de usuário do Lync. Isso indica que o Skype localizou o cliente de SIP URI do Lync com êxito. Clique no nome.
    
    ![Cliente do Skype mostrando um contato do Lync](images/Dn440175.4e690a72-1a54-4442-89cf-0fb45ac5f56a(OCS.15).jpg "Cliente do Skype mostrando um contato do Lync")

5.  No canto superior direito da janela, clique em Adicionar a Contatos.

6.  O novo contato será adicionado a sua lista de contato, mas estará marcado com um ponto de interrogação em vez do ícone de status até o pedido ser aceito. Quando seu novo contato aceitar sua solicitação, você poderá ver se ele está online, iniciar conversas de mensagem instantânea e fazer chamadas de áudio e de vídeo.
    
    ![Conversa de mensagem instantânea de cliente do Skype com um contato do Lync](images/Dn440175.86ca6f81-4db9-45ba-8511-1f7541aaf066(OCS.15).jpg "Conversa de mensagem instantânea de cliente do Skype com um contato do Lync")
    
    > [!IMPORTANT]  
    > O administrador Lync Server deve definir as configurações de política do usuário Lync para permitir solicitações de entrada. Do contrário, o usuário Lync não receberá solicitações de contato do usuário de Skype. Dependendo da configuração de política do usuário, a solicitação para adicionar um usuário Skype aparecerá na guia <strong>Novo</strong> do cliente do Lync. Para iniciar uma conversação com um usuário Skype, o usuário Lync deve adicionar o usuário Skype à lista de Favoritos ou de contatos. A imagem abaixo mostra a localização da guia <strong>Novo</strong> no cliente Lync.    
    ![Página Novos Contatos de cliente do Lync](images/Dn440175.b1cf8570-1401-47d9-ab14-b04f0d7e8a7a(OCS.15).jpg "Página Novos Contatos de cliente do Lync")

O usuário Lync deve definir alertas para garantir que a solicitação enviada pelo usuário Skype apareça e seja descoberta pelo usuário Lync. Para definir alertas no Lync, conclua o procedimento a seguir.

**Configurar Alertas para Lync**

1.  No cliente Lync, clique no ícone **Opções**.

2.  Selecione **Alertas**

3.  Em **Alertas gerais**, marque **Avisar quando alguém me adicionar a sua lista de contatos**.

4.  Em **Contatos externos ao Lync**, selecione **Permitir convites mas bloquear qualquer outro tipo de comunicação**.

5.  Clique em **OK** para fechar a janela de Opções.

![Caixa de diálogo Opções de cliente do Lync, página Alertas](images/Dn440175.b36ed67f-f394-4f66-b60a-b74793001bfc(OCS.15).jpg "Caixa de diálogo Opções de cliente do Lync, página Alertas")

