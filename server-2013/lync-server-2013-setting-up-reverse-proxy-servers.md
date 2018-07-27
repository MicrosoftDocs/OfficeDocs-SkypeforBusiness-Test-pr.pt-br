---
title: 'Lync Server 2013: Configurando servidores de proxy reverso'
TOCTitle: Configurando servidores de proxy reverso
ms:assetid: 00bc138a-243f-4389-bfa5-9c62fcc95132
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398069(v=OCS.15)
ms:contentKeyID: 49305667
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando servidores de proxy reverso para o Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Em implantações do Servidor de Borda do Microsoft Lync Server 2013, é necessário ter um proxy reverso HTTPS na rede de perímetro para que os clientes externos possam acessar os Serviços Web do Lync Server 2013 (chamados de *Web Components* no Office Communications Server) no Diretor e o pool base do usuário. Veja abaixo alguns dos recursos que exigem acesso externo por meio de proxy reverso:

  - Permitir que usuários externos baixem o conteúdo de reunião para suas reuniões.

  - Permitir que usuários externos expandam grupos de distribuição.

  - Permitir que usuários remotos baixem arquivos do serviço de Catálogo de Endereços.

  - Acessar o cliente Lync Web App.

  - Acessar a página da web de Configurações de Conferência Discada.

  - Permitir que dispositivos externos se conectem ao serviço web de Atualização de Dispositivo e obtenham atualizações.

  - Permitir que aplicativos móveis descubram e usem URLs móveis (Mcx) automaticamente da Internet.

  - Permitir que o cliente Lync 2013, o Aplicativo Lync Windows Store e o cliente Lync 2013 Mobile localize as URLs do Lync Discover (descoberta automática) e use a API da Web das Comunicações Unificadas API (UCWA).

Recomendamos que configure seu proxy reverso HTTP para publicar todos os Serviços Web em todos os pools. Publicar https:// *ExternalFQDN* /\* publica todos os diretórios virtuais IIS de um pool. Você precisa de uma regra de publicação para cada servidor Standard Edition, Pool de Front-Ends, Diretor ou Pool de diretores em sua organização.

Além disso, você precisa publicar as URLs simples. Caso a organização possua um Diretor ou Pool de diretores, o proxy reverso HTTP escuta por solicitações HTTP/HTTPS às URLs simples e as encaminha via proxy ao diretório virtual de Serviços Web externos Diretor ou Pool de diretores. Caso você não tenha implantado um Diretor, você precisará designar um pool para manipular as solicitações às URLs simples. (Caso este não seja o pool inicial do usuário, ele irá redirecioná-los para o Serviços Web no pool inicial do usuário). As URLs simples podem ser manipuladas por uma regra de publicação de web dedicada ou você pode adicioná-la aos nomes públicos da regra de publicação de web para o Diretor. Pode ser necessário também publicar a URL externa do Serviço Autodescoberta.

Você pode usar o Microsoft Forefront Threat Management Gateway 2010, o Microsoft Internet Security and Acceleration (ISA) Server 2006 SP1 ou o Internet Information Server 7.0, 7.5 ou 8.0 com o Application Request Routing (IIS ARR) como um proxy reverso. As etapas detalhadas nesta seção descrevem como configurar o Forefront Threat Management Gateway (TMG) 2010 e as etapas para configurar o ISA Server 2006 são quase idênticas. Há orientações também para o IIS ARR. Se você estiver usando outro proxy reverso, consulte a documentação do produto e mapeie os requisitos definidos aqui para os recursos associados em outros proxies reversos.

