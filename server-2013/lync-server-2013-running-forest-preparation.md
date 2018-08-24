---
title: 'Lync Server 2013: Executando preparação de floresta'
TOCTitle: Executando preparação de floresta
ms:assetid: 9d62f7be-bcfe-421d-8d8a-225567102a35
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412732(v=OCS.15)
ms:contentKeyID: 49307617
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Executando preparação de floresta para Lync Server 2013

 

_**Tópico modificado em:** 2012-10-29_

Você pode usar o Setup ou cmdlets do Shell de Gerenciamento do Lync Server para preparar a floresta. O cmdlet que prepara a floresta é **Enable-CsAdForest**.

Depois de preparar a floresta, você deverá verificar se as configurações globais foram replicadas antes de executar a preparação do domínio.

## Para usar a Instalação para preparar a floresta

1.  Faça logon em um computador que seja parte de um domínio como membro do grupo Administradores de Empresa para o domínio raiz da floresta.

2.  A partir da pasta ou mídia de instalação do Lync Server 2013, execute o arquivo Setup.exe para iniciar o Assistente de Implantação.

3.  Clique em **Preparar o Active Directory** e espere que o estado da implantação seja determinado.

4.  Na **Etapa 3: Preparar Floresta Atual** , clique em **Executar** .

5.  Na página **Preparar Floresta** , clique em **Avançar** .
    
    > [!NOTE]  
    > A Preparação da Floresta permite que você escolha onde colocar os Grupos Universais para o Lync Server 2013. Escolha uma localização que seja consistente com os requisitos da sua organização.

6.  Na página **Executando Comandos** , procure **Status da tarefa: Concluída** e clique em **Exibir Log** .

7.  Sob a coluna **Ação** , expanda **Forest Prep** , procure o Resultado de Execução **\<Sucesso\>** ao final de cada tarefa para verificar se a preparação da floresta foi concluída com êxito, feche o log e clique em **Concluir** .

8.  Aguarde a replicação do Active Directory ser concluída ou force a replicação em todos os controladores de domínio listados no snap-in **Sites e Serviços do Active Directory** no controlador de domínio raiz da floresta, antes de executar a preparação do domínio. Force a replicação entre os controladores de domínio em todos os sites do Active Directory para que a replicação nos sites ocorra dentro de alguns minutos.

## Para usar os cmdlets para preparar a floresta

1.  Faça o login em um computador que faz parte de um domínio como membro do grupo Administradores de Domínio no domínio raiz da floresta.

2.  Instale os Componentes principais do Lync Server da seguinte maneira:
    
    1.  Na pasta ou mídia de instalação do Lync Server 2013, execute Setup.exe para iniciar o Assistente de Implantação do Lync Server.
    
    2.  Se você receber uma solicitação para instalar o Microsoft Visual C++ Redistributable, clique em **Sim** .
    
    3.  A caixa de diálogo Instalação do Lync Server 2013 solicita um local de instalação dos arquivos do Lync Server. Escolha o local padrão ou **Procure** um local de sua escolha e clique em **Instalar** .
    
    4.  Na página Contrato de Licença, marque **Aceito os termos do contrato de licença** e, em seguida, clique em **OK** . O instalador instala os Componentes principais do Lync Server 2013.

3.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

4.  Execute:
    
        Enable-CsAdForest [-GroupDomain <FQDN of the domain in which to create the universal groups>]
    
    Por exemplo:
    
        Enable-CsAdForest -GroupDomain domain1.contoso.com 
    
    Se você não especificar o parâmetro GroupDomain, o valor padrão será o domínio local. Se grupos universais tiverem sido criados anteriormente em um domínio que não seja o domínio padrão, será necessário especificar explicitamente o parâmetro GroupDomain.

5.  Aguarde a replicação do Active Directory ser concluída ou force a replicação em todos os controladores de domínio listados no snap-in **Sites e Serviços do Active Directory** no controlador de domínio raiz da floresta, antes de executar a preparação do domínio.

6.  Verificar se a preparação da floresta teve êxito. Execute:
    
        Get-CsAdForest 
    
    Esse cmdlet retorna um valor de **LC\_FORESTSETTINGS\_STATE\_READY** se a preparação da floresta tiver sido bem-sucedida.

## Consulte Também

#### Tarefas

[Usando cmdlets para reverter preparação da floresta no Lync Server 2013](lync-server-2013-using-cmdlets-to-reverse-forest-preparation.md)  

#### Outros Recursos

[Preparando a floresta para Lync Server 2013](lync-server-2013-preparing-the-forest.md)

