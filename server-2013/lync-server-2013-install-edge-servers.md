---
title: 'Lync Server 2013: Instalar Servidores de Borda'
TOCTitle: Instalar Servidores de Borda
ms:assetid: 1655ab69-3899-4ee4-a1cc-8243bc1bfa0f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398230(v=OCS.15)
ms:contentKeyID: 49305993
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalar Servidores de Borda para Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Instale o Lync Server 2013 em Servidores de Borda usando o Assistente de Implantação do Lync Server. Executando o Assistente de Implantação em cada Servidor de Borda, é possível concluir a maioria das tarefas necessárias para configurar o Servidor de Borda. Para implantar o Lync Server 2013 em um Servidor de Borda, você já deve ter executado o Construtor de Topologias para definir e publicar a topologia do Servidor de Borda e tê-la exportado para a mídia que está disponível pelo Servidor de Borda. Para obter detalhes, consulte [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md) e [Exportar sua topologia do Lync Server 2013 e copiá-la na mídia externa para instalação de borda](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md).

Depois de usar o Assistente de Implantação para instalar cada Servidor de Borda, instalar e designar os certificados requisitados e iniciar os serviços necessários, é possível completar a instalação usando as informações de [Configurando suporte para acesso de usuário externo no Lync Server 2013](lync-server-2013-configuring-support-for-external-user-access.md) para habilitar e configurar o acesso de usuários externo e usando as informações de [Verificando a implantação de borda no Lync Server 2013](lync-server-2013-verifying-your-edge-deployment.md) para validar a instalação, incluindo a conectividade de servidor e cliente.

## Para instalar um Servidor de Borda

1.  Faça logon no computador no qual deseja instalar seu Servidor de Borda como um membro do grupo de Administradores locais ou como uma conta com direitos e permissões de usuário equivalentes.

2.  Certifique-se de que o arquivo de configuração da topologia que você criou usando o Construtor de Topologias e que depois exportou e copiou a uma mídia externa está disponível no Servidor de Borda (por exemplo acesse a unidade USB onde você copiou o arquivo de configuração de topologia, ou verifique o acesso ao compartilhamento de rede onde você copiou o arquivo).

3.  Iniciar o assistente de implantação.
    
    > [!NOTE]  
    > Se você receber uma mensagem dizendo que você precisa instalar o Microsoft Visual C++ Redistribuível, clique em <strong>Sim</strong> . Na próxima caixa de diálogo, você pode aceitar o padrão <strong>Local de instalação</strong> ou clique em <strong>Pesquisar</strong> para selecionar um local e alterá-lo, depois clique em <strong>Instalar</strong> . Na próxima caixa de diálogo, marque a caixa de seleção <strong>Aceito os termos do contrato de licença</strong> e clique em <strong>OK</strong> .

4.  No Assistente de Implantação, clique em **Instalar ou Atualizar o Sistema do Lync Server** .

5.  Depois que o assistente determinar o estado da implantação, em **Etapa 1. Instalar repositório de configuração local** , clique em **Executar** e, depois, faça o seguinte:
    
      - Na caixa de diálogo **Configurar réplica local do repositório de gerenciamento central** , clique em **Importar de um arquivo (Recomendado para os Servidores de Borda)** , vá para o local do arquivo de configuração da topologia, selecione o arquivo .zip, clique em **Abrir** e depois em **Avançar** .
    
      - O Assistente de Implantação lê as informações de configuração do arquivo de configuração e grava o arquivo de configuração XML no computador local.
    
      - Depois que o processo de **Execução de Comandos** for concluído, clique em **Concluir** .

6.  No Assistente de Implantação, clique em **Etapa 2: Instalar ou remover componentes do Lync Server** para instalar os componentes de borda do Lync Server 2013 específicos do arquivo de configuração XML que está armazenado no computador local.

7.  Depois de completar a instalação, use as informações em [Configurar certificados de Borda para Lync Server 2013](lync-server-2013-set-up-edge-certificates.md) para instalar e designar os certificados necessários antes de iniciar os serviços.

