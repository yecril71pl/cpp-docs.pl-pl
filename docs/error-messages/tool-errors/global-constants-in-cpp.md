---
title: Stałe globalne w C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 3da61b7718dadba9b454ee079651ce6372f21756
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432620"
---
# <a name="global-constants-in-c"></a>Stałe globalne w C++

Stałe globalne w C++ ma połączenie static. Stanowi to odmianę C. Jeśli spróbujesz użyć globalną stałe języka C++ w wielu plikach wystąpi błąd nierozwiązane zewnętrznych. Kompilator optymalizuje stałe globalne, brakuje miejsca zarezerwowane dla zmiennej.

Jest jednym ze sposobów, aby rozwiązać ten problem do uwzględnienia inicjalizacje const w pliku nagłówkowym, a następnie dołączyć ten nagłówek w plikach CPP, gdy jest to konieczne, tak, jakby była prototypu funkcji. Inną możliwością jest ustaw dla zmiennej niestałe i używać stałe odwołanie, oceniając go.

Poniższy przykład spowoduje wygenerowanie C2019:

```
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

Następnie wyszukaj maszynę

```
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Zobacz też

[Błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)