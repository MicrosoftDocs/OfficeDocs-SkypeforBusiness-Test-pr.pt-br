---
title: Criar ou modificar uma política de local
TOCTitle: Criar ou modificar uma política de local
ms:assetid: 10338418-4da4-42df-b231-f52098c08dae
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687971(v=OCS.15)
ms:contentKeyID: 49886102
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar uma política de local

 

_**Tópico modificado em:** 2012-11-01_

No Lync Server 2013, você pode usar a política de local para aplicar configurações relacionadas à funcionalidade do 9-1-1 Avançado (E9-1-1) e para configurações de localização para usuários ou contatos. A política de local determina se o usuário está habilitado para o E9-1-1 e, se estiver, qual será o comportamento de uma chamada de emergência. Por exemplo, você pode usar a política de local para definir o número que constitui uma chamada de emergência (por exemplo, 911 nos Estados Unidos), se a segurança corporativa deve ser avisada automaticamente e como a chamada deve ser roteada.

Você pode configurar políticas de local no grupo **Configuração da Rede** no Painel de Controle do Lync Server 2013. No Painel de Controle do Lync Server você pode exibir, criar, modificar ou excluir políticas de local. Use os procedimentos nesta seção para criar ou modificar uma política de local. Para detalhes sobre a exclusão de políticas de local, consulte [Excluindo uma política de local](lync-server-2013-deleting-a-location-policy.md).

No Lync Server 2013, você pode substituir a quantidade padrão de tempo entre solicitações do cliente para uma atualização de local a partir do Serviço de Informações de Local. O valor padrão é 4 horas. Use o cmdlet **Set-CsLocationPolicy** com o parâmetro LocationRefreshInterval para substituir o valor padrão.

## Para criar uma nova política de local no Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração de rede** e em **Política de local**.

4.  Na página **Política de local**, clique em **Novo** e depois selecione o tipo de política que deseja criar:
    
      - Para criar uma política de site, clique em **Política de site**. Em **Selecionar um site**, escolha o site ao qual você deseja aplicar a política e clique em **OK**. Na página **Nova política de local**, o campo **Escopo** contém o valor **Site**, e o campo **Nome** contém o nome do site que você escolheu. Você não pode modificar nenhum desses campos. Uma política de site é automaticamente aplicada a todos os usuários no site específico e anula a política global desses usuários.
    
      - Para criar uma **Política de usuário**, clique em **Política de usuário**. Em **Nova política de local**, o campo **Escopo** contém o valor **Usuário**. Você não pode modificar esse valor. No campo **Nome**, digite o nome que você quer dar para essa política. Uma política de usuário não é aplicada automaticamente a nenhum usuário. Depois de criar a política de usuário, você deve conceder a política aos usuários ou sites de rede aos quais você quer aplicá-la.

