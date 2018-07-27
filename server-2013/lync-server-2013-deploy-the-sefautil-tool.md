---
title: Implantar a ferramenta SEFAUtil
TOCTitle: Implantar a ferramenta SEFAUtil
ms:assetid: fb556e50-88dd-4404-a3d5-be36f5ba41e6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945659(v=OCS.15)
ms:contentKeyID: 52057775
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantar a ferramenta SEFAUtil

 

_**Tópico modificado em:** 2016-12-08_

Para implantar e gerenciar o recebimento de chamadas em grupo, você deve usar a ferramenta do kit de recursos SEFAUtil. A ferramenta integra as ferramentas do kit de recursos do Lync Server 2013. Antes de poder instalar a SEFAUtil, você deve ter um pool de aplicativos confiáveis em sua topologia, especificar SEFAUtil como um aplicativo confiável e habilitar a topologia.

> [!IMPORTANT]  
> O Microsoft UCMA (Unified Communications Managed API) 3.0 Core SDK deve estar instalado em qualquer computador no qual você planeja executar a ferramenta SEFAUtil.

Você pode executar a SEFAUtil em qualquer Pool de Front-Ends de sua implantação.

> [!NOTE]  
> Para obter mais detalhes sobre a execução da SEFAUtil, consulte o artigo do blog da TechNet, &quot;How to get SEFAUtil running?&quot; em <a href="http://go.microsoft.com/fwlink/?linkid=278940" class="uri">http://go.microsoft.com/fwlink/?linkid=278940</a>.

## Para implantar a SEFAUtil

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  A ferramenta SEFAUtil só pode ser executada em um computador que integra um pool de aplicativos confiáveis. Se necessário, defina um pool de aplicativos confiáveis para o Pool de Front-Ends no qual você deseja executar a SEFAUtil. Na linha de comando, execute:
    
        New-CsTrustedApplicationPool -id <Pool FQDN> -Registrar <Pool Registrar FQDN> -site Site:<Pool Site>

4.  Defina a ferramenta SEFAUtil como um aplicativo confiável. Na linha de comando, execute:
    
        New-CsTrustedApplication -ApplicationId sefautil -TrustedApplicationPoolFqdn <Pool FQDN>  -Port 7489
    
    > [!NOTE]  
    > Se necessário, você pode usar uma porta diferente.

5.  Habilite a topologia com suas alterações. Na linha de comando, digite:
    
        Enable-CsTopology

6.  Instale as ferramentas do kit de recursos do Lync Server 2013 em uma Servidor Front-End que esteja no pool de aplicativos confiáveis criado na etapa 3.

7.  Verifique se a ferramenta SEFAUtil está sendo executada corretamente conforme segue:
    
    1.  Execute a ferramenta no prompt de comando do Windows com privilégios de administrador para exibir as configurações de encaminhamento de chamada de um usuário de sua implantação.
        
        > [!NOTE]  
        > A ferramenta está localizada em \Arquivos de Programas\Microsoft Lync Server 2013\Reskit.    
    2.  Exiba as configurações de encaminhamento de chamada de um usuário, Na linha de comando, execute:
        
            SEFAUtil.exe <user SIP address> /server:<Lync Server/Pool FQDN>
        
        As configurações de encaminhamento de chamada do usuário serão exibidas.

