---
title: Wskaźniki bazowe (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
ms.openlocfilehash: d1ef1ec98d718e408621f5303e809d09020d5719
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87190250"
---
# <a name="based-pointers-c"></a>Wskaźniki bazowe (C)

**Specyficzne dla firmy Microsoft**

[__based (odwołanie w C++)](../cpp/based-pointers-cpp.md)

W przypadku kompilatorów Microsoft 32-bit i 64-bitowy C, wskaźnik oparty jest 32-bitowego lub 64-bitowego przesunięcia z bazy wskaźnika "32-bit" lub "64-bit". Adresowanie na podstawie jest przydatne do wykonywania kontroli nad sekcjami, w których obiekty są przydzielane, co zmniejsza rozmiar pliku wykonywalnego i zwiększa szybkość wykonywania. Ogólnie rzecz biorąc, formularz służący do określania wskaźnika wskaźnikowego jest

> *Typ* **__based (** *podstawowy* **)** *deklarator*

Odmiana "na podstawie wskaźnika" na podstawie adresu umożliwia określenie wskaźnika jako podstawy. Wskaźnik na podstawie jest przesunięty do sekcji pamięci, zaczynając od początku wskaźnika, na którym jest oparta. Wskaźniki oparte na adresach wskaźnika są jedyną formą **`__based`** słowa kluczowego, które są prawidłowe w 32-bitowych i 64-bitowych kompilacjach. W takich kompilacjach są to 32-bitowe lub 64-bitowe przemieszczenia z bazy 32-bit lub 64-bit.

Jednym z nich użycia dla wskaźników opartych na wskaźnikach jest dla trwałych identyfikatorów, które zawierają wskaźniki. Lista połączona, która składa się ze wskaźników opartych na wskaźniku, może zostać zapisana na dysku, a następnie ponownie załadowana do innego miejsca w pamięci, przy czym pozostałe wskaźniki są prawidłowe.

Poniższy przykład przedstawia wskaźnik na podstawie wskaźnika.

```C
void *vpBuffer;

struct llist_t
{
    void __based( vpBuffer ) *vpData;
    struct llist_t __based( vpBuffer ) *llNext;
};
```

Do wskaźnika `vpBuffer` przypisano adres pamięci przydzielonej w późniejszym czasie w programie. Połączona lista zostanie przeniesiona względem wartości `vpBuffer` .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)
