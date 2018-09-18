---
title: Pimpl hermetyzacji w czasie kompilacji (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83b01a58745185499ac02a254a207fac2779be26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059007"
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

[Witamy z powrotem w C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)