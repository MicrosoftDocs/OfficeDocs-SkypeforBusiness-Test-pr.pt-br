---
title: Migrar catálogo de endereços
TOCTitle: Migrar catálogo de endereços
ms:assetid: ac7f0f39-4c6d-4702-8e25-93a73e3d800f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205160(v=OCS.15)
ms:contentKeyID: 49307770
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar catálogo de endereços

 

_**Tópico modificado em:** 2012-10-09_

Em geral, o Catálogo de Endereços do Lync Server 2010 é migrado juntamente com o restante da sua topologia. No entanto, pode ser necessário realizar algumas etapas após a migração, se você personalizou os seguintes itens em seu ambiente do Lync Server 2010:

  - Defina a propriedade de WMI **PartitionbyOU** para agrupar entradas do Catálogo de Endereços por unidade organizacional (UO).

  - Personalizou as regras de normalização do Catálogo de Endereços

  - Alterou o valor padrão do parâmetro **UseNormalizationRules** para Falso.

**Agrupou entradas do Catálogo de Endereços**

Se você definiu a propriedade de WMI **PartitionbyOU** como True para criar catálogos de endereços para cada UO, é necessário definir o atributo **msRTCSIP-GroupingId** do Active Directory sobre usuários e contatos se você deseja continuar agrupando entradas do catálogo de endereços. Pode ser desejável agrupar entradas do catálogo de endereços para limitar o escopo das pesquisas no Catálogo. Para usar o atributo **msRTCSIP-GroupingId** , escreva um script para popular o atributo, atribuindo o mesmo valor para todos os usuários que você deseja agrupar. Por exemplo, atribua um valor único para todos os usuários em uma UO.

**Regras de Normalização do Catálogo de Endereços**

Se você personalizou as regras de normalização do Catálogo de Endereços em seu ambiente do Lync Server 2010, você deverá migrar as regras personalizadas para seu pool piloto. Se você não personalizou regras de normalização do Catálogo de Endereços, não há nada para migrar para o serviço do Catálogo de Endereços. As regras de normalização padrão do Lync Server 2013 são as mesmas regras padrão do Lync Server 2010. Siga o procedimento posteriormente nesta seção para migrar regras de normalização personalizadas.

> [!NOTE]  
> Se sua organização usa controle de chamadas remotas e você personalizou regras de normalização do Catálogo de Endereços, deve executar o procedimento deste tópico antes de usar o controle de chamadas remotas. O procedimento requer a associação no grupo RTCUniversalServerAdmins ou direitos equivalentes.

**UseNormalizationRules definido como Falso**

Se você definiu o valor de **UseNormalizationRules** como Falso, para que os usuários possam usar números telefônicos como eles são definidos em Serviços de Domínio Active Directory sem que o Lync Server 2013 aplique regras de normalização, é necessário definir os parâmetros de **UseNormalizationRules** e **IgnoreGenericRules** para Verdadeiro. Siga o procedimento posteriormente nesta seção para definir esses parâmetros como Verdadeiro.

## Para migrar regras de normalização personalizadas do Catálogo de Endereços

1.  Encontre o arquivo Company\_Phone\_Number\_Normalization\_Rules.txt na raiz da pasta compartilhada do Catálogo de Endereços e copie-o para a raiz da pasta compartilhada do Catálogo de Endereços em seu pool piloto do Lync Server 2013.
    
    > [!NOTE]  
    > As regras de normalização do Catálogo de Endereços da amostra foram instaladas em seu diretório de arquivos do componente ABS Web. O caminho é <strong>$installedDriveLetter:\Program Files\Microsoft Lync Server 2013\Web Components\Address Book Files\Files\ Sample_Company_Phone_Number_Normalization_Rules.txt,</strong>. Este arquivo pode ser copiado e renomeado como  <strong>Company_Phone_Number_Normalization_Rules.txt</strong> para o diretório raiz da pasta compartilhada do catálogo de endereços. Por exemplo, o catálogo de endereços compartilhado no <strong>$serverX</strong>, o caminho será similar ao: <strong>\\$serverX \LyncFileShare\2-WebServices-1\ABFiles</strong>.

2.  Use um editor de texto, como o Bloco de Notas para abrir o arquivo Company\_Phone\_Number\_Normalization\_Rules.txt.

3.  Determinados tipos de entradas não funcionarão corretamente no Lync Server 2013. Pesquise no arquivo pelos tipos de entrada descritos nesta etapa,m edite-os conforme o necessário e salve as alterações na pasta compartilhada do Catálogo de Endereços em seu pool piloto.
    
    Cadeias de caracteres que incluem espaços em branco ou pontuações obrigatórios causam falha nas regras de normalização porque estes caracteres são excluídos da cadeia de caracteres que serve como entrada para as regras de normalização. Se você tem cadeias de caracteres que incluem espaços em branco ou pontuações obrigatórios, é necessário modificá-las. Por exemplo, a cadeia de caracteres a seguir causaria falha na regra de normalização:
    
        \s*\(\s*\d\d\d\s*\)\s*\-\s*\d\d\d\s*\-\s*\d\d\d\d
    
    A cadeia de caracteres a seguir não causaria falha na regra de normalização:
    
        \s*\(?\s*\d\d\d\s*\)?\s*\-?\s*\d\d\d\s*\-?\s*\d\d\d\d

## Para definir UseNormalizationRules e IgnoreGenericRules como verdadeiro

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Siga um destes procedimentos:
    
      - Se sua implantação contiver apenas o Lync Server 2013, execute o cmdlet a seguir em nível global para alterar os valores de **UseNormalizationRules** e **IgnoreGenericRules** para verdadeiro:
        
            Set-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true
    
      - Se sua implantação incluir uma combinação de Lync Server 2013 e Lync Server 2010 ou Office Communications Server 2007 R2, execute o cmdlet a seguir e atribua-o a cada pool do Lync Server 2013 na topologia:
        
            New-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true

3.  Espere para que a replicação de Repositório de Gerenciamento Central ocorra em todos os pools.

4.  Modifique o arquivo de regras de normalização de telefone, "Company\_Phone\_Number\_Normalization\_Rules.txt", para sua implantação apagar o conteúdo. O arquivo está no compartilhamento de arquivo de cada pool do Lync Server 2013. Se o arquivo não estiver presente, crie então um arquivo vazio chamado "Company\_Phone\_Number\_Normalization\_Rules.txt".

5.  Espere alguns minutos para todos os Pools de Front-Ends lerem os novos arquivos.

6.  Execute o cmdlet a seguir em cada pool do Lync Server 2013 em sua implantação:
    
        Update-CsAddressBook

