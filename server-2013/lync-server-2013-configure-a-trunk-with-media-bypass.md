---
title: 'Lync Server 2013: Configurar um tronco com bypass de mídia'
TOCTitle: Configurar um tronco com bypass de mídia
ms:assetid: 99d729ea-5a4c-4ff2-a4a3-93a24368da6d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398792(v=OCS.15)
ms:contentKeyID: 49307567
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar um tronco com bypass de mídia no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Siga as próximas etapas para configurar um tronco com bypass de mídia habilitado. Para configurar um tronco com bypass de mídia desabilitado, consulte [Configurar um tronco sem bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md). O bypass de mídia é útil quando você deseja minimizar o número de Servidores de Mediação implantados. Em geral, um pool de Servidores de Mediação será implantado em um local central e controlará gateways em filiais. A habilitação do bypass de mídia permite que a mídia de chamadas de PSTN (Rede Telefônica Pública Comutada) de clientes em locais de filiais flua diretamente pelos gateways nesses locais. As rotas de chamada de saída do Lync Server 2013 e as políticas do Enterprise Voice devem ser configuradas corretamente para que as chamadas de PSTN de clientes em uma filial sejam roteadas para o gateway apropriado.

É altamente recomendável habilitar o bypass de mídia. No entanto, antes de habilitá-lo em um tronco SIP, confirme se seu provedor do tronco SIP oferece suporte ao bypass de mídia e pode acomodar os requisitos para habilitar o cenário com êxito. Especificamente, o provedor deve ter os endereços IP dos servidores na rede interna da sua organização. Se o provedor não oferecer suporte a este cenário, o bypass de mídia não terá sucesso. Para detalhes, consulte [Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md) na documentação de Planejamento.

> [!NOTE]  
> O bypass de mídia não interoperará com todos gateways de rede de telefonia comutada pública (PSTN), IP-BX e SBC (Controlador de Borda de Sessão). A Microsoft testou um conjunto de gateways PSTN e SBCs com parceiros certificados e fez alguns testes com IP-PBXs da Cisco. O bypass de mídia é suportado somente por produtos e versões listadas na Infraestrutura qualificada para Microsoft Lync em <a href="http://go.microsoft.com/fwlink/?linkid=214406%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=214406&amp;clcid=0x416</a>.

Uma configuração de tronco, como descrita abaixo, agrupa um conjunto de parâmetros que são aplicados a troncos atribuídos a essa configuração de tronco. O escopo de uma configuração de tronco específica pode ser global (para todos os troncos que não têm configuração de site ou pool mais específica), ou para um site ou pool. A configuração de tronco no nível do pool é usada para fazer o escopo de uma configuração de tronco específico para um único tronco.

## Para configurar um tronco com bypass de mídia

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Roteamento de Voz** e depois, em **Configuração do Tronco** .

4.  Na página **Configuração do Tronco** , use um dos métodos a seguir para configurar um tronco:
    
      - Dê um duplo clique em um tronco existente (por exemplo, o tronco **Global** ) para exibir a caixa de diálogo **Editar Configuração do Tronco** .
    
      - Clique em **Novo** e depois, selecione um escopo para a nova configuração de tronco:
        
          - **Tronco do site :** Escolha o site para esta configuração de tronco em **Selecionar um Site** e depois, clique em **OK** . Observe que se uma configuração de tronco já tiver sido criada para um site, o site não aparecerá em **Selecionar um Site** . Essa configuração de tronco será aplicada a todos os troncos no site.
        
          - **Tronco do pool :** Escolha o nome do tronco ao qual essa configuração de tronco se aplica. Esse tronco pode ser o tronco raiz de qualquer tronco adicional definido em Construtor de Topologias. Em **Selecionar um Serviço** , clique em **OK** . Observe que se uma configuração de tronco já tiver sido criada para um tronco específico, o tronco não aparecerá em **Selecionar um Serviço** .
    
    > [!NOTE]  
    > Depois de selecionar o escopo da configuração de tronco, ele não poderá ser alterado.<br />    O campo <strong>Nome</strong> é pré-preenchido com o nome do site ou serviço associado à configuração de tronco e não pode ser alterado.

