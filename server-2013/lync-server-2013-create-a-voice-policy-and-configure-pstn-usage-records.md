---
title: Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013
TOCTitle: Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013
ms:assetid: e6ff27e0-e2d1-4445-840f-08f738200c20
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399027(v=OCS.15)
ms:contentKeyID: 49308439
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Siga essas etapas se quiser criar uma nova política de voz. Se quiser editar uma política de voz, consulte [Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md) para ver o procedimento.

> [!NOTE]  
> Cada política de voz precisa ter pelo menos um registro de uso de PSTN (Rede Telefônica Pública Comutada) associada. Para ver uma lista de todos os registros de uso de PSTN disponível em sua implantação do Enterprise Voice e ver suas propriedades, consulte <a href="lync-server-2013-view-pstn-usage-records.md">Exibir registros de uso PSTN no Lync Server 2013</a>.

## Para criar uma política de voz

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de Voz** e clique em **Política de Voz**.

4.  Na página **Política de Voz**, clique em **Novo** e selecione um escopo para a nova política:
    
      - **Política do site** se aplica a todo um site, exceto algum usuário ou grupo que tenha recebido uma política de usuário. Se você selecionar Site para um escopo de política, escolha o site na caixa de diálogo **Selecionar um Site**. Se uma política de voz tiver sido criada para um site, o site não aparece na caixa de diálogo **Selecionar um Site**.
    
      - **Política de usuário** pode ser aplicado a usuários ou grupos especificados.

5.  Se o escopo da política de voz for Usuário, digite um nome descritivo para a política no campo **Nome**.
    
    > [!NOTE]  
    > Se o escopo da política de voz for Site, o campo <strong>Nome</strong> na <strong>Nova Política de Voz</strong> será pré-preenchido com o nome do site e não poderá ser alterado.

6.  (Opcional) Insira informações descritivas adicionais para a política de voz.

7.  Marque ou desmarque as caixas de seleção a seguir para habilitar ou desabilitar cada um dos **Recursos de chamada** para esta política de voz:
    
      - **Escape de caixa postal** impede que chamadas sejam imediatamente encaminhadas ao sistema de caixa postal do telefone celular do usuário quando o toque simultâneo estiver configurado e o telefone estiver desligado, sem bateria, ou fora de área.
        
        > [!NOTE]  
        > Este recurso é configurável apenas através do Shell de Gerenciamento do Lync Server    
      - **Encaminhamento de chamadas** permite que os usuários encaminhem chamadas a outros telefones e dispositivos clientes. O Lync Server 2013 oferece uma gama significativamente maior de opções de configuração de encaminhamento de chamadas. Por exemplo, se uma organização não deseja permitir que chamadas de entrada sejam encaminhadas externamente à PSTN, um administrador por aplicar uma política especial de voz para implantar esta restrição. Habilitado por padrão.
    
      - **Delegação** permite que o usuário especifique outros usuários para enviar e receber chamadas em seu nome. No Lync Server 2013, um delegado pode configurar toque simultâneo, o que permite que chamadas de entrada ao seu gerente façam com que todos os destinos de toque simultâneo do delegado toquem. Isso oferece uma maior flexibilidade ao delegado em responder chamadar direcionadas ao gerente. Habilitado por padrão.
    
      - **Transferência de chamada** permite a transferência de chamadas para outros usuários. Habilitado por padrão.
    
      - **Estacionamento de chamada** permite que os usuários estacionem chamadas em espera e atendam à chamada de um telefone ou cliente diferente. Desabilitado por padrão.
    
      - **Toque simultâneo** permite que as chamadas recebidas toquem em telefones adicionais (por exemplo, um celular) ou outros dispositivos de pontos de extremidade. O Lync Server 2013 oferece uma gama significativamente maior de opções de configuração para toque simultâneo. Habilitado por padrão.
    
      - **Chamada de equipe** permite que os usuários de uma equipe definida respondam às chamadas de outros membros da equipe. Habilitado por padrão.
    
      - **Redirecionamento de PSTN** permite que as chamadas realizadas por usuários que receberam essa política para outros usuários empresariais sejam redirecionadas na PSTN (Rede Telefônica Pública Comutada) se a WAN estiver congestionada ou indisponível. Habilitado por padrão.
    
      - **Substituição da política de largura de banda** permite que os administradores substituam as decisões da política de controle de admissão de chamada para um usuário específico. Desabilitada por padrão.
        
        > [!NOTE]  
        > A política será substituída somente para chamadas de entrada para o usuário e não para chamadas de saída feitas pelo usuário. Após o estabelecimento da sessão, o consumo de largura de banda será registrado de forma precisa. Essa configuração deve ser usada com moderação e deve ser reservado em prol de decisões apropriadas de controle de chamada.    
      - **Rastreamento de chamada mal-intencionada** permite que os usuários reportem chamadas mal intencionadas (como ameaças de bomba) usando a UI do cliente, o que por sua vez marca as chamadas nos CDRs (registros de detalhe da chamada). Desabilitado por padrão.

