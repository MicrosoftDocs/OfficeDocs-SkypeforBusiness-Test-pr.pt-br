---
title: 'Lync Server 2013: Definir sua topologia de borda'
TOCTitle: Definir sua topologia de borda
ms:assetid: 787b23f1-8fa0-4c37-abf2-c516c5dd66f0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398591(v=OCS.15)
ms:contentKeyID: 49307182
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir sua topologia de borda no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-28_

Você deve usar a Construtor de Topologias para criar sua topologia e configurar pelo menos um pool de Front-Ends internos ou um servidor Standard Edition antes de poder implantar seu Servidor de Borda. Use o procedimento a seguir para definir a topologia de borda para um único Servidor de Borda e use os procedimentos mostrados em [Publicar sua topologia no Lync Server 2013](lync-server-2013-publish-your-topology.md) e em [Exportar sua topologia do Lync Server 2013 e copiá-la na mídia externa para instalação de borda](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md) para publicar a topologia e disponibilizá-la no seu Servidor de Borda.


> [!NOTE]  
> A interface de Borda interna e externa devem usar o mesmo tipo de balanceamento de carga. Não é possível usar o balanceamento de carga DNS na interface de Borda e o balanceamento de carga de hardware na outra interface de Borda.


Para publicar, habilitar ou desabilitar uma topologia com êxito ao adicionar ou remover uma função do servidor, você deve estar conectado a um usuário membro dos grupos RTCUniversalServerAdmins e de Administradores de Domínio. Também é possível conceder direitos e permissões do administrador exigidos para adicionar funções do servidor a uma conta do usuário. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md) na documentação de Implantação do servidor Standard Edition ou Enterprise Edition. Para outras alterações na configuração, apenas a associação no grupo RTCUniversalServerAdmins é necessária.

Se você definiu sua topologia de borda ao definir e publicar sua topologia interna e nenhuma mudança for necessária para a topologia de borda que você definiu anteriormente, não é necessário definir e publicar novamente. Use o seguinte procedimento apenas se precisa realizar mudanças em sua topologia de borda. Você deve tornar a topologia definida e publicada anteriormente disponível para seus servidores de borda. É possível fazer isso usando o procedimento em [Exportar sua topologia do Lync Server 2013 e copiá-la na mídia externa para instalação de borda](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md).


> [!IMPORTANT]  
> É possível executar o Construtor de Topologias por um Servidor de Borda. Você deve executá-lo do seu Servidor Front-End ou servidores do Standard Edition.


O processo de definição da topologia do servidor de borda é executado no Construtor de Topologias. os três tipos principais de topologias de servidor de borda que você pode planejar e configurar são listados a seguir:

  - Para definir a topologia de um único servidor de borda

  - Para definir a topologia de um pool de servidor de borda de balanceamento de carga

  - Para definir a topologia de um pool de borda com carga de hardware balanceada

## Para definir a topologia para um único Servidor de Borda

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Na árvore de console, expanda o site no qual você deseja implantar um Servidor de Borda.

3.  Com o botão direito em **Pools de borda** e clique em **Novo pool de borda**.

4.  Em **Definir o Novo Pool de Borda**, clique em **Avançar**.

5.  Em **Definir o FQDN do pool de Borda**, faça o seguinte:
    
      - Em **FQDN do Pool**, digite o FQDN (nome de domínio totalmente qualificado) da interface interna do Servidor de Borda.
        
        > [!IMPORTANT]
        > O nome especificado deve ser idêntico ao nome do computador configurado no servidor. Por padrão, o nome de um computador que não é atribuído a um domínio é um nome curto, não um FQDN. O Construtor de Topologias usa FQDNs, não nomes curtos. Portanto, você deve configurar um sufixo DNS no nome do computador para ser implantado como um Servidor de Borda que não é vinculado a um domínio. Use apenas caracteres padrões (incluindo A-Z, a-z, 0-9 e hifens) quando atribuir FQDNs a seus Lync Servers, Servidores de Borda e pools. Não use caracteres Unicode ou sublinhados. Caracteres não padrões em um FQDN frequentemente não são suportados pelo DNS externo e CAs públicas (isso é, quando o FQDN deve ser atribuído ao SN no certificado). Para obter detalhes sobre a adição de um sufixo DNS para um nome do computador, consulte <a href="lync-server-2013-configure-dns-for-edge-support.md">Configurar DNS para suporte à borda no Lync Server 2013</a>.
    
      - Clique em **Pool de computador único** e em **Avançar**.

