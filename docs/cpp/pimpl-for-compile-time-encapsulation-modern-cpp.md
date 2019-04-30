---
title: Mechanizm pimpl hermetyzacji w czasie kompilacji (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: 6e114e2802dd4b2e5d1497867e2224be90c4752d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396109"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Mechanizm pimpl hermetyzacji w czasie kompilacji (Modern C++)

*Pimpl idiom* to technika nowoczesnego języka C++ do ukrywania implementacji, aby zminimalizować sprzężenia i do oddzielnych interfejsów. Pimpl jest skrót od "wskaźnik do implementacji." Może być już można zapoznać się z pojęciem, ale wiedzieć, przy użyciu innych nazw, takich jak idiom Cheshire Cat lub kompilatora zapory.

## <a name="why-use-pimpl"></a>Dlaczego warto używać pimpl?

Poniżej przedstawiono, jak poprawić pimpl idiom życia tworzenia oprogramowania:

- Minimalizacji zależności kompilacji.

- Oddzielenie interfejsu i implementacji.

- Przenośność.

## <a name="pimpl-header"></a>Nagłówek Pimpl

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

Pimpl idiom pozwala uniknąć kaskady ponownej kompilacji i kruchy obiektu układów. Dobrze nadaje się dla (przechodnio) popularnych typów.

## <a name="pimpl-implementation"></a>Implementacja Pimpl

Zdefiniuj `impl` klasy w pliku .cpp.

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

## <a name="best-practices"></a>Najlepsze rozwiązania

Należy rozważyć dodanie obsługi niezgłaszające specjalizacji wymiany.

## <a name="see-also"></a>Zobacz także

[Witaj z powrotem w języku C++ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
