---
title: Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013
TOCTitle: Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013
ms:assetid: 6c53aaf5-218b-4bd4-8cea-31bc9d53f1bd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398511(v=OCS.15)
ms:contentKeyID: 49307033
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Siga estas etapas para modificar uma política de voz. Para criar uma nova política de voz, consulte [Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md) para o procedimento.

> [!NOTE]  
> Se um usuário for atribuído a uma política de voz que não tem registros de uso do PSTN (rede telefônica pública comutada) associados, o usuário não poderá fazer chamadas de saída. Para consultar uma listagem de todos os registros de uso do PSTN disponíveis na implantação do Enterprise Voice e exibir suas propriedades, consulte <a href="lync-server-2013-view-pstn-usage-records.md">Exibir registros de uso PSTN no Lync Server 2013</a>.

## Para modificar uma política de voz

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de Voz** e em **Política de Voz**.

4.  Na página **Política de Voz**, clique duas vezes em um nome de política de voz.
    
    > [!NOTE]  
    > O escopo e o nome foram definidos quando a política de voz foi criada. Eles não podem ser alterados.

5.  (Opcional) Em **Editar Política de Voz**, digite as informações descritivas adicionais para a política de voz.

6.  Marque ou desmarque as seguintes caixas de seleção para habilitar ou desabilitar cada um dos **Recursos de chamada**:
    
      - **Escape de caixa postal** evita que as chamadas sejam encaminhadas imediatamente ao sistema de caixa postal do celular do usuário quando toques simultâneos estão configurados e o telefone está desligado, sem bateria ou sem sinal.
        
        > [!NOTE]  
        > Este recurso só pode ser configurado pelo Shell de Gerenciamento do Lync Server    
      - **Encaminhamento de chamada** permite que os usuários encaminhem chamadas para outros telefones e dispositivos clientes. O Lync Server 2013 proporciona uma gama consideravelmente maior de opções de configuração para encaminhamento de chamadas. Por exemplo, se uma organização não deseja permitir que as chamadas recebidas sejam encaminhadas externamente à PSTN, um administrador pode aplicar um política de voz especial para implantar essa restrição. Habilitado por padrão.
    
      - **Delegação** permite que os usuários especifiquem outros usuários para enviar e receber chamadas em seu nome. No Lync Server 2013, um representante pode configurar toques simultâneos que permitem que as chamadas recebidas para o gerente toquem em todos os destinos de toque simultâneo do representante. Com isso, o representante tem mais flexibilidade para atender a chamadas direcionadas ao gerente. Habilitado por padrão.
    
      - **Transferência de chamadas** permite os usuários transferirem chamadas para outros usuários. Habilitado por padrão.
    
      - **Estacionamento de chamada** permite os usuários estacionarem chamadas em espera e responderem a chamada de um telefone ou cliente diferente. Desabilitado por padrão.
    
      - **Toque simultâneo** permite as chamadas em entrada tocarem em telefones adicionais (por exemplo, um telefone celular) ou outros dispositivos de ponto de extremidade. Lync Server 2013 proporciona uma gama consideravelmente maior de opções de configuração de toque simultâneo. Habilitado por padrão.
    
      - **Chamada em equipe** permite os usuários em uma equipe definida responderem chamadas para outros membros da equipe. Habilitado por padrão.
    
      - **Redirecionamento PSTN** permite que as chamadas realizadas pelos usuários atribuídos com esta política para usuários de outras empresas sejam redirecionados em um PSTN (rede telefônica pública comutada) se o WAN estiver congestionado ou indisponível. Habilitado por padrão.
    
      - **Substituir política de largura de banda** permite os administradores substituírem as decisões da política de CAC (controle de admissão de chamada) de um determinado usuário. Desabilitado por padrão.
        
        > [!NOTE]  
        > A política será substituída apenas para chamadas em entrada do usuário e não para chamadas em saída realizadas pelo usuário. Após a sessão ser estabelecida, o consumo de largura de banda será precisamente registrado. Esta configuração deve ser usada com moderação.    
      - **Rastreamento de chamada mal-intencionada** permite os usuários relatarem chamadas mal-intencionadas (como ameaças de bomba) usando o UI cliente, que sinaliza a chamada nos registros de detalhes de chamada (CDRs). Desabilitado por padrão.

