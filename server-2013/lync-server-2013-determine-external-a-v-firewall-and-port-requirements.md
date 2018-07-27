---
title: 'Lync Server 2013: Determinar firewall A/V externo e requisitos de porta'
TOCTitle: Determinar firewall A/V externo e requisitos de porta
ms:assetid: 3b849dc7-175d-40d1-820d-80e6ade6d332
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425882(v=OCS.15)
ms:contentKeyID: 49306452
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Determinar firewall A/V externo e requisitos de porta para Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A comunicação de A/V (áudio/vídeo) pode ser complexa. Em virtude da natureza dos protocolos usados em A/V e de como os clientes e servidores usam os protocolos, uma seção especial é garantida para explicar as diferenças entre as verões do cliente e do servidor.

Use a tabela Firewalls e Portas de A/V a seguir para determinar os requisitos de firewall e as portas a serem abertas. Em seguida, revise a terminologia do NAT (conversão de endereço de rede), pois o NAT pode ser implementado de muitas formas diferentes. Para ver um exemplo detalhado das configurações de porta do firewall, consulte as arquiteturas de referência em [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).

### Uso do Protocolo Geral para UDP e TCP no tráfego de Mídia e Áudio/Vídeo

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Transporte de Áudio/Vídeo</th>
<th>Uso</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UDP</p></td>
<td><p>Protocolo de camada de transporte preferido para áudio e vídeo</p></td>
</tr>
<tr class="even">
<td><p>TCP</p></td>
<td><p>Protocolo de camada de transporte de fallback para áudio e vídeo</p>
<p>Protocolo de camada de transporte necessário para compartilhamento de aplicativo para Office Communications Server 2007 R2, Lync Server 2010 e Lync Server 2013</p>
<p>Protocolo de camada de transporte necessário para transferência de arquivo para Lync Server 2010 e Lync Server 2013</p></td>
</tr>
</tbody>
</table>


## Requisitos de porta de firewall A/V externa para acesso de usuário externo

Os requisitos de porta do firewall para SIP externo (e interno) e as interfaces de conferência são consistentes, independentemente da versão do cliente ou do parceiro de federação.

O mesmo não é verdadeiro para a interface externa de borda de áudio/vídeo. Para a federação com o Office Communications Server 2007, o serviço de borda de A/V exige que as regras do firewall externo permitam que o tráfego RTP/TCP e RTP/UDP no intervalo de portas de 50.000 a 59.999 flua nas duas direções. A tabela anterior assume que o Lync Server 2013 é o parceiro de federação principal e está configurado para se comunicar com um dentre os outros tipos de parceiro de federação listados.

Configurar a faixa de porta de Áudio/Vídeo para 50.000-59.999 deve levar em consideração que tal faixa de porta conterá portas fonte para comunicações com parceiros de federação. Detalhadamente, considere que uma comunicação é iniciada de um parceiro de federação. A comunicação das portas do Serviço de Borda A/V na faixa 50.000-59.999 conectará à porta esperada TCP 443 do Serviço de Borda A/V do parceiro. Inversamente, o tráfego de entrada para a sua porta TCP 443 Serviço de Borda A/V possuirá uma porta fonte na faixa de 50.000-59.999.

Firewalls diferentes e políticas para administração de firewall podem necessitar apenas que regras de destino sejam configuradas, ou pode necessitar tanto a fonte quando o destino sejam configurados. Se seus requisitos forem apenas para porta de destino, os requisitos para Áudio/Vídeo são:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>IP de origem</th>
<th>IP de destino</th>
<th>Porta de Destino</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Interface do Serviço de Borda A/V</p></td>
<td><p>Qualquer um</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>Interface do Serviço de Borda A/V</p></td>
<td><p>Qualquer um</p></td>
<td><p>UDP 3478</p></td>
</tr>
<tr class="odd">
<td><p>Qualquer um</p></td>
<td><p>Interface do Serviço de Borda A/V</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>Qualquer um</p></td>
<td><p>Interface do Serviço de Borda A/V</p></td>
<td><p>UDP 3478</p></td>
</tr>
</tbody>
</table>


