---
title: Typy liczb całkowitych o rozmiarze C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 037ff61dbe1d1d42d8b0c751fcdc83f01a8dd112
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101426"
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