5.  Especifique um valor em **Máximo de caixas de diálogo iniciais com suporte** . Este é o número máximo de respostas bifurcadas que um gateway de rede de telefonia comutada pública (PSTN), IP-PBX, ou Controlador de Borda de Sessão (SBC) ITSP pode receber para um INVITE enviado para o Servidor de Mediação. O valor padrão é 20.
    
    > [!NOTE]  
    > Antes de alterar este valor, consulte seu provedor de serviços ou fabricante do equipamento para detalhes sobre as capacidades do seu sistema.

6.  Selecione uma das seguintes opções de **Nível de suporte de criptografia** :
    
      - **Requerido :** A criptografia do protocolo de transporte seguro em tempo real (SRTP) deve ser usada para ajudar a proteger o tráfego entre o Servidor de Mediação e o gateway ou PBX (private branch exchange).
    
      - **Opcional :** a criptografia SRTP será usada se o provedor de serviços ou fabricante do equipamento oferecer suporte a ela.
    
      - **Sem Suporte :** a criptografia SRTP não é suportada pelo provedor de serviços ou fabricante do equipamento e, portanto, não será usada.

7.  Selecione a opção **Habilitar bypass de mídia** se você deseja que que a mídia desvie do Servidor de Mediação para processamento pelo ponto do tronco.
    
    > [!IMPORTANT]  
    > Para que o bypass de mídia funcione com êxito, o gateway PSTN gateway, IP-PBX ou Controlador de Borda de Sessão ITSP deve oferecer suporte a determinados recursos. Para detalhes, consulte <a href="lync-server-2013-planning-for-media-bypass.md">Planejamento de bypass de mídia no Lync Server 2013</a> na documentação de Planejamento.

8.  Selecione a opção **Processamento de mídia centralizado** se houver um ponto de terminação de mídia conhecido (por exemplo, um gateway PSTN em que a terminação de mídia tem o mesmo IP da terminação de sinalização). Desmarque esta opção se o tronco não possuir um ponto de terminação de mídia conhecido.

9.  Se o ponto do tronco suportar o recebimento de solicitações SIP REFER do Servidor de Mediação, selecione a caixa de seleção **Permitir envio de referência ao gateway** .
    
    > [!NOTE]  
    > Se esta opção for desabilitada enquanto a opção <strong>Habilitar bypass de mídia</strong> estiver selecionada, configurações adicionais são necessárias. Se o ponto do tronco não oferecer suporte ao recebimento de solicitações SIP REFER do Servidor de Mediação e o bypass de mídia estiver habilitado, você também deve executar o cmdlet <strong>Set-CsTrunkConfiguration</strong> para desabilitar o RTCP para chamadas ativas e em espera para suportar as condições adequadas para bypass de mídia. Para detalhes, consulte a documentação do <a href="lync-server-2013-lync-server-management-shell.md">Shell de gerenciamento do Lync Server</a>.<br />    Como alternativa, é possível selecionar <strong>Ativar referenciamento usando controle de chamada de terceiros</strong> se quiser que as chamadas transferidas contornem a mídia e o gateway não suporte solicitações SIP REFER.

