---
title: '&lt;Zwraca > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- returns C++ XML tag
- <returns> C++ XML tag
ms.assetid: 5e3b0ed9-838d-4953-a93e-76d2d0a19fb9
ms.openlocfilehash: 72a6ad05f3a78919b652f518d11814c3f95c5fd0
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823803"
---
# <a name="ltreturnsgt"></a>&lt;Zwraca&gt;

\<Zwraca > używany tag w komentarzu do deklaracji metody do opisywania wartości zwracanej.

## <a name="syntax"></a>Składnia

```
<returns>description</returns>
```

#### <a name="parameters"></a>Parametry

*description*<br/>
Opis wartość zwracaną.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```
// xml_returns_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_returns_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <returns>Returns zero.</returns>
   int GetZero() { return 0; }
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
