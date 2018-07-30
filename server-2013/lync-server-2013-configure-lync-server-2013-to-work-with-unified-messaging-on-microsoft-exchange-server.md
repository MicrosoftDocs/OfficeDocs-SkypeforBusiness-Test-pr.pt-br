---
title: 'Lync Server 2013: Configurar o Lync Server 2013 para trabalhar com a Unificação de Mensagens no Microsoft Exchange Server'
TOCTitle: Configurar o Lync Server 2013 para trabalhar com a Unificação de Mensagens no Microsoft Exchange Server
ms:assetid: 1098ae4d-f57f-44f3-804e-39889d9fc14e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398193(v=OCS.15)
ms:contentKeyID: 49305914
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar o Lync Server 2013 para trabalhar com a Unificação de Mensagens no Microsoft Exchange Server

 

_**Tópico modificado em:** 2016-12-08_

Esta etapa requer o Utilitário de Integração do UM do Exchange (OcsUmUtil.exe). Esta ferramenta está localizada no servidor do Lync Server 2013 na pasta ..\\Program Files\\Common Files\\Microsoft Lync Server 2013\\Support.

## Executando o Utilitário de Integração do UM do Exchange

O Utilitário de Integração do UM do Exchange deve ser executado em uma conta de usuário com as seguintes características:

  - Associação nos grupos RTCUniversalServerAdmins e RtcUniversalUserAdmins (que inclui a permissão para ler as configurações da Unificação de Mensagens do Exchange Server).

  - Direitos do usuário dentro do domínio para criar objetos de contato no contêiner específico da unidade organizacional (OU).

Quando você executa o Utilitário de Integração do UM do Exchange, ele realiza as seguintes tarefas:

  - Cria objetos de contato para cada atendedor automático e número de telefone do assinante a ser utilizado pelos usuários do Enterprise Voice.

  - Verifica se o nome de cada plano de discagem do Enterprise Voice corresponde ao contexto de telefone do plano de discagem da UM (Unificação de Mensagens). Essa correspondência é necessária somente se o plano de discagem da UM estiver sendo executado em uma versão do Exchange *anterior* ao Exchange 2010 Service Pack 1 (SP1).

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/Gg425939.important(OCS.15).gif" title="important" alt="important" />Importante:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Antes de executar o Utilitário de Integração do UM do Exchange, certifique-se de ter feito o seguinte:<ul><li><p>Criar um ou mais planos de discagem do UM do Exchange, conforme descrito na documentação do produto do Exchange.</p>
<p>Para Microsoft Exchange Server 2010, consulte &quot; Criar um Plano de Discagem da UM&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=186177">http://go.microsoft.com/fwlink/p/?linkId=186177</a>.</p>
<p>Para Microsoft Exchange Server 2007 Service Pack 1 (SP1), consulte &quot;Como criar um plano de discagem URI de SIP de Unificação de Mensagens&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=185771">http://go.microsoft.com/fwlink/p/?linkId=185771</a>.</p></li><li><p>Crie um ou mais planos de discagem correspondentes do Lync Server, conforme descrito em <a href="lync-server-2013-create-a-dial-plan.md">Criar um plano de discagem no Lync Server 2013</a>.</p>

> [!IMPORTANT]  
> Se você estiver utilizando uma versão do Exchange que seja anterior ao Microsoft Exchange Server 2010 SP1, é necessário inserir o FQDN (nome de domínio totalmente qualificado) do plano de discagem de SIP correspondente do Unificação de Mensagens (UM) do Exchange no campo <strong>Nome simples</strong> do plano de discagem do Lync Server 2013. Se você estiver usando o Microsoft Exchange Server 2010 SP1 ou service pack mais recente, essa correspondência de nome de plano de discagem não é necessária.

</li><li><p>Crie um atendedor automático e certifique-se que o número de acesso do assinante e o número do atendedor automático estejam no formato E.164.</p></li></ul></td>
</tr>
</tbody>
</table>


## Para executar o Utilitário de Integração do UM do Exchange

1.  Em um Servidor Front-End, abra um prompt de comando e digite **cd %CommonProgramFiles%\\Microsoft Lync Server 2010\\Support** , depois pressione ENTER.

2.  Digite **OcsUmUtil.exe** e pressione ENTER.

3.  Clique em **Carregar Dados** para localizar todas as florestas confiáveis do Exchange.

4.  Na lista **Planos de Discagem SIP**, selecione o plano de discagem SIP do UM para o qual você deseja criar objetos de contato e clique em **Adicionar**.

5.  Na caixa **Contato**, aceite a unidade organizacional padrão ou clique em **Procurar** para iniciar o **Seletor de UO**. Na caixa **Seletor de UO**, você pode selecionar uma UO e clicar em **OK**, ou pode clicar em **Criar Nova UO** para criar uma nova unidade organizacional na raiz ou em qualquer outra UO do domínio (por exemplo, "OU=RTC Special Accounts,DC=fourthcoffee,DC=com"); em seguida, clique em **OK**.
    
    > [!NOTE]  
    > O nome diferenciado (DN) da UO selecionada ou criada será agora exibido na caixa <strong>Unidade Organizacional</strong>.

6.  Na caixa **Nome**, aceite o nome padrão do plano de discagem ou digite um novo nome de exibição para o objeto de contato que você está criando.
    
    > [!NOTE]  
    > Por exemplo, se estiver criando um objeto de contato de acesso do assinante, bastará nomeá-lo como Acesso do Assinante.

7.  Na caixa **Endereço SIP**, aceite o endereço SIP padrão ou digite um novo endereço SIP.
    
    > [!NOTE]  
    > Se você digitar um novo endereço SIP, ele deve começar com <strong>SIP:</strong> (isto é, &quot;SIP:&quot; incluindo os dois pontos).

8.  Na lista **Servidor ou Pool**, selecione o servidor do Standard Edition ou o Pool de Front-Ends no qual o objeto de contato será habilitado.
    
    > [!NOTE]  
    > Preferencialmente, o pool selecionado é o mesmo em que os usuários habilitados para Enterprise Voice e UM do Exchange estão implantados.

9.  Na lista **Número de Telefone**, selecione **Insira o número de telefone** ou **Usar este número piloto do UM do Exchange** e digite um número de telefone.

10. Na lista **Tipo de Contato**, selecione o tipo de contato que deseja criar e clique em **OK**.

11. Repita as etapas de 1 a 10 para outros objetos de contato que você deseje criar.
    
    > [!NOTE]  
    > Você deve criar pelo menos um contato para cada atendedor automático. Se desejar acesso externo, você também precisará de um contato Acesso do Assinante e terá que especificar números DID (discagem direta interna).

Para verificar se os objetos de contato foram criados, abra Usuários e Computadores do Active Directory e selecione a UO na qual os objetos foram criados. Os objetos de contato devem aparecer no painel de detalhes.

