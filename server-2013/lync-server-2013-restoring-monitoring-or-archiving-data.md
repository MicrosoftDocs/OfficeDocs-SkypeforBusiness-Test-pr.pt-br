---
title: Restauração de monitoramento ou arquivamento de dados
TOCTitle: Restauração de monitoramento ou arquivamento de dados
ms:assetid: 60118526-13bb-4b03-803e-6ffae219d436
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202175(v=OCS.15)
ms:contentKeyID: 52057639
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restauração de monitoramento ou arquivamento de dados

 

_**Tópico modificado em:** 2013-02-18_

A restauração dos dados de Monitoramento e Arquivamento não é necessário para fazer o Lync Server ser iniciado e executado após uma falha. No entanto, se os dados de monitoramento e arquivamento forem fundamentais para a sua organização, você desejará restaurar os dados depois de recriar os bancos de dados.

O procedimento a seguir descreve como usar o SQL Server Management Studio para restaurar os dados de arquivamento ou de monitoramento.

## Para restaurar os dados de monitoramento ou arquivamento de um arquivo de backup

1.  Faça logon no servidor que você estiver restaurando como membro do grupo Administradores no computador local ou de um grupo com direitos equivalentes.

2.  Abra o Server Management Studio: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft SQL Server 2012** ou **Microsoft SQL Server 2008 R2** e clique em **SQL Server Management Studio**.

3.  Em **Conectar ao Servidor**, conecte-se à instância de SQL Server fornecendo pelo menos o nome do servidor e as informações de autenticação.

4.  Em **Pesquisador de Objetos**, clique com o botão direito do mouse em **Bancos de dados** e clique em **Restaurar Banco de Dados**.

5.  Em **Selecionar uma página**, clique em **Geral** e selecione o nome do banco de dados em **Para o banco de dados** da seguinte maneira:
    
      - Para um Banco de dados de arquivamento, selecione **LcsLog**.
    
      - Para um banco de dados CDR (gravação de detalhes de chamada), selecione **LcsCDR**.
    
      - Para um banco de dados QoE (Qualidade da Experiência), selecione **QoEMetrics**.

6.  Clique em **Do dispositivo**.

7.  Em **Selecione os conjuntos de backup a serem restaurados**, clique no arquivo de backup e clique em **Restaurar**.

8.  Em **Selecionar uma página**, clique em **Opções**, verifique se o caminho do arquivo de dados e o caminho de log estão na pasta correta e clique em **OK**.

## Para garantir que as ACLs (listas de controle de acesso) estejam corretas

1.  Expanda **Bancos de dados**, expanda o banco de dados de arquivamento ou monitoramento, expanda **Segurança** e expanda **Usuários**.

2.  Verifique se o grupo de domínio RTCComponentUniversalServices existe como um usuário.

3.  Se RTCComponentUniversalServices não existir em **Usuários**, faça o seguinte:
    
    1.  Clique com o botão direito do mouse em **Usuários** e clique em **Novo Usuário**.
    
    2.  Em **Nome de logon**, digite o nome do grupo ausente, RTCComponentUniversalServices.
    
    3.  Em **Associação à função de banco de dados**, selecione a permissão **ServerRole** e clique em **OK**.
    
    > [!NOTE]  
    > Não é necessário reiniciar o serviço de arquivamento ou monitoramento.
