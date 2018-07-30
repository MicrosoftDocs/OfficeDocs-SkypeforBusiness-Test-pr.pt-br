---
title: Implantando porta não padrão e alias do SQL Server no Lync Server 2013
TOCTitle: Implantando porta não padrão e alias do SQL Server no Lync Server 2013
ms:assetid: 2da92c1f-250e-407a-8651-fb2aec76aeb0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn776290(v=OCS.15)
ms:contentKeyID: 62634504
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando porta não padrão e alias do SQL Server no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Microsoft Lync Server 2013 oferece suporte ao uso de uma porta não padrão e um alias do SQL Server. O uso de uma porta não padrão e um alias do SQL Server aumenta a segurança e cria um ambiente mais flexível para a implantação do Lync. Essas etapas são apenas uma para proteger de forma adequada o ambiente do Lync Server 2013. Etapas adicionais devem ser executadas para reduzir a superfície de ataque de uma implementação do Lync Server 2013.

O artigo a seguir descreve as etapas necessárias para configurar uma porta não padrão e um alias do SQL Server no Lync Server 2013.

## Implantando uma porta não padrão e um alias do SQL Server no Lync Server 2013

O Construtor de Topologias do Lync Server 2013 oferece suporte ao uso de um alias do SQL Server como o FQDN (nome de domínio totalmente qualificado) em vez do FQDN real do SQL Server ao configurar o Lync Server 2013. Isso permite que o FQDN real do SQL Server fique oculto para qualquer invasor mal-intencionado. Além disso, o uso de uma porta não padrão esconde a porta real de qualquer invasor que tentar atacar o banco de dados na porta padrão 1433, conforme mostra a figura a seguir.

![O hacker não sabe o número da porta para atacar.](images/Dn776290.2f3923e0-2bdc-416b-a66b-bf56599eb14e(OCS.15).jpg "O hacker não sabe o número da porta para atacar.")

Para determinar com êxito a porta que o Lync Server 2013 utiliza para se comunicar com o SQL Server, o invasor precisa verificar todas as portas para obter as informações da porta. A verificação de porta realizada por um invasor aumenta as chances de a segurança detectar e interromper a instrução. Além de adicionar mais segurança com uma porta não padrão, também é possível usar um alias do SQL Server para oferecer flexibilidade à implantação. Isso é importante para reduzir as alterações de configuração em situações em que uma alteração de nome no SQL Server é necessária.

> [!NOTE]  
> O SQL Server fornece dois métodos de tolerância a falhas (Cluster de Failover e Espelhamento). Os dois métodos de tolerância a falhas do SQL Server têm suporte ao usar uma porta não padrão e um alias do SQL Server com o Lync Server 2013.

Ao configurar a conectividade do banco de dados do SQL Server a partir do Construtor de Topologias, ou ao utilizar o cmdlet Install-CsDatabase, não é possível definir explicitamente um número de porta não padrão do SQL Server e associá-lo a uma instância SQL. Para definir uma porta não padrão, é necessário usar os utilitários do SQL Server e do Windows Server.

Para configurar uma porta não padrão e um alias do SQL Server para uso com o Lync Server 2013, será necessário concluir três etapas principais. As etapas são:

  - Confirmar que o Lync Server 2013 tem as atualizações mais recentes aplicadas.

  - Configurar a porta não padrão e o alias do SQL Server.

  - Configurar o Lync Server 2013 com o alias do SQL Server utilizando o Construtor de Topologias.

  - Publicar a topologia e verificar o banco de dados.

## Confirmar que o Lync Server 2013 tem as atualizações mais recentes aplicadas

