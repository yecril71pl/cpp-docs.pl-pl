---
title: Stałe globalne w C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: cabe5e92a496181d60536d7274eca388aba5c068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195477"
---
# <a name="global-constants-in-c"></a>Stałe globalne w C++

C++stałe globalne mają połączenie statyczne. Jest to inne niż C. Jeśli spróbujesz użyć stałej globalnej w C++ programie w przypadku wielu plików, wystąpi błąd zewnętrzny. Kompilator optymalizuje stałe globalne, pozostawiając bez miejsca zarezerwowane dla zmiennej.

Jednym ze sposobów na rozwiązanie tego błędu jest dołączenie do pliku nagłówkowego inicjujących inicjalizacje i uwzględnienie tego nagłówka w plikach CPP, podobnie jak w przypadku prototypu funkcji. Kolejną możliwością jest, aby zmienna nie stała i używała stałego odwołania podczas jego oceniania.

Poniższy przykład generuje C2019:

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

a następnie

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Zobacz też

[Błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
