---
title: '&lt;param > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- param
- <param>
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
ms.openlocfilehash: d8ea4feddbe1ec2d5898f8ef698cc2d69d255933
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823299"
---
# <a name="ltparamgt"></a>&lt;param&gt;

\<Param > używany tag w komentarzu do deklaracji metody do opisania jeden z parametrów dla metody.

## <a name="syntax"></a>Składnia

```
<param name='name'>description</param>
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Nazwa parametru metody.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `name`.

*description*<br/>
Opis parametru.

## <a name="remarks"></a>Uwagi

Tekst dla \<param > będą wyświetlane w technologii IntelliSense, [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code)i w raporcie Web komentarzy kodu.

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```cpp
// xml_param_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_param_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <param name="Int1">Used to indicate status.</param>
   void MyMethod(int Int1) {
   }
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