6.  Em **Selecionar recursos**, faça o seguinte:
    
      - Caso planeje usar um único FQDN e endereço IP para um serviço de acesso SIP, serviço de Webconferência do Lync Server 2013 e serviço de borda A/V, marque a caixa de seleção **Use um único FQDN e Endereço IP**.
    
      - Caso planeje habilitar a federação, marque a caixa de seleção **Habilitar federação para este pool de Borda (porta 5061)**
        
        > [!NOTE]  
        > É possível selecionar esta opção, mas apenas um pool de borda ou servidor de borda de sua organização pode ser publicado externamente para federação. Todo o acesso de usuários federados, inclusive usuários públicos de IM (mensagens instantâneas), atravessa o mesmo pool de borda ou servidor de borda único. Por exemplo, se sua implantação contém um pool de borda ou servidor de borda único implantado em Nova Iorque e outro implantado um Londres e você habilita o suporte à federação no pool de borda ou servidor de borda único de Nova Iorque, o tráfego do sinal para os usuários federados atravessará o pool de borda ou servidor de borda único de Nova Iorque. Isso é verdadeiro até mesmo para comunicações com os usuários de Londres, embora um usuário interno de Londres que liga para um usuário federado do Nova Iorque use um pool ou servidor de borda de Londres para o tráfego de áudio/vídeo.
    
      - Caso planeje oferecer suporte ao protocolo XMPP em sua implantação, marque a caixa de seleção **Habilitar federação XMPP (porta 5269)**

7.  Em **Selecionar Opções de IP**, faça o seguinte:
    
      - **Habilitar IPv4 na interface interna** : marque a caixa de seleção caso deseje aplicar um endereço IPv4 à interface interna do Servidor de Borda ou do Pool de borda
    
      - **Habilitar IPv6 na interface interna** : marque a caixa de seleção caso deseje aplicar um endereço IPv6 à interface interna do Servidor de Borda ou do Pool de borda
    
      - **Habilitar IPv4 na interface externa** : marque a caixa de seleção caso deseje aplicar um endereço IPv4 à interface externa do Servidor de Borda ou do Pool de borda
    
      - **Habilitar IPv6 na interface externa** : marque a caixa de seleção caso deseje aplicar um endereço IPv6 à interface externa do Servidor de Borda ou do Pool de borda
    
    Você também pode configurar o Servidor de Borda ou o Pool de borda para usar um endereço de conversão de endereço de rede para endereços IP externos. Faça isso marcando a caixa de seleção **O endereço IP externo desse pool de Borda é convertido pelo NAT**.

8.  Em **FQDNs externos**, faça o seguinte:
    
      - Se em **Selecionar recursos** você escolher usar um FQDN único e o endereço IP para o acesso SIP, o serviço de Webconferência e um serviço de Borda A/V, digite o FQDN externo em **Acesso SIP**.
        
        > [!NOTE]  
        > Se você escolher esta opção, deverá especificar um número de porta diferente para cada um dos serviços de borda (configurações de porta recomendadas: 5061 para serviço de Acesso de Borda, 444 para serviço de Borda de Conferência Web e 443 para serviço de Borda A/V). Esta opção pode ajudar a evitar possíveis problemas de conectividade e simplificar a configuração porque você pode usar o mesmo número de porta (por exemplo, 443) para os três serviços.
    
      - Se em **Selecionar recursos** você não escolheu usar um FQDN e endereço IP único, digite os FQDNs externo para o **Acesso SIP**, **Conferência Web** e **Áudio vídeo**, mantendo as portas padrão.

