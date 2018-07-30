---
title: Migrar configurações do aplicativo de Estacionamento de Chamadas
TOCTitle: Migrar configurações do aplicativo de Estacionamento de Chamadas
ms:assetid: 23b192d2-93ec-42a8-b175-b6ed502a2c35
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687993(v=OCS.15)
ms:contentKeyID: 49886135
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar configurações do aplicativo de Estacionamento de Chamadas

 

_**Tópico modificado em:** 2012-10-19_

A migração do aplicativo de Estacionamento de Chamada do Lync Server 2010 para o Lync Server 2013 inclui o provisionamento do pool do Lync Server 2013 com qualquer música personalizada em arquivos em espera que foram carregados no Lync Server 2010, restaurando as configurações de nível de serviço e redefinindo as órbitas de Estacionamento de Chamada para o pool do Lync Server 2013. Se os arquivos de música em espera personalizada foram configurados no pool do Lync Server 2010, estes arquivos precisam ser copiados para o novo pool do Lync Server 2013. Além disso, é recomendado fazer o backup de qualquer arquivo de música em espera personalizada do Estacionamento de Chamada do Lync Server 2010 para outro destino para manter uma cópia de backup separada de qualquer arquivo de música em espera personalizada que foi carregado para o Estacionamento de Chamada. Os arquivos de música em espera personalizada para o aplicativo de Estacionamento de Chamada são armazenados no repositório de arquivos do pool. Para copiar os arquivos de áudio de um repositório de arquivos do pool do Lync Server 2010 para um repositório de arquivos do Lync Server 2013, use o comando **Xcopy** com os seguintes parâmetros:

    Xcopy <Source: Lync Server 2010 Pool CPS File Store Path> <Destination: Lync Server 2013 Pool CPS File Store Path>

    Example usage:  Xcopy "<Lync Server 2010 File Store Path>\OcsFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\"  "<Lync Server 2013 File Store Path>\OcsFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\" 

Quando todos os arquivos de áudio personalizados forem copiados para o repositório de arquivos do Lync Server 2013, as configurações do aplicativo de Estacionamento de Chamada do pool do Lync Server 2013 devem ser definidas e os intervalos de órbita do Estacionamento de Chamadas associados com o pool do Lync Server 2010 devem ser reatribuídos para o pool do Lync Server 2013.

As configurações do aplicativo de Estacionamento de Chamada incluem o limite de tempo de atendimento, habilitar ou desabilitar a música em espera, o máximo de tentativas de atendimento da chamada e a solicitação de tempo limite. Você deve gerenciar as configurações do aplicativo de Estacionamento de Chamada utilizando o Shell de Gerenciamento do Lync Server para executar o cmdlet **Set-CsCpsConfiguration**. Não é possível gerenciar as configurações do aplicativo de Estacionamento de Chamada usando o Painel de Controle do Lync Server.

**Redefinir as configurações de serviço de Estacionamento de Chamada**

1.  No Servidor de Front End Lync Server 2013, abra o Shell de Gerenciamento do Lync Server.

2.  Na linha de comando, digite o seguinte:
    
    > [!NOTE]  
    > Se suas configurações do aplicativo de Estacionamento de Chamada do Lync Server 2013 são idênticas às configurações herdadas do Lync Server 2010, é possível pular esta etapa. Se as configurações de aplicativo de Estacionamento de Chamada são diferentes para os ambientes do Lync Server 2013 e Lync Server 2010, use o cmdlet abaixo como um modelo para atualizar estas mudanças.    
        Set-CsCpsConfiguration -Identity "<LS2013 Call Park Service ID>" -CallPickupTimeoutThreshold "<LS2010 CPS TimeSpan>" -EnableMusicOnHold "<LS2010 CPS value>" -MaxCallPickupAttempts "<LS2010 CPS pickup attempts>" -OnTimeoutURI "<LS2010 CPS timeout URI>"

Para reatribuir todos os intervalos de órbita do Estacionamento de Chamada do pool do Lync Server 2010 para o pool do Lync Server 2013, é possível usar o Painel de Controle do Lync Server ou o Shell de Gerenciamento do Lync Server.

**Reatribuir todos os intervalos de órbita do Estacionamento de Chamada usando o Painel de Controle do Lync Server**

1.  Abrir o Painel de Controle do Lync Server.

2.  No painel esquerdo, selecione **Recursos de Voz**.

3.  Selecione a guia **Estacionamento de Chamada**.

4.  Para cada intervalo de órbita do Estacionamento de Chamada atribuído a um pool do Lync Server 2010, edite a configuração **FQDN do servidor de destino** e selecione o pool do Lync Server 2013 que processará as solicitações do Estacionamento de Chamada.

5.  Selecione **Confirmar** para salvar as mudanças.

**Reatribuir todos os intervalos de órbita do Estacionamento de Chamada usando o Shell de Gerenciamento do Lync Server**

1.  Abrir o Shell de Gerenciamento do Lync Server.

2.  Na linha de comando, digite o seguinte:
    
        Get-CsCallParkOrbit
    
    Este cmdlet lista todos os intervalos de órbita do Estacionamento de Chamada na implantação. Todas as órbitas do Estacionamento de Chamada que possuem os parâmetros **CallParkServiceId** e **CallParkServerFqdn** definidos como o pool do Lync Server 2010 devem ser reatribuídos.
    
    Para reatribuir os intervalos de órbita do Estacionamento de Chamadas do Lync Server 2010 para o pool do Lync Server 2013, na linha de comando, digite o seguinte:
    
        Set-CsCallParkOrbit -Identity "<Call Park Orbit Identity>" -CallParkService "service:ApplicationServer:<Lync Server 2013 Pool FQDN>"

Após reatribuir todos os intervalos de órbita do Estacionamento de Chamadas para o pool do Lync Server 2013, o processo de migração para o aplicativo de Estacionamento de Problemas será concluído e o pool do Lync Server 2013 lidará com todas as futuras solicitações de Estacionamento de Chamadas.

