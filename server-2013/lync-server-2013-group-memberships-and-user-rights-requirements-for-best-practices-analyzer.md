---
title: "Assoc. de Grupo e Requis. de Direitos do Usuário p/ o Analis. de Práticas Recom."
TOCTitle: "Assoc. de Grupo e Requis. de Direitos do Usuário p/ o Analis. de Práticas Recom."
ms:assetid: f812e343-8f75-454e-b7a8-1b404e32071a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg591354(v=OCS.15)
ms:contentKeyID: 49308652
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Associações de Grupo e Requisitos de Direitos do Usuário para o Analisador de Práticas Recomendadas

 

_**Tópico modificado em:** 2012-10-21_

Para executar com êxito o Analisador de Práticas Recomendadas, a conta de usuário utilizada para fazer login deve ser membro do grupo Administradores no computador local. Além disso, para verificar o seu ambiente, a conta de usuário deve ser membro dos seguintes grupos:

  - **Admins. do Domínio**   Para listar as informações dos Serviços de Domínio Active Directory e chamar os provedores do Windows Management Instrumentation (WMI) nos controladores do domínio e servidores de catálogo global.

  - **Administradores**   Necessário para cada computador interno do Lync Server 2013 e para cada Servidor de Borda chamar os provedores do Windows Management Instrumentation (WMI) e acessar o registro.

  - **RTCUniversalReadOnlyAdmins**   Direitos administrativos somente leitura delegados ou completos do Lync Server 2013.

  - **Administrador somente exibição do Exchange**   Administrador somente exibição completo ou delegado do Exchange na organização Microsoft Exchange.

Se a sua conta de usuário não tem os direitos de usuário suficientes, você tem duas opções:

  - No prompt de comandos, use o comando **runas** para executar a ferramenta na conta com direitos de usuários suficientes. A sintaxe é a seguinte:
    
        runas /netonly /user:<domain>\<userName> rtcbpa.exe

  - Na página **Conectar-se ao Active Directory**, defina as credenciais das contas que planeja usar para executar o Analisador de Práticas Recomendadas. Clique em **Mostrar opções de login avançadas**. Você pode inserir três contas: uma para se conectar aos Serviços de Domínio Active Directory, uma para se conectar ao Lync Server 2013Servidores de Borda e uma para se conectar aos servidores do Exchange. Se você não especificar nenhuma destas contas, a conta do usuário utilizada para fazer login e executar o Analisador de Práticas Recomendadas é usada.

