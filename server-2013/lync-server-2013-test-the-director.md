---
title: 'Lync Server 2013: Testar o Diretor'
TOCTitle: Testar o Diretor
ms:assetid: 9627a7e2-28cc-429c-b79b-7c7a27573bb7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398767(v=OCS.15)
ms:contentKeyID: 49307524
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Testar o Diretor no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Neste estágio, você tem um Diretor ou pool de Diretores configurado, mas as entradas SRV do DNS ainda apontam os clientes para fazer logon usando um pool ou servidor Standard Edition. Antes de alterar o registro DNS para fazer com que os clientes do Lync 2013 façam logon automaticamente usando o Diretor, teste um cliente apontando-o manualmente para o Diretor.

## Para testar a implantação

1.  Faça logon no computador em que o Painel de Controle do Lync Server está instalado com uma conta de domínio que seja parte do grupo **CSAdministrator** .

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  No painel de navegação, clique em **Topologia** e, na coluna **Status** , confirme se existe um servidor verde com uma seta (ou seja, ![Ícone do servidor com seta verde](images/Gg398767.2263cdb7-7e60-457a-a528-a3a082bd051b(OCS.15).jpg "Ícone do servidor com seta verde")) para seu Diretor ou pool de Diretores.

4.  Conecte dois computadores clientes com o cliente do Lync Server 2013 instalado e faça logon com uma conta de usuário diferente, habilitada para o Lync Server 2013 em cada computador.

5.  Em um dos computadores cliente, clique no menu **Opções** , selecione o grupo de configurações **Pessoal** , clique em **Avançado** , em **Configuração Manual** e defina o **Nome do servidor interno ou endereço IP** como o nome totalmente qualificado (FQDN) do novo Diretor ou pool de Diretores.

6.  Faça logon em ambos os clientes e verifique se o cliente que está entrando usando o Diretor consegue fazer logon com êxito, veja o status da presença do outro usuário e se podem trocar mensagens instantâneas.

