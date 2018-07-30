---
title: Configurar o Unified Messaging no Microsoft Exchange para Lync Server 2013
TOCTitle: Configurar o Unified Messaging no Microsoft Exchange para Lync Server 2013
ms:assetid: 07547968-c59b-4dde-ace4-9fd286933759
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398129(v=OCS.15)
ms:contentKeyID: 49305785
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar o Unified Messaging no Microsoft Exchange para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este tópico descreve como configurar o Unificação de Mensagens (UM) do Exchange em um Microsoft Exchange Server para uso com o Enterprise Voice.

> [!NOTE]  
> Os exemplos de cmdlet neste tópico fornecem a sintaxe para a versão do Exchange 2007 do Shell de Gerenciamento do Exchange. Se o Exchange 2010 ou o Exchange 2013 estiver sendo executado, consulte a documentação apropriada como referência.

## Para configura um servidor que execute a UM do Exchange Server

1.  Crie um plano de discagem do Identificador de recurso uniforme (URI) do Protocolo de iniciação de sessão (SIP) do UM para cada perfil de local do Enterprise Voice. Se a opção for por usar o Console de Gerenciamento do Exchange, crie um novo plano de discagem com a definição de segurança **Seguro (preferencial)**.
    

    > [!WARNING]
    > Se você definir o valor de configuração de segurança como <STRONG>SIP Seguro</STRONG> para exigir criptografia apenas para o tráfego do SIP, como recomendado anteriormente, observe que essa definição de segurança em um plano de discagem é insuficiente se o pool de Front-Ends estiver configurado para exigir criptografia, o que significa que o pool exige criptografia para o tráfego de SIP e de RTP. Quando as definições de plano de discagem e de configurações de segurança não são compatíveis, todas as chamadas para o UM do Exchange a partir do pool de Front-Ends falharão, resultando em um erro que indica que há uma “Configuração de segurança incompatível”.

    
    Se o Shell de Gerenciamento do Exchange for usado, digite:
    
        New-UMDialPlan -Name <dial plan name> -UriType "SipName" -VoipSecurity <SIPSecured|Unsecured|Secured> -NumberOfDigitsInExtension <number of digits> -AccessTelephoneNumbers <access number in E.164 format>
    
    Para obter detalhes, consulte:
    
      - Para o Office Communications Server 2007, consulte "Como criar um plano de discagem URI de SIP de Unificação de Mensagens" em [http://go.microsoft.com/fwlink/?linkid=268632\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268632%26clcid=0x416) e "New-UMDialplan" em [http://go.microsoft.com/fwlink/?linkid=196455\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=196455%26clcid=0x416).
    
      - Para o Exchange 2010, consulte "Criar um Plano de Discagem da UM" em [http://go.microsoft.com/fwlink/?linkid=268674\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268674%26clcid=0x416) e "New-UMDialplan: Exchange 2010 Help" em [http://go.microsoft.com/fwlink/?linkid=268680\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268680%26clcid=0x416).
    
      - Para o Exchange 2013, consulte "Unified Messaging" em [http://go.microsoft.com/fwlink/?linkid=266579\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x416).
    
    > [!NOTE]  
    > A escolha do nível de segurança do <strong>SIPSecured</strong> ou do <strong>Secured</strong> depende de se o secure real-time transport protocol (SRTP) está ativado ou desativado para criptografia de mídia. Para a integração do Lync Server 2010 com a UM do Exchange, a escolha deveria corresponder ao nível de criptografia na configuração de mídia do Lync Server. Essa configuração de mídia do Lync Server pode ser visualizada com a execução do cmdlet <strong>Get-CsMediaConfiguration</strong>. Para obter mais detalhes, consulte Get-CsMediaConfiguration na documentação do Shell de Gerenciamento do Lync Server.<br />    Para obter detalhes sobre como selecionar a configuração de Segurança VoIP apropriada, consulte <a href="lync-server-2013-deployment-process-for-integrating-on-premises-unified-messaging.md">Processo de implantação para integração de Unificação de Mensagens local com Lync Server 2013</a>.

2.  Execute o cmdlet a seguir para obter o nome de domínio totalmente qualificado (FQDN) para cada plano de discagem da UM:
    
    ``` 
    (Get-UMDialPlan <dialplanname>).PhoneContext  
    ```
    
    Para obter detalhes, consulte:
    
      - Para o Exchange 2007, consulte "Get-UMDialplan: Exchange 2007 Help" em [http://go.microsoft.com/fwlink/?linkid=268678\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268678%26clcid=0x416).
    
      - Para o Exchange 2010, consulte "Get-UMDialplan: Exchange 2010 Help" em [http://go.microsoft.com/fwlink/?linkid=268679\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268679%26clcid=0x416).
    
      - Para o Exchange 2013, consulte "Unified Messaging" em [http://go.microsoft.com/fwlink/?linkid=266579\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x416).

3.  Grave cada nome de plano de discagem da UM. Dependendo da versão do Exchange Server, talvez seja preciso usar o FQDN de cada plano de discagem posteriormente como o nome cada plano de discagem do Lync Server correspondente aos da UM para que eles combinem.
    
    > [!NOTE]  
    > Os nomes dos planos de discagem do Lync Server só devem combinar com os da UM se o plano de discagem da Um estiver sendo executado em uma versão do Exchange <em>anterior</em> ao Exchange 2010 SP1.

4.  Adicione o plano de discagem ao servidor que está executando o UM do Exchange conforme a seguir:
    
      - Se você optar por usar o Console de Gerenciamento do Exchange, pode adicionar o plano de discagem contido na folha de propriedades do servidor. Para obter instruções específicas, consulte a documentação de produto do Exchange Server.
        
        Para o Exchange 2007, consulte "Como adicionar um servidor de Unificação de Mensagens a um plano de discagem" em [http://go.microsoft.com/fwlink/?linkid=268681\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268681%26clcid=0x416).
        
        Para o Exchange 2010, consulte "Exibir ou Configurar as Propriedades de um Servidor da UM" em [http://go.microsoft.com/fwlink/?linkid=268682\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268682%26clcid=0x416).
        
        Para o Exchange 2013, consulte "Unified Messaging" em [http://go.microsoft.com/fwlink/?linkid=266579\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x416).
    
      - Se o Shell de Gerenciamento do Exchange for usado, execute as ações a seguir para cada um dos servidores UM do Exchange:
        
            $ums=get-umserver; 
            $dp=get-umdialplan -id <name of dial-plan created in step 1>; 
            $ums[0].DialPlans +=$dp.Identity; 
            set-umserver -instance $ums[0]
    
    > [!NOTE]  
    > Antes de realizar a etapa a seguir, certifique-se que todos os usuários do Enterprise Voice foram configurados com uma caixa de correio do Exchange Server.<br />    Para o Exchange 2007, consulte o TechNet Library do Exchange Server 2007 em <a href="http://go.microsoft.com/fwlink/?linkid=268685%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=268685&amp;clcid=0x416</a>.<br />    Para o Exchange 2010, consulte o TechNet Library do Exchange Server 2010 em <a href="http://go.microsoft.com/fwlink/?linkid=268686%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=268686&amp;clcid=0x416</a>.<br />    Ao especificar uma política de caixa de correio para cada plano de discagem criado na etapa 1, selecione a política padrão ou uma que você criou.

5.  Navegue até \<*Diretório de Instalação do Exchange*\>\\Scripts, e se o Exchange estiver implantado em uma única floresta, digite:
    
        exchucutil.ps1
    
    Se o Exchange estiver implantado em várias florestas, digite:
    
        exchucutil.ps1 -Forest:"<forest FQDN>"
    
    onde *FQDN da floresta* especifica a floresta na qual o Lync Server está implantado.
    
    Se houver um ou mais planos de discagem da UM associados a vários gateways IP, vá para a etapa 6. Se seus planos de discagem estão associados a um único gateway IP, pule a etapa 6.
    
    > [!IMPORTANT]  
    > Certifique-se de reiniciar o serviço do <strong>Lync Server Front-End</strong> (rtcsrv.exe) <em>depois</em> de executar o exchucutil.ps1. Caso contrário, o Lync Server não detectará a Mensagem Unificada na topologia.

6.  Usando o Shell de Gerenciamento do Exchange ou o Console de Gerenciamento do Exchange, desabilite as chamadas de saída de todos os gateways IP, com exceção de um, associados a cada um dos planos de discagem.
    
    > [!NOTE]  
    > Essa etapa é necessária para garantir que as chamadas de saída do servidor que estiver executando a UM do Exchange Server para usuários externos (por exemplo, como o caso dos cenários tocar no telefone) atravesse com segurança o firewall da empresa.    
    > [!IMPORTANT]  
    > Ao selecionar o gateway IP da UM através dos qual as chamadas de saída são permitidas, escolha um que provavelmente manipule a maior parte do tráfego. Não permita o tráfego de saída através de um gateway IP que se conecte a um pool de Diretores do Lync Server. Evite também pools em outro site central ou de filial. Você pode usar os métodos a seguir para impedir que as chamadas de saída passem por um gateway IP:    
      - Se você usar o Shell de Gerenciamento do Exchange, desabilite cada gateway IP executando o seguinte comando:
        
            Set-UMIPGateway <gatewayname> -OutcallsAllowed $false
        
        Para o Exchange 2007, consulte "Set-UMIPGateway: Exchange 2007 Help" em [http://go.microsoft.com/fwlink/?linkid=268687\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268687%26clcid=0x416)
        
        Para o Exchange 2010, consulte "Set-UMIPGateway: Exchange 2010 Help" em [http://go.microsoft.com/fwlink/?linkid=268688\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268688%26clcid=0x416).
    
      - Se você usar o Console de Gerenciamento do Exchange, desmarque a caixa de seleção **Permitir chamadas de saída por meio deste gateway IP do UM**.
    
    > [!IMPORTANT]  
    > Se seu plano de discagem do SIP URI da UM estiver associado a apenas um gateway IP, não desabilite as chamadas de saída através desse gateway.

7.  Crie um atendimento automático da UM para cada plano de diálogo do Lync Server.
    
    > [!IMPORTANT]  
    > Não inclua espaços no nome do atendedor automático.    
        New-umautoattendant -name <auto attendant name> -umdialplan < name of dial plan created in step 1> -PilotIdentifierList <auto attendant phone number in E.164 format> -SpeechEnabled $true -Status Enabled
    
    Para obter detalhes, consulte:
    
      - Para o Exchange 2007, consulte "New-UMAutoAttendant: Exchange 2007 Help" em [http://go.microsoft.com/fwlink/?linkid=268689\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268689%26clcid=0x416).
    
      - Para o Exchange 2010, consulte o "New-UMAutoAttendant: Exchange 2010 Help" em [http://go.microsoft.com/fwlink/?linkid=268690\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268690%26clcid=0x416).
    
    A etapa a seguir deve ser realizada por cada usuário depois de você ter habilitado os usuários do Lync Server para o Enterprise Voice e depois de conhecer seus URIs do SIP.

8.  Associe os usuários da UM do Exchange (cada um deve possuir uma caixa de correio do Exchange) a um plano de discagem da UM e crie um URI do SIP para cada usuário.
    
    > [!NOTE]  
    > O <strong>SIPResourceIdentifier</strong> do exemplo a seguir deve ser o endereço do SIP do usuário do Lync Server.    
        enable-ummailbox -id <user name> -ummailboxpolicy <name of the mailbox policy for the dial plan created in step 1> -Extensions <extension> -SIPResourceIdentifier "<user name>@<full domain name>" -PIN <user pin>
    
    Para obter detalhes, consulte:
    
      - Para o Exchange 2007, consulte "Enable-UMMailbox: Exchange 2007 Help" em [http://go.microsoft.com/fwlink/?linkid=268691\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268691%26clcid=0x416).
    
      - Para o Exchange 2010, consulte "Enable-UMMailbox: Exchange 2010 Help" em [http://go.microsoft.com/fwlink/?linkid=268692\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268692%26clcid=0x416).

