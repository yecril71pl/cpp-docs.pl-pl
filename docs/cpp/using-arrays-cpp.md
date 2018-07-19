---
title: Używanie tablic (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 980aaa5bf0b9472e8fb1c6d7f6b3c56aa255d00b
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947764"
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
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../cpp/arrays-cpp.md)