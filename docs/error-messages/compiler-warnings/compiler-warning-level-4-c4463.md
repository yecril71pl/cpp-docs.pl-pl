---
title: Kompilatora (poziom 4) ostrzeżenie C4463 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4463
dev_langs:
- C++
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c13e0a79c667ecedbf3fd065338892d3af9c2ee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294443"
---
# <a name="compiler-warning-level-4-c4463"></a>Kompilator C4463 ostrzegawcze (poziom 4)  
  
> przepełnienie; Przypisywanie *wartość* do pola bitowego, która może zawierać wartości z *low_value* do *high_value*  
  
Przypisane *wartość* znajduje się poza zakresem wartości, które mogą zawierać pola bitowego. Typy ze znakiem pola bitowego Użyj znaczących bitów symbol, więc jeśli *n* jest rozmiar pola bitowego zakresu -2 jest podpisem pól bitowych<sup>n-1</sup> 2<sup>n-1</sup>-1, gdy bez znaku pola bitowe mieć zakresu od 0 do 2<sup>n</sup>-1.  
  
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
