---
title: Configurar monitoramento SCOM
TOCTitle: Configurar monitoramento SCOM
ms:assetid: 4003d225-2a33-448c-abd9-571750661140
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688033(v=OCS.15)
ms:contentKeyID: 49886189
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar monitoramento SCOM

 

_**Tópico modificado em:** 2012-10-04_

Após migrar para o Microsoft Lync Server 2013, você deve concluir algumas tarefas para configurar o Lync Server 2013 para funcionar com o System Center Operations Manager.

  - Aplique atualizações Lync Server 2010 a um servidor eleito a gerenciar a lógica da descoberta central.

  - Atualize a chave de registro do servidor candidato a descoberta central.

  - Configure seu servidor de gerenciamento System Center Operations Manager primário para substituir o nó do candidato de descoberta central.

Instruções para executar cada uma dessas tarefas são fornecidas abaixo.

**Aplique atualizações Lync Server 2010 a um servidor eleito a gerenciar a lógica da descoberta central.**

1.  Eleja um servidor que possua os arquivos do agente do Gerenciador de Operações do Sistema Central instalados e esteja configurado como nó de descoberta central.

2.  Aplique atualizações Lync Server 2010 a este servidor. Consulte o tópico [Aplicar atualizações do Lync Server 2010](apply-lync-server-2010-updates.md).

**Atualize a chave de registro do servidor candidato a descoberta central.**

1.  No servidor eleito a gerenciar a lógica de descoberta central, abra uma janela de comando Windows PowerShell.

2.  Na linha de comando, digite o seguinte:
    
    ```
        New-Item -Path "HKLM:\Software\Microsoft\Real-Time Communications\Health"
    ```
    ```    
        New-Item -Path "HKLM:\Software\Microsoft\Real-Time Communications\Health\CentralDiscoveryCandidate"
    ```

    > [!NOTE]  
    > Sempre que você editar o registro, você poderá receber um erro em que o comando falha caso a chave de registro já exista. Caso isso aconteça, você pode ignorar com segurança o erro.

**Configurar o servidor de gerenciamento System Center Operations Manager primário para substituir o nó do candidato a inspetor de descoberta central.**

1.  Em um computador onde o console do Gerenciador de Operações do System Center foi instalado, expanda **Objetos do Pacote de Gerenciamento** e selecione **Descobertas de Objeto**.

2.  Clique em **Alterar escopo...**

3.  Da página **Escopo de Objetos do Pacote de Gerenciamento**, selecione **Candidato a Descoberta LS**.

4.  Substitua o **Valor Efetivo de Candidato a Descoberta LS** para o nome do servidor de candidato eleito para o procedimento anterior.

Por fim, finalize as alterações, reinicie o serviço de integridade no Servidor de Gerenciamento de Raiz de Gerenciamento de Operações do System Center.

