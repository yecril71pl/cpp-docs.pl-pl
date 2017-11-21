---
title: "Używanie tablic (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b77d561f0d33e86ef2e8c9c9fd009febd392281d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-arrays-c"></a>Używanie tablic (C++)
Dostęp do poszczególnych elementów w tablicy za pomocą operatora indeksu dolnego tablicy (`[ ]`). Jeśli jest tablicą jednowymiarową jest używany w wyrażeniu, która ma indeks nie, nazwa tablicy ocenia się na wskaźnik do pierwszego elementu w tablicy.  
  
```  
// using_arrays.cpp  
int main() {  
   char chArray[10];  
   char *pch = chArray;   // Evaluates to a pointer to the first element.  
   char   ch = chArray[0];   // Evaluates to the value of the first element.  
   ch = chArray[3];   // Evaluates to the value of the fourth element.  
}  
```  
  
 Użycie tablic wielowymiarowych, można używać różnych w wyrażeniach.  
  
```  
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
  
 W powyższym kodzie `multi` jest tablicą trójwymiarową typu `double`. `p2multi` Wskazuje wskaźnik do tablicy typu `double` rozmiaru trzech. W tym przykładzie tablicy jest używany z jednego, dwóch do trzech indeksów dolnych. Chociaż jest bardziej popularne, aby określić wszystkie indeksy dolne, podobnie jak w `cout` instrukcji, jest czasami warto wybrać konkretnego podzestawu elementów tablicy, jak pokazano w instrukcji, które należy wykonać `cout`.  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../cpp/arrays-cpp.md)