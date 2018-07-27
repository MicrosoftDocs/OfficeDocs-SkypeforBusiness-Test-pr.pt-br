---
title: Configurando estados de presença personalizados
TOCTitle: Configurando estados de presença personalizados
ms:assetid: e17364a8-8b93-45fc-a614-c80e45435d42
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398997(v=OCS.15)
ms:contentKeyID: 52057747
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando estados de presença personalizados

 

_**Tópico modificado em:** 2016-12-08_

Para definir estados de presença personalizados no Lync 2013, crie um arquivo de configuração de presença XML personalizada e especifique sua localização usando os cmdlets do Shell de Gerenciamento do Lync Server**New-CSClientPolicy** ou **Set-CSClientPolicy** com o parâmetro CustomStateURL.

Os arquivos de configuração têm as seguintes propriedades:

  - Estados de presença personalizados podem ser configurados com os indicadores de presença Disponível, Ocupado e Não perturbe.

  - O atributo de disponibilidade determina qual indicador de presença está associado ao texto de status do estado personalizado. No exemplo posterior neste tópico, o texto de status Trabalhando de casa é exibido à direita do indicador de presença verde (Disponível).

  - O tamanho máximo do texto de status é de 64 caracteres.

  - É possível adicionar no máximo quatro estados de presença personalizados.

  - O parâmetro CustomStateURL especifica o local para o arquivo de configuração. Em Lync 2013, o modo de alta segurança do SIP é habilitado por padrão, portanto você precisará armazenar o arquivo de configuração de presença personalizado em um servidor Web que tenha HTTPS habilitado. Caso contrário, clientes Lync 2013 não poderão se conectar a ele. Por exemplo, um endereço válido seria `https://lspool.corp.contoso.com/ClientConfigFolder/CustomPresence.xml`.


> [!NOTE]  
> Apesar de não ser recomendado em um ambiente de produção, você pode testar um arquivo de configuração localizado em um compartilhamento de arquivos que não sejam HTTPS pelo uso da configuração de registro EnableSIPHighSecurityMode, para desabilitar o modo de alta segurança SIP no cliente. Então você pode utilizar a configuração de registro CustomStateURL para especificar um local que não seja HTTPS para o arquivo de configuração. Observe que o Lync 2013 honra as definições de registro do Lync 2010, mas a ramificação do registro terá sido atualizada. Você criaria as definições de registro como demonstrado a seguir:
> <ul><li><p>HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync\EnableSIPHighSecurityMode</p>
> <p>Tipo: DWORD</p>
> <p>Dado do valor: 0</p></li><li><p>HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync\CustomStateURL</p>
> <p>Tipo: String (REG_SZ)</p>
> <p>Dados do valor (exemplos): file://\\lspool.corp.contoso.com\LSFileShare\ClientConfigFolder\Presence.xml or file:///c:/LSFileShare/ClientConfigFolder/Group_1_Pres.xml</p></li></ul>


Localize seu estado de presença personalizado especificando um ou mais esquema de LCID (ID de localidade) no arquivo de configuração XML. O exemplo mais tarde neste tópico mostra a localização para Inglês - Estados Unidos (1033), Norueguês - Bokmål (1044), Francês - França (1036) e Turco (1055). Para obter uma lista de LCIDs, consulte os IDs de localidade atribuídos pela Microsoft em <http://go.microsoft.com/fwlink/?linkid=157331>.

## Para adicionar estados de presença personalizados ao Lync 2013

1.  Crie um arquivo de configuração XML que usa o formato do exemplo a seguir:
    
        <?xml version="1.0"?>
        <customStates xmlns="http://schemas.microsoft.com/09/2009/communicator/customStates">
          <customState ID="1" availability="online">
            <activity LCID="1033">Working from Home</activity>
            <activity LCID="1044">activity 2 for 1044</activity>
            <activity LCID="1055">activity 3 for 1055</activity>
          </customState>
          <customState ID="2" availability="busy">
            <activity LCID="1033">In a Live Meeting</activity>
            <activity LCID="1036">Equivalent French String for - In a Live Meeting </activity>
          </customState>
          <customState ID="3" availability="busy">
            <activity LCID="1033">Meeting with Customer</activity>
            <activity LCID="1055">meeting with client</activity>
            <activity LCID="1036">Equivalent French String for - Meeting with Customer</activity>
          </customState>
          <customState ID="4" availability="do-not-disturb">
            <activity LCID="1033">Interviewing</activity>
          </customState>
        </customStates>

2.  Salve o arquivo de configuração XML em um servidor Web com HTTPS habilitado. Neste exemplo, o arquivo é chamado Presence.xml e foi salvo no local https://lspool.corp.contoso.com/ClientConfigFolder/CustomPresence.xml.

3.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

4.  No Shell de Gerenciamento do Lync Server, defina o local de seu arquivo de configuração XML usando um comando parecido com o seguinte:
    
        New-CsClientPolicy -Identity ContosoCustomStates 
        -CustomStateURL "https://lspool.corp.contoso.com/ClientConfigFolder/CustomPresence.xml"

5.  Use o cmdlet **Grant-CSClientPolicy** para atribuir essa nova política aos usuários.

Para obter detalhes, consulte [New-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientPolicy) e [Grant-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsClientPolicy) na documentação Shell de Gerenciamento do Lync Server.

> [!NOTE]  
> <ul>
> 
> <li><p>Por padrão, o Lync Server 2013 atualiza políticas e configurações de cliente a cada três horas.</p></li>
> 
> 
> <li><p>Se você desejar continuar a usar configurações de políticas de grupo de versões anteriores, como CustomStateURL, o Lync 2013 reconhecerá essas configurações caso estejam localizadas na nova ramificação de registro da política (HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync). Porém, políticas de cliente baseadas em servidor têm precedência.</p></li></ul>

