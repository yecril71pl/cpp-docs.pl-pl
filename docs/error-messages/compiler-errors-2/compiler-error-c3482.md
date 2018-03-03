---
title: "C3482 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3482
dev_langs:
- C++
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ff7a17d663be7168c5743838d782043d7c0ee92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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