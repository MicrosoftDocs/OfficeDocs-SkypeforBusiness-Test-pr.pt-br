---
title: Restaurando um servidor membro do Enterprise Edition
TOCTitle: Restaurando um servidor membro do Enterprise Edition
ms:assetid: d960b19c-2104-4719-b736-0d940f254d42
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202191(v=OCS.15)
ms:contentKeyID: 52057738
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurando um servidor membro do Enterprise Edition

 

_**Tópico modificado em:** 2013-02-18_

Se um servidor que estiver executando uma das seguintes funções de servidor falhar, siga o procedimento neste tópico para restaurar o servidor. Se vários servidores falharem de forma independente, execute o procedimento para cada servidor.

  - Servidor Front-End

  - Servidor de mediação

  - Diretor

  - Servidor de chat persistente

  - Servidor de Borda


> [!TIP]
> Recomendamos que você faça uma cópia da imagem do sistema antes de iniciar a restauração. Você pode utilizar essa imagem como ponto de reversão caso ocorra algo errado durante a restauração. Convém usar a cópia da imagem depois de instalar o sistema operacional e o SQL Server e restaurar ou registrar novamente os certificados.



## Para restaurar um servidor membro

1.  Comece com um servidor novo ou limpo que tenha o mesmo FQDN (nome de domínio totalmente qualificado) que o servidor que falhou, instale o sistema operacional e restaure os certificados ou registre-os novamente.
    
    > [!NOTE]  
    > Siga os procedimentos de implantação de servidor de sua organização para executar essa etapa.

2.  Em uma conta de usuário que seja membro do grupo RTCUniversalServerAdmins, faça logon no servidor que você está restaurando.

3.  Vá até a pasta ou mídia de instalação do Lync Server e inicie o Assistente de Implantação do Lync Server, localizado em \\setup\\amd64\\Setup.exe.

4.  Execute o Assistente de Implantação para fazer o seguinte:
    
    1.  Execute **Etapa 1: Instalar Repositório de Configuração Local** para instalar os arquivos de configuração locais.
    
    2.  Execute **Etapa 2: Instalar ou Remover Componentes do Lync** para instalar a função de servidor do Lync Server.
    
    3.  Execute **Etapa 3: Solicitar, Instalar ou Ceder Certificados** para atribuir os certificados.
    
    4.  Execute **Etapa 4: Iniciar os Serviços** para iniciar os serviços no servidor.
    
    Para obter detalhes sobre como executar o Assistente de Implantação, consulte a Documentação de implantação para a função de servidor que você está restaurando.