9.  Clique em **Avançar**.

10. Em **Definir o endereço IP interno**, digite o endereço IP do seu Servidor de Borda em **Endereço IPv4 interno** e **Endereço IPv6 interno** conforme apropriado para seus requisitos. Clique em **Avançar**.

11. Em **Definir endereço IP externo**, faça o seguinte:
    
      - Caso opte por usar um único FQDN e endereço IP para o acesso SIP, serviço de Webconferência e serviço de borda A/V, digite o endereço IPv4 externo do servidor de borda em **Acesso SIP** e clique em **Avançar**.
    
      - Caso opte por usar endereços IPv6, digite o endereço IPv6 externo do servidor de borda em **Acesso SIP** e clique em **Avançar**.
    
      - Se você não escolheu usar um FQDN e endereço IP único para o acesso SIP, o serviço de Webconferência e o serviço de Borda A/V, digite os endereços IPv4 externos do Servidor de Borda em **Acesso SIP**, **Webconferência** e **Conferência A/V**, e clique em **Avançar**.
    
      - Se você optou por usar endereços IPv6 e não escolheu usar um FQDN e endereço IPv6 único para o acesso SIP, o serviço de Webconferência e o serviço de Borda A/V, digite os endereços IP externos do Servidor de Borda em **Acesso SIP**, **Webconferência** e **Conferência A/V**, e clique em **Avançar**.
        
        > [!NOTE]  
        > Caso não tenha optado por habilitar e atribuir endereços IPv6, você não verá esta caixa de diálogo.


12. Se você optou por usar NAT, uma caixa de diálogo será aberta. Em **Endereço IPv4 público para o serviço de Borda A/V**, digite o endereço IPv4 público a ser convertido pelo NAT e clique em **Avançar**.
    
    > [!NOTE]  
    > Esse endereço deve ser o endereço IP externo do serviço de Borda. A/V.


13. Se você optou por usar NAT e endereços IPv6, uma caixa de diálogo será aberta. Em **Endereço IPv6 público para o serviço de Borda A/V**, digite o endereço IPv6 público a ser convertido pelo NAT e clique em **Avançar**.
    
    > [!NOTE]  
    > Esse endereço deve ser o endereço IP externo do serviço de Borda. A/V.

14. Em **Definir o próximo salto**, em **Próximo pool de salto**, selecione o nome do pool interno, que pode ser um pool de Front-Ends ou um pool do Standard Edition. Em alternativa, se sua implantação incluir um Diretor, selecione o Diretor e clique em **Avançar**.

15. Em **Associar pools de Front-Ends**, especifique um ou mais pools internos, que podem incluir pools de Front-Ends e servidores Standard Edition, para serem associados com este Servidor de Borda selecionando os nomes dos pools internos que devem usar este Servidor de Borda para comunicação com os usuários externos suportados.
    
    > [!NOTE]  
    > Somente um pool de Borda com balanceamento de carga ou Servidor de Borda único pode ser associado a um cada pool interno para tráfego de A/V. Se você já possui um pool interno associado a um pool de Borda ou Servidor de Borda, um aviso será exibido, indicando que o pool interno já está associado a um pool de Borda ou Servidor de Borda. Se um pool que já está associado a outro Servidor de Borda for selecionado, ele alterará a associação.


16. Clique em **Concluir**.

17. Publique sua topologia.

## Para definir a topologia para um pool de Servidor de Borda com balanceamento de carga de DNS

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Na árvore do console, expanda o site em que deseja implantar Servidores de Borda.

3.  Clique com o botão direito em **Pools de Borda** e clique em **Novo Pool de Borda**.