7.  Para associar e configurar os registros de uso PSTN para esta política de voz, faça um dos seguintes:
    
      - Para selecionar um ou mais registros em uma lista de todos os registros de uso do PSTN disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar**. Realce os registros que deseja associar a esta política de voz e clique em **OK**.
    
      - Para remover um registro de uso PSTN desta política de voz, destaque o registro e clique em **Remover**.
    
      - Para definir um novo registro de uso PSTN e associá-lo com esta política de voz, faça o seguinte:
        
        1.  Clique em **Novo**.
        
        2.  No campo **Nome**, insira um nome descritivo exclusivo para o registro. Por exemplo, você pode desejar criar um registro de uso do PSTN chamado **Redmond** para funcionários efetivos localizados em Redmond e outro registro chamado **RedmondTemps** para funcionários temporários.
            
            > [!NOTE]  
            > O nome do registro de uso PSTN deve ser exclusivo na implantação do Enterprise Voice. Após o registro ser salvo, o campo <strong>Nome</strong> não pode ser editado.        
        3.  Use qualquer um dos métodos a seguir para associar e configurar roteamentos para este registro de uso PSTN:
            
              - Para selecionar uma ou mais rotas da lista com todas as rotas disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar**, realce as rotas que deseja associar a este registro de uso do PSTN e clique em **OK**.
            
              - Para remover uma rota do registro de uso PSTN, destaque a rota e clique em **Remover**.
            
              - Para definir uma nova rota e associá-la com este registro de uso PSTN, clique em **Novo**. Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
            
              - Para editar uma rota já associada com este registro de uso PSTN, destaque a rota e clique em **Exibir detalhes**. Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
        
        4.  Clique em **OK**.
    
      - Para editar um registro de uso PSTN já associado com esta política de voz, faça o seguinte:
        
        1.  Realce o registro de uso do PSTN que deseja editar e clique em **Mostrar detalhes**.
        
        2.  Use qualquer um dos métodos a seguir para associar e configurar roteamentos para este registro de uso PSTN:
            
              - Para selecionar uma ou mais rotas da lista com todas as rotas disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar**, realce as rotas que deseja associar a este registro de uso do PSTN e clique em **OK**.
            
              - Para remover uma rota desse registro de uso do PSTN, realce a rota e clique em **Remover**.
            
              - Para definir uma nova rota e associar esse registro de uso do PSTN, clique em **Novo**. Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
            
              - Para editar uma rota que já está associada a esse registro de uso do PSTN, realce a rota e clique em **Mostrar detalhes**. Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
        
        3.  Clique em **OK**.

8.  Organize os registros de uso PSTN para melhor desempenho. Para alterar a posição do registro na lista, destaque o nome do registro e clique na seta para cima ou para baixo.
    
    > [!NOTE]  
    > A ordem na qual os registros de uso PSTN são listados na política de voz é significante. O Lync Server passa pela lista de cima para baixo. Recomendamos que você organize a lista por frequência de uso, por exemplo: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup.