8.  Para associar e configurar registros de uso do PSTN para essa política de voz, execute um destes procedimentos:
    
      - Para escolher um ou mais registros de uma lista de todos os registros de uso de PSTN disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar**. Realce os registros que você deseja associar a essa política de voz e clique em **OK**.
    
      - Para remover um registro de uso de PSTN desta política de voz, realce o registro e clique em **Remover**.
    
      - Para definir um novo registro de uso PSTN e associá-lo a essa política de voz, faça o seguinte:
        
        1.  Clique em **Novo**.
        
        2.  No campo **Nome**, digite um nome descritivo para o registro. Por exemplo, convém criar um registro de uso PSTN chamado **Redmond** para funcionários em tempo integral localizados em Redmond e outro chamado **RedmondTemps** para funcionários temporários.
            
            > [!NOTE]  
            > O nome do registro de uso de PSTN deve ser exclusivo dentro de implantação do Enterprise Voice. Após a gravação do registro, o campo <strong>Nome</strong> não pode ser editado.        
        3.  Use qualquer um dos métodos a seguir para associar e configurar rotas para este registro de uso do PSTN:
            
              - Para escolher uma ou mais rotas da lista de todas as rotas disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** , realce as rotas que você deseja associar a esse registro de uso do PSTN e clique em **OK** .
            
              - Para remover uma rota do registro de uso do PSTN, realce a rota e então clique em **Remover**.
            
              - Para definir uma nova rota e associar esse registro de uso do PSTN, clique em **Novo**. Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
            
              - Para editar uma rota que já está associada a esse registro de uso do PSTN, realce a rota e clique em **Mostrar detalhes**. Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
        
        4.  Clique em **OK**.
    
      - Para editar um registro de uso de PSTN que já está associado a essa política de voz, faça o seguinte:
        
        1.  Realce o registro de uso do PSTN que você deseja editar e então clique em **Mostrar detalhes**.
        
        2.  Use qualquer um dos métodos a seguir para associar e configurar rotas para este registro de uso do PSTN:
            
              - Para escolher uma ou mais rotas da lista de todas as rotas disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** , realce as rotas que você deseja associar a esse registro de uso do PSTN e clique em **OK** .
            
              - Para remover uma rota desse registro de uso do PSTN, realce a rota e então clique em **Remover**.
            
              - Para definir uma nova rota e associar esse registro de uso do PSTN, clique em **Novo**. Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
            
              - Para editar uma rota que já está associada a esse registro de uso do PSTN, realce a rota e clique em **Mostrar detalhes**. Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
        
        3.  Clique em **OK**.

9.  Organize os registros de uso do PSTN para obter o melhor desempenho. Para alterar a posição de um registro na lista, realce o nome de registro e clique na seta para cima ou para baixo.
    
    > [!IMPORTANT]  
    > A ordem na qual PSTN registros de uso são listados na diretiva de voz é significativa. Lync Serverpercorre a lista de cima para baixo. Recomendamos que você organize a lista por freqüência de uso, por exemplo: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup.