4.  Em **Definir o Novo Pool de Borda**, clique em **Avançar**.

5.  Em **Definir o FQDN do pool de Borda**, faça o seguinte:
    
      - Em **FQDN do pool**, digite o nome de domínio totalmente qualificado (FQDN) para a conexão interna do pool de Borda.
        
        > [!IMPORTANT]  
        > O nome especificado para o pool deve ser o nome do pool de borda interno. Ele deve ser definido como um FQDN. Construtor de Topologias usa FQDNs, não nomes curtos. Use somente caracteres padrão (incluindo A-Z, a-z, 0-9 e hifens) ao atribuir FQDNs dos seus Lync Servers, Servidores de Borda e pools. Não use caracteres Unicode nem sublinhados. Muitas vezes, o DNS externo e as autoridades de certificação públicas não oferecem suporte a caracteres diferentes do padrão em um FQDN (quando o FQDN deve ser atribuído ao SN no certificado).
    
      - Clique em **Pool de vários computadores** e, em seguida, clique em **Avançar**.

6.  Em **Selecionar recursos**, faça o seguinte:
    
      - Caso planeje usar um único FQDN e endereço IP para o acesso SIP, o serviço de Webconferências do Lync Server 2013 e os serviços de Borda de A/V, selecione a opção **Usar um único FQDN e Endereço IP**.
    
      - Se você planeja habilitar a federação, marque a caixa de seleção **Habilitar federação para este pool de Borda (porta 5061)**. Clique em **Avançar**.
        
        > [!NOTE]  
        > Você pode selecionar esta opção, mas somente um pool de Borda ou Servidor de Borda em sua organização pode ser publicado externamente para federação. Todo o acesso por usuários federados, incluindo sistemas de mensagens instantâneas (IM) públicos, passam pelo mesmo pool de Borda ou Servidor de Borda único. Por exemplo, se sua implantação inclui um pool de Borda ou Servidor de Borda único implantado em Nova York e um implantado em Londres e você habilitar o suporte a federação no pool de Borda de Nova York ou no Servidor de Borda único, o tráfego do sinal para usuários federados passará pelo pool de Borda de Nova York ou Servidor de Borda único. Isto é verdade mesmo para comunicações com usuários de Londres, embora um usuário interno de Londres ligando para um usuário federado de Londres use o pool desta cidade ou o Servidor de Borda para tráfego de A/V.
    
      - Caso planeje oferecer suporte ao protocolo XMPP em sua implantação, marque a caixa de seleção **Habilitar federação XMPP (porta 5269)**

7.  Clique em **Avançar**.

8.  Em **Selecionar Opções de IP**, faça o seguinte:
    
      - **Habilitar IPv4 na interface interna** : marque a caixa de seleção caso deseje aplicar um endereço IPv4 à interface interna do Servidor de Borda ou do Pool de borda
    
      - **Habilitar IPv6 na interface interna** : marque a caixa de seleção caso deseje aplicar um endereço IPv6 à interface interna do Servidor de Borda ou do Pool de borda
    
      - **Habilitar IPv4 na interface externa** : marque a caixa de seleção caso deseje aplicar um endereço IPv4 à interface externa do Servidor de Borda ou do Pool de borda
    
      - **Habilitar IPv6 na interface externa** : marque a caixa de seleção caso deseje aplicar um endereço IPv6 à interface externa do Servidor de Borda ou do Pool de borda
    
    Você também pode configurar o Servidor de Borda ou o Pool de borda para usar um endereço de conversão de endereço de rede para endereços IP externos. Faça isso marcando a caixa de seleção **O endereço IP externo desse pool de Borda é convertido pelo NAT**.

