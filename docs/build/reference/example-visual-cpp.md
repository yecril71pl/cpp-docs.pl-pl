---
title: '&lt;przykład > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
ms.openlocfilehash: 69e4ad8315948c9c77e99f6ebece4debbe3831b5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823295"
---
# <a name="ltexamplegt"></a>&lt;Przykład&gt;

\<Przykład > należy określić przykładem przedstawiającym sposób użycia metody lub innego członka biblioteki. Często również wymagałoby to użycia [ \<kodu >](code-visual-cpp.md) tagu.

## <a name="syntax"></a>Składnia

```
<example>description</example>
```

#### <a name="parameters"></a>Parametry

*description*<br/>
Opis przykładowego kodu.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

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

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
