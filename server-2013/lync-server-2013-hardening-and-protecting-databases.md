---
title: 'Lync Server 2013: Protegendo os bancos de dados'
TOCTitle: Protegendo os bancos de dados do Lync Server 2013
ms:assetid: 6953e721-3511-4235-b848-51bab093dc89
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn518330(v=OCS.15)
ms:contentKeyID: 60505936
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Protegendo os bancos de dados do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Lync Server 2013 também depende de bancos de dados do SQL Server para armazenar informações do usuário, o estado da conferência, os dados de arquivamento e os registros de detalhes da chamada (CDRs). Você pode maximizar a disponibilidade dos dados do Lync Server 2013 nos bancos de dados back-end do Lync Server, particionando os dados do aplicativo de modo que melhore a tolerância a falhas e simplifique a solução de problemas. Para atingir essas metas, particione os dados do aplicativo:

  - **Usando práticas recomendadas de particionamento do servidor**   Separe o sistema operacional, o aplicativo e os arquivos de programa dos arquivos de dados.

  - **Armazenando arquivos de log de transação e arquivos de banco de dados**   Armazene esses arquivos separadamente para aumentar a tolerância a falhas e otimizar a recuperação, e armazene-os em um disco ou volume criptografado.

  - **Usando a clusterização de servidor**   Clusterize os servidores back-end para otimizar a disponibilidade do sistema do Lync Server 2013.

  - **Verifique se todos os backups de dados estão criptografados e corretamente tratados**    Mídias de backup perdidas, descartadas ou colocadas incorretamente podem significar uma grande ameaça para a segurança dos dados nas implantações do Lync Server 2013

Em qualquer servidor Lync Server 2013, exceto no servidor Standard Edition, a instância do SQL Server Express (instância RTCLOCAL) não pode ser acessada remotamente, e nenhuma exceção de firewall local é criada, exceto para o SQL Server Express em um servidor Standard Edition. Em um servidor Standard Edition, o banco de dados back-end e o Repositório de Gerenciamento Central (CMS) são configurados para serem remotamente acessíveis. Para aumentar a segurança dos bancos de dados do SQL Server, faça o seguinte:

  - Personalize o firewall do SQL Server Express nos servidores Standard Edition, limitando o escopo dos servidores que podem acessar remotamente o banco de dados. Por padrão, qualquer endereço IP pode acessar remotamente o banco de dados.

  - Use o SQL Server Configuration Manager para especificar o protocolos, os endereços IP e as portas para acesso remoto do SQL Server:
    
      - O Lync Server 2013 usa o protocolo TCP/IP. Ele oferece suporte a IP versão 4 (IPv4), mas não a IP versão 6 (IPv6).
        
        > [!NOTE]  
        > O Lync Server 2013 pode funcionar em uma rede com pilha IP dupla habilitada.    
      - O Lync Server 2013 oferece suporte a vários endereços IP (cartões de endereço de rede com diversas bases). Você pode especificar que o SQL Server realize a escuta apenas de endereços IP específicos (endereço individual ou por sub-rede) e use apenas protocolos específicos.
    
      - O Lync Server 2013 oferece suporte a portas estáticas e dinâmicas do SQL Server.

  - Execute o SQL Server em uma porta estática (não-padrão) e não execute o SQL Server Browser (assim ele não poderá relatar a porta de listening ao cliente). Isso requer uma configuração personalizada em cada cliente do SQL Server, incluindo servidores front-end, Monitoring Server, servidor de arquivamento, consoles administrativos (que estejam executando o Shell de Gerenciamento do Lync Server, Painel de Controle do Lync Server ou Construtor de Topologias) e todos os outros servidores que executam bancos de dados do Lync Server).

> [!NOTE]  
> O acesso a bancos de dados deve ser limitado a administradores de banco de dados confiáveis. Um administrador de banco de dados mal-intencionado pode inserir ou modificar dados nos bancos de dados para obter privilégios sobre os servidores do Lync Server 2013 ou obter informações confidenciais dos serviços, mesmo se o administrador do banco de dados não tiver recebido acesso direto ou controle dos servidores do Lync Server 2013.

Para obter informações detalhadas sobre configurações personalizadas e aumento da segurança dos bancos de dados do SQL Server, consulte o artigo "Usando o Lync Server 2010 com uma configuração de rede personalizada do SQL Server" (em inglês) do blog NextHop em [http://go.microsoft.com/fwlink/p/?LinkId=214008](http://go.microsoft.com/fwlink/p/?linkid=214008).

> [!NOTE]  
> Você também pode aumentar a segurança dos sistemas operacionais e servidores de aplicativo, e usar a Política de Grupo para implementar bloqueios de segurança na implantação do Lync Server. Para obter detalhes, consulte <a href="lync-server-2013-hardening-and-protecting-servers-and-applications.md">Protegendo servidores e aplicativos para Lync Server 2013</a>.
