---
title: Configurando um nó inspetor para usar a autenticação de servidor confiável
TOCTitle: Configurando um nó inspetor para usar a autenticação de servidor confiável
ms:assetid: 42d879ac-aa90-4ed6-b5e2-1e208711672a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204852(v=OCS.15)
ms:contentKeyID: 49306548
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando um nó inspetor para usar a autenticação de servidor confiável

 

_**Tópico modificado em:** 2012-10-22_

Caso o seu computador de nó do inspetor estiver dentro da rede de perímetro, utilizar uma autenticação de Servidor Confiável pode reduzir drasticamente as taxas de administração para manter um único certificado em vez de diversas senhas de conta de usuário.

A primeira etapa na configuração da autenticação de Servidor Confiável é criar um pool de aplicativo confiável para hospedar o computador de nó do inspetor. Depois que o pool de aplicativo confiável tiver sido criado, você deverá então configurar transações sintéticas nos nós do inspetor para executar como um aplicativo confiável.

> [!NOTE]  
> Um aplicativo confiável é um aplicativo que recebe o status de confiável para executar como parte do Lync Server 2013, mas que não é parte incorporada do produto. O status de confiável significa que o aplicativo não será desafiado para autenticação toda vez que executar.

Para criar um pool de aplicativo confiável, abra o Shell de Gerenciamento do Lync Server 2013 e execute um comando similar a este:

    New-CsTrustedApplicationPool -Identity atl-watcher-001.litwareinc.com -Registrar atl-cs-001.litwareinc.com -ThrottleAsServer $True -TreatAsAuthenticated $True -OutboundOnly $False -RequiresReplication $True -ComputerFqdn atl-watcher-001.litwareinc.com -Site Redmond

> [!NOTE]  
> Para detalhes sobre os parâmetros utilizados no comando anterior, digite o seguinte no prompt do Shell de Gerenciamento do Lync Server:<br />Get-Help New-CsTrustedApplicationPool -Full | more

Após criar o pool de aplicativo confiável, configure o computador de nó do inspetor para executar transações sintéticas como aplicativo confiável. Isso é feito utilizando o cmdlet **New-CsTrustedApplication** e um comando similar a este:

    New-CsTrustedApplication -ApplicationId STWatcherNode -TrustedApplicationPoolFqdn atl-watcher-001.litwareinc.com -Port 5061

Quando o comando estiver concluído e o aplicativo confiável for criado, execute Enable-CsTopology para certificar-se de que as alterações tenham efeito:

    Enable-CsTopology

Após executar o Enable-CsTopology, recomendamos que você reinicie o computador.

Para verificar que o novo aplicativo confiável foi criado, digite o seguinte no prompt do Shell de Gerenciamento do Lync Server:

    Get-CsTrustedApplication -Identity "atl-watcher-001.litwareinc.com/urn:application:STWatcherNode"

## Configurando um certificado padrão no nó do inspetor

Cada nó do inspetor deve ter um certificado padrão atribuído utilizando o Assistente de Implantação do Lync Server.

**Para atribuir um certificado padrão**

1.  Clique em **Iniciar**, clique em **Todos os Programas**, clique em **Servidor Lync** e, então, em **Assistente de Implantação do Lync Server**.

2.  Em Assistente de Implantação do Lync Server, clique em **Instalar ou Atualizar o Sistema do Servidor Lync** e clique em **Executar**, sob o cabeçalho **Solicitar, Instalar ou Atribuir Certificado**.
    
    > [!NOTE]  
    > Caso o botão <strong>Executar</strong> esteja inativo, talvez você precise clicar primeiro em <strong>Executar</strong>, sob <strong>Instalar Repositório de Configuração Local</strong>.

3.  Faça um dos seguintes:
    
      - Se você já tiver um certificado que possa ser utilizado como certificado padrão, clique em **Padrão** no assistente de Certificado e, então, clique em **Atribuir**. Siga as etapas no assistente de Atribuição de Certificado para atribuí-lo.
    
      - Se você precisar solicitar um certificado para utilizar o certificado padrão, clique em **Solicitar** e, então, siga as etapas no assistente de Solicitação de Certificado. Se você utilizar valores padrão para o certificado de Servidor da Web, você terá um certificado que pode ser atribuído como certificado padrão.

## Instalando e configurando um nó de inspetor

Depois de ter reiniciado o computador de nó do inspetor e configurado o certificado, você precisará executar o arquivo Watchernode.msi. (Você deve executar o Watchernode.msi em um computador onde ambos os arquivos de agente do Gerenciador de Operações e os componentes principais do Lync Server 2013 estão instalados.)

**Para instalar e configurar um nó de inspetor**

1.  Abra o Shell de Gerenciamento do Lync Server clicando em **Iniciar**, então em **Todos os Programas**, **Servidor Lync** e, então, em **Shell de Gerenciamento do Lync Server**.

2.  Em Shell de Gerenciamento do Lync Server, digite o seguinte comando e pressione ENTER (especifique o caminho atual para a cópia do Watchernode.msi):
    
        C:\Tools\Watchernode.msi Authentication=TrustedServer
    
    > [!NOTE]  
    > Você também pode executar o Watchernode.msi de uma janela de comando. Para abrir uma janela de comando, clique em <strong>Iniciar</strong>, clique com o botão direito do mouse em <strong>Prompt de comando</strong> e, então, em <strong>Executar como administrador</strong>. Quando a janela de comando abrir, digite o mesmo comando anterior.

Observe que o par de valor/nome no comando anterior Authentication=TrustedServer diferencia maiúscula de minúscula. Você deve digitar exatamente como mostrado. O comando a seguir falha porque não utiliza a formatação correta:

C:\\Tools\\Watchernode.msi authentication=trustedserver

Você pode utilizar o modo TrustedServer apenas com computadores que estão localizados na rede do perímetro. Quando um nó de inspetor está executando no modo TrustedServer, os administradores não precisam manter senhas de usuário de teste no computador.

