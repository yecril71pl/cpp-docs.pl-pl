---
title: C3489 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3489
dev_langs:
- C++
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd620c969f89b1889384fe3f4d7f899957ae620b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3489"></a>C3489 błąd kompilatora
"var" jest wymagany, gdy domyślny tryb przechwytywania działa przez wartość  
  
 Po określeniu, czy domyślny tryb przechwytywania Wyrażenie lambda jest przez wartość, nie można przekazać zmiennej przez wartość do klauzuli przechwytywania tego wyrażenia.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Nie są jawnie przekazywane zmienna klauzuli przechwytywania, lub  
  
-   Nie określaj przez wartości jako domyślny tryb przechwytywania, lub  
  
-   Określ-reference jako domyślny tryb przechwytywania, lub  
  
-   W odniesieniu do klauzuli przechwytywania jest przekazanie zmiennej. (Może to zmianę zachowania wyrażenia lambda).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje zmiennej C3489 `n` pojawia się zgodnie z wartości w klauzuli przechwytywania wyrażenia lambda, której domyślnym trybem jest przez wartość:  
  
```  
// C3489a.cpp  
  
int main()  
{  
   int n = 5;  
   [=, n]() { return n; } (); // C3489  
}  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono cztery możliwe rozwiązania do C3489:  
  
```  
// C3489b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass n to the capture clause.  
   [=]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-value as the default capture mode.  
   [n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-reference as the default capture mode.  
   [&, n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by reference to the capture clause.  
   [&n]() { return n; } ();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)