---
title: "C3489 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3489
dev_langs: C++
helpviewer_keywords: C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b4a0115bbb6d00a4e83d0ae3343b1af1b8024002
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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