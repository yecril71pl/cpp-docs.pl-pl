---
title: '&lt;przykład&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <example>
- example
dev_langs:
- C++
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e596d38b52e36c20c28eaab66e24805696865b17
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421664"
---
# <a name="ltexamplegt-visual-c"></a>&lt;przykład&gt; (Visual C++)

\<Przykład > należy określić przykładem przedstawiającym sposób użycia metody lub innego członka biblioteki. Często również wymagałoby to użycia [ \<kodu >](../ide/code-visual-cpp.md) tagu.

## <a name="syntax"></a>Składnia

```
<example>description</example>
```

#### <a name="parameters"></a>Parametry

*Opis elementu*<br/>
Opis przykładowego kodu.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```
// xml_example_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_example_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>
   /// GetZero method
   /// </summary>
   /// <example> This sample shows how to call the GetZero method.
   /// <code>
   /// int main()
   /// {
   ///    return GetZero();
   /// }
   /// </code>
   /// </example>
   static int GetZero() {
      return 0;
   }
};
```

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)