---
title: Kompilatora (poziom 1) ostrzeżenie C4715 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4715
dev_langs:
- C++
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57bd7f86a06c060a469d31e5fbdfcfbd7afb8c80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283027"
---
# <a name="compiler-warning-level-1-c4715"></a>Kompilator C4715 ostrzegawcze (poziom 1)
"Funkcja": nie niewszystkie ścieżki kodu zwracają wartość  
  
 Określona funkcja potencjalnie nie może zwracać wartości.  
  
## <a name="example"></a>Przykład  
  
```  
// C4715a.cpp  
// compile with: /W1 /LD  
int func1( int i )  
{  
   if( i )  
   return 3;  // C4715 warning, nothing returned if i == 0  
}  
```  
  
 Aby uniknąć tego ostrzeżenia, należy zmodyfikować kod, tak aby wszystkie ścieżki przypisać wartość zwracaną funkcji:  
  
```  
// C4715b.cpp  
// compile with: /LD  
int func1( int i )  
{  
   if( i ) return 3;  
   else return 0;     // OK, always returns a value  
}  
```  
  
 Istnieje możliwość, że kod może zawierać wywołania funkcji, które nigdy nie powraca, jak w poniższym przykładzie:  
  
```  
// C4715c.cpp  
// compile with: /W1 /LD  
void fatal()  
{  
}  
int glue()  
{  
   if(0)  
      return 1;  
   else if(0)  
      return 0;  
   else  
      fatal();   // C4715  
}  
```  
  
 Ten kod również generuje ostrzeżenie, ponieważ wiadomo, że kompilator `fatal` nigdy nie zwraca. Aby uniknąć tego kodu generuje komunikat o błędzie, należy zadeklarować `fatal` przy użyciu [__declspec(noreturn)](../../cpp/noreturn.md).