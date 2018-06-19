---
title: Kompilatora (poziom 1) ostrzeżenie C4750 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4750
dev_langs:
- C++
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ffe378f8d2466e702c90127e44f3b48831abf50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282447"
---
# <a name="compiler-warning-level-1-c4750"></a>Kompilator C4750 ostrzegawcze (poziom 1)
"identyfikator": funkcja zawierająca _alloca() została wbudowana w pętlę  
  
 Funkcja 'Identyfikator' powoduje rozszerzenie funkcji wbudowanej z [_alloca](../../c-runtime-library/reference/alloca.md) funkcję w pętlę, która może spowodować przepełnienie stosu podczas wykonywania pętli.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że funkcja 'Identyfikator' nie jest modyfikowany z [__forceinline](../../cpp/inline-functions-cpp.md) specyfikator.  
  
2.  Upewnij się, że funkcja 'Identyfikator' nie zawiera [_alloca](../../c-runtime-library/reference/alloca.md) funkcji, który jest zawarty w pętli.  
  
3.  Nie określaj [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [ox](../../build/reference/ox-full-optimization.md), lub [/Og](../../build/reference/og-global-optimizations.md) przełącznika kompilacji.  
  
4.  Miejsce [_alloca](../../c-runtime-library/reference/alloca.md) działać w [spróbuj-except — instrukcja](../../cpp/try-except-statement.md) który będzie przechwytywać przepełnienia stosu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przykładowy wywołania `MyFunction` w pętli, i `MyFunction` wywołania `_alloca` funkcji. `__forceinline` Modyfikator powoduje rozszerzenie funkcji wbudowanej z `_alloca` funkcji.  
  
```  
// c4750.cpp  
// compile with: /O2 /W1 /c  
#include <intrin.h>  
  
char * volatile newstr;  
  
__forceinline void myFunction(void) // C4750 warning  
{  
// The _alloca function does not require a __try/__except   
// block because the example uses compiler option /c.  
    newstr = (char * volatile) _alloca(1000);  
}  
  
int main(void)  
{  
    for (int i=0; i<50000; i++)  
       myFunction();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [_alloca](../../c-runtime-library/reference/alloca.md)