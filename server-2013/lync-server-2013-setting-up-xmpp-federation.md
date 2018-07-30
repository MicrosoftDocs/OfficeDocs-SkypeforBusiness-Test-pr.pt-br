---
title: 'Lync Server 2013: Configurando federação de XMPP'
TOCTitle: Configurando federação de XMPP
ms:assetid: 5fda6cb7-8d4d-495d-90c7-601f1036e085
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204939(v=OCS.15)
ms:contentKeyID: 49306868
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando federação de XMPP no Lync Server 2013

 

_**Tópico modificado em:** 2012-12-03_

Para implantar o proxy XMPP no servidor de borda, você deve configurar o servidor de borda para a federação XMPP. Para isso, execute as etapas a seguir.

## Configurando a Federação XMPP

1.  Faça logon no computador no qual o Assistente de Implantação do Lync Server está instalado como um membro do grupo Admins. do Domínio e do grupo RTCUniversalServerAdmins.

2.  No servidor front-end, abra o Assistente para Implantação do Lync Server. Clique em Instalar ou Atualizar o Sistema do Lync Server e depois em Instalar ou Remover os Componentes de Servidor do Lync Server. Clique em Executar Novamente.

3.  Em Instalar Componentes do Lync Server, clique em Avançar. A tela de resumo mostrará as ações conforme forem executadas. Depois que a implantação estiver concluída, clique em Exibir Log para exibir os arquivos de log disponíveis. Clique em Concluir para concluir a implantação.

4.  No servidor de borda, abra o assistente Implantação do Lync Server. Clique em Instalar ou Atualizar Sistema do Lync Server e, então, clique em Instalar ou Remover Componentes do Lync Server. Clique em Executar Novamente.

5.  Em Instalar Componentes do Lync Server, clique em Avançar. A tela de resumo mostrará as ações conforme forem executadas. Depois que a implantação estiver concluída, clique em Exibir Log para exibir os arquivos de log disponíveis. Clique em Concluir para concluir a implantação.

6.  No Servidor de Borda, no Assistente de Implantação, próximo a Etapa 3: Solicitar, instalar ou atribuir certificados, clique em Executar novamente.
    

    > [!TIP]
    > Se estiver implantando o Servidor de Borda pela primeira vez, você verá Executar ao invés de Executar novamente.



7.  Na página Tarefas de Certificado Disponíveis, clique em Criar uma nova solicitação de certificado.

8.  Na página Solicitação de Certificado, clique em Certificado de Borda Externa.

9.  Na página Solicitação Atrasada ou Imediata, marque a caixa de seleção Preparar a solicitação agora, mas enviá-la depois.

10. Na página Arquivo de Solicitação de Certificado, digite o nome de arquivo e o caminho completo do arquivo no qual a solicitação será salva (por exemplo, c:\\cert\_exernal\_edge.cer).

11. Na página Especificar Modelo de Certificado Alternativo, para usar um modelo diferente do modelo WebServer padrão, marque a caixa de seleção Usar o modelo de certificado alternativo para a autoridade de certificação selecionada.

12. Na página Nome e Configurações de Segurança, siga estes procedimentos:
    
    1.  Em Nome Amigável, digite um nome de exibição para o certificado.
    
    2.  Em Comprimento de bit, especifique o comprimento de bit (normalmente o padrão de 2048).
    
    3.  Verifique se a caixa de seleção Marcar chave privada de certificado como exportável está marcada.

13. Na página Informações da Organização, digite o nome da organização e a unidade organizacional (por exemplo, uma divisão ou um departamento).

14. Na página Informações Geográficas, especifique as informações de localização.

15. Na página Nome da Entidade/Nomes Alternativos da Entidade, as informações a serem preenchidas automaticamente pelo assistente são exibidas. Se nomes alternativos de entidade adicionais forem necessários, especifique-os nas próximas duas etapas.

16. Na página Configuração do Domínio SIP em SANs (Nomes Alternativos da Entidade), marque a caixa de seleção do domínio para adicionar uma entrada sip.\<domínio\_sip\> à lista de nomes alternativos da entidade.

17. Na página Configurar Nomes Alternativos da Entidade Adicionais, especifique os nomes alternativos de entidade adicionais que sejam necessários.
    

    > [!TIP]
    > Se o proxy XMPP é instalado, por padrão o nome de domínio (como contoso.com) é preenchido nas entradas SAN. Se você precisa de mais entradas, adicione-as nesta etapa.



18. Na página Resumo da Solicitação, examine as informações do certificado a ser usado para gerar a solicitação.

19. Após o comando finalizar a execução, é possível Exibir o Log ou clicar em Avançar para continuar.

20. Na página Arquivo de solicitação de certificado, é possível exibir o arquivo CSR gerado clicando em Exibir ou sair do Assistente de Certificado clicando em Concluir.

21. Copie o arquivo solicitado e envie-o para a autoridade de certificação pública.

22. Após receber, importar e atribuir o certificado público, você deve parar e reiniciar os serviços do Servidor de Borda. Você faz isso digitando no console do Gerenciamento do Lync Server:
    
```
        Stop-CsWindowsService
```
```    
        Start-CsWindowsService
```

