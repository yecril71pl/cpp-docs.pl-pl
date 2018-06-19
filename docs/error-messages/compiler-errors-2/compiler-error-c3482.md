---
title: C3482 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3482
dev_langs:
- C++
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad7ea983d13f03add2772da173062b1ad5652d3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258637"
---
# <a name="compiler-error-c3482"></a>C3482 błąd kompilatora
"this" można użyć tylko jako przechwyt lambdy w obrębie funkcji niestatycznego elementu członkowskiego  
  
 Nie można przekazać `this` na liście przechwytywania wyrażenia lambda, które są zadeklarowane w statycznej metody lub funkcji globalnej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Konwertuj funkcji otaczającej Metoda niestatyczna lub  
  
-   Usuń `this` wskaźnika z listy przechwytywania lambda wyrażenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3482:  
  
```  
// C3482.cpp  
// compile with: /c  
  
class C  
{  
public:  
   static void staticMethod()  
   {  
      [this] {}(); // C3482  
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)