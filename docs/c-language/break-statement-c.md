---
title: break — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: c46173ceebd7291336c18d36203d1e4dc59ce46d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222007"
---
# <a name="break-statement-c"></a>break — instrukcja (C)

**`break`** Instrukcja kończy wykonywanie najbliższej otaczającej **`do`** , **`for`** , **`switch`** lub **`while`** instrukcji, w której występuje. Kontrolka przechodzi do instrukcji, która następuje po instrukcji zakończony.

## <a name="syntax"></a>Składnia

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przerwij**

**`break`** Instrukcja jest często używana do kończenia przetwarzania określonego przypadku w **`switch`** instrukcji. Brak otaczającej instrukcji iteracyjnej or **`switch`** generuje błąd.

W zagnieżdżonych instrukcjach **`break`** instrukcja kończy tylko **`do`** **`for`** instrukcję,, **`switch`** , lub, **`while`** która bezpośrednio należy do niej. Możesz użyć **`return`** instrukcji lub, **`goto`** Aby przenieść kontrolę w innym miejscu poza zagnieżdżoną strukturę.

Ten przykład ilustruje **`break`** instrukcję:

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

[Break, instrukcja](../cpp/break-statement-cpp.md)