23. Para configurar o DNS para a federação XMPP, adicione o seguinte registro SRV ao DNS externo:\_xmpp-server.\_tcp.\<nome de domínio\> O registro SRV será resolvido no FQDN (nome de domínio totalmente qualificado) de borda de acesso do servidor de borda com o valor de porta 5269. Além disso, configure um registro de host "A" (por exemplo, xmpp.contoso.com) que aponte para o endereço IP do servidor de borda de acesso.
    
    > [!IMPORTANT]  
    > Se você tiver pools de borda em vários sites, é recomendável que adicione vários registros SRV para federação XMPP. Adicione um registro SRV para cada pool de borda de sua organização e atribua a cada um desses registros SRV uma prioridade diferente. Quando todos os pools de borda estiverem em execução, as solicitações XMPP serão todas manipuladas pelo pool de borda com a maior prioridade, mas, se esse pool de borda ficar inoperante, você não precisará adicionar um novo registro SRV para recuperar a funcionalidade de federação XMPP.

24. Configure uma nova política de acesso externo para habilitar todos os usuários abrindo o Shell de Gerenciamento do Lync Server no front-end e digitando:
    
    ```
        New-CsExternalAccessPolicy -Identity <name of policy to create.  If site scope, prepend with 'site:'> -EnableFederationAcces $true -EnablePublicCloudAccess $true
    ```
    ```    
        New-CsExternalAccessPolicy -Identity FedPic -EnableFederationAcces $true -EnablePublicCloudAccess $true
    ```
    ```    
        Get-CsUser | Grant-CsExternalAccessPolicy -PolicyName FedPic
    ```
    ```
    Habilite o acesso XMPP para usuários externos digitando:
    ```
    ```    
        Set-CsExternalAccessPolicy -Identity <name of the policy being used> EnableXmppAccess $true
    ```
    ```    
        Set-CsExternalAccessPolicy -Identity FedPic -EnableXmppAccess $true
    ```

25. No Servidor de Borda em que o proxy XMPP está implantado, abra um prompt de comando ou uma Interface da linha de comando do Windows PowerShell™ e digite o seguinte:
    
    ```
        Netstat -ano | findstr 5269
    ```
    ```    
        Netstat -ano | findstr 23456
    ```    
    
    O comando **netstat –ano** é um comando de estatísticas de rede, os parâmetros **–ano** exigem que netstat exiba todas as conexões e portas de escuta, que o endereço e as portas sejam exibidos em um formato numérico, e que o ID do processo proprietário seja associado a cada conexão. O caractere **|** define uma barra vertical ao próximo comando, **findstr**, ou localizar cadeia de caracteres. O número 5269 e 23456 passado ao findstr como parâmetro instrui findstr a pesquisar a saída de netstat para a cadeia de caracteres 5269 e 23456. Se XMPP estiver configurado corretamente, o resultado dos comandos deve resultar em conexões estabelecidas e de escuta nas interfaces externa (porta 5269) e interna (porta 23456) do Servidor de Borda.
    
    Se os comandos não retornarem as portas estabelecidas ou de escuta em 5269 e 23456, verifique o seguinte:

## Solucionando problemas da federação XMPP

1.  Para determinar se o proxy XMPP está em execução, faça o seguinte:

2.  Faça logon no servidor de borda que está executando o serviço do proxy XMPP como membro do grupo de administrador local.

3.  Clique em **Iniciar**, em **Todos os Programas**, em **Ferramentas Administrativas** e em **Serviços**

4.  Em Serviços, localize Proxy do Gateway de Tradução XMPP do Lync Server. O serviço deverá estar no estado **Iniciado**. Se ele não estiver iniciado, clique no ícone **Iniciar** na barra de ferramentas. O ícone se parece com uma seta verde apontando para a direita.

5.  Confirme se o serviço mudou para **Iniciado**. Se ele tiver sido iniciado com êxito, feche **Serviços** e continue o procedimento.
    
    Se o serviço não tiver sido iniciado com êxito, nas Ferramentas Administrativas, abra o Visualizador de Eventos e consulte os erros e avisos na parte **Lync Server** em **Logs de Aplicativos e Serviços**.

6.  Depois que o serviço **Proxy do Gateway de Tradução XMPP do Lync Server** estiver em execução, verifique novamente os comandos netstat usados anteriormente. Se as sessões estabelecidas e de escuta não forem exibidas, verifique se a **Rota de Federação XMPP** está configurada corretamente no Construtor de Topologias

7.  Faça logon no computador no qual o Construtor de Topologias está instalado como um membro do grupo Admins. do Domínio ou do grupo RTCUniversalServerAdmins.

8.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

9.  No Construtor de Topologias, selecione o site para a rota de federação XMPP e verifique para confirmar se a **Atribuição da rota de federação do site** para **Federação XMPP** mostra seu Servidor de Borda ou seu Pool de borda como a atribuição de rota de federação XMPP.
    
    Se a atribuição de rota estiver incorreta ou não estiver definida, clique com o botão direito do mouse no site e depois em **Editar Propriedades**. Marque a caixa de seleção de federação XMPP e selecione o Servidor de Borda ou Pool de borda correto.

10. Publique a topologia. Para obter detalhes, consulte [Publicar sua topologia no Lync Server 2013](lync-server-2013-publish-your-topology.md)
    

    > [!TIP]
    > Embora não seja obrigatório e geralmente não seja necessário, eventualmente, você talvez precise reiniciar os Servidores de Borda



11. Usando o processo netstat descrito anteriormente, confirme se o Servidor de Borda agora está ouvindo e tem sessões estabelecidas nas portas 5269 e 23456.

12. Se as sessões esperadas ainda não forem exibidas, verifique o Visualizador de Eventos para ver se há possíveis causas para o problema de comunicação.

## Consulte Também

#### Tarefas

[Exemplo de configuração de XMPP no Lync Server 2013 – federação XMPP com Google Talk](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  

#### Outros Recursos

[Gerenciar parceiros XMPP federados no Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)