Se as suas políticas necessitarem de definições de regra de firewall de entrada e saída, os requisitos para Áudio/Vídeo são:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>IP de origem</th>
<th>IP de destino</th>
<th>Porta de origem</th>
<th>Porta de Destino</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Interface do Serviço de Borda A/V</p></td>
<td><p>Qualquer um</p></td>
<td><p>TCP 50.000-59.999</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>Interface do Serviço de Borda A/V</p></td>
<td><p>Qualquer um</p></td>
<td><p>UDP 3478</p></td>
<td><p>UDP 3478</p></td>
</tr>
<tr class="odd">
<td><p>Qualquer um</p></td>
<td><p>Interface do Serviço de Borda A/V</p></td>
<td><p>Qualquer um</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>Qualquer um</p></td>
<td><p>Interface do Serviço de Borda A/V</p></td>
<td><p>Qualquer um</p></td>
<td><p>UDP 3478</p></td>
</tr>
</tbody>
</table>


> [!IMPORTANT]  
> O Microsoft Office Communications Server 2007 requer uma configuração um pouco diferente. A faixa de porta TCP e UDP de 50.000-59.999 deve ser aberta como de entrada e saída. Este requisito é apenas para Office Communicator 2007. Office Communications Server 2007 R2e Lync Server 2010, e Lync Server 2013 requer apenas a faixa TCP de 50.000-59.999 de saída aberta.

## Requisitos de NAT para acesso de usuário externo

NAT geralmente é uma função de roteamento, mas dispositivos mais recentes, como firewalls e até mesmo balanceadores de carga de hardware podem ser configurados para NAT. Em vez de focar em qual dispositivo está executando NAT, este tópico descreve o comportamento do NAT necessário.

O Lync Server 2013  software de comunicação não dá suporte a NAT para tráfego para ou da interface interna de borda, mas para a interface externa de borda, o comportamento do NAT a seguir é necessário.

> [!IMPORTANT]  
> É preciso configurar NAT para o tráfego de entrada e saída. NAT simétrico é a tecnologia de NAT descrita neste tópico.

Esta documentação usa os acrônimos ChangeDST e ChangeSRC das tabelas e desenhos para definir o seguinte comportamento necessário:

  - **ChangeDST**   o processo de alterar o endereço IP de destino em pacotes destinados à rede que está usando o NAT. Isso também é conhecido como transparência, encaminhamento de porta, modo de NAT de destino ou modo de NAT parcial.

  - **ChangeSRC**   o processo de alterar o endereço IP de origem nos pacotes que saem da rede que está usando o NAT. Isso também é conhecido como proxy, NAT seguro, NAT com estado, NAT de origem ou modo de NAT completo.

Independentemente da convenção de nomenclatura usada, o comportamento NAT exigido para a interface externa do Servidor de Borda é:

  - Para tráfego da Internet para a interface externa de Borda:
    
      - Altere o endereço IP de destino do pacote de entrada do endereço IP público da interface externa de Borda para o endereço IP convertido da interface externa de Borda.
    
      - Deixe o endereço IP de origem intacto para que haja uma rota de retorno para o tráfego.

  - Para tráfego da interface externa de Borda para a Internet:
    
      - Altere o endereço IP de origem do pacote que está saindo da interface externa de Borda, do endereço IP convertido para o endereço IP público da interface externa de Borda, para que o endereço IP de Borda interno não seja exposto e porque ele é um endereço IP não roteável.
    
      - Deixe o endereço IP de destino intacto nos pacotes de saída.

A figura a seguir mostra a distinção entre alterar o endereço IP de destino (ChangeDST) para tráfego de entrada e alterar o endereço IP de origem (ChangeSRC) para tráfego de saída usando a borda A/V como exemplo.

**Alterando o endereço IP de destino (ChangeDST) para tráfego de entrada e alterando o endereço IP de origem (ChangeSRC)**

![Alterando endereços IP de destino/origem](images/Gg425882.0fee7ec5-4cb8-4aff-9164-e7fbab73336d(OCS.15).jpg "Alterando endereços IP de destino/origem")

Os pontos principais são:

  - Para o tráfego de entrada no servidor que executa o Serviço de Borda A/V, o endereço IP de origem não é alterado, mas o endereço IP de destino é alterado do 131.107.155.30 para o endereço IP convertido 10.45.16.10.

  - Para o tráfego de saída do servidor que executa o Serviço de Borda A/V de volta para a estação de trabalho, o endereço IP de origem é alterado do endereço IP público do servidor para o endereço IP público do servidor que executa o Serviço de Borda A/V. O IP de destino permanece sendo o endereço IP público da estação de trabalho. Depois que o pacote deixa o primeiro dispositivo de NAT de saída, a regra do dispositivo de NAT altera o endereço IP de origem do servidor que executa o endereço IP (10.45.16.10) da interface externa do Serviço de Borda A/V para o respectivo endereço IP público (131.107.155.30).