9.  Em **FQDNs externos**, faça o seguinte:
    
      - Se em **Selecionar recursos** você optou por usar um único FQDN e Endereço IP para o acesso SIP, serviço de Webconferências e serviço de Borda de A/V, digite o FQDN externo em **Acesso SIP**.
        
        > [!NOTE]  
        > Se você escolher esta opção, deverá especificar um número de porta diferente para cada um dos serviços de borda (configurações de porta recomendadas: 5061 para serviço de Acesso de Borda, 444 para serviço de Borda de Conferência Web e 443 para serviço de Borda A/V). Esta opção pode ajudar a evitar possíveis problemas de conectividade e simplificar a configuração porque você pode usar o mesmo número de porta (por exemplo, 443) para os três serviços.
    
      - Se em **Selecionar recursos** você não optou por usar um único FQDN e Endereço IP, digite o FQDN escolhido para o lado voltado ao público do pool de borda em **Acesso SIP**. Em **Webconferências**, digite o FQDN escolhido para o lado voltado ao público do pool de Borda. Em **Áudio/Vídeo**, digite o FQDN escolhido para o lado voltado ao público do pool de Borda. Use as portas padrão.

10. Clique em **Avançar**.

11. Em **Definir os computadores neste pool**, clique em **Adicionar**.

12. Em **FQDN e endereço IP internos**, faça o seguinte:
    
      - Em **Endereço IPv4 interno**, digite o endereço IPv4 e o **Endereço IPv6 interno** conforme apropriado para seus requisitos para o primeiro servidor de borda que deseja criar no pool.
    
      - Em **FQDN Interno**, digite o FQDN do primeiro Servidor de Borda que deseja criar neste pool.
        
        > [!NOTE]  
        > O nome especificado deve ser idêntico ao nome do computador configurado no servidor. Por padrão, o nome de um computador que não é atribuído a um domínio é um nome curto, não um FQDN. O Construtor de Topologias usa FQDNs, não nomes curtos. Portanto, você deve configurar um sufixo DNS no nome do computador para ser implantado como um Servidor de Borda que não é vinculado a um domínio. Use apenas caracteres padrões (incluindo A-Z, a-z, 0-9 e hífens) quando atribuir FQDNs a seus Lync Servers, Servidores de Borda, pools e matrizes. Não use caracteres Unicode ou sublinhados. Caracteres não padrões em um FQDN frequentemente não são suportados pelo DNS externo e CAs públicos (isso é, quando o FQDN deve ser atribuído ao SN no certificado). Para obter detalhes sobre a adição de um sufixo DNS para um nome do computador, consulte <a href="lync-server-2013-configure-dns-for-edge-support.md">Configurar DNS para suporte à borda no Lync Server 2013</a>.


13. Clique em **Avançar**.

14. Em **Definir os endereços IP externos**, faça o seguinte:
    
      - Se você optou por usar um único FQDN e Endereço IP para o acesso SIP, serviço de Webconferências e serviço de Borda de A/V, digite o endereço IP externo do Servidor de Borda em **Acesso SIP**.
    
      - Se você não optou por usar um único FQDN e Endereço IP para o acesso SIP, serviço de Webconferências e serviço de Conferências de A/V, digite o endereço IP escolhido para o lado voltado ao público deste servidor de pool de Borda no **Acesso SIP**. Em **Webconferências**, digite o endereço IP escolhido para o lado voltado ao público deste servidor de pool de Borda. Em **Conferências de A/V**, digite o endereço IP escolhido para o lado voltado ao público deste servidor de pool de Borda.

15. Clique em **Avançar**.

