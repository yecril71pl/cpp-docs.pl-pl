---
title: '&lt;c > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- <c>
helpviewer_keywords:
- <c> C++ XML tag
- c C++ XML tag
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
ms.openlocfilehash: 43e1417e5a749f2ea51346bbf6db235ba08a7bcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294775"
---
# <a name="ltcgt"></a>&lt;c&gt;

\<c > tag wskazuje, że tekst w opis powinien być oznaczony jako kod. Użyj [ \<kodu >](code-visual-cpp.md) aby wskazać wiele wierszy, jako kod.

## <a name="syntax"></a>Składnia

```
<c>text</c>
```

#### <a name="parameters"></a>Parametry

*Tekst*<br/>
Tekst, który chcesz oznaczyć jako kod.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```cpp
// xml_c_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_c_tag.xdc

/// Text for class MyClass.
class MyClass {
public:
   int m_i;
   MyClass() : m_i(0) {}

   /// <summary><c>MyMethod</c> is a method in the <c>MyClass</c> class.
   /// </summary>
   int MyMethod(MyClass * a) {
      return a -> m_i;
   }
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
