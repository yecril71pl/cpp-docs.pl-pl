---
title: Obiekty posiadają zasoby (RAII)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f86b484e-5a27-4c3b-a92a-dfaa5dd6d93a
ms.openlocfilehash: 5705fc1996343141b13e37d1267b2e8c981c1eba
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220429"
---
# <a name="objects-own-resources-raii"></a>Obiekty posiadają zasoby (RAII)

Upewnij się, że obiekty własnych zasobów. Ta zasada jest znany także jako "pozyskiwanie zasobów jest zainicjowanie" lub "RAII."

## <a name="example"></a>Przykład

Przekaż każdy obiekt "new" jako argumentu konstruktora do innego obiektu o nazwie, który jest właścicielem go (prawie zawsze unique_ptr).

```cpp
void f() {
    unique_ptr<widget> p( new widget() );
    my_class x( new widget() );
    // ...
} // automatic destruction and deallocation for both widget objects
  // automatic exception safety, as if "finally { p->dispose(); x.w.dispose(); }"
```

Zawsze od razu przekazania nowego zasobu do innego obiektu, który jest jego właścicielem.

```cpp
void g() {
    other_class y( OpenFile() );
    // ...
} // automatic closing and release for file resource
  // automatic exception safety, as if "finally { y.file.dispose(); }"
```

## <a name="see-also"></a>Zobacz także

[Witaj z powrotem w języku C++ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
