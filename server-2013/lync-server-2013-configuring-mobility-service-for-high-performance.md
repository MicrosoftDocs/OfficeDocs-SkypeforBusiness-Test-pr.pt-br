---
title: Configurando o serviço de mobilidade para alto desempenho
TOCTitle: Configurando o serviço de mobilidade para alto desempenho
ms:assetid: c2b8aadb-cffb-49f0-ba7a-e8541a1ff475
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690042(v=OCS.15)
ms:contentKeyID: 49308015
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o serviço de mobilidade para alto desempenho

 

_**Tópico modificado em:** 2013-02-17_

Ao instalar o Serviço de Mobilidade do Lync Server 2013 no IIS (Serviços de Informações da Internet) 7.5, o instalador do Serviço de Mobilidade define algumas configurações de desempenho no Servidor Front-End. Recomendamos o uso do IIS 7.5 para mobilidade. Se você usar o IIS 7.0 no Windows Server 2008, será necessário definir essas configurações manualmente. As configurações afetam o número máximo de solicitações de usuário simultâneas e o número máximo de segmentos permitidos para o Serviço de Mobilidade.

As configurações de desempenho são as seguintes:

  - **maxConcurrentThreadsPerCPU** está definido como zero (0).

  - **maxConcurrentRequestsPerCPU** está definido como zero (0).

  - O modelo de processo ASP.NET está definido como AutoConfig (somente para IIS 7.5).

  - O limite de fila HTTP.sys está definido como 1.000 (por padrão).

Se você usar o IIS 7.0, recomendamos a instalação da atualização disponível no artigo 2290617 da Base de Conhecimento da Microsoft, "CORREÇÃO: Um hotfix está disponível para permitir a configuração de algumas propriedades do ASP.NET para cada pool de aplicativos no IIS 7.0" em [http://go.microsoft.com/fwlink/?linkid=3052\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=3052%26clcid=0x416) de modo que você possa aplicar as alterações somente para o Serviço de Mobilidade e não afete outros serviços da Web.

O procedimento a seguir descreve como alterar a solicitação simultânea do ASP.NET e limite máximo de segmento no IIS 7.0 se você não instalar a atualização disponível no artigo 2290617 da Base de Conhecimento. No entanto, mesmo se você instalar o artigo 2290617, deverá usar a documentação fornecida pelo artigo para aplicar as mesmas alterações somente para os pools de aplicativo ISS internos e externos de Mobilidade. Nesse caso, use um arquivo de configuração separado para as configurações ASP.NET.

> [!IMPORTANT]  
> Se você usar o procedimento a seguir para alterar os limites máximos, as alterações afetarão todos os pools de aplicativo IIS.

Para obter detalhes sobre como definir essas configurações, consulte [http://go.microsoft.com/fwlink/?linkid=234537\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=234537%26clcid=0x416).

## Para alterar a solicitação simultânea e os limites máximos de segmento

1.  Clique em **Iniciar** e em **Executar**.

2.  Na caixa **Executar**, digite o seguinte:
    
        notepad %SystemRoot%\Microsoft.NET\Framework64\v2.0.50727\Aspnet.config

3.  Clique em **OK**.

4.  Adicione ou substitua o seguinte elemento \<system.web\> como um filho do elemento \<configuration\> no arquivo Aspnet.config:
    
        <system.web>
        <applicationPool maxConcurrentRequestsPerCPU="<#>" maxConcurrentThreadsPerCPU="0" requestQueueLimit="5000"/>
        </system.web>
    
    onde \# é 0 para remover o limite ou o novo número, conforme descrito anteriormente nesta seção

5.  Salve o arquivo Aspnet.config e feche o Bloco de notas.

