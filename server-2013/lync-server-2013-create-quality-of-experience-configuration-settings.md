---
title: Criar configurações da qualidade de experiência
TOCTitle: Criar configurações da qualidade de experiência
ms:assetid: 64f05569-07c7-4f76-a96b-ea4125a510d5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521006(v=OCS.15)
ms:contentKeyID: 49306927
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar configurações da qualidade de experiência

 

_**Tópico modificado em:** 2015-03-09_

As métricas de QoE (qualidade da experiência) registram a qualidade das chamadas de áudio e vídeo realizadas na organização, inclusive dados como o número de pacotes de rede perdidos, o ruído de fundo e a quantidade de "tremulação" (diferenças no atraso de pacotes). Essas métricas são armazenadas em um banco de dados separadas de outros dados (como registros de detalhes das chamadas), permitindo a habilitação e a desabilitação das informações de QoE, independentemente de outros registros de dados.

Quando você instala o Microsoft Lync Server 2013, um conjunto global exclusivo de configurações de QoE é criado para você. Os administradores também têm a opção de criar configurações personalizadas no escopo do site. Sempre que essas configurações do escopo do site forem usadas, elas prevalecerão sobre as configurações globais. Por exemplo, se você criar configurações de escopo de site para o site da cidade de Redmond, essas configurações (em vez das globais) serão usadas para gerenciar a QoE em Redmond.

As configurações de QoE podem ser criadas no Painel de Controle do Lync Server ou com o uso do cmdlet [New-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsQoEConfiguration). Se você usar o Painel de Controle do Lync Server para criar novas configurações, as seguintes opções estarão disponíveis:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuração da interface do usuário</th>
<th>Parâmetro do PowerShell</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nome</p></td>
<td><p>Identity</p></td>
<td><p>Identificador exclusivo das configurações a serem criadas. As configurações de QoE só podem ser criadas no escopo do site.</p></td>
</tr>
<tr class="even">
<td><p>Habilitar monitoramento de dados de QoE</p></td>
<td><p>EnableQoE</p></td>
<td><p>Especifica se os registros de QoE serão coletados e salvos no banco de dados de monitoramento.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar limpeza de dados de QoE</p></td>
<td><p>EnablePurging</p></td>
<td><p>Especifica se os registros serão apagados ao final do período definido na propriedade <strong>Manter dados de QoE por um período máximo de (dias)</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Manter dados de QoE por um período máximo de (dias)</p></td>
<td><p>KeepQoEDataForDays</p></td>
<td><p>O número de dias durante os quais os dados de QoE permanecerão armazenados antes de serem apagados do banco de dados. Esse valor será ignorado se a limpeza estiver desabilitada.</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> O cmdlet New-CsQoEConfiguration inclui opções adicionais não disponíveis no Painel de Controle do Lync Server. Para obter mais informações, consulte o tópico de ajuda <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsQoEConfiguration">New-CsQoEConfiguration</a>.

## Para criar configurações de QoE usando o Painel de Controle do Lync Server

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Monitoramento e Arquivamento** e em **Dados de Qualidade da Experiência**.

4.  Na página **Dados de Qualidade da Experiência**, clique em **Novo**.

5.  Em **Selecionar um site**, clique no site ao qual a política deverá ser aplicada e depois em **OK**.

6.  Em **Criar Nova Configuração da Qualidade da Experiência**, faça o seguinte:
    
      - Selecione **Habilitar monitoramento de dados de QoE** para habilitar o monitoramento.
    
      - Selecione **Habilitar limpeza de dados de QoE** para habilitar a limpeza.
    
      - Em **Manter dados de QoE por um período máximo de (dias)**, selecione o número máximo de dias durante os quais os registros de QoE deverão ser mantidos.

7.  Clique em **Confirmar**.

## Para criar configurações de QoE usando os cmdlets do Windows PowerShell

Você também pode criar configurações de QoE usando o Windows PowerShell e o cmdlet New-CsQoEConfiguration. Esse cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para criar um novo conjunto de configurações de QoE

  - Este comando cria um novo conjunto de configurações de QoE que será aplicado ao site de Redmond:
    
        New-CsQoEConfiguration -Identity "site:Redmond"

## Para criar um conjunto de configurações de QoE com o monitoramento de QoE desabilitado

  - Como nenhum parâmetro (além do parâmetro Identity obrigatório) foi especificado no comando anterior, o novo conjunto de configurações usará os valores padrão para todas as respectivas propriedades. Para criar configurações que usem outros valores de propriedade, basta incluir o parâmetro e o valor de parâmetro desejados. Por exemplo, para criar um conjunto de configurações de QoE que, por padrão, permita a desabilitação do registro de QoE, use um comando como o seguinte:
    
        New-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $False

## Para especificar vários valores de propriedade ao criar um novo conjunto de configurações de QoE

  - Você pode especificar vários valores de propriedade incluindo vários parâmetros. Por exemplo, o seguinte comando define as novas configurações para manter os dados de QoE por 30 dias e para apagar os dados antigos às 3:00 AM:
    
        New-CsQoEConfiguration -Identity "site:Redmond" -KeepQoEDataForDays 30 -PurgeHourOfDay 3

Para obter mais informações, consulte o tópico de ajuda do cmdlet [New-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsQoEConfiguration).

