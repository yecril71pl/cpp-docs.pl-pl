---
title: Typy liczb całkowitych o rozmiarze C
ms.date: 11/04/2016
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: 3ced46b401296045909f5c812ca09abd3a5887f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432100"
---
# <a name="c-sized-integer-types"></a>Typy liczb całkowitych o rozmiarze C

**Microsoft Specific**

Funkcje C firmy Microsoft obsługuje typy wielkości liczb całkowitych. 8-, 16-, 32- lub 64-bitową liczbę całkowitą zmiennych można zadeklarować za pomocą __int*n* wpisz specyfikator, gdzie *n* rozmiar w bitach zmiennej liczby całkowitej. Wartość *n* może być 8, 16, 32 lub 64. Poniższy przykład deklaruje jedną zmienną dla każdego z czterech typów liczb całkowitych o rozmiarze:

```
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Pierwsze trzy typy wielkości liczb całkowitych są synonimy dla typów ANSI, które mają taki sam rozmiar i są przydatne w przypadku pisania przenośny kod, który zachowuje się tak samo na wielu platformach. Należy pamiętać, że typ danych __int8 synonimem typu char \__int16 jest synonimem typu short, i \__int32 jest synonimem typu int. \__Int64 typu nie ma odpowiednika równoważne ANSI.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)