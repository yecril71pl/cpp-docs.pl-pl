---
title: "C3495 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3495
dev_langs: C++
helpviewer_keywords: C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8cf93a5de639ce0c8270ef374eabdedb6c6551bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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


