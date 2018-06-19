---
title: Kompilatora (poziom 4) ostrzeżenie C4754 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4754
dev_langs:
- C++
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7f4e42d2e44a55c98abdcd5c3e723e2a9269a1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302857"
---
# <a name="compiler-warning-level-4-c4754"></a>Kompilator C4754 ostrzegawcze (poziom 4)
Reguły konwersji dla operacji arytmetycznych w porównaniu oznaczają, że jedna gałąź nie może zostać wykonana.  
  
 Ostrzeżenie C4754 zostanie wyświetlone, ponieważ wynik porównania jest zawsze taki sam. Oznacza to, że jednej z gałęzi warunku nie został wykonany, prawdopodobnie ponieważ wyrażenie całkowite skojarzony jest niepoprawny. Wada kodu często występuje w kontroli przeciążenia niepoprawna liczba całkowita architektur 64-bitowych.  
  
 Reguły konwersji całkowitą są złożone i istnieje wiele problemów niewielkie. Jako alternatywę do ustalania każdego ostrzeżenie C4754 można zaktualizować kodu w celu użycia [Biblioteka SafeInt](../../windows/safeint-library.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie generuje C4754:  
  
```cpp  
// C4754a.cpp  
// Compile with: /W4 /c  
#include "errno.h"  
  
int sum_overflow(unsigned long a, unsigned long b)   
{  
   unsigned long long x = a + b; // C4754  
  
   if (x > 0xFFFFFFFF)   
   {  
      // never executes!  
      return EOVERFLOW;  
   }  
   return 0;  
}  
```  
  
 Dodanie `a + b` może spowodować przepełnienie arytmetyczne, zanim wynik będzie upcast na wartość 64-bitowych i przypisaną do zmiennej 64-bitowych `x`. Oznacza to, że kontrola na `x` jest nadmiarowa i nigdy nie będzie catch przepełnienie. W takim przypadku kompilator emituje to ostrzeżenie:  
  
```Output  
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).  
```  
  
 Aby usunąć to ostrzeżenie, można zmienić w instrukcji przypisania do rzutowania argumentów operacji 8-bajtowych wartości:  
  
```cpp  
// Casting one operand is sufficient to force all the operands in   
// the addition be upcast according to C/C++ conversion rules, but  
// casting both is clearer.  
unsigned long long x =   
   (unsigned long long)a + (unsigned long long)b;  
```  
  
## <a name="example"></a>Przykład  
 Następna próbka generuje również C4754.  
  
```cpp  
// C4754b.cpp  
// Compile with: /W4 /c  
#include "errno.h"  
  
int wrap_overflow(unsigned long a)   
{  
   if (a + sizeof(unsigned long) < a) // C4754  
   {   
      // never executes!  
      return EOVERFLOW;  
   }  
   return 0;  
}  
```  
  
 `sizeof()` Operator zwraca `size_t`, którego rozmiar jest zależny od architektury. Przykładowy kod działa na 32-bitowej architektury gdzie `size_t` jest 32-bitowego typu. Jednakże w przypadku architektury 64-bitowych `size_t` jest 64-bitowego typu. Reguły konwersji dla liczb całkowitych oznaczają, że `a` jest rzutowany w górę do 64-bitową wartość w wyrażeniu `a + b < a` tak, jakby jego napisanych `(size_t)a + (size_t)b < (size_t)a`. Gdy `a` i `b` są 32-bitowych liczb całkowitych, operacja dodawania 64-bitowe nigdy nie może się przelewać i nigdy nie przechowuje ograniczenia. W związku z tym kod nigdy nie wykrywa nastąpiło przepełnienie liczby całkowitej na architektur 64-bitowych. W tym przykładzie powoduje, że kompilator Emituj to ostrzeżenie:  
  
```Output  
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).  
```  
  
 Powiadomienie komunikat ostrzegawczy jawnie zawierający wartości stałej 4 zamiast oryginalnej ciąg źródłowy — w czasie analizy ostrzeżenie napotka ataku kod `sizeof(unsigned long)` została przekonwertowana na stałą. W związku z tym należy śledzić dół wyrażenie, które w źródle kod jest powiązany z wartości stałej w komunikacie ostrzegawczym. Najbardziej typowe źródła kodu został rozpoznany jako stałe w C4754 komunikaty ostrzegawcze są takie jak wyrażenia `sizeof(TYPE)` i `strlen(szConstantString)`.  
  
 W takim przypadku stałego kodu wyglądać następująco:  
  
```cpp  
// Casting the result of sizeof() to unsigned long ensures  
// that all the addition operands are 32-bit, so any overflow   
// is detected by the check.  
if (a + (unsigned long)sizeof(unsigned long) < a)  
  
```  
  
 **Uwaga** numer wiersza określony w ostrzeżeń kompilatora jest ostatni wiersz instrukcji. W komunikat ostrzegawczy dotyczący złożonych instrukcji warunkowej, który jest rozłożona na wiele wierszy linii wad kodu może być kilka wierszy przed wierszem raportowana. Na przykład:  
  
```cpp  
unsigned long a;  
  
if (a + sizeof(unsigned long) < a || // incorrect check  
    condition1() ||   
    a == 0) {    // C4754 warning reported on this line  
         // never executes!  
         return INVALID_PARAMETER;  
}  
```