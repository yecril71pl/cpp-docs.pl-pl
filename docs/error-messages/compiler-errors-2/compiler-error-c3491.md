---
title: C3491 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bd856f50f3528b3895e4495215b2e479d8a424b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257296"
---
# <a name="compiler-error-c3491"></a>C3491 błąd kompilatora
"var": Przechwytywanie przez wartości nie można modyfikować w niemodyfikowalnym wyrażeniu lambda  
  
 Wyrażenie niemodyfikowalnym wyrażeniu lambda nie można zmodyfikować wartość zmiennej, która jest przechwytywany przez wartość.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Deklarowanie wyrażenia lambda za pomocą `mutable` — słowo kluczowe, lub  
  
-   Przekazanie zmiennej w odniesieniu do listy przechwytywania lambda wyrażenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3491, ponieważ zmienna przechwytywania modyfikuje treści wyrażenia lambda niemodyfikowalnym `m`:  
  
```  
// C3491a.cpp  
  
int main()  
{  
   int m = 55;  
   [m](int n) { m = n; }(99); // C3491  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa C3491 przez zadeklarowanie wyrażenia lambda za pomocą `mutable` — słowo kluczowe:  
  
```  
// C3491b.cpp  
  
int main()  
{  
   int m = 55;  
   [m](int n) mutable { m = n; }(99);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)