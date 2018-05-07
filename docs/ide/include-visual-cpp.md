---
title: '&lt;obejmują&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- include
- <include>
dev_langs:
- C++
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4c1a75acb89d9510dd7f489e5d0d582611da8de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltincludegt-visual-c"></a>&lt;obejmują&gt; (Visual C++)
\<Obejmują > należy odwoływać się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa do wprowadzania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.  Na przykład można użyć \<obejmują > Wstaw komentarze standardowe "standardowy", które są używane w całym zespołu lub firmy.  
  
## <a name="syntax"></a>Składnia  
  
```  
<include file='filename' path='tagpath' />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku zawierającego w dokumentacji. Nazwa pliku może być kwalifikowany za pomocą ścieżki.  Nazwę należy ująć w cudzysłów pojedynczym lub podwójnym.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `filename`.  
  
 `tagpath`  
 Prawidłowe wyrażenie XPath, które wybiera żądany zestaw węzłów zawarte w pliku.  
  
 `name`  
 Określenie nazwy w tagu poprzedzający komentarze; `name` będzie mieć `id`.  
  
 `id`  
 Identyfikator znacznika poprzedzający komentarze.  Nazwę należy ująć w cudzysłów pojedynczym lub podwójnym.  
  
## <a name="remarks"></a>Uwagi  
 \<Obejmują > tag używa składni XML XPath. Zapoznaj się z dokumentacją XPath o sposobach dostosowywania za pomocą \<obejmują >.  
  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 To jest przykład wiele plików. Pierwszy plik, który używa \<obejmują >, zawiera następujące komentarzy dokumentacji:  
  
```  
// xml_include_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_include_tag.dll  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />  
public ref class Test {  
   void TestMethod() {  
   }  
};  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />  
public ref class Test2 {  
   void Test() {  
   }  
};  
```  
  
 Drugi plik, xml_include_tag.doc, zawiera następujące komentarzy dokumentacji:  
  
```  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a>Dane wyjściowe programu  
  
```  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>t2</name>  
    </assembly>  
    <members>  
        <member name="T:Test">  
            <summary>  
The summary for this type.  
</summary>  
        </member>  
        <member name="T:Test2">  
            <summary>  
The summary for this other type.  
</summary>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)