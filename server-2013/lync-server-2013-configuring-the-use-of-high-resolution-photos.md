---
title: Configurando o Uso de Fotos de Alta Resolução no Microsoft Lync Server 2013
TOCTitle: Configurando o Uso de Fotos de Alta Resolução no Microsoft Lync Server 2013
ms:assetid: 995da78a-dc44-45a3-908d-16fe36cfa0d9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688150(v=OCS.15)
ms:contentKeyID: 49886325
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o Uso de Fotos de Alta Resolução no Microsoft Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Lync Server 2010 fornecia a capacidade aos usuários de exibir fotos de seus contatos (e de tornar suas fotos disponíveis aos outros). Geralmente, essas fotos eram armazenadas como parte do atributo thumbnailPhoto do usuário, no Active Directory. Isso criava uma séria limitação no tamanho e resolução das fotos: o atributo thumbnailPhoto pode conter apenas uma fotografia com tamanho máximo de 48 pixels por 48 pixels.

No Microsoft Lync Server 2013, entretanto, as fotos podem ser armazenadas na caixa de correio do Microsoft Exchange Server 2013 do usuário; isso permite fotos de até 648 pixels por 648 pixels. Além disso, o Exchange 2013 pode redimensionar essas fotos para usar em diferentes produtos, conforme o necessário. Geralmente, isso significa três tamanhos e resoluções de fotos diferentes.

  - 48 pixels por 48 pixels, o tamanho utilizado pelo atributo thumbnailPhoto do Active Directory. Se você fizer o upload de uma foto para o Exchange 2013, o Exchange criará automaticamente um versão de 48 pixels por 48 pixels dessa foto e atualizará o atributo thumbnailPhoto. Observe, no entanto, que o inverso não é verdadeiro: se você atualizar manualmente o atributo thumbnailPhoto no Active Directory, a foto na caixa de correio do Exchange 2013 do usuário não será automaticamente atualizada.

  - 96 pixels por 96 pixels, para usar no Microsoft Outlook 2013 Web App, Microsoft Outlook 2013, Microsoft Lync Web App e Lync 2013.

  - 648 pixels por 648 pixels para usar noLync 2013 e Microsoft Lync Web App.

> [!NOTE]  
> Se você tiver recursos, recomendamos fazer upload de fotos de 648x648; isso fornece a resolução máxima e qualidade de imagem ideal em qualquer aplicativo do Office 2013. Cada foto JPEG com tamanho de 648x648 e profundidade de 24 bits resulta em um arquivo de aproximadamente 240 kilobytes. Isso significa que você precisará de aproximadamente 1 megabyte de espaço em disco para cada 4 fotos de usuário.

Fotos de alta resolução, que serão acessadas usando os serviços web do Exchange, podem ser enviadas por usuários que executam o Outlook 2013 Web App; os usuários só têm permissão para atualizar sua própria foto. Administradores, no entanto, podem atualizar a foto de qualquer usuário usando o Shell de Gerenciamento do Exchange e uma série de comandos Windows PowerShell parecidos com os seguintes:

    $photo = ([Byte[]] $(Get-Content -Path "C:\Photos\Kenmyer.jpg" -Encoding Byte -ReadCount 0))
    Set-UserPhoto -Identity "Ken Myer" -PictureData $photo -Confirm:$False
    Set-UserPhoto -Identity "Ken Myer" -Save -Confirm:$False

O primeiro comando no exemplo anterior usa o cmdlet Get-Content para ler o conteúdo do arquivo C:\\Photos\\Kenmyer.jpg e armazenar esses dados em uma variável chamada $photo. No segundo comando, o cmdlet Set-UserPhoto do Exchange é usado para enviar a foto e anexá-la à conta de usuário de Ken Myer.

> [!NOTE]  
> Neste exemplo, o nome de exibição do Active Directory de Ken Myer é usado como a identidade da conta de usuário. Você também pode referenciar uma conta de usuário usando outros identificadores como endereço SMTP do usuário ou seu nome principal de usuário. Consulte a documentação do cmdlet Set-UserPhoto em <a href="http://go.microsoft.com/fwlink/?linkid=268536%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=268536&amp;clcid=0x416</a> para obter mais informações

Fazer upload da foto não é o mesmo que atribuir essa foto à conta de usuário de Ken Myer. Em vez disso, fazer o upload da foto simplesmente resulta em uma visualização dessa foto que será exibida na página Opções do Outlook Web App. Para realmente atribuir essa foto à conta de usuário, o usuário deve clicar em **Salvar** na página Opções ou o administrador deve executar o terceiro comando no exemplo. Esse terceiro comando usa o parâmetro Salvar para atribuir a foto à conta de usuário de Ken Myer.

    Set-UserPhoto -Identity "Ken Myer" -Save -Confirm:$False

Para verificar se essa nova foto foi atribuída à conta do usuário, Ken Myer pode fazer log on no Lync 2013, selecionar **Opções** e depois selecionar **Minha Imagem**. A foto recém carregada deve ser exibida como a foto pessoal de Ken. Como alternativa, os administradores podem verificar a foto de qualquer usuário iniciando o Internet Explorer e navegando a um URL similar a esse:

    https://atl-mail-001.litwareinc.com/ews/Exchange.asmx/s/GetUserPhoto?email=kenmyer@litwareinc.com&size=HR648x648

Se o administrador pode ver a foto usando o Internet Explorer, mas o usuário não pode ver sua foto no Lync 2013, isso geralmente indica um problema de conectividade com os Serviços Web do Exchangeou com o serviço de descoberta automática do Exchange.

Observe também que nenhuma configuração adicional é necessária para tornar essa foto disponível no Lync 2013. Em vez disso, a foto ficará disponível instantaneamente depois que for carregada e após a execução do cmdlet Set-UserPhoto.

