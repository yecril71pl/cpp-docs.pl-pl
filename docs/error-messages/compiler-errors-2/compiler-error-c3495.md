---
title: C3495 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3495
dev_langs:
- C++
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7accbc422256abbd75d518acce72c522fbb67c14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253665"
---
# <a name="compiler-error-c3495"></a>C3495 błąd kompilatora
"var": przechwytywania lambda musi mieć automatycznym okresem magazynu  
  
 Nie można dokonać przechwytu zmiennej, która nie ma automatycznym okresem magazynu, takich jak zmienna, która jest oznaczony jako `static` lub `extern`.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Nie przekazuj `static` lub `extern` zmienną do listy przechwytywania lambda wyrażenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3495, ponieważ `static` zmiennej `n` pojawią się na liście przechwytywania wyrażenia lambda:  
  
```  
// C3495.cpp  
  
int main()  
{  
   static int n = 66;  
   [&n]() { return n; }(); // C3495  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)   


