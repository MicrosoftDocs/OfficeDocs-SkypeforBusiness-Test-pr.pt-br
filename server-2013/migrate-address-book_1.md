---
title: Migrar catálogo de endereços
TOCTitle: Migrar catálogo de endereços
ms:assetid: b6e000ce-8b2e-460c-8a8b-000254b9d778
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205198(v=OCS.15)
ms:contentKeyID: 49307878
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar catálogo de endereços

 

_**Tópico modificado em:** 2012-10-02_

**Para migrar regras de normalização personalizadas do Catálogo de Endereços**

1.  Encontre o arquivo Company\_Phone\_Number\_Normalization\_Rules.txt na raiz da pasta compartilhada do Catálogo de Endereços e copie-o para a raiz da pasta compartilhada do Catálogo de Endereços em seu pool piloto do Lync Server 2013.
    
    > [!NOTE]  
    > As regras de normalização do Catálogo de Endereços da amostra foram instalados em seu diretório de arquivos de componentes do ABS Web. O caminho é <strong>$installedDriveLetter:\Program Files\Microsoft Lync Server 2013\Web Components\Address Book Files\Files\ Sample_Company_Phone_Number_Normalization_Rules.txt,</strong>. Este arquivo pode ser copiado e renomeado como  <strong>Company_Phone_Number_Normalization_Rules.txt</strong>  para o diretório raiz da pasta compartilhada do catálogo de endereços. Por exemplo, o catálogo de endereços compartilhado em <strong>$serverX</strong>, terá o caminho similar ao: <strong>\\$serverX \LyncFileShare\2-WebServices-1\ABFiles</strong>.

2.  Use um editor de texto, como o Bloco de Notas para abrir o arquivo Company\_Phone\_Number\_Normalization\_Rules.txt.

3.  Determinados tipos de entradas não funcionarão corretamente no Lync Server 2013. Pesquise no arquivo pelos tipos de entrada descritos nesta etapa,m edite-os conforme o necessário e salve as alterações na pasta compartilhada do Catálogo de Endereços em seu pool piloto.
    
    Cadeias de caracteres que incluem espaços em branco ou pontuações obrigatórios causam falha nas regras de normalização porque estes caracteres são excluídos da cadeia de caracteres que serve como entrada para as regras de normalização. Se você tem cadeias de caracteres que incluem espaços em branco ou pontuações obrigatórios, é necessário modificá-las. Por exemplo, a cadeia de caracteres a seguir causaria falha na regra de normalização:
    
        \s*\(\s*\d\d\d\s*\)\s*\-\s*\d\d\d\s*\-\s*\d\d\d\d
    
    A cadeia de caracteres a seguir não causaria falha na regra de normalização:
    
        \s*\(?\s*\d\d\d\s*\)?\s*\-?\s*\d\d\d\s*\-?\s*\d\d\d\d

