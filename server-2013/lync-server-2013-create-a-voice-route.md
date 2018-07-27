---
title: Criar um roteamento de voz no Lync Server 2013
TOCTitle: Criar um roteamento de voz no Lync Server 2013
ms:assetid: d189057d-cc9d-4622-9d10-f5385d703faf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398898(v=OCS.15)
ms:contentKeyID: 49308196
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar um roteamento de voz no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O procedimento a seguir explica como criar uma nova rota de voz usando o Painel de Controle do Lync Server 2013. Para editar uma rota existente, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md) para ver o procedimento.

## Para criar uma rota de voz usando o Painel de Controle do Lync Server

1.  Faça logon no computador como membro do grupo RTCUniversalServerAdmins ou como membro da função administrativa **CsVoiceAdministrator**, **CsServerAdministrator** ou **CsAdministrator**.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de Voz**.

4.  Clique em **Rota**.

5.  Clique em **Novo** para exibir a caixa de diálogo **Nova Rota de Voz**.

6.  No campo **Nome**, digite o nome descritivo da rota de voz.

7.  (Opcional) Em **Descrição**, digite outras informações descritivas para a rota de voz.

8.  Para especificar os padrões que você deseja acomodar com essa rota, é possível usar a ferramenta **Compilar um padrão para correspondência** para gerar uma expressão regular ou escrever manualmente a expressão regular.
    
      - Para usar a ferramenta **Compilar um padrão para correspondência** para gerar uma expressão regular, digite os valores da seguinte maneira. É possível especificar dois tipos de correspondência de padrão:
        
          - **Dígitos iniciais para números que você deseja permitir:** digite valores de prefixo que essa rota deve acomodar (incluindo o + inicial, se for necessário). Por exemplo, digite **+425** e clique em **Adicionar**. Repita isso para cada valor de prefixo que você deseja incluir na rota.
        
          - **Exceções:** se você deseja especificar uma ou mais exceções para números para um valor de prefixo, relace o prefixo e clique em **Exceções**. Digite um ou mais valores para os padrões de correspondência que você *não* deseja acomodar com essa rota. Por exemplo, para excluir números que começam com +425237 da rota, digite um valor de **+425237** no campo **Exceções** e clique em **OK**.
    
      - Para definir manualmente um padrão de correspondência, clique em **Editar** na ferramenta **Compilar um padrão para correspondências** e digite uma expressão .NET Framework regular para especificar o padrão de correspondência para números de telefone de destino aos quais a rota é aplicada. Para obter informações sobre como escrever expressões regulares, consulte "Expressões Regulares do .NET Framework" em [http://go.microsoft.com/fwlink/?linkid=140927\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=140927%26clcid=0x416).

9.  Selecione **Suprimir ID de chamadas** se não quiser que o ID do telefone que está fazendo a chamada apareça no destinatário da chamada. Se você selecionar essa opção, especifique um **ID de chamadas alternativo** que aparecerá no display de ID da chamada do destinatário.

10. Para associar um ou mais troncos à rota de voz, clique em **Adicionar** e selecione um tronco SIP ou gateway na lista.
    
    > [!NOTE]  
    > Se sua implantação incluir quaisquer Servidores de Mediação do Microsoft Office Communications Server 2007 R2, eles também estarão disponíveis na lista.

11. Para associar um ou mais uso do PSTN à rota de voz, clique em **Selecionar** e escolha um registro na lista de registros de uso PSTN definida para sua implantação do Enterprise Voice.
    
    > [!NOTE]  
    > Para exibir as propriedades de cada um dos registros de uso PSTN disponíveis, consulte <a href="lync-server-2013-view-pstn-usage-records.md">Exibir registros de uso PSTN no Lync Server 2013</a>.<br />    Para criar ou editar registros de uso de PSTN, consulte <a href="lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md">Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013</a> ou <a href="lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md">Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013</a>.

12. Organize os registros de uso do PSTN para obter o melhor desempenho. Para alterar a posição de um registro na lista, realce o nome de registro e clique na seta para cima ou para baixo.
    
    > [!NOTE]  
    > Em contraste à política de voz, onde a ordem no qual os registros de uso PSTN estão listados é importante, a ordem na qual os registros de uso PSTN estão listados na rota de voz é insignificante. No entanto, recomendamos organizar a lista por frequência de uso. Por exemplo: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup. (o Lync Server atravessa a lista de cima para baixo.)

13. (Opcional) Digite um valor no campo **Insira um número convertido para testar** e clique em **Ir**. Os resultados do teste são exibidos abaixo do campo.
    
    > [!NOTE]  
    > É possível salvar uma rota de voz que não passou ainda no teste e reconfigurá-la mais tarde. Para obter detalhes, consulte <a href="lync-server-2013-test-voice-routing.md">Testar roteamento de voz no Lync Server 2013</a>.

14. Clique em **OK** para salvar a rota de voz.

> [!IMPORTANT]  
> Sempre que você criar uma rota de voz, deverá executar o comando <strong>Confirmar tudo</strong> para publicar a alteração da configuração. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a>.

## Consulte Também

#### Tarefas

[Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md)  
[Exibir registros de uso PSTN no Lync Server 2013](lync-server-2013-view-pstn-usage-records.md)  
[Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### Outros Recursos

[Testar roteamento de voz no Lync Server 2013](lync-server-2013-test-voice-routing.md)

