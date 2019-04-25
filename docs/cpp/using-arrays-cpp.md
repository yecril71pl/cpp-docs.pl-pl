---
title: Używanie tablic (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
ms.openlocfilehash: 7f7a987a2b4c18e59dd058ccfc4375c304188398
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152751"
---
# <a name="using-arrays-c"></a>Używanie tablic (C++)

Dostęp do poszczególnych elementów tablicy za pomocą operatora indeksu dolnej tablicy (`[ ]`). Jeśli Jednowymiarowa tablica jest używany w wyrażeniu, które nie posiada indeksu dolnego, nazwa tablicy ocenia do wskaźnika do pierwszego elementu w tablicy.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

Użycie tablic wielowymiarowych, można użyć różnych kombinacji w wyrażeniach.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

W poprzednim kodzie `multi` jest tablicą trójwymiarową typu **double**. `p2multi` Wskaźnik wskazuje na tablicę typu **double** o rozmiarze 3. W tym przykładzie tablica jest używana z jednym, dwoma i trzema indeksami dolnymi. Mimo że jest to bardziej powszechne, aby określić wszystkie indeksy dolne, jak w `cout` instrukcji, warto czasami wybrać określony podzbiór elementów tablicy, jak pokazano w następujących instrukcjach `cout`.

## <a name="see-also"></a>Zobacz także

[Tablice](../cpp/arrays-cpp.md)