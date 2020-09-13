---
title: '&lt;wyjątek> (Komentarze w dokumentacji C++)'
ms.date: 11/04/2016
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: 7e4b2276ecf5f4f4c4c05b389eb98a0f572f8027
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042111"
---
# <a name="ltexceptiongt-tag"></a>&lt;&gt;tag wyjątku

\<exception>Tag pozwala określić, które wyjątki mogą być zgłaszane. Ten tag jest stosowany do definicji metody.

## <a name="syntax"></a>Składnia

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parametry

*członkiem*<br/>
Odwołanie do wyjątku, które jest dostępne w bieżącym środowisku kompilacji. Przy użyciu reguł wyszukiwania nazw kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member` .

Ujmij nazwę w pojedyncze lub podwójne cudzysłowy.

Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [\<see>](see-visual-cpp.md) .

*zharmonizowan*<br/>
Opis.

## <a name="remarks"></a>Uwagi

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

Kompilator MSVC podejmie próbę rozpoznania odwołań cref w jednym przejściu poprzez Komentarze do dokumentacji.  W związku z tym, w przypadku używania reguł wyszukiwania C++ symbol nie zostanie znaleziony przez kompilator, odwołanie zostanie oznaczone jako nierozwiązane. [\<seealso>](seealso-visual-cpp.md)Aby uzyskać więcej informacji, zobacz.

## <a name="example"></a>Przykład

```cpp
// xml_exception_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_exception_tag.dll
using namespace System;

/// Text for class EClass.
public ref class EClass : public Exception {
   // class definition ...
};

/// <exception cref="System.Exception">Thrown when... .</exception>
public ref class TestClass {
   void Test() {
      try {
      }
      catch(EClass^) {
      }
   }
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
