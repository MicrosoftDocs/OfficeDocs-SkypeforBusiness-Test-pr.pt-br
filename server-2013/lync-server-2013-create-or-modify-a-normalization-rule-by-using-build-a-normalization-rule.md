---
title: 'Lync Server 2013: Criar ou modificar uma regra de normalização usando a Regra Construir uma Normalização'
TOCTitle: Criar ou modificar uma regra de normalização usando a Regra Construir uma Normalização
ms:assetid: e8547d7b-f74d-4a73-9a7d-df20d7a87fcd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399036(v=OCS.15)
ms:contentKeyID: 49308460
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar uma regra de normalização usando a Regra Construir uma Normalização no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Execute as etapas a seguir se quiser criar ou modificar uma regra de normalização usando Construir Regra de Normalização no Painel de Controle do Lync Server. Como alternativa, se quiser criar uma regra de normalização manualmente, consulte [Criar ou modificar uma regra de normalização manualmente no Lync Server 2013](lync-server-2013-create-or-modify-a-normalization-rule-manually.md).

## Para definir uma regra usando Compilar uma Regra de Normalização

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  (Opcional) Execute as etapas em [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md) até a etapa 11 ou [Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md) até a etapa 10.

4.  Em **Nova Regra de Normalização** ou **Editar Regra de Normalização** , digite um nome que descreva o padrão numérico que está sendo normalizado em **Nome** (por exemplo, **5DigitExtension** ).

5.  (Opcional) Em **Descrição** , digite uma descrição da regra de normalização (por exemplo, "Converte extensões de cinco dígitos").

6.  Em **Compilar uma Regra de Normalização** , digite valores nos campos a seguir:
    
      - **Dígitos iniciais**    (Opcional) Especifique os dígitos iniciais dos números discados aos quais você deseja que o padrão corresponda. Por exemplo, digite **425** se quiser que o padrão corresponda aos números discados que comecem com 425.
    
      - **Tamanho**    Especifique o número de dígitos no padrão de correspondência e selecione se deseja que o padrão corresponda exatamente a esse tamanho, corresponda aos números discados menores do que esse tamanho ou corresponda aos números discados de qualquer tamanho.
    
      - **Dígitos a serem removidos**    (Opcional) Especifique o número de dígitos iniciais a serem removidos dos números discados aos quais você deseja que o padrão corresponda.
    
      - **Dígitos a adicionar**    (Opcional) Especifique dígitos a serem adicionados aos números discados aos quais você deseja que o padrão corresponda.
    
    Os valores inseridos nesses campos são refletidos em **Padrão a ser correspondido** e **Regra de conversão** . Por exemplo, se você deixar **Dígitos iniciais** vazio, digite **7** no campo **Tamanho** e selecione **Exatamente** e especifique **0** em **Dígitos a serem removidos** , a expressão regular resultante em **Padrão a ser correspondido** será:
    
    **^(\\d{7})$**

7.  Em **Regra de conversão** , especifique um padrão para o formato de números de telefone E.164 convertido da seguinte maneira:
    
      - Um valor que representa o número de dígitos especificado no padrão de correspondência. Por exemplo, se o padrão de correspondência for **^(\\d{7})$** , **$1** na regra de conversão representará números discados de sete dígitos.
    
      - (Opcional) Digite um valor no campo **Dígitos a adicionar** para especificar os dígitos a serem anexados ao número convertido, (por exemplo **+1425** ).
    
    Por exemplo, se **Padrão a ser correspondido** contiver **^(\\d{7})$** como padrão para números discados e **Regra de conversão** contiver **+1425$1** como o padrão para números de telefone E.164, a regra normalizará 5550100 para +14255550100.

8.  (Opcional) Se a regra de normalização resulta em um número de telefone interno à sua organização, selecione **Extensão interna** .

9.  (Opcional) Insira um número para testar a regra de normalização e clique em **Ir** . Os resultados do teste são exibidos em **Inserir um número para testar** .
    
    > [!NOTE]  
    > É possível salvar uma regra de normalização que ainda não passou no teste e reconfigurá-la posteriormente. Para obter detalhes, consulte <a href="lync-server-2013-test-voice-routing.md">Testar roteamento de voz no Lync Server 2013</a>.

10. Clique em **OK** para salvar a regra de normalização.

11. Clique em **OK** para salvar o plano de discagem.

12. Na página **Plano de Discagem** , clique em **Confirmar** e clique em **Confirmar tudo** .
    
    > [!NOTE]  
    > Sempre que criar ou alterar uma regra de normalização, você deve executar o comando <strong>Confirmar todos</strong> para publicar a alteração na configuração. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação de Operações.

## Consulte Também

#### Tarefas

[Criar ou modificar uma regra de normalização manualmente no Lync Server 2013](lync-server-2013-create-or-modify-a-normalization-rule-manually.md)  
[Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md)  
[Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### Outros Recursos

[Testar roteamento de voz no Lync Server 2013](lync-server-2013-test-voice-routing.md)

