---
title: Zwężanie liczb całkowitych
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: edfb8f03094c10cf0cf33b0eb799d5d822ac017d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234408"
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

## <a name="see-also"></a>Zobacz także

[Liczby całkowite](../c-language/integers.md)
