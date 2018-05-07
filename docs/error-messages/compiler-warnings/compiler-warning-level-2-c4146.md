---
title: Kompilatora (poziom 2) ostrzeżenie C4146 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4146
dev_langs:
- C++
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40a94d2aed0b455fda646214f4488c53045b7f6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4146"></a>Kompilator C4146 ostrzegawcze (poziom 2)
Jednoargumentowy minus operator zastosowany do typu unsigned, wynik nadal unsigned  
  
 Typy bez znaku może zawierać tylko nieujemnej wartości, więc jednoargumentowy minus (negacji) nie mają zwykle sensu, gdy jest stosowany do typu bez znaku. Zarówno argument i wynik jest ujemna.  
  
 W praktyce występuje to, gdy próbuje express wartość minimalna liczba całkowita, która jest -2147483648 programistę. Nie można zapisać tej wartości jako -2147483648, ponieważ wyrażenie jest przetwarzany w dwóch etapach:  
  
1.  Numer 2147483648 jest obliczane. Ponieważ jest większa niż wartość maksymalna liczba całkowita 2147483647, nie jest typem 2147483648 [int](../../c-language/integer-types.md), ale `unsigned int`.  
  
2.  Jednoargumentowy minus została zastosowana do wartości z wynikiem bez znaku, który występuje także być 2147483648.  
  
 Typ bez znaku wyniku może spowodować nieoczekiwane zachowanie. Jeśli zostanie użyty wynik porównania, a następnie niepodpisane porównania mogą być używane, na przykład w przypadku drugiego operandu `int`. W tej sekcji wyjaśniono, dlaczego program przykładzie poniżej drukuje tylko jeden wiersz.  
  
 Oczekiwano drugi wiersz `1 is greater than the most negative int`, nie jest drukowany, ponieważ `((unsigned int)1) > 2147483648` ma wartość false.  
  
 Można uniknąć C4146 przy użyciu int_min — z Limits.h —, który ma typ **podpisany int**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4146:  
  
```  
// C4146.cpp  
// compile with: /W2  
#include <stdio.h>  
  
void check(int i)   
{  
    if (i > -2147483648)   // C4146  
        printf_s("%d is greater than the most negative int\n", i);  
}  
  
int main()   
{  
    check(-100);  
    check(1);  
}  
```