---
title: 'Lync Server 2013: Verificar acesso por meio de seu proxy reverso'
TOCTitle: Verificar acesso por meio de seu proxy reverso
ms:assetid: 3076a786-e022-4d41-91ec-1bf252b2a468
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429697(v=OCS.15)
ms:contentKeyID: 49306291
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar acesso por meio de seu proxy reverso no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-29_

Execute o procedimento a seguir para verificar se os usuários podem acessar informações no proxy reverso. Talvez seja necessário concluir a configuração do firewall e do DNS (Sistema de Nomes de Domínio) para que o acesso funcione corretamente.

## Para verificar se você pode acessar o site via Internet

  - Abra um navegador da Web e, na barra **Endereço** , digite as URLs que são usadas pelos clientes para acessar os arquivos do Catálogo de Endereços e o site de Webconferências da seguinte forma:
    
      - Para o Servidor de Catálogo de Endereços, digite uma URL parecida com a seguinte: **https:// *externalwebfarmFQDN* /abs** onde *externalwebfarmFQDN* é o FQDN externo dos serviços da Web externos que hospeda os serviços do Catálogo de Endereço. O usuário deve receber um desafio HTTP, pois a segurança do diretório na pasta do Servidor de Catálogo de Endereço está configurada para autenticação do Windows por padrão.
    
      - Para conferência, digite uma URL parecida com a seguinte: **https:// *externalwebfarmFQDN* /meet** onde *externalwebfarmFQDN* é o FQDN externo do web farm que hospeda o conteúdo da reunião. Essa URL deve exibir a página de solução de problemas para conferência. Em alternativa, confirme que sua URL Simples para conferência funcione corretamente. Uma URL Simples de exemplo para participar da conferência pode ser https://meet.contoso.com.
    
      - Para expansão do grupo de distribuição, digite uma URL parecida com a seguinte: **https:// *externalwebfarmFQDN* /GroupExpansion/service.svc**. O usuário deve receber um desafio HTTP, pois a segurança do diretório no serviço de expansão do grupo de distribuição está configurada para autenticação do Windows por padrão.
    
      - Para discagem, digite a URL simples semelhante à seguinte **https:// *externalwebfarmFQDN* /dialin** onde *externalwebfarmFQDN* é o FQDN externo no farm da web que hospeda a página de discagem para conferência discada. O usuário deve ser redirecionado para a página de discagem. Em alternativa, confirme que sua discagem de URL simples funcione corretamente. Uma URL Simples de exemplo para discagem pode ser https://dialin.contoso.com
    
      - Para confirmar que a URL de descoberta automática esteja funcionando, digite https://lyncdiscover. *FQDNdodomínioexterno* . O navegador deverá solicitar que você abra um arquivo. Selecione o Bloco de Notas para abri-lo. Uma resposta típica seria semelhante a:
        
            {"AccessLocation":"External","Root":{"Links":[{"href":"https:\/\/extweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/domain","token":"Domain"},
            {"href":"https:\/\/extweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/user","token":"User"},
            {"href":"https:\/\/lyncweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/oauth\/user","token":"OAuth"}]}}

