---
title: "C3480 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3480
dev_langs: C++
helpviewer_keywords: C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d84314d20ea00e880981e418c2b5b11008f74229
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3480"></a>C3480 błąd kompilatora
"var": zmienna przechwytująca lambdę musi być z otaczającego zakresu funkcji  
  
 Zmienna przechwytywania lambda nie pochodzi z otaczającego zakresu funkcji.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń zmienną z listy przechwytywania lambda wyrażenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3480, ponieważ zmienna `global` nie pochodzi z otaczającego zakresu funkcji:  
  
```  
// C3480a.cpp  
  
int global = 0;  
int main()  
{  
   [&global] { global = 5; }(); // C3480  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa C3480 przez usunięcie zmiennej `global` na liście przechwytywania wyrażenia lambda:  
  
```  
// C3480b.cpp  
  
int global = 0;  
int main()  
{  
   [] { global = 5; }();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)