10. Para associar e configurar registros de uso do PSTN para enchaminhamento de chamadas e toque simultâneo nesta política de voz, execute um destes procedimentos:
    
      - Para usar os mesmos registros de uso de PSTN para enchaminhamento de chamadas e toque simultâneo que esta política de voz, selecione a opção **Encaminhar usando os usos de PSTN da chamada** no menu suspenso.
    
      - Para permitir enchaminhamento de chamadas e toque simultâneo apenas a usuários internos do Lync, selecione a opção **Encaminhar apenas para usuários internos do Lync** no menu suspenso. As chamadas não serão encaminhadas para números PSTN externos.
    
      - Para especificar registros de uso de PSTN diferentes para encaminhamento de chamadas e toque simultâneos que os usados para esta política de voz, selecione a opção **Encaminhar usando usos de PSTN personalizados** no menu suspenso. Essa opção exibe um controle para selecionar registros de uso de PSTN existentes ou criar novos registros de uso de PSTN especificamente para encaminhamento de chamadas e toque simultâneo.
        
          - Para selecionar um ou mais registros de uma lista de registros de uso de PSTN para encaminhamento de chamadas e toque simultâneo, clique em **Selecionar**. Realce os registros que você deseja associar a essa política de encaminhamento de chamada e toque simultâneo, e então clique em **OK**.
        
          - Para remover um registro de uso de PSTN desta política de encaminhamento de chamadas e toque simultâneo, realce o registro e clique em **Remover**.
        
          - Para definir um novo registro de uso de PSTN e associá-lo a esta política de encaminhamento de chamadas e toque simultâneo, siga estes passos:
            
            1.  Clique em **Novo**.
            
            2.  No campo **Nome**, digite um nome descritivo para o registro.
                
                > [!NOTE]  
                > O nome do registro de uso de PSTN deve ser exclusivo dentro de implantação do Enterprise Voice. Após a gravação do registro, o campo <strong>Nome</strong> não pode ser editado.            
            3.  Use qualquer um dos métodos a seguir para associar e configurar rotas para este registro de uso do PSTN:
                
                  - Para escolher uma ou mais rotas da lista de todas as rotas disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** , realce as rotas que você deseja associar a esse registro de uso do PSTN e clique em **OK** .
                
                  - Para remover uma rota do registro de uso do PSTN, realce a rota e clique em **Remover**.
                
                  - Para definir uma nova rota e associar esse registro de uso do PSTN, clique em **Novo**. Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
                
                  - Para editar uma rota que já está associada a esse registro de uso do PSTN, realce a rota e clique em **Mostrar detalhes**. Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
            
            4.  Clique em **OK**.
        
          - Para editar um registro de uso de PSTN que já está associado a essa política de voz, faça o seguinte:
            
            1.  Realce o registro de uso do PSTN que você deseja editar e clique em **Mostrar detalhes**.
            
            2.  Use qualquer um dos métodos a seguir para associar e configurar rotas para este registro de uso do PSTN:
                
                  - Para escolher uma ou mais rotas da lista de todas as rotas disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** , realce as rotas que você deseja associar a esse registro de uso do PSTN e clique em **OK** .
                
                  - Para remover uma rota desse registro de uso do PSTN, realce a rota e clique em **Remover**.
                
                  - Para definir uma nova rota e associar esse registro de uso do PSTN, clique em **Novo**. Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
                
                  - Para editar uma rota que já está associada a esse registro de uso do PSTN, realce a rota e clique em **Mostrar detalhes**. Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
            
            3.  Clique em **OK**.

11. (Opcional) Insira um número para testar a política de voz e clique em **Ir** . Os resultados do teste são exibidos em **Número convertido para fazer um teste**.
    
    > [!NOTE]  
    > É possível salvar uma política de voz que não passou ainda no teste e reconfigurá-la mais tarde. Para obter detalhes, consulte <a href="lync-server-2013-test-voice-routing.md">Testar roteamento de voz no Lync Server 2013</a>.

12. Clique em **OK**.

13. Na página **Política de Voz**, clique em **Confirmar** e clique em **Confirmar tudo**.
    
    > [!NOTE]  
    > Sempre que você criar ou modificar uma política de voz, será necessário executar o comando <strong>Confirmar tudo</strong> para publicar a alteração de configuração. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação Operações.

14. (Opcional) O Escape de Caixa Postal detecta que uma chamada foi imediatamente atendida pela caixa postal do celular do usuário e desconecta a chamada da caixa postal de telefone celular. Isso permite que uma chamada continue a tocar nos outros pontos de extremidade do usuário, dando ao usuário a oportunidade de atender uma chamada. Para obter detalhes sobre como configurar uma política de caixa postal, consulte [Configurando escape da caixa postal no Lync Server 2013](lync-server-2013-configuring-voice-mail-escape.md).

## Consulte Também

#### Tarefas

[Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)  
[Exibir registros de uso PSTN no Lync Server 2013](lync-server-2013-view-pstn-usage-records.md)  
[Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md)  
[Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  
[Configurando escape da caixa postal no Lync Server 2013](lync-server-2013-configuring-voice-mail-escape.md)  

#### Outros Recursos

[Testar roteamento de voz no Lync Server 2013](lync-server-2013-test-voice-routing.md)

