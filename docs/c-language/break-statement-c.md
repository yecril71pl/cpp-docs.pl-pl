---
title: break — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: b38ff6c535c142bd15ea09a4d7c80010c3fff31f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313366"
---
# <a name="break-statement-c"></a>break — instrukcja (C)

`break` Instrukcja kończy wykonywanie najbliższej otaczającej `do`, `for`, `switch`, lub `while` instrukcji, w której występuje. Kontrola przechodzi do instrukcji następującej instrukcji zakończone.

## <a name="syntax"></a>Składnia

*Instrukcja skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przerwij;**

`break` Instrukcji jest często używany do zakończenia przetwarzania konkretnej wielkość liter w obrębie `switch` instrukcji. Brak otaczającego iteracji lub `switch` instrukcja generuje błąd.

W obrębie zagnieżdżonych instrukcji `break` kończy się tylko `do`, `for`, `switch`, lub `while` instrukcji, która bezpośrednio ją obejmuje. Możesz użyć `return` lub `goto` instrukcję, aby przekazać sterowanie w innym miejscu poza struktury zagnieżdżonej.

Ten przykład ilustruje `break` instrukcji:

```
#include <stdio.h>
int main() {
   char c;
   for(;;) {
      printf_s( "\nPress any key, Q to quit: " );

      // Convert to character value
      scanf_s("%c", &c);
      if (c == 'Q')
          break;
   }
} // Loop exits only when 'Q' is pressed
```

## <a name="see-also"></a>Zobacz także

[break, instrukcja](../cpp/break-statement-cpp.md)
