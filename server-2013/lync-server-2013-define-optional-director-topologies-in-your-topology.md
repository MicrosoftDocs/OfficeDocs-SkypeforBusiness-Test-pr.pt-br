---
title: 'Lync Server 2013: Definir topologias opcionais de Diretor em sua topologia'
TOCTitle: Definir topologias opcionais de Diretor em sua topologia
ms:assetid: 8e9a659d-23b0-401d-b296-59c7df414d49
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398717(v=OCS.15)
ms:contentKeyID: 49307417
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir topologias opcionais de Diretor em sua topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Os Diretores do Lync Server 2013 podem ser servidores de instância única ou podem ser instalados como um pool com carga balanceada de vários Diretores para disponibilidade e capacidade mais altas. O balanceamento de carga de hardware e o balanceamento de carga de DNS têm suporte. Este tópico explica como configurar o balanceamento de carga de DNS para pools de Diretores.

Para publicar, habilitar ou desabilitar uma topologia com sucesso ao adicionar ou remover uma função de servidor, você deve estar conectado como um usuário que seja membro dos grupos **RTCUniversalServerAdmins** e **Administradores de Domínio**. Você também pode delegar os direitos e permissões de administrador adequados para adicionar funções de servidor. Para detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md) na documentação do servidor Standard Edition ou do servidor Enterprise Edition. Para outras alterações de configuração, somente a inscrição no grupo **RTCUniversalServerAdmins** é necessária.

Este tópico descreve as etapas para definir e publicar a topologia de duas topologias do Diretor:

  - Para definir o Diretor (instância única)

  - Para definir o Diretor (pool de vários Diretores)

## Para definir o Diretor (instância única)

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Na página de boas-vindas, clique em **Baixar Topologia da Implantação Existente**.

3.  Na caixa de diálogo **Salvar Topologia Como**, digite o nome o local da cópia local da topologia existente e clique em **Salvar**.

4.  Expanda o site no qual você planeja adicionar o Diretor, clique com o botão direito do mouse em **Pools de Diretores** e clique em **Novo Pool de Diretores**.

5.  Na caixa de diálogo **Definir o FQDN do pool de Diretores**, faça o seguinte:
    
      - Em **FQDN do Pool**, digite o FQDN do pool de Diretores.
    
      - Clique em **Pool de computador único** e em **Avançar**.

6.  Na caixa de diálogo **Definir o compartilhamento de arquivo**, siga um destes procedimentos:
    
    1.  Para usar um compartilhamento de arquivo existente, clique em **Usar um compartilhamento de arquivos previamente definido**, selecione um compartilhamento de arquivo na lista e clique em **Avançar**.
    
    2.  Para criar um novo compartilhamento de arquivo, clique em **Definir um novo compartilhamento de arquivo**, digite o FQDN do local do compartilhamento de arquivo em **FQDN do servidor de arquivos**, digite o nome do compartilhamento em **Compartilhamento de Arquivo** e clique em **Avançar**.
    
    > [!IMPORTANT]  
    > O compartilhamento de arquivo especificado ou criado nesta etapa precisa existir ou ser criado antes da publicação da topologia.<br />    O compartilhamento de arquivo atribuído a um Diretor não é realmente usado. Dessa forma, você pode atribuir o compartilhamento de arquivo de qualquer pool na organização.

7.  Na caixa de diálogo **Especificar a URL dos Serviços Web**, em **URL Base Externa**, especifique o FQDN para os Diretores e clique em **Concluir**.
    
    > [!IMPORTANT]  
    > O nome deve ser resolvido a partir dos servidores DNS da Internet e apontar para o endereço IP público do proxy reverso, que escuta solicitações HTTP/HTTPS para aquela URL e as encaminha via proxy para o diretório virtual dos Serviços Web externos naquele Diretor.    

    > [!WARNING]
    > Se você tiver mais de um Pool de Front-Ends ou Servidor Front-End, os serviços FQDN de Web externo devem ser exclusivos. Por exemplo, se você definir os serviços FQDN de Web externo de um Servidor Front-End como <STRONG>pool01.contoso.com</STRONG>, você não pode usar <STRONG>pool01.contoso.com</STRONG> para outro Pool de Front-Ends ou Servidor Front-End. Se você também estiver implantando Diretores, os serviços FQDN de Web externo definidos por qualquer Diretor ou Pool de diretores devem ser exclusivos de qualquer outro Diretor ou Pool de diretores, além de qualquer Pool de Front-Ends ou Servidor Front-End. Se você decidir ultrapassar os serviços de web internos com um FQDN autodefinido, cada FQDN deve ser exclusivo a partir de qualquer outro Pool de Front-Ends, Diretor ou um Pool de diretores.



