---
title: 'Lync Server 2013: Configurar certificados do Diretor'
TOCTitle: Configurar certificados do Diretor
ms:assetid: 22988186-15ae-43b1-92f4-0adb3b75a7fd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398296(v=OCS.15)
ms:contentKeyID: 49306135
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar certificados do Diretor no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

> [!IMPORTANT]  
> Ao executar o Assistente de Certificado, certifique-se de que você está conectado usando uma conta que seja membro de um grupo ao qual tenham sido atribuídas as permissões apropriadas para o tipo de modelo de certificado que será utilizado. Por padrão, uma solicitação de certificado do Lync Server 2013 utilizará o modelo de certificado do Servidor Web. Se uma conta membro do grupo RTCUniversalServerAdmins for utilizada para solicitar um certificado usando este modelo, verifique se foram atribuídas as permissões Inscrever a este grupo, necessárias para usar o modelo.

Cada Diretor exige um certificado padrão, um certificado da Web interno e um externo. Para obter detalhes sobre os requisitos de certificado para Diretores, consulte [Requisitos de certificado para servidores internos no Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md), na documentação de Planejamento.

Use o procedimento a seguir para configurar certificados de Diretor. Repita o procedimento para cada Diretor. As etapas deste procedimento descrevem como configurar um certificado de uma autoridade de certificação (CA) raiz corporativa interna implantada pela organização e processamento de solicitação offline. Para obter detalhes sobre como obter certificados de uma CA externa, contate a equipe de suporte.

## Configurar certificados para o Diretor ou pool de Diretores

1.  No Assistente de Implantação do Lync Server, ao lado de **Etapa 3: Solicitar, instalar ou atribuir certificados**, clique em **Executar**.

2.  Na página **Assistente de Certificados**, clique em **Solicitar**.

3.  Na página **Solicitação de Certificado**, clique em **Avançar**.

4.  Na página **Solicitações atrasadas ou imediatas**, aceite a opção padrão **Enviar solicitação imediatamente para uma autoridade de certificação online** e clique em **Avançar**.

5.  Na página **Escolher uma autoridade de certificação (CA)**, clique na autoridade de certificação interna do Windows que você deseja usar e em **Avançar**.

6.  Na página **Conta da autoridade de certificação**, especifique as credenciais alternativas a serem usadas se a conta na qual você está conectado não possui autoridade suficiente para solicitar o certificado e clique em **Avançar**.

7.  Na página **Especificar modelo do certificado alternativo**, clique em **Avançar**.

8.  Na página **Nome e configurações de segurança**, é possível especificar um **Nome amigável**, aceitar o comprimento de chave de 2048 bits e clicar em **Avançar**.

9.  Na página **Informação da organização**, especifique opcionalmente a informação de organização e clique em **Avançar**.

10. Na página **Informação geográfica**, especifique opcionalmente a informação geográfica e clique em **Avançar**.

11. Na página **Nome do assunto/Nomes alternativos do assunto**, clique em **Avançar**.
    
    > [!NOTE]  
    > A lista de nomes alternativo de assunto deve conter o nome do computador no qual você está instalando o Diretor (se um único Diretor) ou o nome do pool de Diretores e os nomes de URL simples configurados para a organização.

12. Na página **Configuração de domínio SIP no SAN**, selecione **Domínios SIP configurados** para todos os domínios que você deseja que o Diretor trate e clique em **Avançar**.

13. Na página **Configurar nomes alternativos do assunto adicional**, adicione qualquer nome alternativo do assunto necessário e clique em **Avançar**.

14. Na página **Resumo da solicitação de certificado**, clique em **Avançar**.

15. Na página **Executar comandos**, clique em **Avançar** após a conclusão da execução dos comandos.

16. Na página **Status da solicitação de certificado online**, clique em **Finalizar**.

17. Na página **Atribuição de certificado**, clique em **Avançar**.
    
    > [!NOTE]  
    > Para exibir o certificado, clique duas vezes no certificado da lista.

18. Na página **Resumo da atribuição de certificado**, clique em **Avançar**.

19. Na página **Executar comandos**, clique em **Finalizar** após a conclusão da execução de comandos.

20. Na página **Assistente de certificado**, clique em **Fechar**.

