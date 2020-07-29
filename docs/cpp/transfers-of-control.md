---
title: Transferowanie kontroli
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: ef437d0a691ceff72485be1ff9584052f540031a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232186"
---
# <a name="transfers-of-control"></a>Transferowanie kontroli

Możesz użyć **`goto`** instrukcji lub **`case`** etykiety w **`switch`** instrukcji, aby określić program, który oddziałuje poza inicjatorem. Taki kod jest niedozwolony, chyba że deklaracja zawierająca inicjator znajduje się w bloku ujętym w blok, w którym występuje instrukcja skoku.

Poniższy przykład pokazuje pętlę, która deklaruje i inicjuje obiekty `total` , `ch` i `i` . Istnieje również błędne **`goto`** instrukcje, które przesyła kontrolkę poza inicjatorem.

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

W poprzednim przykładzie **`goto`** instrukcja próbuje przenieść kontrolkę poza inicjalizacją `i` . Jednakże jeśli `i` zostały zadeklarowane, ale nie zainicjowano, transfer będzie dozwolony.

Obiekty `total` i `ch` , zadeklarowane w bloku, który służy jako *instrukcja* **`while`** instrukcji, są niszczone, gdy ten blok jest zakończony przy użyciu **`break`** instrukcji.
