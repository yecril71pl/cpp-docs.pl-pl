---
title: "C3481 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3481
dev_langs:
- C++
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 316bf1e6bdbe3837c744642b61f1023566fd0095
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3481"></a>C3481 błąd kompilatora
"var": nie znaleziono zmiennej przechwytującej lambdę  
  
 Kompilator nie można odnaleźć definicji zmiennej, który został przekazany do listy przechwytywania wyrażenia lambda.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń zmienną z listy przechwytywania lambda wyrażenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3481, ponieważ zmienna `n` nie jest zdefiniowana:  
  
```  
// C3481.cpp  
  
int main()  
{  
   [n] {}(); // C3481  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)