---
title: 'Lync Server 2013: Definir um Servidor ou Aparelho de Filial Persistente'
TOCTitle: Definir um Servidor ou Aparelho de Filial Persistente
ms:assetid: 1f49cfbe-30b3-4600-af15-47cb2f58d18a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398280(v=OCS.15)
ms:contentKeyID: 49306087
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir um Servidor ou Aparelho de Filial Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-07_

Execute este procedimento no local central caso não tenha definido o Servidor ou o Aparelho de Filial Persistente quando o adicionou à sua topologia.

## Para definir um Aparelho de Filial Persistente ou Servidor de Filial Persistente

1.  Clique em **Iniciar**, em **Todos os programas**, em **Microsoft Lync Server 2013** e em **Lync ServerConstrutor de Topologias**.

2.  Na árvore de console, expanda o site central, expanda **Sites em lote** e expanda o nome do site em lote que você planeja implantar o Aparelho de Filial Persistente ou o Servidor de Filial Persistente.

3.  Clique com o botão direito em **Aparelho de Filial Persistente** e clique em **Novo Aparelho de Filial Persistente**.
    
    > [!IMPORTANT]  
    > <strong>Aparelho de Filial Persistente</strong> é onde você define o Servidor de Filial Persistente e o Aparelho de Filial Persistente.

4.  Na caixa de diálogo **Definir Aparelho de Filial Persistente**, clique em **FQDN**, digite o FQDN do Aparelho de Filial Persistente ou Servidor de Filial Persistente que você irá implantar neste site de lote e clique em **Avançar**.
    
    > [!IMPORTANT]  
    > Se você está definindo um Aparelho de Filial Persistente, o nome inserido em <strong>FQDN</strong> deve ser igual ao FQDN do Aparelho de Filial Persistente que você atribuiu ao atributo <strong>servicePrincipalName</strong>. Para obter detalhes, consulte <a href="lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md">Adicionar um Aplicativo de Filial Persistente ao Active Directory no Lync Server 2013</a>.

5.  Clique em **Pool de Front-End**, clique no Servidor de Front-End (pool de Serviços do Usuário) no site central ao qual este Aparelho de Filial Persistente ou Servidor de Filial Persistente irá se conectar e clique em **Avançar**.

6.  Clique em **Servidor de Borda**, clique no Pool de borda que este Aparelho de Filial Persistente ou Servidor de Filial Persistente irá se conectar para oferecer conectividade PSTN para usuários remotos do site de lote e clique em **Avançar**.

7.  Clique em **FQDN ou Endereço IP do Gateway**, e em seguida digite o FQDN ou endereço IP do ponto de gateway ao qual o Aparelho de Filial Persistente ou Servidor de Filial Persistente é associado para rotear chamadas de PSTN de entrada ou saída.
    
    > [!IMPORTANT]  
    > Se você está definindo um Aparelho de Filial Persistente, este é o gateway ao qual o Servidor de Mediação dentro do Aparelho de Filial Persistente irá se conectar para a conectividade de PSTN.

8.  Clique em **Porta de Escuta para Gateway de IP/PSTN** e aceite a porta padrão.

9.  Em **Protocolo de Transporte Sip**, clique no protocolo de transporte que o Aparelho de Filial Persistente ou Servidor de Filial Persistente usará e clique em **Concluir**.
    
    > [!NOTE]  
    > Por motivos de segurança, recomendamos que você use o TLS. Se você está definindo um Aparelho de Filial Persistente, consulte a documentação do fornecedor do Aparelho de Filial Persistente para verificar se o Aparelho de Filial Persistente suporta o protocolo TLS.

10. Na árvore do console, clique com o botão direito no novo Aparelho ou Servidor de Filial Persistente, clique em **Topologia** e em **Publicar**.

**Próxima etapa**: [Implantar Servidor ou Aparelho de Filial Persistente com Lync Server 2013 - tarefa de site de filial](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md)

