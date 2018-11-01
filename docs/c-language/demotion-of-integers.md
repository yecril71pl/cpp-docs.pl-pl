---
title: Zwężanie liczb całkowitych
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: 5dca8d414e7cf7dd04d405208ad6a86dd4372542
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480913"
---
# <a name="demotion-of-integers"></a>Zwężanie liczb całkowitych

**ANSI 3.2.1.2** wynik konwersji całkowitą liczbę całkowitą ze znakiem krótszy lub wynik konwersji liczbą całkowitą bez znaku na liczbę całkowitą ze znakiem o równej długości, jeśli wartość nie może być przedstawiony

Gdy **długie** liczba całkowita jest rzutowany na **krótki**, lub **krótki** jest rzutowany na `char`, najmniej znaczący bajtów są zachowywane.

Na przykład w tym wierszu

```
short x = (short)0x12345678L;
```

przypisuje wartość 0x5678 `x`, a ten wiersz

```
char y = (char)0x1234;
```

przypisuje wartość 0x34 `y`.

Wzorce bitowe podpisane zmienne są konwertowane na typy bez znaku i na odwrót, pozostają niezmienione. Na przykład rzutowanie -2 (0xFE) do wartości bez znaku daje 254 (również 0xFE).

## <a name="see-also"></a>Zobacz też

[Liczby całkowite](../c-language/integers.md)