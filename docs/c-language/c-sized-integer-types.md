---
title: Typy liczb całkowitych o rozmiarze C
ms.date: 11/04/2016
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: 136065466d3adb4017cf18f2baf8c3387ffbd035
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313301"
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

## <a name="see-also"></a>Zobacz także

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
