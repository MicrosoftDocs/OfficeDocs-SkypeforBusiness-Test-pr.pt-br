---
title: "Autorizar conexão com o serv.de borda do Office Communications Server 2007 R2"
TOCTitle: "Autorizar conexão com o serv.de borda do Office Communications Server 2007 R2"
ms:assetid: 14f6798a-28d6-4b3d-8734-942192e1bbf5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204702(v=OCS.15)
ms:contentKeyID: 49305974
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Autorizar a conexão com o servidor de borda do Office Communications Server 2007 R2

 

_**Tópico modificado em:** 2012-09-28_

Para cada servidor Front-End do Lync Server 2013 ou servidor Standard Edition em seu pool piloto, você deve atualizar a lista de servidores internos que estão autorizados a conectar ao Servidor de Borda do Office Communications Server 2007 R2. Sem estas atualizações, conferências A/V (audiovisual) externas para usuários ingressando usando o Servidor de Borda herdado não irão funcionar.

## Para autorizar conexão ao Servidor de Borda do Office Communications Server 2007 R2

1.  A partir do Servidor de Borda do Office Communications Server 2007 R2, do grupo **Ferramentas Administrativas** , abra o snap-in **Gerenciamento do Computador** .

2.  Na árvore do console, expanda **Serviços e Aplicativos** .

3.  Clique com o botão direito em **Office Communications Server 2007 R2**, e então clique em **Propriedades** .

4.  Clique na guia **Interno** .

5.  Em **Adicionar Servidor** , clique em **Adicionar** .

6.  Na caixa de diálogo **Adicionar Office Communications Server**, insira as informações adequadas:
    
      - Especifique o FQDN (nome de domínio totalmente qualificado) de cada servidor Front-End do Lync Server 2013 ou servidor Standard Edition e pool do Lync Server 2013.
    
      - Especifique o FQDN do Diretor do Lync Server 2013 se você configurou um roteamento estático no pool que especifica o próximo computador de salto por seu FQDN.

7.  Após ter adicionado uma entrada para cada Lync Server 2013, servidor Front-End, servidor Standard Edition, pool e Diretor, clique em **Aplicar** e então em **OK** para fechar a página Propriedades.

