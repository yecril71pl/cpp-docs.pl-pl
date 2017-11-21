---
title: "C3491 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3491
dev_langs: C++
helpviewer_keywords: C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 58458a1ab0b67eb4fa6d38d0be2fb38f6d7496eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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