9.  Para associar e configurar registros de uso do PSTN para essa política de voz, execute um destes procedimentos:
    
      - Para usar os mesmos registros de uso do PSTN para encaminhamento de chamadas e toque simultâneo como esta política de voz, selecione a opção **Rotear com usos de PSTN de chamada** no menu suspenso.
    
      - Para permitir o encaminhamento de chamadas e toques simultâneos apenas para usuário do Lync, selecione **Rotear somente para usuários internos do Lync** no menu suspenso. As chamadas não serão encaminhadas para números PSTN externos.
    
      - Para usar registros de uso do PSTN diferentes dos usados nesta política de voz para encaminhamento de chamadas e toque simultâneo, selecione a opção **Rotear com usos de PSTN personalizados** no menu suspenso. Esta opção exibe um controle para selecionar registros de uso do PSTN existentes ou criar novos registros de uso do PSTN, especificamente para encaminhamento de chamadas e toques simultâneos.
        
          - Para escolher um ou mais registros de uma lista de todos os registros de uso do PSTN para encaminhamento de chamadas e toques simultâneos, clique em **Selecionar**. Realce os registros que deseja associar a esta política de encaminhamento de chamadas e toques simultâneos e clique em **OK**.
        
          - Para remover um registro de uso do PSTN desta política de encaminhamento de chamadas e toques simultâneos, realce o registro e clique em **Remover**.
        
          - Para definir um novo registro de uso do PSTN e associá-lo a essa política de encaminhamento de chamadas e toques simultâneos, faça o seguinte:
            
            1.  Clique em **Novo**.
            
            2.  No campo **Nome**, insira um nome descritivo exclusivo para o registro.
                
                > [!NOTE]  
                > O nome do registro de uso do PSTN deve ser exclusivo dentro de implantação do Enterprise Voice. Após a gravação do registro, o campo <strong>Nome</strong> não pode ser editado.            
            3.  Use qualquer um dos métodos a seguir para associar e configurar rotas para este registro de uso do PSTN:
                
                  - Para selecionar uma ou mais rotas da lista com todas as rotas disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar**, realce as rotas que deseja associar a este registro de uso do PSTN e clique em **OK**.
                
                  - Para remover uma rota do registro de uso do PSTN, realce a rota e clique em **Remover**.
                
                  - Para definir uma nova rota e associar esse registro de uso do PSTN, clique em **Novo**. Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
                
                  - Para editar uma rota que já está associada a esse registro de uso do PSTN, realce a rota e clique em **Mostrar detalhes**. Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
            
            4.  Clique em **OK**.
        
          - Para editar um registro de uso do PSTN que já está associado a essa política de voz, faça o seguinte:
            
            1.  Realce o registro de uso do PSTN que deseja editar e clique em **Mostrar detalhes**.
            
            2.  Use qualquer um dos métodos a seguir para associar e configurar rotas para este registro de uso do PSTN:
                
                  - Para escolher um ou mais rotas na lista de todas as rotas disponíveis na sua implantação do Enterprise Voice, clique em **Selecionar**, destaque as rotas que deseja associar com este registro de uso PSTN e clique em **OK**.
                
                  - Para remover uma rota deste registro de uso PSTN, destaque a rota e clique em **Remover**.
                
                  - Para definir uma nova rota e associá-la com este registro de uso PSTN, clique em **Novo**. Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
                
                  - Para editar uma rota já associada com este registro de uso PSTN, destaque a rota e clique em **Exibir detalhes**. Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
            
            3.  Clique em **OK**.

10. (Opcional) Insira um número para testar a política de voz e clique em **Ir** . Os resultados do teste são exibidos em **Número convertido para fazer um teste**.
    
    > [!NOTE]  
    > Você pode salvar uma política de voz que ainda não passou no teste e reconfigurá-la mais tarde. Para obter detalhes, consulte <a href="lync-server-2013-test-voice-routing.md">Testar roteamento de voz no Lync Server 2013</a>.

11. Clique em **OK**.

12. Na página **Política de Voz**, clique em **Confirmar** e em **Confirmar todos**.
    
    > [!NOTE]  
    > Sempre que criar ou modificar uma política de voz, você deve executar o comando <strong>Confirmar todos</strong> para publicar a alteração da configuração. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação de Operações.

13. (Opcional) O escape de caixa postal detecta que uma chamada foi imediatamente atendida pelo correio de voz do celular do usuário e desconecta a chamada à caixa postal do celular. Isso permite que a chamada continue a tocar nos outros pontos de extremidade do usuário, permitindo que ele atenda à chamada. Para obter detalhes a respeito de como configurar uma política de caixa postal, consulte [Configurando escape da caixa postal no Lync Server 2013](lync-server-2013-configuring-voice-mail-escape.md).

## Consulte Também

#### Tarefas

[Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[Exibir registros de uso PSTN no Lync Server 2013](lync-server-2013-view-pstn-usage-records.md)  
[Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md)  
[Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  
[Configurando escape da caixa postal no Lync Server 2013](lync-server-2013-configuring-voice-mail-escape.md)  

#### Outros Recursos

[Testar roteamento de voz no Lync Server 2013](lync-server-2013-test-voice-routing.md)

