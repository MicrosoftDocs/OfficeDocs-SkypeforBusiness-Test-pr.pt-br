---
title: 'Lync Server 2013: Executando preparação de domínio'
TOCTitle: Executando preparação de domínio
ms:assetid: 95dab800-1f2c-4506-b36c-99986643b149
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398761(v=OCS.15)
ms:contentKeyID: 49307515
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Executando preparação de domínio para Lync Server 2013

 

_**Tópico modificado em:** 2013-04-16_

Você pode usar o Setup ou cmdlets do Shell de Gerenciamento do Lync Server para preparar domínios. O cmdlet que prepara um domínio é **Enable-CsAdDomain**.

A preparação do domínio é a etapa final da preparação do Serviços de Domínio Active Directory para o Lync Server 2013.

## Para usar a Instalação para preparar domínios

1.  Faça logon em qualquer servidor no domínio como membro do grupo Admins. do domínio.

2.  Na pasta ou mídia de instalação do Lync Server 2013, execute Setup.exe para iniciar o Assistente de Implantação do Lync Server.

3.  Clique em **Preparar o Active Directory** e espere que o estado da implantação seja determinado.

4.  Na **Etapa 5: Preparar o Domínio Atual** , clique em **Executar** .

5.  Na página **Preparar Domínio** , clique em **Avançar** .

6.  Na página **Executando Comandos** , procure **Status da tarefa: Concluída** e clique em **Exibir Log** .

7.  Sob a coluna **Ação** , expanda **Domain Prep** , procure o Resultado de Execução **\<Sucesso\>** ao final de cada tarefa para verificar se a preparação do domínio foi concluída com sucesso, feche o log e clique em **Concluir** .

8.  Aguarde a conclusão da replicação do Active Directory ou force a replicação para todos os controladores de domínio listados no snap-in Sites e Serviços do Active Directory para o controlador de domínio raiz da floresta.

## Para usar cmdlets para preparar o domínio

1.  Faça logon em qualquer servidor no domínio como membro do grupo Admins. do domínio.

2.  Instale os Componentes principais do Lync Server da seguinte maneira:
    
    1.  Na pasta ou mídia de instalação do Lync Server 2013, execute Setup.exe para iniciar o Assistente de Implantação do Lync Server.
    
    2.  Se você receber uma solicitação para instalar o Microsoft Visual C++ Redistributable, clique em **Sim** .
    
    3.  A caixa de diálogo Instalação do Lync Server 2013 solicita um local de instalação dos arquivos do Lync Server. Escolha o local padrão ou **Procure** um local de sua escolha e clique em **Instalar** .
    
    4.  Na página Contrato de Licença, marque **Aceito os termos do contrato de licença** e, em seguida, clique em **OK** . O instalador instala os Componentes principais do Lync Server 2013.

3.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

4.  Execute:
    
        Enable-CsAdDomain [-Domain <DomainFQDN>] 
    
    Por exemplo:
    
        Enable-CsAdDomain -Domain domain1.contoso.net 
    
    Se você não especificar o parâmetro de Domínio, o padrão é o domínio local.

5.  Verificar se a preparação de domínio teve êxito. Execute:
    
        Get-CsAdDomain [-Domain <Domain FQDN>] [-DomainController <Domain controller FQDN>] [-GlobalCatalog <Global catalog server FQDN>] [-GlobalSettingsDomainController <Domain controller FQDN where global settings are stored>] 
    
    Por exemplo:
    
        Get-CsAdDomain -Domain domain1.contoso.net -GlobalSettingsDomainController dc01.domain1.contoso.com
    
    > [!NOTE]  
    > O parâmetro GlobalSettingsDomainController permite indicar onde as configurações globais estão armazenadas. Se estiverem armazenadas no contêiner Sistema (o que é comum, quando as importações de atualização não tiveram a configuração global migrada para o contêiner Configuração), você definirá um controlador de domínio na raiz da sua floresta do Active Directory. Se as configurações globais estiverem no contêiner Configuração (o que é comum nas novas implantações ou nas atualizadas, onde as configurações foram migradas para o contêiner Configuração), você definirá qualquer controlador de domínio na floresta. Se você não especificar esse parâmetro, o cmdlet supõe que todas as configurações estão armazenadas no contêiner Configuração e se refere a qualquer controlador de domínio no AD DS.    
    Se você não especificar o parâmetro **Domain**, o padrão será o domínio local.
    
    Esse cmdlet retorna um valor **LC\_DOMAINSETTINGS\_STATE\_READY** se a preparação de domínio teve êxito.

## Consulte Também

#### Tarefas

[Usando cmdlets para reverter a preparação do domínio para o Lync Server 2013](lync-server-2013-using-cmdlets-to-reverse-domain-preparation.md)  

#### Outros Recursos

[Preparando domínios para Server 2013](lync-server-2013-preparing-domains.md)

