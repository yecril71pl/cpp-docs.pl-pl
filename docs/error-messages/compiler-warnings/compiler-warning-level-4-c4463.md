---
title: "Kompilatora (poziom 4) ostrzeżenie C4463 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4463
dev_langs: C++
helpviewer_keywords: C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bc76019182c376decdd8658defb64dbf90dcfaa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4463"></a>Kompilator C4463 ostrzegawcze (poziom 4)  
  
> przepełnienie; Przypisywanie *wartość* do pola bitowego, która może zawierać wartości z *low_value* do *high_value*  
  
Przypisane *wartość* znajduje się poza zakresem wartości, które mogą zawierać pola bitowego. Typy ze znakiem pola bitowego Użyj znaczących bitów symbol, więc jeśli  *n*  jest rozmiar pola bitowego zakresu -2 jest podpisem pól bitowych<sup>n-1</sup> 2<sup>n-1</sup>-1, podczas pól bitowych unsigned mieć zakresu od 0 do 2<sup>n</sup>-1.  
  
## <a name="example"></a>Przykład  
  
W tym przykładzie generuje C4463, ponieważ próbuje on przypisać wartość 3 pola bitowego typu `int` o rozmiarze 2, która ma zakres od -2 do 1.  
  
Aby rozwiązać ten problem, można zmienić przypisaną wartość na coś dopuszczalnego zakresu. Jeśli pola bitowego jest przeznaczony do przechowywania wartości bez znaku z zakresu od 0 do 3, można zmienić typu deklaracji `unsigned`. Jeśli pole jest przeznaczony do przechowywania wartości w zakresie -4-3, można zmienić rozmiar pola bitowego do 3.  
  
```cpp  
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S { 
    int x : 2; // int type treats high-order bit as sign
}; 

int main() { 
    S s; 
    s.x = 3; // warning C4463: overflow; assigning 3 
    // to bit-field that can only hold values from -2 to 1 
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type 
    // to unsigned.
} 
```  
