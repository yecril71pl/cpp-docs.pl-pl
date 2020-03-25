---
title: Transferowanie kontroli
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: c9a46ccb1cf519080c5105855e41ecd3ebc23f77
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188054"
---
# <a name="transfers-of-control"></a>Transferowanie kontroli

Można użyć instrukcji **goto** lub etykiety **Case** w instrukcji **Switch** , aby określić program, który oddziałuje poza inicjatorem. Taki kod jest niedozwolony, chyba że deklaracja zawierająca inicjator znajduje się w bloku ujętym w blok, w którym występuje instrukcja skoku.

Poniższy przykład pokazuje pętlę, która deklaruje i inicjuje obiekty `total`, `ch`i `i`. Istnieje również błędna instrukcja **goto** , która przenosi formant poza inicjator.

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

W poprzednim przykładzie instrukcja **goto** próbuje przenieść kontrolkę poza inicjalizacją `i`. Jeśli jednak `i` zostały zadeklarowane, ale nie zainicjowano, transfer będzie dozwolony.

Obiekty `total` i `ch`, zadeklarowane w bloku, który służy jako *instrukcja* instrukcji **while** , są niszczone, gdy ten blok jest zakończony przy użyciu instrukcji **Break** .