16. Caso opte por habilitar endereços IPv6, em **Definir endereços IP externos**, faça o seguinte:
    
      - Se você optou por usar um único FQDN e Endereço IPv6 para o acesso SIP, serviço de Webconferências e serviço de Borda de A/V, digite o endereço IP externo do Servidor de Borda em **Acesso SIP**.
    
      - Se você não optou por usar um único FQDN e Endereço IP para o acesso SIP, serviço de Webconferências e serviço de Conferências de A/V, digite o endereço IPv6 escolhido para o lado voltado ao público deste servidor de pool de Borda no **Acesso SIP**. Em **Webconferências**, digite o endereço IPv6 escolhido para o lado voltado ao público deste servidor de pool de Borda. Em **Conferências de A/V**, digite o endereço IPv6 escolhido para o lado voltado ao público deste servidor de pool de Borda.
    
    > [!NOTE]
    > Caso não tenha optado por habilitar e atribuir endereços IPv6, você não verá esta caixa de diálogo.


17. Clique em **Concluir**.
    
    > [!NOTE]  
    > Agora você verá o primeiro Servidor de Borda criado em seu pool na caixa de diálogo <strong>Definir os computadores neste pool</strong>.


18. Em **Definir os computadores neste pool**, clique em **Adicionar** e repita as etapas 11 até 14 para o segundo Servidor de Borda que deseja adicionar ao seu pool de Borda.

19. Depois de repetir as etapas 11 a 14, clique em **Avançar** em **Definir os computadores neste pool**.
    
    > [!NOTE]  
    > Neste ponto, você poderá ver ambos os Servidores de Borda em seu pool.


20. Se você optou por usar NAT, uma caixa de diálogo será aberta. Em **Endereço IP público**, digite o endereço IPv4 e IPv6 público (se apropriado) a ser convertido pelo NAT e clique em **Avançar**.
    
    > [!NOTE]  
    > Este deve ser o endereço IP externo da Borda de A/V.

21. Em **Definir o próximo salto**, na lista **Pool do próximo salto**, selecione o nome do pool interno, que pode ser um pool de Front-Ends ou um pool Standard Edition. Ou, se sua implantação inclui um Diretor, selecione o nome do Diretor. Em seguida, clique em **Avançar**.

22. Em **Associar pools de Front End**, especifique um ou mais pools internos, que podem incluir pools de Front End e servidores Standard Edition, a serem associados a este Servidor de Borda, selecionando os nomes do(s) pool(s) interno(s) que usará(ão) este Servidor de Borda para comunicação com usuários externos suportados.
    
    > [!NOTE]  
    > Somente um pool de Borda com balanceamento de carga ou Servidor de Borda único pode ser associado a um cada pool interno para tráfego de A/V. Se você já possui um pool interno associado a um pool de Borda ou Servidor de Borda, um aviso será exibido, indicando que o pool interno já está associado a um pool de Borda ou Servidor de Borda. Se um pool que já está associado a outro Servidor de Borda for selecionado, ele alterará a associação.


23. Clique em **Concluir**.

24. Publique sua topologia.

## Para definir a topologia de um pool de Servidor de Borda com balanceamento de carga de hardware

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Na árvore do console, expanda o site em que deseja implantar Servidores de Borda.

3.  Clique com o botão direito do mouse em **Pools de Borda** e clique em **Novo Pool de Borda**.

4.  Em **Definir o Novo Pool de Borda**, clique em **Avançar**.

5.  Em **Definir o FQDN do pool de Borda**, faça o seguinte:
    
      - Em **FQDN**, digite o FQDN (nome de domínio totalmente qualificado) escolhido para o lado interno do pool de borda.
        
        
        > [!IMPORTANT]  
        > O nome especificado para o pool deve ser o nome do pool de borda interno. Ele deve ser definido como um FQDN. Construtor de Topologias usa FQDNs, não nomes curtos. Use somente caracteres padrão (incluindo A-Z, a-z, 0-9 e hifens) ao atribuir FQDNs dos seus Lync Servers, Servidores de Borda e pools. Não use caracteres Unicode nem sublinhados. Muitas vezes, o DNS externo e as autoridades de certificação públicas não oferecem suporte a caracteres diferentes do padrão em um FQDN (quando o FQDN deve ser atribuído ao SN no certificado).
    
    <!-- end list -->
    
      - Clique em **Vários pools de computador** e em **Avançar**.

