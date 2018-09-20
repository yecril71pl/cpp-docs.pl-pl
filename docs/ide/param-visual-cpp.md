---
title: '&lt;param&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- param
- <param>
dev_langs:
- C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94382cb1f2bab59fae6c397f8ad6dadee221c96b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434846"
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)

\<Param > używany tag w komentarzu do deklaracji metody do opisania jeden z parametrów dla metody.

## <a name="syntax"></a>Składnia

```
<param name='name'>description</param>
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Nazwa parametru metody.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `name`.

*Opis elementu*<br/>
Opis parametru.

## <a name="remarks"></a>Uwagi

Tekst dla \<param > będą wyświetlane w technologii IntelliSense, [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code)i w raporcie Web komentarzy kodu.

Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

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

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)