---
title: 'Lync Server 2013: Suporte adicional e requisitos de servidor'
TOCTitle: Suporte adicional e requisitos de servidor
ms:assetid: 7622986b-abd6-4f45-8b5b-d5e2368521e8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398577(v=OCS.15)
ms:contentKeyID: 49307144
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte adicional e requisitos de servidor no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Além do suporte ao software descrito em outras seções desta documentação sobre ajuste de suporte, o Lync Server 2013 tem as seguintes limitações de suporte:

  - O Lync Server 2013 oferece suporte ao DNS (Sistema de Nomes de Domínio) e ao balanceamento de carga de hardware para funções de servidor específicas. Ele também suporta o balanceamento de carga de aplicativo para Servidores de Mediação, onde for aplicável. Para obter detalhes sobre quando usar cada um, consulte a documentação de Planejamento.

  - O Lync Server 2013 usa o protocolo DLX (Expansão de Lista de Distribuição) para expandir as listas de distribuição. Esse protocolo também especifica o método de serviço Web que é usado para obter a participação de uma lista de distribuição. O Microsoft Exchange Server oferece suporte a grupos dinâmicos que não têm membros atribuídos estaticamente. Em vez disso, eles armazenam consultas que são avaliadas quando o grupo é expandido. O DLX não oferece suporte a listas de distribuição dinâmicas.

  - O Assistente para Habilitar Usuário não oferece suporte à conversão automática de caracteres do inglês para um URI compatível com SIP; portanto, você deve modificar manualmente o endereço SIP.

  - Para os servidores que executam software antivírus, consulte [Exclusões de verificação de antivírus para Lync Server 2013](lync-server-2013-antivirus-scanning-exclusions.md) para ver informações sobre exclusões de vírus sugeridas e outras recomendações relacionadas à segurança.

  - Se você usa o IPsec, recomendamos desativar o IPsec nos intervalos de porta usados para o tráfego de áudio e vídeo. Para obter detalhes, consulte [Exceções Ipsec no Lync Server 2013](lync-server-2013-ipsec-exceptions.md) na documentação de Planejamento.

  - Se a sua organização usa uma infraestrutura de QoS (Qualidade de Serviço), o subsistema de mídia é projetado para funcionar com essa infraestrutura existente. Para obter detalhes sobre a implementação de QoS, consulte [Gerenciando a QoS (Qualidade de Serviço) no Lync Server 2013](lync-server-2013-managing-quality-of-service-qos.md) na documentação de Operações.

  - O uso do firewall do sistema operacional é suportado. O Lync Server 2013 gerencia as exceções do firewall para o firewall do sistema operacional, exceto para o software de banco de dados do Microsoft SQL Server. Para obter detalhes sobre os requisitos de firewall SQL Server, consulte a documentação do SQL Server.

  - As interfaces externas usadas para implementar o suporte ao acesso de usuário externo devem estar em uma sub-rede separada, *não* na mesma rede que as interfaces internas.

  - O recurso XMPP do Lync Server 2013 é testado pela Microsoft e ela oferece suporte para federação de mensagens instantâneas com o Google Talk. Para quaisquer outros sistemas XMPP, entre em contato com o fornecedor do mesmo para verificar se eles suportam federação com o Lync Server 2013, e para quaisquer recomendações de implantação ou solução de problemas.

  - Com o lançamento das Atualizações Cumulativas do Lync Server 2013: julho de 2013, o Lync Server 2013 agora dá suporte à autenticação de dois fatores. Para obter mais informações, consulte [Planejamento e implantação da autenticação de dois fatores no Lync Server 2013](lync-server-2013-planning-for-and-deploying-two-factor-authentication.md).

  - A maioria dos servidores internos requer um tipo de certificado definido como **Autenticação Aberta** (OAuth). Você é obrigado a solicitar e atribuir um certificado OAuth durante a fase de **solicitação, instalação e atribuição de certificados** do Assistente de Implantação do Lync Server. O tamanho mínimo da chave de um certificado OAuth é 1024 bits. Um aviso poderá ser exibido se você solicitar um certificado com uma chave menor que 2048 bits. Para evitar possíveis problemas caso uma chave de 2048 bits seja imposta (em vez de ser emitido o aviso), recomenda-se enfaticamente o uso de uma chave com tamanho de 2048 bits para certificados OAuth.

  - O Service Pack 1 (SP1) Lync Server 2013 e o Microsoft Exchange Server 2010 operam com suporte para os algoritmos 140-2 do padrão FIPS se os sistemas operacionais Windows Server 2008 R2 estão configurados para usar os algoritmos do FIPS 140-2 na criptografia do sistema. Para implementar o suporte ao FIPS, é necessário configurar cada servidor que execute o Lync Server 2013 para suportá-lo. Para obter detalhes sobre os algoritmos compatíveis com FIPS e sobre como implementar o suporte ao FIPS, consulte o artigo 811833 da Base de Dados de Conhecimento da Microsoft, “Criptografia de sistema: usar algoritmos compatíveis com FIPS para criptografia, hash e assinatura" no Windows XP e em versões posteriores do Windows,” em <http://support.microsoft.com/kb/811833>. Para obter detalhes sobre o suporte ao FIPS 140-2 e suas limitações no Exchange 2010, consulte “Exchange 2010 SP1 e suporte aos algoritmos compatíveis com FIPS” em <http://go.microsoft.com/fwlink/?linkid=205335>.

O Lync Server 2013 requer a instalação de outro software de componentes específicos antes ou durante a implantação. Isso inclui o software que está disponível com o sistema operacional (o software para download) e ele é instalado automaticamente durante a instalação do Lync Server 2013. A seguinte lista cita os softwares adicionais que podem ser necessários:

  - Windows Update

  - Windows Identity Foundation

  - Microsoft .NET 4.5 Framework

  - Microsoft Visual C++ 2012 Redistributable
    
    > [!NOTE]  
    > O Microsoft Visual C++ 2012 Redistributable é automaticamente instalado quando você instala o Lync Server 2013. Você não deve instalar nem usar outras versões.

  - URL Rewrite Module versão 2.0 Redistributable

  - Tempo de Execução do Windows Media Format

  - Windows PowerShell versão 3.0

  - Plug-in do navegador Microsoft Silverlight 4 (Silverlight 4.0.50524.0 ou a versão mais recente do Painel de Controle do Lync Server)

  - Ferramentas do Serviços de Domínio Active Directory

Alguns desses requisitos de software se aplicam somente a funções específicas de servidor ou componentes. Para obter detalhes sobre esses requisitos de software, consulte [Requisitos adicionais de software para Lync Server 2013](lync-server-2013-additional-software-requirements.md) na documentação de Planejamento.

