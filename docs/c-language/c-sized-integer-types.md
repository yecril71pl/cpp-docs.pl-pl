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

**Specyficzne dla firmy Microsoft**

Funkcje Microsoft C obsługują typy liczb całkowitych. Można zadeklarować 8-, 16-, 32-lub 64-bitowe zmienne całkowite przy użyciu specyfikatora typu __int*n* , gdzie *n* jest rozmiarem zmiennej całkowitej w bitach. Wartość *n* może być 8, 16, 32 lub 64. Poniższy przykład deklaruje jedną zmienną dla każdego z czterech typów liczb całkowitych:

```
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Pierwsze trzy typy liczb całkowitych są synonimami dla typów ANSI, które mają ten sam rozmiar i są przydatne do pisania kodu przenośnego, który działa identycznie na wielu platformach. Zwróć uwagę, że typ danych __int8 jest synonimem typu char \_, _int16 jest synonimem typu short, \_a _int32 jest synonimem typu int. Typ \__int64 nie ma równoważnego odpowiednika ANSI.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
