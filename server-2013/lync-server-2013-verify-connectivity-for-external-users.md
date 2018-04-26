---
title: 'Lync Server 2013: Verificar conectividade para usuários externos'
TOCTitle: Verificar conectividade para usuários externos
ms:assetid: 5c02bd6e-1c96-448a-a21d-58c9961c6640
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398402(v=OCS.15)
ms:contentKeyID: 49306831
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar conectividade para usuários externos no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Para validar a conectividade de usuários externos, é necessário garantir a conectividade dos usuários com o servidor e a porta do Serviço de Borda de Acesso.

Um recurso útil para confirmar sua configuração e a capacidade de conectar-se, enviar e receber as mensagens corretas em situações em que o acesso de usuários externos é necessário é o site Analisador de Conectividade Remota (<https://www.testocsconnectivity.com/>). O site é gerenciado e mantido pelo Suporte da Microsoft. Para acessar o Analisador de Conectividade Remota, abra o site da Web em um navegador e siga as instruções para selecionar o cenário.

## Teste a conectividade de usuários externos e do acesso externo

Os testes de acesso de usuários externos devem incluir todos os tipos de usuário externo aceitos pela sua organização, incluindo um ou todos os seguintes:

  - Os usuários de pelo menos um domínio federado e o teste de IM, presença, A/V e compartilhamento de área de trabalho.

  - Os usuários de cada provedor de serviços públicos de IM que tem suporte em sua empresa (e para o qual o provisionamento foi concluído).

  - Usuários anônimos.

  - Usuários em sua organização que fizeram logon no Lync remotamente, mas sem usar VPN.

Esses testes determinam se o Servidor de Borda:

  - Escuta as portas necessárias usando um cliente telnet de fora da rede.
    
      - Exemplo: telnet sip.contoso.com 443
    
      - Executa o teste anterior nas portas que você está usando no Servidor de Borda ou no pool do Servidor de Borda dependendo da sua implantação.

  - Executa a resolução DNS externa precisa.
    
      - De fora da sua rede, execute ping em cada FQDN externo da Borda ou do pool de Borda. Mesmo se o ping falhar, você verá os endereços IP, que poderá comparar com aqueles que você atribuiu.

