---
title: 'Lync Server 2013: Criar ou modificar um intervalo de números não atribuídos'
TOCTitle: Criar ou modificar um intervalo de números não atribuídos
ms:assetid: a102b226-0460-4d5c-82f9-79b8444fa958
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412748(v=OCS.15)
ms:contentKeyID: 49307645
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar um intervalo de números não atribuídos no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Use um dos seguintes procedimentos para configurar intervalos de números não atribuídos para o Aplicativo Comunicado.

> [!IMPORTANT]  
> Antes de configurar a tabela de números não atribuídos, um ou mais comunicados já devem estar definidos ou um Atendedor Automático da Unificação de Mensagens (UM) do Exchange deve estar configurado.

## Para usar o Painel de Controle do Lync Server para configurar intervalos de números não atribuídos

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Recursos de Voz** e depois, em **Número Não Atribuído**.

4.  Na página **Números não atribuídos**, siga um destes procedimentos:
    
      - Para criar um novo intervalo de números, clique em **Novo**. Em **Nome**, digite o nome que identifica este intervalo de números.
        
        > [!NOTE]  
        > Depois de confirmar o novo intervalo de números não atribuídos para o banco de dados, não é possível alterar este nome.    
      - Para modificar um intervalo de números existente, digite todo o nome do intervalo de órbita, ou parte dele, no campo de pesquisa. Na lista de resultados de intervalos de número, clique no nome desejado, clique em **Editar** e depois, clique em **Exibir Detalhes**.

5.  No primeiro campo **Intervalo Numérico**, digite o número inicial do intervalo e no segundo campo **Intervalo Numérico** digite o número final do intervalo.
    
    > [!NOTE]  
    > <ul>    
> <li><p>O número inicial do intervalo deve ser menor ou igual ao número final.</p></li>    
> 
> <li><p>Se o número inicial ou o número final do intervalo incluir um número de ramal, ambos os números devem incluir um ramal, que deve ser o mesmo para ambos.</p></li>    
> 
> 
> <li><p>Os números devem corresponder à expressão regular (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?. Isso significa que o número pode começar com a cadeia de caracteres tel: (se você não especificar essa cadeia de caracteres, ela será adicionada automaticamente), um sinal de adição (+) e um dígito de 1 a 9. O número de telefone pode ter até 17 dígitos e pode ser seguido de um ramal no formato ;ext= seguido do número do ramal.</p></li>    </ul>


6.  Em **Serviço de Comunicado**, execute um dos seguintes procedimentos:
    
      - Clique em **Comunicado**.
    
      - Clique em **UM do Exchange**.

7.  Se, na etapa anterior, você clicou em **Comunicado**, execute:
    
    1.  Sob **FQDN do servidor de destino**, clique em **Selecionar**, clique no ID do serviço de Aplicativo que executa o Aplicativo Comunicado que manipulará chamadas de entrada para este intervalo de números não atribuídos e clique em **OK**.
    
    2.  Em **Comunicado**, clique no comunicado a ser reproduzido para este intervalo de números não atribuídos.

8.  Se, na etapa anterior, você clicou em **UM do Exchange**, sob **Número de telefone do Atendedor Automático**, clique em **Selecionar**, clique no número de telefone a ser usado para este intervalo de números não atribuídos e clique em **OK**.

9.  Clique em **OK**.

10. Na página **Número Não Atribuído**, certifique-se de que os intervalos numéricos não atribuídos estejam organizados da ordem que você deseja. Para alterar a posição do intervalo na tabela, clique em um ou mais nomes consecutivos na lista de intervalos e clique na seta para cima ou para baixo.
    

    > [!TIP]
    > O Lync Server pesquisa a tabela de números não atribuídos de cima para baixo e usa o primeiro intervalo que corresponda ao número não atribuído. Se você tem intervalos sobrepostos e um intervalo que especifica uma última ação de reclassificação, certifique-se de que o intervalo esteja no final da lista.



11. Quando os intervalos numéricos não atribuídos estiverem na ordem desejada, clique em **Confirmar tudo**.

## Para usar o Windows PowerShell para configurar intervalos de números não atribuídos

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Use **New-CsUnassignedNumber** para criar um intervalo de números não atribuídos. Use **Set-CsUnassignedNumber** para modificar um intervalo de números não atribuídos existente.
    

    > [!TIP]
    > Se você tiver intervalos sobrepostos e desejar que os intervalos sejam aplicados em uma ordem específica, inclua o parâmetro Prioridade. O intervalo com a maior prioridade será aplicado à chamada.

    
    No linha de comando, siga um destes procedimentos:
    
      - Para criar um intervalo numérico para um serviço de Comunicado, execute:
        
            New-CsUnassignedNumber -Identity <unique identifier for unassigned number range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range> -AnnouncementName <announcement name> -AnnouncementService <FQDN or service ID of the Announcement service>
    
      - Ou para criar um intervalo numérico para Atendedor Automático do UM do Exchange, execute:
        
            New-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber <phone number> -Identity <unique identifier for unassigned number range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range>
    
    Por exemplo:
    
        New-CsUnassignedNumber -Identity "Unassigned range 1" -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551100" -AnnouncementName "Welcome Announcement" -AnnouncementService ApplicationServer:Redmond.contoso.com
    
    Ou
    
        New-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber "+12065551234" -Identity "Unassigned range 1" -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551100"
    
    O exemplo a seguir mostra como modificar os números em um intervalo numérico não atribuído existente.
    
        Set-CsUnassignedNumber -Identity "Unassigned range 1" -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551900"

## Consulte Também

#### Tarefas

[Excluir um intervalo de número não atribuído no Lync Server 2013](lync-server-2013-delete-an-unassigned-number-range.md)  

#### Outros Recursos

[New-CsUnassignedNumber](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsUnassignedNumber)  
[Set-CsUnassignedNumber](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsUnassignedNumber)  
[Get-CsUnassignedNumber](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUnassignedNumber)

