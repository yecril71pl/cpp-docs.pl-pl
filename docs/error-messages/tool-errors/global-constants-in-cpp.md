---
title: Stałe globalne w C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 2f0621f52fe445f8f2058ef902824ddc1f5e2bb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255433"
---
# <a name="global-constants-in-c"></a>Stałe globalne w C++

Stałe globalne w C++ ma połączenie static. Stanowi to odmianę C. Jeśli spróbujesz użyć globalną stałe języka C++ w wielu plikach wystąpi błąd nierozwiązane zewnętrznych. Kompilator optymalizuje stałe globalne, brakuje miejsca zarezerwowane dla zmiennej.

Jest jednym ze sposobów, aby rozwiązać ten problem do uwzględnienia inicjalizacje const w pliku nagłówkowym, a następnie dołączyć ten nagłówek w plikach CPP, gdy jest to konieczne, tak, jakby była prototypu funkcji. Inną możliwością jest ustaw dla zmiennej niestałe i używać stałe odwołanie, oceniając go.

Poniższy przykład spowoduje wygenerowanie C2019:

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

Następnie wyszukaj maszynę

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Zobacz także

[Błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)