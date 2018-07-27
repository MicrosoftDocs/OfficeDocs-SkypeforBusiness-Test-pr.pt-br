---
title: Restaurando um servidor do Standard Edition
TOCTitle: Restaurando um servidor do Standard Edition
ms:assetid: d1845663-3138-4fd6-b3e7-337e294d40d8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202190(v=OCS.15)
ms:contentKeyID: 52057727
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurando um servidor do Standard Edition

 

_**Tópico modificado em:** 2013-02-21_

Se um servidor Standard Edition que não hospeda o Repositório de Gerenciamento Central falhar, siga os procedimentos nesta seção. Se o Repositório de Gerenciamento Central falhar, consulte [Restaurar o servidor que hospeda o Repositório de Gerenciamento Central](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md).


> [!TIP]
> Recomendamos que você faça uma cópia da imagem do sistema antes de iniciar a restauração. Você poderá usar essa imagem como um ponto de reversão caso ocorra algo errado durante a restauração. Convém usar a cópia da imagem depois de instalar o sistema operacional e o SQL Server e restaurar ou registrar novamente os certificados.



## Para restaurar um servidor Standard Edition

1.  Comece com um servidor novo ou limpo que tenha o mesmo FQDN (nome de domínio totalmente qualificado) que o computador que falhou, instale o sistema operacional e restaure os certificados ou registre-os novamente.
    
    > [!NOTE]  
    > Siga os procedimentos de implantação de servidor de sua organização para executar essa etapa.

2.  Em uma conta de usuário membro do grupo RTCUniversalServerAdmins e do grupo Administradores Locais, faça logon no servidor que você está restaurando.

3.  Restaure o Repositório de Arquivos copiando o Repositório de Arquivos apropriado de $Backup para o local de Repositório de Arquivos no servidor e compartilhe a pasta.
    
    > [!IMPORTANT]  
    > O caminho e o nome de arquivo para o Repositório de Arquivos restaurado devem ser exatamente iguais ao Repositório de Arquivos armazenado em backup para que os componentes que usam os arquivos possam acessá-los.

4.  Execute Construtor de Topologias:
    
    1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.
    
    2.  Clique em **Baixar Topologia da implantação existente** e clique em **OK**.
    
    3.  Selecione a topologia e clique em **Salvar**. Clique em **Sim** para confirmar sua seleção.

5.  Vá até a pasta ou mídia de instalação do Lync Server, em seguida inicie o Assistente de Implantação do Lync Server localizado em \\setup\\amd64\\Setup.exe. Use o Assistente de Implantação do Lync Server para fazer o seguinte:
    
    1.  Execute **Etapa 1: Instalar Repositório de Configuração Local** para instalar os arquivos de configuração locais.
    
    2.  Execute **Etapa 2: Instalar ou Remover Componentes do Lync** para instalar as funções de servidor do Lync Server.
    
    3.  Execute **Etapa 3: Solicitar, Instalar ou Ceder Certificados** para atribuir os certificados.
    
    4.  Execute **Etapa 4: Iniciar os Serviços** para iniciar os serviços no servidor.
    
    Para obter detalhes sobre como executar o Assistente de Implantação, consulte a documentação Implantação para a função de servidor que você está restaurando.

6.  Restaure os dados do usuário executando o seguinte:
    
    1.  Copie ExportedUserData.zip de $Backup\\ para um diretório local.
    
    2.  Antes de você restaurar os dados do usuário, você precisa parar os serviços Lync. Para fazer isso, digite:
        
            Stop-CsWindowsService
    
    3.  Para restaurar os dados do usuário, na linha de comando, digite:
        
            Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
        
        Por exemplo:
        
            Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
    
    4.  Reinicie os serviços Lync digitando:
        
            Start-CsWindowsService

7.  Se você implantou o Grupo de Resposta neste Servidor Standard Edition, restaure os dados de configuração do Grupo de Resposta. Para obter informações detalhadas, consulte [Restaurando as configurações do grupo de resposta](lync-server-2013-restoring-response-group-settings.md).

8.  Se você implantou Chat Persistente nesse servidor Standard Edition, restaure o banco de dados de Chat Persistente (mgc.mdf).
    
    Se você utilizou SQL Server Backup para realizar backup do banco de dados de Chat Persistente, use os procedimentos de restauração do SQL Server para restaurá-lo.
    
    Se você utilizou o cmdlet Export-CsPersistentChatData cmdlet para fazer o backup, use Import-CsPersistentChatData para restaurá-lo.

