---
title: 'Lync Server 2013: Configurar uma rota estática para controle de chamada remota'
TOCTitle: Configurar uma rota estática para controle de chamada remota
ms:assetid: f7003023-443d-48ee-989b-71e8b0b0abbd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615051(v=OCS.15)
ms:contentKeyID: 49308638
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar uma rota estática para controle de chamada remota no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-22_

O controle de chamada remota exige que cada pool do Lync Server seja configurado com um caminho desse pool para o gateway SIP/CSTA que se conecta ao PBX (central privada de comutação telefônica). Esse caminho exige que cada pool tenha um roteamento estático para cada gateway no qual o pool usará uma mensagem de controle de chamada de SIP proxy associada às chamadas feitas para o PBX. Se você configurar um roteamento estático global para controle de chamada remota, cada pool não configurado com um roteamento estático no nível do pool usará o roteamento estático global.

## Para configurar uma rota estática para o controle de chamada remota

1.  Faça login em um computador onde o Shell de Gerenciamento do Lync Server é instalado como um membro do grupo RTCUniversalServerAdmins ou função de controle de acesso baseado em função (RBAC) aos quais você atribuiu o cmdlet **New-CsStaticRoute**.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para criar um roteamento estático e colocá-lo na variável $TLSRoute ou $TCPRoute, siga um destes procedimentos:
    

    > [!TIP]
    > Para corresponder a domínios filhos de um domínio, é possível especificar um valor curinga no parâmetro MatchUri. Por exemplo, <STRONG>*. contoso.net</STRONG> . O valor corresponde a qualquer domínio que termina com o sufixo <STRONG>contoso.net</STRONG> .

    
      - Para uma conexão TLS (Transport Layer Security), digite o seguinte no prompt de comando:
        
            $TLSRoute = New-CsStaticRoute -TLSRoute -Destination <gateway FQDN> -Port <gateway SIP listening port> -UseDefaultCertificate $true -MatchUri <destination domain>
        
        Por exemplo:
        
            $TLSRoute = New-CsStaticRoute -TLSRoute -Destination rccgateway.contoso.net -Port 5065 -UseDefaultCertificate $true -MatchUri *.contoso.net
        
        Se UseDefaultCertificate for definido como Falso, você deve especificar os parâmetros TLSCertIssuer e TLSCertSerialNumber. Esses parâmetros indicam o nome da autoridade de certificação (CA) que emitiu o certificado usado no roteamento estático e o número de série do certificado TLS, respectivamente. Para obter detalhes sobre esses parâmetros, consulte Ajuda do Shell de Gerenciamento do Lync Server digitando o seguinte no prompt de comando:
        
            Get-Help New-CsStaticRoute -Full
    
      - Para uma conexão TCP (Transmission Control Protocol), digite o seguinte no prompt de comando:
        
        > [!NOTE]  
        > Se especificar um nome de domínio totalmente qualificado (FQDN), você deve configurar um registro A de DNS primeiro.        
            $TCPRoute = New-CsStaticRoute -TCPRoute -Destination <gateway IP address or FQDN> -Port <gateway SIP listening port> -MatchUri <destination domain>
        
        Por exemplo:
        
            $TCPRoute = New-CsStaticRoute -TCPRoute -Destination 192.168.0.240 -Port 5065 -MatchUri *.contoso.net
        
        Estes são os valores padrões para parâmetros opcionais de roteamento estático:
        
          - Habilitado = Verdadeiro
        
          - MatchOnlyPhoneUri = Falso
        
          - ReplaceHostInRequestUri = Falso
        
        Recomendamos que você não altere esses valores padrões. No entanto, se você deve alterar esses parâmetros, consulte a Ajuda do Shell de Gerenciamento do Lync Server digitando o seguinte no prompt de comando:
        
            Get-Help New-CsStaticRoute -Full

4.  Para manter um roteamento estático recém-criado no Repositório de Gerenciamento Central, execute um dos seguintes conforme apropriado:
    
    ```
            Set-CsStaticRoutingConfiguration -Route @{Add=$TLSRoute}
    ```
    ```
        Set-CsStaticRoutingConfiguration -Route @{Add=$TCPRoute}
    ```

## Consulte Também

#### Tarefas

[Configurar uma entrada de aplicativo confiável para controle de chamada remota no Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md)  
[Definir um endereço SIP de gateway SIP/CSTA no Lync Server 2013](lync-server-2013-define-a-sip-csta-gateway-ip-address.md)

