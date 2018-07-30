---
title: Configurando intervalo de portas de mídia
TOCTitle: Configurando intervalo de portas de mídia
ms:assetid: 2c4b7c0b-0dce-48f4-a489-336d6e526f7c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204770(v=OCS.15)
ms:contentKeyID: 49306234
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando intervalo de portas de mídia

 

_**Tópico modificado em:** 2015-03-09_

As configurações de intervalo da porta de mídia podem impactar significantemente o desempenho do cliente e devem ser configuradas. É possível definir estas configurações usando o Shell de Gerenciamento do Lync Server.

### Configurações do Intervalo da Porta de Mídia

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuração</th>
<th>Descrição</th>
<th>Cmdlet do Shell de Gerenciamento do Lync Server</th>
<th>Parâmetros do cmdlet</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Portrange\Enabled</p></td>
<td><p>Especifica se os intervalos de porta enviados pelo servidor devem ser usados pelo cliente para mídia e sinalização. Usado em conjunto com os subvalores MinMediaPort e MaxMediaPort.</p></td>
<td><p><strong>CsConferencingConfiguration</strong></p></td>
<td><p>ClientMediaPortRangeEnabled</p></td>
</tr>
<tr class="even">
<td><p>Portrange\MinMediaPort</p></td>
<td><p>Especifica o número de porta inicial a usar para a mídia. Combina com o MaxMediaPort para especificar o intervalo de portas. O intervalo mínimo recomendado é de 40 portas.</p></td>
<td><p><strong>CsConferencingConfiguration</strong></p></td>
<td><p>ClientMediaPort (representa o número de porta inicial para usar na mídia do cliente)</p></td>
</tr>
<tr class="odd">
<td><p>Portrange\MaxMediaPort</p></td>
<td><p>Especifica o maior número de porta para usar na mídia. Combina com MinMediaPort para especificar o intervalo de portas. O intervalo mínimo recomendado é de 40 portas.</p></td>
<td><p><strong>CsConferencingConfiguration</strong></p></td>
<td><p>ClientMediaPortRange (indica o número total de portas disponíveis para a mídia do cliente; o padrão é 40)</p></td>
</tr>
</tbody>
</table>


## Para definir as configurações do intervalo de porta da mídia

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o seguinte cmdlet:
    
        Get-CsConferencingConfiguration
    
    Este cmdlet retorna as definições de configuração de conferência.

3.  Execute o seguinte cmdlet com os parâmetros e valores que você deseja para alterar (para obter detalhes sobre os parâmetros deste cmdlet, consulte a documentação do Shell de Gerenciamento do Lync Server):
    
        Set-CsConferencingConfiguration
    
    > [!NOTE]  
    > É possível criar conjuntos adicionais de definições de configuração de conferência para sites específicos. Use o cmdlet <strong>New- CsConferencingConfiguration</strong> com uma identidade de site. Ao criar uma nova definição de configuração de conferência, as configurações do site têm precedência sobre as configurações globais. Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server.
