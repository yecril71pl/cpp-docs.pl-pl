---
title: Wskaźniki bazowe (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
ms.openlocfilehash: e5d8c529adfb92c9db1fdcc5a38f688853606d5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327434"
---
# <a name="based-pointers-c"></a>Wskaźniki bazowe (C)

**Microsoft Specific**

[__based (C++ odwołania)](../cpp/based-pointers-cpp.md)

Kompilatory C Microsoft 32-bitowych i 64-bitowe wskaźnik bazowy jest 32-bitową lub 64-bitowe przesunięcie z 32-bitową lub 64-bitowego wskaźnika podstawowego. Adresowanie na podstawie jest przydatne w przypadku sprawowanie kontroli nad sekcje, w których obiekty są przydzielane, a tym samym zmniejszenie rozmiaru pliku wykonywalnego i zwiększyć szybkość realizacji. Ogólnie rzecz biorąc jest formularz do określania wskaźnik bazowy

> *Typ* **__based (** *podstawowy* **)** *deklaratora*

"Na podstawie wskaźnika" typ variant adresowania w oparciu o umożliwia specyfikację wskaźnika jako podstawy. Wskaźnik bazowy jest następnie przesunięcie do sekcji pamięci, zaczynając od początku wskaźnik, na którym bazuje. Wskaźniki oparte wskaźnikiem adresów są jedynymi `__based` — słowo kluczowe prawidłowy w kompilacjach kodu 32-bitowych i 64-bitowych. W takich kompilacje są 32-bitową lub 64-bitowych przemieszczanie od podstawy 32-bitową lub 64-bitowych.

Jednym z zastosowań wskaźniki oparte na wskaźnikach jest trwały identyfikatorów, które zawierają wskaźniki. Połączonej listy, która składa się z wskaźniki oparte na wskaźnik może można zapisywany na dysku, a następnie ponownie załadowany do innego miejsca w pamięci, za pomocą wskaźników pozostałe prawidłowe.

Poniższy przykład pokazuje wskaźnika, w oparciu o wskaźnik.

```C
void *vpBuffer;

struct llist_t
{
    void __based( vpBuffer ) *vpData;
    struct llist_t __based( vpBuffer ) *llNext;
};
```

Wskaźnik `vpBuffer` ma przypisany adres pamięci przydzielonej w pewnym momencie później w programie. Połączonej listy jest przenoszony z uwzględnieniem wartości `vpBuffer`.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)