> [!IMPORTANT]  
> O Internet Information Server Application Request Routing (IIS ARR) é uma opção totalmente testada e compatível para a implementação de um proxy reverso para o Lync Server 2010 e o Lync Server 2013. Em novembro de 2012, a Microsoft encerrou a venda de licenças do ForeFront Threat Management Gateway 2010 (TMG). O TMG ainda conta com suporte completo e está disponível para venda em dispositivos vendidos por terceiros. Além disso, muitos balanceadores de carga de hardware e firewalls de terceiros oferecem suporte a proxy reverso. Para saber quais balanceadores de carga de hardware e firewalls oferecem recursos de proxy reverso, consulte seu fornecedor para obter instruções específicas sobre como configurar seus produtos para ter suporte ao proxy reverso para o Lync Server. Você também pode ver outros fabricantes que enviaram documentações de seus produtos à Microsoft. A responsabilidade pelo suporte é do fabricante de cada solução. Para ver outros fabricantes que são ativos no fornecimento de soluções, consulte <a href="http://go.microsoft.com/fwlink/?linkid=268730">Infra-estruturar qualificada para o Microsoft Lync</a>268730

Os tópicos e procedimentos a seguir usam o Forefront Threat Management Gateway 2010 e o IIS ARR como base para os procedimentos de implantação e configuração.

  - [Configurar FQDNs da web farm para Lync Server 2013](lync-server-2013-configure-web-farm-fqdns.md)

  - [Configurar adaptadores de rede no Lync Server 2013](lync-server-2013-configure-network-adapters.md)

  - [Solicitar e configurar um certificado para seu proxy HTTP reverso no Lync Server 2013](lync-server-2013-request-and-configure-a-certificate-for-your-reverse-http-proxy.md)

  - [Configurar regras de publicação na Web para um único pool interno no Lync Server 2013](lync-server-2013-configure-web-publishing-rules-for-a-single-internal-pool.md)

  - [Verificar ou configurar autenticação e certificação nos diretórios virtuais de IIS no Lync Server 2013](lync-server-2013-verify-or-configure-authentication-and-certification-on-iis-virtual-directories.md)

  - [Criar registros de DNS para servidores de proxy reverso no Lync Server 2013](lync-server-2013-create-dns-records-for-reverse-proxy-servers.md)

  - [Verificar acesso por meio de seu proxy reverso no Lync Server 2013](lync-server-2013-verify-access-through-your-reverse-proxy.md)

## Antes de começar

Para implantar com êxito o Forefront Threat Management Gateway 2010 como seu proxy reverso, é necessário configurar um servidor, usando os pré-requisitos e requisitos de hardware definidos na documentação do Forefront Threat Management Gateway 2010. Consulte os tópicos a seguir para configurar apropriadamente o hardware e instalar o Forefront Threat Management Gateway 2010 no servidor antes de continuar.

   [Forefront Threat Management Gateway (TMG) 2010](http://go.microsoft.com/fwlink/?linkid=291292)

   [Recomendações de hardware do Forefront TMG 2010](http://go.microsoft.com/fwlink/?linkid=291293)

Para implementar com sucesso o IIS ARR como seu proxy reverso, leia os tópicos a seguir para configurar o hardware e o software necessário.

   Para instalar o IIS no Windows Server 2008 ou no Windows Server 2008 R2, consulte [Instalação do IIS 7 no Windows Server 2008 ou no Windows Server 2008 R2](http://go.microsoft.com/fwlink/?linkid=291296)

   Para instalar o IIS no Windows Server 2012, consulte [Instalação do IIS 8 no Windows Server 2012](http://go.microsoft.com/fwlink/?linkid=291297)

   Para instalar o IIS em Windows Server 2012 R2, consulte [Instalação do IIS 8.5 no Windows Server 2012 R2](http://go.microsoft.com/fwlink/?linkid=330687)

   Para baixar a extensão do Application Request Routing para o IIS, siga as instruções em [Baixar o Application Request Routing v2.5](http://go.microsoft.com/fwlink/?linkid=291298)

   Para instalar o ARR, siga as instruções em [Instalar o Application Request Routing Version 2](http://go.microsoft.com/fwlink/?linkid=291299)
    
    > [!NOTE]  
    > As instruções publicadas atualmente aplicam-se ao ARR 2.0. Para instalar a extensão, não há diferença entre as duas versões.
