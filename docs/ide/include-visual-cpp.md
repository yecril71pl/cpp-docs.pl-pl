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
ms.openlocfilehash: 95a336319861ef44f65f0573389f09c3e9a45573
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425850"
---
# <a name="ltincludegt-visual-c"></a>&lt;obejmują&gt; (Visual C++)

\<Obejmują > tag pozwala odwoływać się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa do wprowadzania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.  Na przykład, można użyć \<obejmują > Aby wstawić komentarze standardowy "standardowy", które są używane przez cały zespół lub firma.

## <a name="syntax"></a>Składnia

```
<include file='filename' path='tagpath' />
```

#### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa pliku zawierającego dokumentację. Nazwa pliku może być kwalifikowana przy użyciu ścieżki.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `filename`.

*tagpath*<br/>
Prawidłowe wyrażenie XPath wybierające żądany zestaw węzłów znajdujących się w pliku.

*Nazwa*<br/>
Określenie nazwy w tagu, który poprzedza komentarzy; `name` będzie miał `id`.

*id*<br/>
Identyfikator tagu, który poprzedza komentarze.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.

## <a name="remarks"></a>Uwagi

\<Obejmują > tag używa składni XML XPath. Zajrzyj do dokumentacji wyrażenie XPath sposoby dostosowywania za pomocą \<obejmują >.

Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

To jest przykład wieloplikowego. Pierwszy plik, który używa \<obejmują >, zawiera następujące komentarzy dokumentacji:

```cpp
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

```xml
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

```xml
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