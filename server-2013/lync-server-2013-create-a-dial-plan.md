---
title: 'Lync Server 2013: Criar um plano de discagem'
TOCTitle: Criar um plano de discagem
ms:assetid: d2fef3d0-7e78-4591-b712-d62ac71d71a5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398909(v=OCS.15)
ms:contentKeyID: 49308213
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar um plano de discagem no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-24_

Para criar um novo plano de discagem, execute as etapas do procedimento a seguir. Se você deseja editar um plano de discagem, consulte [Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md).

## Para criar um plano de discagem

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de Voz** e clique em **Plano de Discagem** .

4.  Na página **Plano de Discagem** , clique em **Novo** e selecione um escopo para o plano de discagem:
    
      - **Plano de discagem do Site** se aplica a todo um site, exceto quaisquer usuários ou grupos que recebem um plano de discagem de usuário. Se você selecionar **Site** para o escopo de um plano de discagem, deverá escolher o site na caixa de diálogo **Selecionar um Site** . Se já houver um plano de discagem para um site, o site não aparecerá na caixa de diálogo **Selecionar um Site** .
    
      - **Plano de discagem do pool** pode se aplicar a um gateway de PSTN (Rede Telefônica Pública Comutada) ou um registrador. Se você selecionar **Pool** para o escopo de um plano de discagem, escolha o gateway PSTN ou registrador na caixa de diálogo **Selecionar um Serviço** . Se um plano de discagem já tiver sido criado para um serviço (gateway PSTN ou registrador), o serviço não aparecerá na lista.
    
      - **Plano de discagem do usuário** pode ser aplicado a usuários ou grupos especificados.
    
    > [!NOTE]  
    > Depois de selecionar o escopo do plano de discagem, não é possível alterá-lo.

5.  Se você estiver criando um plano de discagem do usuário, insira um nome descritivo no campo **Nome** na caixa de diálogo **Novo Plano de Discagem** . Após o nome ser salvo, não será possível alterá-lo.
    
    > [!NOTE]  
    > Para planos de discagem do site, o campo <strong>Nome</strong> é pré-preenchido com o nome do site e não pode ser alterado.<br />    Para planos de discagem do pool, o campo <strong>Nome</strong> é pré-preenchido com o gateway PSTN ou o nome do registrador e não pode ser alterado.

