---
title: 'Lync Server 2013: Criar ou modificar uma regra de normalização manualmente'
TOCTitle: Criar ou modificar uma regra de normalização manualmente
ms:assetid: fc0335e6-8830-4cfb-8c64-6aeb98c0a992
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413074(v=OCS.15)
ms:contentKeyID: 49308701
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar uma regra de normalização manualmente no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-22_

Conclua as etapas a seguir para criar ou modificar uma regra de normalização manualmente. Para criar ou modificar uma regra de normalização usando Construir uma Regra de Normalização no Painel de Controle do Lync Server, consulte [Criar ou modificar uma regra de normalização usando a Regra Construir uma Normalização no Lync Server 2013](lync-server-2013-create-or-modify-a-normalization-rule-by-using-build-a-normalization-rule.md).

## Para definir uma regra de normalização manualmente

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  (Opcional) Siga as etapas em [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md) ou [Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md).

4.  Em **Nova regra de normalização** ou **Editar regra de normalização** , digite um nome que descreve o padrão de número que está sendo normalizado em **Nome** (por exemplo, o nome da regra de normalização **5DigitExtension** ).

5.  (Opcional) No campo **Descrição** , digite uma descrição da regra de normalização (por exemplo, "Traduzir extensões de 5 dígitos").

6.  Em **Criar uma regra de normalização** , clique em **Editar** .

7.  Digite o seguinte em **Digitar uma expressão regular** :
    
      - Em **Corresponder este padrão** , especifique o padrão que você deseja usar para coincidir com o número de telefone discado.
    
      - Em **Regra de tradução** , especifique um padrão para o formato dos números de telefone E.164 traduzidos.
    
    Por exemplo, se você digitar **^ (\\d{7})$** em **Corresponder este padrão** e **+1425$1** em **Regra de tradução** , a regra normaliza 5550100 para +14255550100.

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

[Criar ou modificar uma regra de normalização usando a Regra Construir uma Normalização no Lync Server 2013](lync-server-2013-create-or-modify-a-normalization-rule-by-using-build-a-normalization-rule.md)  
[Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md)  
[Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### Outros Recursos

[Testar roteamento de voz no Lync Server 2013](lync-server-2013-test-voice-routing.md)

