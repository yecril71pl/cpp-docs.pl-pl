---
title: '&lt;przykład&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
ms.openlocfilehash: 6fb6a83a170cfcf3e394ac8b0b15af869d6e59fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641639"
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