10. (Opcional) Para permitir roteamento entre troncos, associe e configure os registros de uso de PSTN a essa configuração de tronco. O uso de PSTN associado com essa configuração de tronco será aplicado a todas as chamadas recebidas através do tronco que não estiverem se originando de um ponto de extremidade do Lync. Para gerenciar os registros de uso de PSTN associados à configuração de tronco, use um dos métodos a seguir:
    
      - Para escolher um ou mais registros de uma lista de todos os registros de uso de PSTN disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** . Realce os registros que você deseja associar a essa configuração de tronco e depois, clique em **OK** .
    
      - Para remover um registro de uso de PSTN desta configuração de tronco, selecione o registro e clique em **Remover** .
    
      - Para definir um novo registro de uso PSTN e associá-lo a essa configuração de tronco, faça o seguinte:
        
        1.  Clique em **Novo** .
        
        2.  No campo **Nome** , especifique um nome descritivo que seja exclusivo para o registro.
            
            > [!NOTE]  
            > O nome do registro de uso de PSTN deve ser exclusivo dentro da implantação do Enterprise Voice. Após a gravação do registro, o campo <strong>Nome</strong> não poderá ser editado.        
        3.  Use um dos métodos a seguir para associar e configurar rotas para este registro de uso do PSTN:
            
              - Para selecionar uma ou mais rotas da lista de todas as rotas disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** . Destaque as rotas que você deseja associar a esse registro de uso do PSTN e clique em **OK** .
            
              - Para remover uma rota do registro de uso do PSTN, selecione a rota e clique em **Remover** .
            
              - Para definir uma nova rota e associá-la ao registro de uso do PSTN, clique em **Novo** . Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
            
              - Para editar uma rota que está associada a esse registro de uso do PSTN, selecione a rota e clique em **Exibir detalhes** . Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
        
        4.  Clique em **OK** .
    
      - Para editar um registro de uso de PSTN que já está associado a essa configuração de tronco, faça o seguinte:
        
        1.  Selecione o registro de uso do PSTN que você deseja editar e clique em **Mostrar detalhes** .
        
        2.  Use um dos métodos a seguir para associar e configurar rotas para este registro de uso do PSTN:
            
              - Para selecionar uma ou mais rotas da lista de todas as rotas disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** . Destaque as rotas que você deseja associar a esse registro de uso do PSTN e clique em **OK** .
            
              - Para remover uma rota do registro de uso do PSTN, selecione a rota e clique em **Remover** .
            
              - Para definir uma nova rota e associá-la ao registro de uso do PSTN, clique em **Novo** . Para obter detalhes, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md).
            
              - Para editar uma rota que está associada a esse registro de uso do PSTN, selecione a rota e clique em **Exibir detalhes** . Para obter detalhes, consulte [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
        
        3.  Clique em **OK** .
    
    > [!IMPORTANT]  
    > É importante associar registros de uso do PSTN de acordo com o ponto do Servidor de Mediação associado ao tronco que está sendo configurado. Se o ponto do Servidor de Mediação for um gateway do PSTN ou um Controlador de Borda de Sessão (SBC), recomenda-se que a configuração de tronco não seja associada com um registro de uso do PSTN ou qualquer outro sistema downstream conectado através do Lync Server.

11. Organize os registros de uso do PSTN para obter o melhor desempenho. Para alterar a posição de um registro na lista, selecione o registro de uso e clique na seta para cima ou para baixo.
    
    > [!IMPORTANT]  
    > A ordem na qual PSTN registros de uso são listados na configuração de tronco é significativa. O Lync Server percorre a lista de cima para baixo.

12. **Enable RTP Latching** deve ser selecionado para permitir desvio de mídia para clientes atrás de uma NAT (conversão de endereço de rede) ou firewall, e um SBC que suporte travamento.

13. **Enable forward call history** deve ser selecionado para permitir envio de informações de histórico de chamada ao ponto do gateway do Servidor de Mediação.

14. **Enable forward P-Asserted-Identity data** deve ser selecionado para permitir que informações de originador de chamadas do P-Asserted-Identity (PAI) sejam encaminhadas entre o lado do Servidor de Mediação e do gateway side (e vice-versa), quando presente.

15. **Enable outbound routing failover timer** deve ser selecionado para permitir failover rápido. O gateway associado com esse tronco pode fornecer notificações em 10 segundos de que está processando uma chamada de saída. Um novo roteamento para outro tronco ocorrerá se essa notificação não for recebida pelo Servidor de Mediação. Em redes onde a latência pode atrasar o tempo de resposta ou o gateway levar mais de 10 segundos para responder, o failover rápido deverá ser desativado.

16. (Opcional) Associe e configure as **regras de conversão do número de chamada** do tronco. Essas regras de conversão se aplicam ao número chamado para chamadas de saída.
    
      - Para escolher uma ou mais regras de uma lista de todas as regras de conversão que estão disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** . Em **Selecionar Regras de Conversão** , clique nas regras que você deseja associar com o tronco, e depois em **OK** .
    
      - Para definir uma nova regra de conversão e associá-la ao tronco, clique em **Novo** . Para obter detalhes sobre a definição de uma nova regra, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md) na documentação Implantação.
    
      - Para editar uma regra de conversão que já esteja associada ao tronco, clique no nome da regra e clique em **Exibir detalhes** . Para obter detalhes, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md) na documentação de Implantação.
    
      - Para copiar uma regra de conversão existente para usar como ponto de partida para definir uma nova regra, clique no nome da regra e clique em **Copiar** e clique em **Copiar** . Para detalhes, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md).
    
      - Para remover uma regra de conversão do tronco, destaque o nome da regra e clique em **Remover** .
    

    > [!WARNING]
    > Não associe regras de conversão a um tronco se não houver regras de conversão configuradas no ponto do tronco associado porque as duas regras podem entrar em conflito.



