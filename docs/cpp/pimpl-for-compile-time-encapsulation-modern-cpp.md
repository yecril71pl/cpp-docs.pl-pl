---
title: Mechanizm pimpl hermetyzacji w czasie kompilacji (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: f1eb06ad3a52be486f085babf699677951b1ee71
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245176"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Mechanizm pimpl hermetyzacji w czasie kompilacji (Modern C++)

*Mechanizm pimpl hermetyzacji idiom* jest nowoczesnym C++ techniką do ukrycia implementacji, minimalizowania sprzęgu i oddzielenia interfejsów. Mechanizm pimpl hermetyzacji jest krótkie dla "wskaźnika do implementacji". Użytkownik może już znać koncepcję, ale znać inne nazwy, takie jak Cheshire Cat lub kompilator idiom.

## <a name="why-use-pimpl"></a>Dlaczego warto używać Mechanizm pimpl hermetyzacji?

Oto, jak Mechanizm pimpl hermetyzacji idiom może ulepszyć cykl programowania oprogramowania:

- Minimalizacja zależności kompilacji.

- Rozdzielenie interfejsu i implementacji.

- Przenośność.

## <a name="pimpl-header"></a>Mechanizm pimpl hermetyzacji — nagłówek

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

Mechanizm pimpl hermetyzacji idiom pozwala uniknąć ponownego kompilowania kaskad i układów obiektów kruchy. Jest to dobrze dostosowane do popularnych typów (przechodnie).

## <a name="pimpl-implementation"></a>Implementacja Mechanizm pimpl hermetyzacji

Zdefiniuj klasę `impl` w pliku CPP.

```cpp
// my_class.cpp
class my_class::impl {  // defined privately here
  // ... all private data and functions: all of these
  //     can now change without recompiling callers ...
};
my_class::my_class(): pimpl( new impl )
{
  // ... set impl values ...
}
```

## <a name="best-practices"></a>Najlepsze praktyki

Weź pod uwagę, czy dodać obsługę niezgłaszanej specjalizacji wymiany.

## <a name="see-also"></a>Zobacz także

[Zapraszamy ponownie doC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
