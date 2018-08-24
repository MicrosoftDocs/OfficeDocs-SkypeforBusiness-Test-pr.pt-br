---
title: 'Lync Server 2013: Executando preparação de esquema'
TOCTitle: Executando preparação de esquema
ms:assetid: 9d02bdb1-ff29-417a-bcce-b068b31207d8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412729(v=OCS.15)
ms:contentKeyID: 49307598
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Executando preparação de esquema de Active Directory no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Você pode usar o Setup ou cmdlets do Shell de Gerenciamento do Lync Server para preparar o esquema do Active Directory. O cmdlet que estende o esquema do Active Directory é **Install-CsAdServerSchema**.

> [!NOTE]  
> O cmdlet de preparação de esquema (<strong>Install-CsAdServerSchema</strong>) deve acessar o mestre de esquema, que requer que o serviço do registro remoto esteja em execução e que a chave do registro remoto esteja habilitada. Se o serviço do registro remoto não puder ser habilitado no mestre de esquema, você poderá executar o cmdlet localmente no mestre de esquema. Para obter detalhes sobre o acesso remoto ao registro, consulte o artigo 314837 da Base de Dados de Conhecimento da Microsoft, &quot;Como gerenciar o Acesso Remoto ao Registro&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=125769">http://go.microsoft.com/fwlink/p/?linkId=125769</a>.

Após a conclusão da preparação do esquema, verifique manualmente se a partição do esquema foi replicada antes de prosseguir para a preparação da floresta. Para obter detalhes, consulte [Verificando a replicação de esquema do Active Directory no Lync Server 2013](lync-server-2013-verifying-schema-replication.md).

## Para usar a Instalação para preparar o esquema da floresta atual

1.  Faça logon em um servidor em sua floresta como membro do grupo Administradores de Esquema e com direitos de administrador no mestre de esquema.

2.  A partir da pasta ou mídia de instalação do Lync Server 2013, execute o arquivo Setup.exe para iniciar o Assistente de Implantação.

3.  Se você receber uma solicitação para instalar o Microsoft Visual C++ Redistributable, clique em **Sim**.

4.  A caixa de diálogo Instalação do Lync Server 2013 solicita um local de instalação dos arquivos do Lync Server. Escolha o local padrão ou **Procure** um local de sua escolha e clique em **Instalar**.

5.  Na página Contrato de Licença, marque **Aceito os termos do contrato de licença** e, em seguida, clique em **OK**.

6.  O instalador instala os Componentes principais do Lync Server.

7.  Quando o Assistente de Implantação estiver pronto, clique em **Preparar Active Directory** e espere que o estado da implantação seja determinado.

8.  Na **Etapa 1: Preparar Esquema**, clique em **Executar**.

9.  Na página **Preparar Esquema**, clique em **Avançar**.

10. Na página **Executando Comandos**, procure **Status da tarefa: Concluída** e clique em **Exibir Log**.

11. Sob a coluna **Ação**, expanda **Schema Prep**, procure o Resultado de Execução **\<Sucesso\>** ao final de cada tarefa para verificar se a preparação do esquema foi concluída com êxito, feche o log e clique em **Concluir**.

12. Aguarde a replicação do Active Directory ser concluída ou force a replicação.

13. Verifique manualmente se as alterações do esquema foram replicadas para todos os outros controladores de domínio. Para obter detalhes, consulte [Verificando a replicação de esquema do Active Directory no Lync Server 2013](lync-server-2013-verifying-schema-replication.md).

## Para usar cmdlets para preparar o esquema da floresta atual

1.  Faça logon em um computador na floresta como um membro do grupo Administradores de Esquemas e com direitos de administrador no mestre de esquema.

2.  Instale os Componentes principais do Lync Server da seguinte maneira:
    
    1.  Na pasta ou mídia de instalação do Lync Server 2013, execute Setup.exe para iniciar o Assistente de Implantação do Lync Server.
    
    2.  Se você receber uma solicitação para instalar o Microsoft Visual C++ Redistributable, clique em **Sim**.
    
    3.  A caixa de diálogo Instalação do Lync Server 2013 solicita um local de instalação dos arquivos do Lync Server. Escolha o local padrão ou **Procure** um local de sua escolha e clique em **Instalar**.
    
    4.  Na página Contrato de Licença, marque **Aceito os termos do contrato de licença** e, em seguida, clique em **OK**. O instalador instala os Componentes principais do Lync Server 2013.

3.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

4.  Execute:
    
        Install-CsAdServerSchema [-Ldf <directory where the .ldf file is located>] 
    
    Se o parâmetro Ldf não for especificado, o valor padrão será o caminho de instalação do Lync Server 2013 que é lido a partir do registro.
    
    Por exemplo:
    
        Install-CsAdServerSchema -Ldf "C:\Program Files\Microsoft Lync Server 2013\Deployment\Setup"

5.  Use o cmdlet a seguir para verificar se a preparação do esquema foi executada até o final.
    
        Get-CsAdServerSchema 
    
    Este cmdlet retorna o valor **SCHEMA\_VERSION\_STATE\_CURRENT** se a preparação do esquema foi bem sucedida.

6.  Aguarde a replicação do Active Directory ser concluída ou force a replicação.

7.  Verifique manualmente se as alterações do esquema foram replicadas para todos os outros controladores de domínio. Para obter detalhes, consulte [Verificando a replicação de esquema do Active Directory no Lync Server 2013](lync-server-2013-verifying-schema-replication.md).

## Consulte Também

#### Tarefas

[Verificando a replicação de esquema do Active Directory no Lync Server 2013](lync-server-2013-verifying-schema-replication.md)  

#### Conceitos

[Preparando o esquema do Active Directory no Lync Server 2013](lync-server-2013-preparing-the-active-directory-schema.md)

