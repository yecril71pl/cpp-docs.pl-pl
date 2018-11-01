---
title: Transferowanie kontroli
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: 1fc487628f26dcac097109bc71fa960e501d0797
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469644"
---
# <a name="transfers-of-control"></a>Transferowanie kontroli

Możesz użyć **goto** instrukcji lub **przypadek** etykiety w **Przełącz** instrukcję, aby określić program, który gałęzie ostatnie inicjatora. Taki kod jest niedozwolone, chyba że deklaracja, która zawiera inicjator jest w bloku ujęta w bloku, w której występuje instrukcja skoku.

Poniższy przykład pokazuje pętlę, która deklaruje i inicjuje obiekty `total`, `ch`, i `i`. Istnieje również błędne **goto** instrukcji, która przenosi sterowanie na ostatnie inicjatora.

```cpp
// transfers_of_control.cpp
// compile with: /W1
// Read input until a nonnumeric character is entered.
int main()
{
   char MyArray[5] = {'2','2','a','c'};
   int i = 0;
   while( 1 )
   {
      int total = 0;

      char ch = MyArray[i++];

      if ( ch >= '0' && ch <= '9' )
      {
         goto Label1;

         int i = ch - '0';
      Label1:
         total += i;   // C4700: transfers past initialization of i.
      } // i would be destroyed here if  goto error were not present
   else
      // Break statement transfers control out of loop,
      //  destroying total and ch.
      break;
   }
}
```

W powyższym przykładzie **goto** instrukcji spróbuje przekazać sterowanie ostatnie inicjowanie `i`. Jednak jeśli `i` zostały zadeklarowane, ale nie został zainicjowany, transfer będą prawnych.

Obiekty `total` i `ch`, zadeklarowanych w bloku, który służy jako *instrukcji* z **podczas** instrukcji, są niszczone, gdy tego bloku jest został zakończony, za pomocą  **podział** instrukcji.