6.  Em **Selecionar recursos**, faça o seguinte:
    
      - Se você planeja usar um único endereço IP e FQDN para o serviço de acesso SIP, o serviço de Webconferência do Lync Server e os serviços de Borda de A/V, marque a caixa de seleção **Use um único FQDN e Endereço IP**.
    
      - Se você planeja habilitar a federação, marque a caixa de seleção **Habilitar federação para este pool de Borda (porta 5061)**.
        
        > [!NOTE]  
        > Você pode selecionar esta opção, mas somente um pool de Borda ou Servidor de Borda em sua organização pode ser publicado externamente para federação. Todo o acesso por usuários federados, incluindo as mensagens instantâneas públicas de usuários, percorrem o mesmo pool de Borda ou um único Servidor de Borda. Por exemplo, se sua implantação inclui um pool de Borda ou único Servidor de Borda implantado em Nova York e um implantado em Londres e você ativar o suporte à federação no pool de Borda de Nova York ou no Servidor de Borda único, o tráfego de sinal para os usuários federados passará através do pool de Borda de Nova York ou do Servidor de Borda único. Isso se aplica mesmo para a comunicação com os usuários de Londres, embora um usuário interno de Londres que chama um usuário federado de Londres use o pool de Londres ou o Servidor de Borda para um tráfego de A/V.
    
      - Caso planeje oferecer suporte ao protocolo XMPP em sua implantação, marque a caixa de seleção **Habilitar federação XMPP (porta 5269)**

7.  Clique em **Avançar**.

8.  Em **Selecionar Opções de IP**, faça o seguinte:
    
      - **Habilitar IPv4 na interface interna** : marque a caixa de seleção caso deseje aplicar um endereço IPv4 à interface interna do Servidor de Borda ou do Pool de borda
    
      - **Habilitar IPv6 na interface interna** : marque a caixa de seleção caso deseje aplicar um endereço IPv6 à interface interna do Servidor de Borda ou do Pool de borda
    
      - **Habilitar IPv4 na interface externa** : marque a caixa de seleção caso deseje aplicar um endereço IPv4 à interface externa do Servidor de Borda ou do Pool de borda
    
      - **Habilitar IPv6 na interface externa** : marque a caixa de seleção caso deseje aplicar um endereço IPv6 à interface externa do Servidor de Borda ou do Pool de borda
    
    > [!IMPORTANT]  
    > <strong>Não</strong> marque a caixa de seleção <strong>O endereço IP externo do pool de Borda é convertido pelo NAT</strong>. A NAT (conversão de endereços de rede) não é suportada quando você está usando o balanceamento de carga de hardware.


9.  Em **FQDNs externos**, faça o seguinte:
    
      - Se em **Selecionar recursos** você escolher usar um FQDN único e o endereço IP para o acesso SIP, o serviço de Webconferência e um serviço de Borda A/V, digite o FQDN externo em **Acesso SIP**.
        
        > [!NOTE]  
        > Se você escolher esta opção, deverá especificar um número de porta diferente para cada um dos serviços de borda (configurações de porta recomendadas: 5061 para serviço de Acesso de Borda, 444 para serviço de Borda de Conferência Web e 443 para serviço de Borda A/V). Esta opção pode ajudar a evitar possíveis problemas de conectividade e simplificar a configuração porque você pode usar o mesmo número de porta (por exemplo, 443) para os três serviços.
    
      - Se em **Selecionar recursos** você não optou por usar um único FQDN e Endereço IP, digite o FQDN escolhido para o lado voltado ao público do pool de borda em **Acesso SIP**. Em **Webconferências**, digite o FQDN escolhido para o lado voltado ao público do pool de Borda. Em **Áudio/Vídeo**, digite o FQDN escolhido para o lado voltado ao público do pool de Borda. Use as portas padrão.
        
        > [!NOTE]  
        > Estes serão os FQDNs de IP virtual (VIP) voltados ao público para o pool.