É importante manter o Lync Server 2013 atualizado. Para verificar as atualizações mais recentes e as informações sobre como aplicá-las, consulte [Atualizações para o Lync Server 2013](http://support.microsoft.com/kb/2809243).

## Configurar a porta não padrão e o alias do SQL Server

A porta não padrão e o alias do SQL Server devem ser configurados na instância do banco de dados para que sejam referenciados a partir do Construtor de Topologias do Lync Server 2013 . Para configurar uma porta não padrão e um alias do SQL Server, será necessário concluir três etapas principais. As etapas são:

  - Alterar os valores do protocolo TCP/IP padrão.

  - Criar e configurar um alias do SQL Server.

  - Criar um registro de recurso do CNAME (Nome Canônico) do DNS (Sistema de Nomes de Domínio).

**Modificar os valores do protocolo TCP/IP padrão**

1.  Selecione **Iniciar** e escolha **SQL Server Configuration Manager**, conforme mostra a figura a seguir.
    
    ![O ícone do SQL Server Management Studio](images/Dn776290.6e811f27-cea9-4437-b44c-55bff013150f(OCS.15).png "O ícone do SQL Server Management Studio")

2.  No painel de navegação, opte por expandir a **instância do SQL Server**, a **Configuração de rede do SQL Server** e escolha **Protocolos para \<instance name\>**, conforme mostra a figura a seguir.
    
    ![Navegar para propriedades de TCP/IP](images/Dn776290.3d7a964c-f17e-47fd-8f0c-535453da7fad(OCS.15).jpg "Navegar para propriedades de TCP/IP")

3.  No painel à direita, clique com o botão direito em **TCP/IP** e selecione **Propriedades**. A caixa de diálogo Propriedades de TCP/IP é exibida.

4.  Selecione a guia **Endereços IP**. A guia Endereços IP exibe todos os endereços IP ativos no servidor. Eles estão no formato IP1, IP2, até IPAll, conforme mostra a figura a seguir.
    
    ![Abrir propriedades de TCP/IP.](images/Dn776290.ed2fd70d-1836-4ebf-80fe-09191d96585e(OCS.15).jpg "Abrir propriedades de TCP/IP.")

5.  Limpe o campo **Portas Dinâmicas TCP** de todos os endereços IP. Se o campo contiver um caractere zero, isso significa que o SQL Server está realizando a escuta nas portas dinâmicas. Certifique-se de que esses campos sejam limpos e não contenham zero.

6.  Para o endereço IP que o Lync Server utilizará para se conectar ao banco de dados, certifique-se de que **Enabled** esteja definido como **Sim**, conforme mostra a figura a seguir.
    
    ![Definir habilitado como Sim para o IP correto.](images/Dn776290.7f818b91-0793-4594-8932-90447270fad9(OCS.15).jpg "Definir habilitado como Sim para o IP correto.")

7.  Na seção **IPAll** na parte inferior da caixa de diálogo, insira a porta desejada no campo **Porta TCP**, conforme mostra a figura a seguir. Neste exemplo, utilizamos a porta 50062, mas é possível usar qualquer porta entre 49152 e 65535. Essas são as portas atribuídas ao uso dinâmico e privado, e isso garante que não haverá conflito com outras portas em uso na implantação do Lync Server 2013.
    
    ![Definir porta na seção IPAll.](images/Dn776290.b5af53e2-7961-4664-b586-3ca8f3a17f06(OCS.15).jpg "Definir porta na seção IPAll.")

8.  Escolha **OK** para sair da caixa de diálogo Propriedades de TCP/IP.

9.  Reinicie a instância do SQL Server com a seleção de **Serviços do SQL Server** no painel à esquerda do SQL Server Configuration Manager. Em seguida, clique com o botão direito em **\<instance name\> do SQL Server** no painel à direita e selecione **Reiniciar**, conforme mostra a figura a seguir.
    
    ![Redefinir o serviço SQL Server para instância.](images/Dn776290.a965c8cf-f769-4b52-bb38-c48a438cf491(OCS.15).jpg "Redefinir o serviço SQL Server para instância.")

> [!IMPORTANT]  
> Certifique-se de atualizar as configurações de firewall para acomodar a nova porta do SQL Server.

**Criar e configurar um alias do SQL Server**

1.  Selecione **Iniciar** e escolha **SQL Server Configuration Manager**, conforme mostra a figura a seguir.
    
    ![O ícone do SQL Server Management Studio](images/Dn776290.6e811f27-cea9-4437-b44c-55bff013150f(OCS.15).png "O ícone do SQL Server Management Studio")

2.  No painel à esquerda, opte por expandir **instância do SQL Server**, **Configuração do SQL Native Client \<version\>** e escolha **Aliases**, conforme mostra a figura a seguir.
    
    ![Alias no SQL Server Configuration Manager.](images/Dn776290.95341826-55d7-425f-ae19-d47d6668c5d8(OCS.15).jpg "Alias no SQL Server Configuration Manager.")

3.  Clique com o botão direito em **Aliases** e selecione **Novo Alias…**.

4.  Insira o **Nome do Alias**, **Número da Porta**, **Protocolo** e **Servidor**, conforme mostra a figura a seguir.
    
    ![Criando um novo alias](images/Dn776290.03653588-aecf-4fdd-b58a-95f5b372d478(OCS.15).jpg "Criando um novo alias")
    

    > [!WARNING]
    > Certifique-se de inserir a mesma porta não padrão utilizada na etapa anterior, pois ela é a porta na qual o SQL Server fará a escuta. Se um alias configurado estiver conectado ao FQDN ou à Instância incorretos do SQL Server, desabilite e reabilite o protocolo de rede associado. Essa operação limpa qualquer informação de conexão em cache e permite que o cliente se conecte corretamente.



**Criar um registro de recurso de CNAME de DNS**

1.  Entre no computador que gerencia o DNS.

2.  Selecione **Iniciar** e escolha **Gerenciador de Servidores**, conforme mostra a figura a seguir.
    
    ![Abrindo o Gerenciador de Servidores](images/Dn776290.3e4bd8ad-2a65-4a05-af40-c8dd3583bc8f(OCS.15).jpg "Abrindo o Gerenciador de Servidores")

3.  Escolha o menu suspenso **Ferramentas** e selecione **DNS**, conforme mostra a figura a seguir.
    
    ![Abrindo DNS no Gerenciador de Servidores.](images/Dn776290.415e1da1-7c9a-4a4e-a896-ca34a76aaeff(OCS.15).jpg "Abrindo DNS no Gerenciador de Servidores.")

4.  No painel à esquerda, expanda o nó de nomes de servidor, o nó de Zonas de pesquisa direta e escolha o domínio relevante.

5.  Clique com o botão direito e selecione **Novo Alias (CNAME)…**, conforme mostra a figura a seguir.
    
    ![Selecionando opção para criar um novo alias CNAME](images/Dn776290.abe66cca-b53c-427a-9094-1a59dc6840ca(OCS.15).jpg "Selecionando opção para criar um novo alias CNAME")

6.  Insira o **Nome do Alias** e o **FQDN para SQL Server**, conforme mostra a figura a seguir.
    
    ![Preenchendo a caixa de diálogo de novo alias CNAME.](images/Dn776290.dd0ebd2d-3407-4459-8bd9-2b389a7bc440(OCS.15).jpg "Preenchendo a caixa de diálogo de novo alias CNAME.")

7.  Escolha **OK** para salvar o CNAME e exibi-lo no Gerenciador DNS.

## Validar a conectividade do banco de dados

Há muitas maneiras diferentes para se certificar de que esteja funcionando. Você quer ter certeza de que o banco de dados do SQL Server está fazendo a escuta na porta especificada que utiliza o alias. Uma verificação rápida pode ser concluída utilizando os comandos **netstat** e **telnet**.

> [!NOTE]  
> O Cliente Telnet é um recurso que acompanha o Windows Server, mas que deve ser instalado. Abra o Gerenciador de Servidores e selecione Adicionar Funções e Recursos no menu Gerenciar para instalar um recurso do Windows Server.

**Usar netstat e telnet para verificar a conectividade do banco de dados**

1.  Selecione **Iniciar** e digite **cmd** para abrir o prompt de comando.

2.  Digite **netstat -a -f** e confirme se o SQL Server está sendo executado com a porta correta, conforme mostra a figura a seguir.
    
    ![Usando o netstat para verificar porta.](images/Dn776290.4ff3a1b2-c5eb-4496-8be7-374c351fa027(OCS.15).jpg "Usando o netstat para verificar porta.")

3.  Digite **telnet \<alias name\> \<port \#\>** para confirmar a conexão com a instância do SQL Server. Se a conexão for bem-sucedida, telnet será conectado e não será exibido nenhum erro. Isso mostra que a instância do SQL Server está fazendo a escuta na porta correta com o alias correto. Se houver um problema ao conectar ao banco de dados do SQL Server, telnet exibirá um erro informando que não é possível fazer a conexão. Depois de verificar a conectividade do banco de dados no servidor do banco de dados, faça o mesmo no Lync Server (pela rede) e certifique-se de que não haja firewalls bloqueando o acesso.

## Conclusão

Depois de configurar o alias do SQL Server, utilize-o para criar uma topologia do Lync Server 2013 na ferramenta Construtor de Topologias. Para mais informações sobre topologias, consulte [Definindo e configurando a topologia no Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md).

## Consulte Também

#### Conceitos

[Microsoft Lync Server 2013](microsoft-lync-server-2013.md)  

#### Outros Recursos

[Planejando a segurança no Lync Server 2013](lync-server-2013-planning-for-security.md)  
[Definindo e configurando a topologia no Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md)  
[Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md)