6.  O campo **Nome simples** é pré-preenchido com o mesmo nome que aparece no campo **Nome** . Como opção, é possível editar esse campo para especificar um nome mais descritivo que reflete o site, o serviço ou o usuário ao qual o plano de discagem se aplica.
    
    > [!IMPORTANT]  
    > O <strong>Nome simples</strong> precisa ser exclusivo entre os planos de discagem dentro da implantação do Lync Server. Ele não pode exceder 256 caracteres Unicode, e cada um deles pode ser um caractere alfabético ou numérico, um hífen (-), um ponto (.) ou um sublinhado (_).<br />    Caracteres <strong>não suportados</strong> incluem espaços e caracteres reservados, conforme definido no RFC 3966 (http://www.ietf.org/rfc/rfc3966.txt). Caracteres reservados <strong>não suportados</strong> no <strong>Nome Simples</strong> incluem o seguinte:<br />    &quot;;&quot; &quot;/&quot; &quot;?&quot; &quot;:&quot; &quot;@&quot; &quot;&amp;&quot; &quot;=&quot; &quot;+&quot; &quot;$&quot; &quot;,&quot;

7.  (Opcional) No campo **Descrição** , você pode digitar informações descritivas adicionais sobre o plano de discagem.

8.  (Opcional) Se você quiser usar esse plano de discagem como uma região para números de acesso de discagem, especifique uma **Região de conferência de discagem** . Se você não quiser usar esse plano de discagem para números de acesso de discagem, deixe esse campo vazio.
    
    > [!NOTE]  
    > As regiões de conferência d discagem são necessárias para associar números de acesso de conferência de discagem a um ou mais planos de discagem.

9.  (Opcional) No campo **Prefixo de acesso externo** , especifique um valor somente se os usuários precisarem discar um ou mais dígitos iniciais adicionais (por exemplo, 9) para obter uma linha externa. É possível digitar um valor de prefixo de até quatro caracteres (\#, \* e 0 a 9).
    
    > [!NOTE]  
    > Se você especificar um prefixo de acesso externo, não será necessário criar uma nova regra de normalização para acomodar o prefixo.

10. Associe e configure as regras de normalização para o plano de discagem da seguinte maneira:
    
      - Para escolher uma ou mais regras de uma lista de regras de normalização disponível em sua implantação do Enterprise Voice, clique em **Selecionar** . Em **Selecionar as Regras de Normalização** , realce as regras que você deseja associar ao plano de discagem e clique em **OK** .
    
      - Para definir uma nova regra de normalização e associá-la ao plano de discagem, clique em **Novo** . Para obter detalhes sobre como definir uma nova regra, consulte [Definindo regras de normalização no Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - Para editar uma regra de normalização que já está associada ao plano de discagem, realce o nome da regra e clique em **Mostrar detalhes** . Para obter detalhes sobre como editar a regra, consulte [Definindo regras de normalização no Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - Para copiar uma regra de normalização existente a fim de usá-la como um ponto de partida para a definição de uma nova regra, realce o nome da regra e clique em **Copiar** e clique em **Colar** . Para obter detalhes sobre como editar a cópia, consulte [Definindo regras de normalização no Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - Para remover uma regra de normalização do plano de discagem, realce o nome da regra e clique em **Remover** .
    
    > [!NOTE]  
    > Cada plano de discagem precisa ter pelo menos uma regra de normalização associada. Para obter informações sobre como determinar todas as regras de normalização exigidas por um plano de discagem, consulte <a href="lync-server-2013-dial-plans-and-normalization-rules.md">Planos de discagem e regras de normalização no Lync Server 2013</a> na documentação Planejamento.

11. Verifique se as regras de normalização do plano de discagem são organizadas na ordem correta. Para alterar a posição de uma regra na lista, realce o nome da regra e clique na seta para cima ou para baixo.
    
    > [!IMPORTANT]  
    > O Lync Server analisa a lista de regras de normalização do início ao fim e usa a primeira regra que corresponde ao número discado. Se você configurar um plano de discagem de modo que um número discado possa corresponder a mais de uma regra de normalização, certifique-se de que as regras mais restritivas sejam classificadas acima das menos restritivas.<br />    A regra de normalização padrão <strong>Manter todos</strong> <strong>^(\d{11})$</strong> corresponde a qualquer número de 11 dígitos. Por exemplo, se você adicionar uma regra de normalização que corresponda aos números de 11 dígitos que começam com 1425, certifique-se de que <strong>Manter todos</strong> esteja classificada abaixo da regra <strong>^(1425\d{7})$</strong> mais restritiva.

12. (Opcional) Insira um número para testar o plano de discagem e, em seguida, clique em **Ir** . Os resultados do teste são exibidos em **Insira um número de teste** .
    
    > [!NOTE]  
    > É possível salvar um plano de discagem que não passou ainda no teste e reconfigurá-lo mais tarde. Para obter detalhes, consulte <a href="lync-server-2013-test-voice-routing.md">Testar roteamento de voz no Lync Server 2013</a>.

13. Clique em **OK** .

14. Na página **Plano de Discagem** , clique em **Confirmar** e clique em **Confirmar tudo** .
    
    > [!NOTE]  
    > Sempre que você criar um plano de discagem, será necessário executar o comando <strong>Confirmar tudo</strong> para publicar a alteração na configuração. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação Operações.

## Consulte Também

#### Tarefas

[Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### Outros Recursos

[Definindo regras de normalização no Lync Server 2013](lync-server-2013-defining-normalization-rules.md)

