---
title: Usando Config.xml para Tarefas de Instalação
TOCTitle: Usando Config.xml para Tarefas de Instalação
ms:assetid: 0813184a-ab40-417c-b3a3-c2090766b831
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204651(v=OCS.15)
ms:contentKeyID: 49305797
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando Config.xml para Tarefas de Instalação

 

_**Tópico modificado em:** 2016-12-08_

Embora a Ferramenta de Personalização do Office (OCT) seja a ferramenta principal para instalação com personalização, os administradores podem usar o arquivo Config.xml para especificar instruções de instalação adicionais que não estão disponíveis na OCT. As personalizações a seguir só podem ser feitas usando o arquivo Config.xml:

  - Especificar o caminho do ponto de instalação de rede.

  - Selecionar os produtos a serem instalados.

  - Configure o registro em log e o local do arquivo de personalização da Instalação e atualizações de software.

  - Especifique as opções de instalação, como nome do usuário.

  - Copiar a LIS (origem de instalação local) no computador do usuário, mas sem instalar o Office.

  - Adicionar ou remover idiomas da instalação.

Recomendamos o uso do arquivo Config.xml para configurar uma instalação silenciosa do Lync 2013.

Por padrão, o arquivo Config.xml, armazenado no pasta principal do produto (por exemplo \\*produto*.WW) direciona a Instalação desse produto. Por exemplo, o arquivo Config.xml na pasta a seguir instala o Lync 2013:

  - \\\\server\\share\\Lync15\\Lync.WW \\Config.xml

Os elementos Config.xml usados com mais frequência para instalação do Lync 2013 estão listados na tabela a seguir.

### Elementos de Config.xml

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Elemento</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuração</p></td>
<td><p>Elemento de nível superior (obrigatório). Contém o atributo Product, por exemplo: Product=Lync</p></td>
</tr>
<tr class="even">
<td><p>OptionState</p></td>
<td><p>Especifica como os recusos de produto específicos são manipulados durante a instalação. Use os seguintes atributos para impedir a instalação de Serviços Corporativos de Conectividade, que inclui componentes compartilhados que interferem com Outlook 2010:</p>
<ul>
<li><p>Id=&quot;LOBiMain&quot;</p></li>
<li><p>State=&quot;Absent&quot;</p></li>
<li><p>Children=&quot;Force&quot;</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Display</p>
<p></p></td>
<td><p>O nível deUI que a Instalação exibe para o usuário. Entre os atributos comuns estão os seguintes:</p>
<ul>
<li><p>CompletionNotice=&quot;Yes&quot; | &quot;No&quot;(padrão)</p></li>
<li><p>AcceptEula=&quot;Yes&quot; | &quot;No&quot;(padrão)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Logging</p></td>
<td><p>Opções para o tipo de registro em log executado pela Instalação. Entre os atributos comuns estão os seguintes:</p>
<ul>
<li><p>Type =&quot;Off&quot; | &quot;Standard&quot;(padrão) | &quot;Verbose&quot;</p></li>
<li><p>Template=”<em>filename</em>.txt” (o nome do arquivo de log)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Setting</p></td>
<td><p>Especifica valores para as propriedades do Windows Installer. Entre os atributos comuns estão os seguintes:</p>
<ul>
<li><p>Setting Id=&quot;<em>name</em>&quot; (o nome da propriedade do Windows Installer)</p></li>
<li><p>Value=&quot;<em>value</em>&quot; (o valor para atribuir à propriedade)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>DistributionPoint</p></td>
<td><p>O caminho totalmente qualificado do ponto de instalação de rede do qual a instalação deve ser executada. Inclui o atributo Location:</p>
<ul>
<li><p>Location=”<em>path</em>”</p></li>
</ul></td>
</tr>
</tbody>
</table>


O exemplo a seguir mostra um arquivo Config.xml para uma instalação silenciosa típica de Lync 2013.

    <Configuration Product="Lync">
      <OptionState Id="LOBiMain" State="Absent" Children="Force" />
      <Display Level="None" CompletionNotice="No" AcceptEula="Yes" />
      <Logging Type="verbose" Path="%temp%" Template="LyncSetupVerbose(*).log" />
      <Setting Id="SETUP_REBOOT" Value="Never" />
      <DistributionPoint Location="\\server\share\Lync15" />
    </Configuration>

Consulte mais informações sobre como usar o arquivo Config.xml para executar tarefas de manutenção e instalação do Office em [http://go.microsoft.com/fwlink/?linkid=267514\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=267514%26clcid=0x416).

## Para personalizar o arquivo Config.xml

1.  Abra o arquivo Config.xml usando uma ferramenta editora de texto, como o Bloco de Notas.

2.  Localize as linhas que contêm os elementos que você deseja alterar.

3.  Modifique a entrada do elemento com as opções silenciosas que você deseja usar. Remova os delimitadores de comentário, "\<\!--" e "--\>". Por exemplo, use a seguinte sintaxe:
    
        < DistributionPoint Location="\\server\share\Lync15" />

4.  Salve o arquivo Config.xml.

