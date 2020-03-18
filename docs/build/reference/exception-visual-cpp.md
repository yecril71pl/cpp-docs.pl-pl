---
title: '> &lt;wyjątku (C++ Komentarze do dokumentacji)'
ms.date: 11/04/2016
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: d56e0ce7c892cfd9fd909b5268043d77929bd43c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439862"
---
# <a name="ltexceptiongt"></a>&lt;wyjątek&gt;

Tag \<Exception > pozwala określić, które wyjątki mogą być zgłaszane. Ten tag jest stosowany do definicji metody.

## <a name="syntax"></a>Składnia

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parametry

*członkiem*<br/>
Odwołanie do wyjątku, które jest dostępne w bieżącym środowisku kompilacji. Przy użyciu reguł wyszukiwania nazw kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

Ujmij nazwę w pojedyncze lub podwójne cudzysłowy.

Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [\<see >](see-visual-cpp.md).

*zharmonizowan*<br/>
Opis.

## <a name="remarks"></a>Uwagi

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

Kompilator MSVC podejmie próbę rozpoznania odwołań cref w jednym przejściu poprzez Komentarze do dokumentacji.  W związku z tym, C++ w przypadku używania reguł odnośników nie znaleziono symbolu przez kompilator, odwołanie zostanie oznaczone jako nierozwiązane. Aby uzyskać więcej informacji, zobacz [\<seealso — >](seealso-visual-cpp.md) .

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

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](xml-documentation-visual-cpp.md)
