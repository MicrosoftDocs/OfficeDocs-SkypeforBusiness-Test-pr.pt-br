---
title: 'Lync Server 2013: Implantando pools Front-End emparelhados para recuperação de desastre'
TOCTitle: Implantando pools Front-End emparelhados para recuperação de desastre
ms:assetid: 2f12467c-8b90-43e6-831b-a0b096427f17
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204773(v=OCS.15)
ms:contentKeyID: 49306269
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando pools Front-End emparelhados para recuperação de desastre no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

É possível implantar facilmente a topologia de recuperação de desastres do Pools de Front-Ends emparelhado usando o Construtor de Topologias.

## Para implantar um par de pools do Front-End

1.  Se os pools são novos e ainda não foram definidos, use o Construtor de Topologias para criar os pools.

2.  No Construtor de Topologias, clique com o botão direito em um dos dois pools e clique em **Editar propriedades**.

3.  Clique em **Resiliência** no painel esquerdo e selecione **Pool de backup associado** no painel direito.

4.  Na caixa abaixo **Pool de backup associado**, selecione o pool que você deseja emparelhar com este pool. Apenas pools existentes que não estão emparelhados com outro pool estarão disponíveis para selecionar.
    
    ![Caixa de diálogo Resiliência](images/JJ204773.36080581-db76-497d-bf9e-f02b39574d0e(OCS.15).png "Caixa de diálogo Resiliência")  

5.  Selecione **Failover automático e failback para voz** e clique em **OK**.
    
    Ao exibir os detalhes sobre este pool, o pool associado agora aparece no painel direito em **Resiliência**.

6.  Use o Construtor de Topologias para publicar a topologia.

7.  Se os dois pools ainda não foram implantados, implante-os e a configuração estará concluída. É possível pular as duas etapas finais neste procedimento.
    
    No entanto, se os pools já foram implantados antes de você definir a relação emparelhada, você deve concluir as seguintes duas etapas finais.

8.  Em cada Servidor de Front-End Server nos pools, execute o seguinte:
    
        <system drive>\Program Files\Microsoft Lync Server 2013\Deployment\Bootstrapper.exe 
    
    Isto configura outros serviços necessários para que o emparelhamento de backup funcione corretamente.

9.  De um prompt de comando do Shell de Gerenciamento do Lync Server, execute o seguinte:
    
        Start-CsWindowsService -Name LYNCBACKUP

10. Force o usuário e os dados de conferência de ambos os pools para sincronização um com o outro, com os seguintes cmdlets:
    
```
        Invoke-CsBackupServiceSync -PoolFqdn <Pool1 FQDN>
```
```    
        Invoke-CsBackupServiceSync -PoolFqdn <Pool2 FQDN>
```

    A sincronização dos dados pode levar algum tempo. É possível usar os seguintes cmdlets para verificar o status. Certifique-se de que o status em ambas as direções esteja em um estado estável.
    
```
        Get-CsBackupServiceStatus -PoolFqdn <Pool1 FQDN>
```
```    
        Get-CsBackupServiceStatus -PoolFqdn <Pool2 FQDN>
```

> [!NOTE]  
> A opção <strong>Failover automático e failback para voz</strong> e os intervalos de tempo associado no Construtor de Topologias se aplicam apenas aos recursos de resiliência de voz introduzidos no Lync Server 2010. Selecionar esta opção não implica que o failover de pool discutido neste documento seja automático. O failover de pool e failback sempre exige que um administrador invoque manualmente os cmdlets de failover e failback, respectivamente.