5.  Preencha os campos restantes conforme segue:
    
      - **Habilitar serviços de emergência avançados**   Marque essa caixa de seleção para habilitar os usuários associados com essa política do E9-1-1. Quando os serviços de emergência estão habilitados, os clientes do Lync Server recuperarão as informações de local no registro e as incluirão quando uma chamada de emergência for feita.
    
      - **Local**   Especifique um dos valores a seguir:
        
          - **Obrigatório**   Será solicitado ao usuário que insira as informações de local quando o cliente se registra em um novo local. O usuário pode recusar o aviso, sem digitar qualquer informação. Se as informações forem inseridas, uma chamada de emergência será respondida primeiro pelo provedor de serviços de emergência para verificar o local antes de ser roteado ao operador do ponto de atendimento público seguro (PSAP) (isso é, o operador do 911).
        
          - **Não obrigatório**   Não será solicitado um local ao usuário. Quando uma chamada é feita sem a informação de local, o provedor de serviços de emergência irá responder à chamada e pedir por um local.
        
          - **Aviso de isenção de responsabilidade**   Esta opção é a mesma que a opção **Obrigatório**, exceto pelo fato de não ser possível ao usuário ignorar a solicitação sem inserir as informações de local. O usuário ainda pode completar uma chamada de emergência, mas nenhuma outra chamada pode ser completada sem inserir as informações. Além disso, será exibido um texto de isenção de responsabilidade ao usuário, alertando-o sobre as consequências de se recusar a digitar as informações de local. Para definir o texto do aviso de isenção, você deve usar o Shell de Gerenciamento do Lync Server para executar o cmdlet **Set-CsLocationPolicy** ou o cmdlet **New-CsLocationPolicy** com o parâmetro EnhancedEmergencyServiceDisclaimer. Para detalhes, consulte [Set-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsLocationPolicy) ou [New-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsLocationPolicy) na documentação do Shell de Gerenciamento do Lync Server.
            
            > [!NOTE]  
            > No Lync Server 2013, você pode usar a política de local para definir avisos de isenção diferentes para locais diferentes ou conjuntos diferentes de usuários, ao contrário do Lync Server 2010, onde seria possível especificar somente um aviso de isenção global para toda a organização.    
      - **Usar local somente para serviços de emergência**   O Lync pode usar informações de local por várias razões (por exemplo, para notificar membros de equipe sobre sua localização atual). Marque essa caixa de seleção para garantir que as informações de local estejam disponíveis apenas para o uso em uma chamada de emergência.
    
      - **Uso de PSTN**   O uso de rede telefônica pública comutada (PSTN) que será usada para determinar qual rota de voz será usada para rotear chamadas de emergência de clientes usando esse perfil. A rota associada a esse uso deve apontar para um tronco SIP dedicado a chamadas de emergência ou a um número de gateway de Emergency Location Identification Number (ELIN) que rota chamadas de emergência ao ponto de atendimento público seguro (PSAP).
    
      - **Número de discagem de emergência**   O número que é discado para obter serviços de emergência. Nos Estados Unidos, esse valor é 911. A cadeia de caracteres deve ser composta pelos dígitos 0 a 9 e pode ter entre um e dez dígitos de comprimento.
    
      - **Máscara de discagem de emergência**   Um número que você quer traduzir em um valor de número de discagem de emergência quando for discado. Por exemplo, se você inserir um valor de 212 nesse campo, e o campo do número de discagem de emergência tem um valor de 911, se um usuário discar 212, a chamada será feita para o 911. Isso permite que números de emergência diferentes sejam discados e ainda atinjam os serviços de emergência (por exemplo, se alguém de um país ou região que tenha um número de emergência diferente tentar discar o número da sua área em vez do número do local onde está). É possível definir diversas máscaras de discagem de emergência, separando-se os valores por ponto-e-vírgula. Por exemplo, 212;414. O comprimento máximo da cadeia de caracteres é 100. Cada caractere deve ser um dígito entre 0 e 9.
        
        > [!IMPORTANT]  
        > Garanta que o valor da máscara de discagem especificado não seja igual a um número no intervalo da órbita de estacionamento de chamadas. O roteamento do estacionamento de chamadas terá precedência sobre a conversão de cadeias de caracteres de discagem de emergência. Para ver os intervalos de órbita de estacionamento de chamadas existentes, clique em <strong>Recursos de voz</strong> na barra de navegação à esquerda e clique em <strong>Estacionamento de chamada</strong>. Para obter informações detalhadas, consulte <a href="lync-server-2013-configure-phone-number-extensions-for-parking-calls.md">Configurar extensões de números de telefone para estacionamento de chamadas</a>.    
      - **URI de Notificação**   Um ou mais URIs de SIP a serem notificados quando uma chamada de emergência é feita. Por exemplo, o escritório de segurança da empresa poderia ser avisado, por meio de uma mensagem instantânea, sempre que ocorrer uma chamada de emergência. Se o local do chamador estiver disponível, ele será incluído na notificação. Vários URIs de SIP podem ser incluídos como uma lista separada por vírgulas. Por exemplo, "sip:security@litwareinc.com","sip:kmyer@litwareinc.com". Listas de distribuição são compatíveis. A cadeia de caracteres deve ter entre 1 e 256 e deve começar com o prefixo "sip:". Antes de clicar no campo URI de Notificação, um exemplo é exibido.
    
      - **URI de Conferência**   É o URI de SIP (neste caso, o número de telefone) de uma terceira parte que será entrará em uma conferência a partir de qualquer chamada de emergência realizada. Por exemplo, o setor de segurança da empresa pode receber uma chamada quando a chamada de emergência é feita e ouvir ou participar da mesma (dependendo do valor fornecido no campo **Modo de conferência**). A cadeia de caracteres deve ter entre um e 256 caracteres de comprimento e deve começar com o prefixo sip: um exemplo é exibido até que você clique dentro desse campo.
    
      - **Modo de conferência**   Se você especificar um valor no campo **URI de conferência**, o **Modo de conferência** determina se uma terceira parte pode participar da chamada ou apenas ouvi-la. Especifique uma das opções a seguir:
        
          - **Unidirecional**   Um terceiro só pode ouvir a conversa entre um chamador e o operador de PSAP.
        
          - **Bidirecional**   Um terceiro pode ouvir e participar da chamada entre o chamador e o operador de PSAP.

6.  Clique em **Confirmar**.
    
    > [!IMPORTANT]  
    > Quando você cria uma política de usuário, inicialmente, essa política não é aplicada a nenhum usuário ou site de rede. Para aplicar a política a um usuário, clique em <strong>Usuários</strong> na barra de navegação à esquerda. Encontre os usuários aos quais quer aplicar a política. No menu <strong>Editar</strong>, clique em <strong>Mostrar detalhes</strong>. Na página <strong>Editar Usuário do Lync Server</strong>, selecione a nova política de local na lista suspensa <strong>Política local</strong> e clique em <strong>Confirmar</strong>.<br />    Para aplicar a política a um site de rede, clique em <strong>Configuração de rede</strong> na barra de navegação à esquerda e clique em <strong>Site</strong>. Encontre o site de rede ao qual você quer aplicar a política. No menu <strong>Editar</strong>, clique em <strong>Mostrar detalhes</strong>. Em <strong>Editar Site</strong>, selecione a nova política de local na lista suspensa <strong>Política de local</strong> e clique em <strong>Confirmar</strong>.

## Para modificar uma política de local no Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração de rede** e clique em **Política de local**.

4.  Na página **Política de local**, selecione a política de local que você deseja modificar.

5.  No menu **Editar**, clique em **Exibir detalhes**.

6.  Na página **Editar política de local**, modifique os campos conforme necessário (para obter detalhes, consulte a Etapa 5 nos procedimentos "Para criar uma nova política de local" anteriormente neste tópico).

7.  Clique em **Confirmar**.

## Consulte Também

#### Tarefas

[Excluindo uma política de local](lync-server-2013-deleting-a-location-policy.md)  

#### Conceitos

[Definindo a política de local para Lync Server 2013](lync-server-2013-defining-the-location-policy.md)  

#### Outros Recursos

[Configurar extensões de números de telefone para estacionamento de chamadas](lync-server-2013-configure-phone-number-extensions-for-parking-calls.md)

