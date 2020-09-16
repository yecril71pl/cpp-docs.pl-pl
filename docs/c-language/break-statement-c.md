---
title: break — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: 5322f8cb5218882d891e2cd66704f9dbfd1bc149
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683471"
---
# <a name="break-statement-c"></a>break — instrukcja (C)

**`break`** Instrukcja kończy wykonywanie najbliższej otaczającej **`do`** , **`for`** , **`switch`** lub **`while`** instrukcji, w której występuje. Kontrolka przechodzi do instrukcji, która następuje po instrukcji zakończony.

## <a name="syntax"></a>Składnia

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przerwij**

**`break`** Instrukcja jest często używana do kończenia przetwarzania określonego przypadku w **`switch`** instrukcji. Brak otaczającej instrukcji iteracyjnej or **`switch`** generuje błąd.

W zagnieżdżonych instrukcjach **`break`** instrukcja kończy tylko **`do`** **`for`** instrukcję,, **`switch`** , lub, **`while`** która bezpośrednio należy do niej. Możesz użyć **`return`** instrukcji lub, **`goto`** Aby przenieść kontrolę w innym miejscu poza zagnieżdżoną strukturę.

Ten przykład ilustruje **`break`** instrukcję:

```C
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
