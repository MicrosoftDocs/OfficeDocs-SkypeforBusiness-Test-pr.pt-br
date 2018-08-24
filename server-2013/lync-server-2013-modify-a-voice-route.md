---
title: Modificar um roteamento de voz no Lync Server 2013
TOCTitle: Modificar um roteamento de voz no Lync Server 2013
ms:assetid: afc562cc-8807-489b-8850-dbbe1c1ab9f5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412838(v=OCS.15)
ms:contentKeyID: 49307826
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar um roteamento de voz no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este tópico explica como editar uma rota de voz. Para criar uma nova rota, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).

## Para modificar uma rota de voz

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Roteamento de voz** e, em seguida, clique em **Rota**.

4.  Na página **Rota**, use um dos métodos a seguir par modificar uma rota de voz:
    
      - Clique no nome de uma rota de voz, clique em **Editar** e em **Exibir detalhes**.
    
      - Clique no nome de uma rota de voz, clique em **Editar**, **Copiar** e, em seguida, em **Colar**. Clique na nova cópia da rota de voz que você acabou de criar, clique em **Editar** e em **Exibir detalhes**.

5.  No campo **Nome** na página **Editar Rota de Voz**, digite um nome descritivo para a rota de voz.

6.  (Opcional) No campo **Descrição**, digite informações descritivas adicionais para a rota de voz.

7.  Para especificar os padrões a serem acomodados por esta rota, você pode usar a ferramenta **Compilar um padrão para correspondência** para gerar uma expressão regular ou a escreva manualmente.
    
      - Para usa a ferramenta **Compilar um padrão para correspondência** para gerar uma expressão regular, insira os valores da forma a seguir. Você pode especificar dois tipos de correspondência de padrão:
        
          - **Dígitos iniciais para números que você deseja permitir:** Insira valores de prefixo que esta rota deve acomodar (incluindo o caractere + à esquerda, se necessário). Por exemplo, digite **+425** e clique em **Adicionar**. Repita este procedimento para cada valor de prefixo que deseja incluir na rota.
        
          - **Exceções:** se deseja especificar uma ou mais exceções para um valor de prefixo, marque o prefixo e clique em **Exceções**. Digite um ou mais valores de padrões correspondentes que você *não* deseja que essa rota acomode. Por exemplo, para excluir números que começam com +425237 da rota, digite o valor **+425237** no campo **Exceções** e clique em **OK**.
    
      - Para definir o padrão de correspondência manualmente, clique em **Editar** na ferramenta **Compilar um padrão para correspondência** e digite uma expressão regular do .NET Framework para especificar um padrão de correspondência para números de telefone de destino para os quais a rota será aplicada. Pra informações sobre como escrever expressões regulares, consulte "Expressões Regulares do .NET Framework" em [http://go.microsoft.com/fwlink/?linkid=140927\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=140927%26clcid=0x416).

8.  Selecione **Suprimir ID de chamadas** se não deseja que a ID do telefone que faz a chamada de saída apareça para o destinatário da chamada. Se você selecionar essa opção, é necessário especificar uma **ID de chamada alternativa** que aparecerá na tela do ID de chamada do destinatário.

9.  Para associar um ou mais troncos PSTN À rota de voz, clique em **Adicionar** e selecione um tronca da lista.
    
    > [!NOTE]  
    > Se sua implantação incluir Servidores de Mediação do Microsoft Office Communications Server 2007 R2, eles também estarão disponíveis na lista.

10. Para associar um ou mais usos do PSTN à rota de voz, clique em **Selecionar** e escolha um registro da lista de registros de uso do PSTN que foram definidos para a sua implantação Enterprise Voice.
    
    > [!NOTE]  
    > Para exibir as propriedades de cada um dos registros de uso do PSTN disponíveis, consulte <a href="lync-server-2013-view-pstn-usage-records.md">Exibir registros de uso PSTN no Lync Server 2013</a>.<br />    Para criar ou editar registros de uso do PSTN, consulte <a href="lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md">Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013</a> ou <a href="lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md">Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013</a>.

11. Organize os registros de uso do PSTN para proporcionar um desempenho ideal. Para mudar a posição de um registro, destaque o nome do registro e clique na seta para cima ou para baixo
    
    > [!NOTE]  
    > Contrastando com a política de voz, em que a ordem em que os registros de uso do PSTN são listados é importante, a ordem dos registros de uso do PSTN em uma rota de voz é insignificante.No entanto, é recomendável organizar a lista por frequência de uso, por exemplo: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup. (Lync Server atravessa a lista do início ao fim).

12. (Opcional) Digite um valor no campo **Insira um número convertido para testar** e clique em **Ir**. Os resultados do teste são exibidos abaixo do campo.
    
    > [!NOTE]  
    > Você pode salvar uma rota de voz que ainda não passou no teste e reconfigurá-la depois. Para detalhes, consulte <a href="lync-server-2013-test-voice-routing.md">Testar roteamento de voz no Lync Server 2013</a>.

13. Clique em **OK**.

14. Na página **Rota**, clique em **Confirmar** e em **Confirmar tudo**.
    
    > [!NOTE]  
    > Toda vez que criar ou modificar uma rota de voz, você deve executar o comando <strong>Confirmar tudo</strong> para publicar a alteração na configuração. Para detalhes, consulte, <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação de Operações.

## Consulte Também

#### Tarefas

[Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md)  
[Exibir registros de uso PSTN no Lync Server 2013](lync-server-2013-view-pstn-usage-records.md)  
[Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### Outros Recursos

[Testar roteamento de voz no Lync Server 2013](lync-server-2013-test-voice-routing.md)