8.  Publique a topologia.

## Para definir o Diretor (pool de vários Diretores)

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Na página de boas-vindas, clique em **Baixar Topologia da Implantação Existente**.

3.  Na caixa de diálogo **Salvar Topologia Como**, digite o nome o local da cópia local da topologia existente e clique em **Salvar**.

4.  Expanda o site no qual você planeja adicionar o Diretor, clique com o botão direito do mouse em **Pools de Diretores** e clique em **Novo Pool de Diretores**.

5.  Na caixa de diálogo **Definir o FQDN do pool de Diretores**, faça o seguinte:
    
      - Em **FQDN do Pool**, digite o FQDN do pool de Diretores.
    
      - Clique em **Pool de vários computadores** e, em seguida, clique em **Avançar**.

6.  Na caixa de diálogo **Definir os computadores neste pool**, faça o seguinte:
    
      - Especifique o FQDN do computador do primeiro membro do pool e clique em **Adicionar**.
    
      - Repita a etapa anterior para cada computador que você deseja adicionar. Quando terminar, clique em **Avançar**.

7.  Na caixa de diálogo **Definir o compartilhamento de arquivo**, siga um destes procedimentos:
    
      - Para usar um compartilhamento de arquivo existente, clique em **Usar um compartilhamento de arquivos previamente definido**, selecione um compartilhamento de arquivo na lista e clique em **Avançar**.
    
      - Para criar um novo compartilhamento de arquivo, clique em **Definir um novo compartilhamento de arquivo**, digite o FQDN do local do compartilhamento de arquivo em **FQDN do servidor de arquivos**, digite o nome do compartilhamento em **Compartilhamento de Arquivo** e clique em **Avançar**.
    
    > [!IMPORTANT]  
    > O compartilhamento de arquivo especificado ou criado nesta etapa precisa existir ou ser criado antes da publicação da topologia.<br />    O compartilhamento de arquivo atribuído a um Diretor não é realmente usado. Dessa forma, você pode atribuir o compartilhamento de arquivo de qualquer pool na organização.

8.  Na caixa de diálogo **Especificar a URL dos Serviços Web**, em **URL Base Externa**, especifique o FQDN para os Diretores e clique em **Concluir**.
    
    > [!IMPORTANT]  
    > O nome precisa ser resolvido a partir dos servidores DNS de Internet e apontar para o endereço IP público do proxy reverso, que escuta as solicitações HTTP/HTTPS enviadas a essa URL e as atribui ao diretório virtual dos Serviços Web nesse pool de Diretores.    

    > [!WARNING]
    > Se você tiver mais de um Pool de Front-Ends ou Servidor Front-End, os serviços FQDN de Web externo devem ser exclusivos. Por exemplo, se você definir os serviços FQDN de Web externo de um Servidor Front-End como <STRONG>pool01.contoso.com</STRONG>, você não pode usar <STRONG>pool01.contoso.com</STRONG> para outro Pool de Front-Ends ou Servidor Front-End. Se você também estiver implantando Diretores, os serviços FQDN de Web externo definidos por qualquer Diretor ou Pool de diretores devem ser exclusivos de qualquer outro Diretor ou Pool de diretores, além de qualquer Pool de Front-Ends ou Servidor Front-End. Se você decidir ultrapassar os serviços de web internos com um FQDN autodefinido, cada FQDN deve ser exclusivo a partir de qualquer outro Pool de Front-Ends, Diretor ou um Pool de diretores.



9.  Publique a topologia.

