---
title: 'Lync Server 2013: Modificar um plano de discagem'
TOCTitle: Modificar um plano de discagem
ms:assetid: a91f02df-cf60-40cf-82fe-e0342c118b91
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412797(v=OCS.15)
ms:contentKeyID: 49307737
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar um plano de discagem no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Para modificar um plano de discagem existente, execute as etapas do procedimento a seguir. Se quiser criar um novo plano de discagem, consulte [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md).

## Para modificar um plano de discagem

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de Voz** e clique em **Plano de Discagem**.

4.  Na página **Plano de Discagem**, dê um duplo clique no nome de um plano de discagem.
    
    > [!NOTE]  
    > O escopo e o nome do plano de discagem foram definidos quando o plano de discagem foi criado. Eles não podem ser alterados.

5.  (Opcional) Em **Editar Plano de Discagem**, edite o campo **Nome simples**, que é pré-preenchido com o mesmo nome que aparece no campo **Nome** para especificar um nome mais descritivo que reflita o site, serviço ou usuário para o qual o plano de discagem se aplica.
    
    > [!IMPORTANT]  
    > O <strong>Nome simples</strong> precisa ser exclusivo entre os planos de discagem dentro da implantação do Lync Server 2013. Ele não pode exceder 256 caracteres Unicode, e cada um deles pode ser um caractere alfabético ou numérico, um hífen (-), um ponto (.), um sinal de adição (+) ou um sublinhado (_).<br />    Espaços não são permitidos no campo <strong>Nome simples</strong>.

6.  (Opcional) No campo **Descrição**, digite informações descritivas sobre o plano de discagem.

7.  (Opcional) Se você quiser usar esse plano de discagem como uma região para números de acesso de discagem, especifique uma **Região de conferência de discagem**. Se você não quiser usar esse plano de discagem para números de acesso de discagem, deixe esse campo vazio.
    
    > [!NOTE]  
    > As regiões de conferência d discagem são necessárias para associar números de acesso de conferência de discagem a um ou mais planos de discagem.

8.  (Opcional) No campo **Prefixo de acesso externo**, especifique um valor somente se usuários precisarem discar um ou mais dígitos primeiro para obter uma linha externa (por exemplo, 9). Você pode digitar um valor de prefixo de até quatro caracteres (isto é, \#, \* e 0-9).
    
    > [!NOTE]  
    > Se você especificar um prefixo de acesso externo, não será necessário criar uma nova regra de normalização para acomodar o prefixo.

9.  Associe e configure regras de normalização para o plano de discagem:
    
      - Para escolher uma ou mais regras de uma lista de todas as regras de normalização disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar**. Na caixa de diálogo **Selecionar Regras de Normalização**, destaque as regras que deseja associar ao plano de discagem e clique em **OK**.
    
      - Para definir uma nova regra de normalização e associá-la ao plano de discagem, clique em **Novo**. Para obter detalhes sobre como definir uma nova regra, consulte [Definindo regras de normalização no Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - Para editar uma regra de normalização que já está associada ao plano de discagem, realce o nome da regra e clique em **Mostrar detalhes**. Para obter detalhes sobre como editar a regra, consulte [Definindo regras de normalização no Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - Para copiar uma regra de normalização existente a fim de usá-la como um ponto de partida para a definição de uma nova regra, realce o nome da regra e clique em **Copiar** e clique em **Colar**. Para obter detalhes sobre como editar a cópia, consulte [Definindo regras de normalização no Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - Para remover uma regra de normalização do plano de discagem, realce o nome da regra e clique em **Remover**.
    
    > [!NOTE]  
    > Cada plano de discagem deve ter no mínimo uma regra de normalização associada. Para detalhes sobre como determinar todas as regras de normalização necessárias para um plano de discagem, consulte <a href="lync-server-2013-dial-plans-and-normalization-rules.md">Planos de discagem e regras de normalização no Lync Server 2013</a> na documentação de Planejamento.

10. Verifique se as regras de normalização do plano de discagem são organizadas na ordem correta. Para alterar a posição de uma regra na lista, realce o nome da regra e clique na seta para cima ou para baixo.
    
    > [!IMPORTANT]  
    > O Lync Server analisa a lista de regras de normalização do início ao fim e usa a primeira regra que corresponde ao número discado. Se você configurar um plano de discagem de modo que um número discado possa corresponder a mais de uma regra de normalização, certifique-se de que as regras mais restritivas sejam classificadas acima das menos restritivas.<br />    A regra de normalização padrão <strong>Manter todos</strong> <strong>^(\d{11})$</strong> corresponde a qualquer número de 11 dígitos. Se, por exemplo, você adicionar uma regra de normalização que corresponda a números de 11 dígitos que começam com 1425, certifique-se de que <strong>Manter todos</strong> esteja classificado abaixo da regra <strong>^(1425\d{7})$</strong> mais restritiva.

11. (Opcional) Insira um número para testar o plano de discagem e, em seguida, clique em **Ir** . Os resultados do teste são exibidos em **Insira um número de teste** .
    
    > [!NOTE]  
    > É possível salvar um plano de discagem que não passou ainda no teste e reconfigurá-lo mais tarde. Para obter detalhes, consulte <a href="lync-server-2013-test-voice-routing.md">Testar roteamento de voz no Lync Server 2013</a>.

12. Clique em **OK**.

13. Na página **Plano de Discagem**, clique em **Confirmar** e clique em **Confirmar tudo**.
    
    > [!NOTE]  
    > Sempre que criar ou modificar um plano de discagem, você deve executar o comando <strong>Confirmar tudo</strong> para publicar as alterações de configuração. Para detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação de Operações.

## Consulte Também

#### Tarefas

[Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### Outros Recursos

[Definindo regras de normalização no Lync Server 2013](lync-server-2013-defining-normalization-rules.md)

