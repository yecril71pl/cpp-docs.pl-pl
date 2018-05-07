---
title: C3488 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3488
dev_langs:
- C++
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1f872e308c5c80e806ed13d94cd46fb27cdbd47
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3488"></a>C3488 błąd kompilatora
"var" nie jest dozwolona, gdy domyślny tryb przechwytywania odbywa się przez odwołanie  
  
 Po określeniu dla wyrażenia lambda domyślny tryb przechwytywania odbywa się przez odwołanie, nie można przekazać zmiennej w odniesieniu do klauzuli przechwytywania tego wyrażenia.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Nie są jawnie przekazywane zmienna klauzuli przechwytywania, lub  
  
-   Nie należy określać-reference jako domyślny tryb przechwytywania, lub  
  
-   Określ przez wartość jako domyślny tryb przechwytywania, lub  
  
-   Przekazanie przez wartość zmiennej, do klauzuli przechwytywania. (Może to zmianę zachowania wyrażenia lambda).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3488, ponieważ odwołanie do zmiennej `n` pojawia się w klauzuli przechwytywania wyrażenia lambda, którego domyślny tryb odbywa się przez odwołanie:  
  
```  
// C3488a.cpp  
  
int main()  
{  
   int n = 5;  
   [&, &n]() { return n; } (); // C3488  
}  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono cztery możliwe rozwiązania do C3488:  
  
```  
// C3488b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass &n to the capture clause.  
   [&]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-reference as the default capture mode.  
   [&n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-value as the default capture mode.  
   [=, &n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by value to the capture clause.  
   [n]() { return n; } ();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)