17. (Opcional) Associe e configure as **regras de conversão de números chamados** do tronco. As regras de conversão se aplicam ao número chamado em uma chamada de saída.
    
      - Para escolher uma ou mais regras de uma lista de todas as regras de conversão que estão disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** . Em **Selecionar Regras de Conversão** , clique nas regras que você deseja associar com o tronco, e depois em **OK** .
    
      - Para definir uma nova regra de conversão e associá-la ao tronco, clique em **Novo** . Para obter detalhes sobre a definição de uma nova regra, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md) na documentação Implantação.
    
      - Para editar uma regra de conversão que já esteja associada ao tronco, clique no nome da regra e clique em **Exibir detalhes** . Para obter detalhes, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md) na documentação de Implantação.
    
      - Para copiar uma regra de conversão existente para usar como ponto de partida para definir uma nova regra, clique no nome da regra e clique em **Copiar** e clique em **Copiar** . Para detalhes, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md).
    
      - Para remover uma regra de conversão do tronco, destaque o nome da regra e clique em **Remover** .
    

    > [!WARNING]
    > Não associe regras de conversão a um tronco se não houver regras de conversão configuradas no ponto do tronco associado porque as duas regras podem entrar em conflito.



18. Verifique se as regras de conversão do tronco estão organizadas na ordem correta. Para alterar a posição de uma regra na lista, realce o nome da regra e clique na seta para cima ou para baixo.
    
    > [!IMPORTANT]  
    > O Lync Server 2013 percorre a lista de regras de conversão de cima para baixo e usa a primeira regra que corresponda ao número discado. Se você configurar um tronco de forma que um número discado possa corresponder a mais de uma regra de conversão, certifique-se de que as regras mais restritivas estejam classificadas acima das regras menos restritivas. Por exemplo, se você incluiu uma regra de conversão que corresponda a qualquer número de 11 dígitos e uma regra de conversão que corresponda somente a números de 11 dígitos que comecem com +1425, certifique-se de que a regra que corresponda a qualquer número de 11 dígitos esteja classificada <em>abaixo</em> da regra mais restritiva.

19. Ao terminar de configurar o tronco, clique em **OK** .

20. Na página **Configuração do Tronco** , clique em **Confirmar** e clique em **Confirmar tudo** .
    
    > [!NOTE]  
    > Sempre que criar ou modificar uma configuração de tronco, você deve executar o comando <strong>Confirmar tudo</strong> para publicar a alteração na configuração. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação de Operações.

Depois de concluir a configuração do tronco, continue configurando o bypass de mídia escolhendo entre as opções de bypass de mídia global, conforme descrito em [Opções de bypass de mídia global no Lync Server 2013](lync-server-2013-global-media-bypass-options.md) na documentação de Implantação.

## Consulte Também

#### Tarefas

[Configurar um tronco sem bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md)  

#### Conceitos

[Configurar bypass de mídia no Lync Server 2013](lync-server-2013-configure-media-bypass.md)  
[Opções de bypass de mídia global no Lync Server 2013](lync-server-2013-global-media-bypass-options.md)  

#### Outros Recursos

[Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md)