10. Clique em **Avançar**.

11. Em **Definir os computadores neste pool**, clique em **Adicionar**.

12. Em **Definir os endereços IP externos**, faça o seguinte:
    
      - Caso opte por usar um único FQDN e endereço IP para o acesso SIP, serviço de Webconferência e serviço de borda A/V, digite o endereço IPv4 externo do servidor de borda em **Acesso SIP**.endereço IP externo do servidor de borda em **Acesso SIP**.
    
      - Se você não optou por usar um único FQDN e Endereço IP para o acesso SIP, serviço de Webconferências e serviço de Conferências de A/V, digite o endereço IP escolhido para o lado voltado ao público deste servidor de pool de Borda no **Acesso SIP**. Em **Webconferências**, digite o endereço IP escolhido para o lado voltado ao público deste servidor de pool de Borda. Em **Conferências de A/V**, digite o endereço IP escolhido para o lado voltado ao público deste servidor de pool de Borda.

13. Clique em **Avançar**.

14. Caso opte por habilitar endereços IPv6, em **Definir endereços IP externos**, faça o seguinte:
    
      - Se você optou por usar um único FQDN e Endereço IPv6 para o acesso SIP, serviço de Webconferências e serviço de Borda de A/V, digite o endereço IP externo do Servidor de Borda em **Acesso SIP**.
    
      - Se você não optou por usar um único FQDN e Endereço IP para o acesso SIP, serviço de Webconferências e serviço de Conferências de A/V, digite o endereço IPv6 escolhido para o lado voltado ao público deste servidor de pool de Borda no **Acesso SIP**. Em **Webconferências**, digite o endereço IPv6 escolhido para o lado voltado ao público deste servidor de pool de Borda. Em **Conferências de A/V**, digite o endereço IPv6 escolhido para o lado voltado ao público deste servidor de pool de Borda.
    
    > [!NOTE]  
    > Caso não tenha optado por habilitar e atribuir endereços IPv6, você não verá esta caixa de diálogo.


15. Clique em **Concluir**.
    
    > [!NOTE]  
    > Agora você verá o primeiro Servidor de Borda criado em seu pool na caixa de diálogo <strong>Definir os computadores neste pool</strong>.


16. Em **Definir os computadores deste pool**, clique em **Adicionar** e repita as etapas de 11 a 14 para o segundo Servidor de Borda que você deseja adicionar ao pool de Borda.

17. Depois de repetir as etapas 11 a 14, clique em **Avançar** em **Definir os computadores neste pool**.
    
    > [!NOTE]  
    > Neste ponto, você poderá ver ambos os Servidores de Borda em seu pool.


18. Em **Definir o próximo salto**, na lista **Pool do próximo salto**, selecione o nome do pool interno, que pode ser um pool de Front-Ends ou um pool Standard Edition. Ou, se sua implantação inclui um Diretor, selecione o nome do Diretor. Em seguida, clique em **Avançar**.

19. Em **Associar pools de Front End**, especifique um ou mais pools internos, que podem incluir pools de Front End e servidores Standard Edition, a serem associados a este Servidor de Borda, selecionando os nomes do(s) pool(s) interno(s) que usará(ão) este Servidor de Borda para comunicação com usuários externos suportados.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Somente um pool de Borda com balanceamento de carga ou Servidor de Borda único pode ser associado a um cada pool interno para tráfego de A/V. Se você já possui um pool interno associado a um pool de Borda ou Servidor de Borda, um aviso será exibido, indicando que o pool interno já está associado a um pool de Borda ou Servidor de Borda. Se um pool que já está associado a outro Servidor de Borda for selecionado, ele alterará a associação.</td>
    </tr>
    </tbody>
    </table>


20. Clique em **Concluir**.

21. Publique sua topologia.

