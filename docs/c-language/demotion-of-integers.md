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

**3.2.1.2 ANSI** Wynik konwersji liczby całkowitej na krótszą cyfrę całkowitą lub wynik konwersji liczby całkowitej bez znaku do podpisanej liczby całkowitej o równej długości, jeśli wartość nie może być reprezentowana

Gdy liczba **całkowita jest** rzutowana na **krótką**lub **krótka** jest rzutowana na wartość `char`, są zachowywane najmniej znaczące bajty.

Na przykład ten wiersz

```
short x = (short)0x12345678L;
```

przypisuje wartość 0x5678 do `x`, a ten wiersz

```
char y = (char)0x1234;
```

przypisuje wartość 0x34 do `y`.

Gdy zmienne podpisane są konwertowane na niepodpisane i na odwrót, wzorce bitowe pozostają takie same. Na przykład rzutowanie-2 (0xFE) na wartość bez znaku daje 254 (również 0xFE).

## <a name="see-also"></a>Zobacz też

[Liczby całkowite](../c-language/integers.md)
