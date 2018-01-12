---
title: "C3498 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3498
dev_langs: C++
helpviewer_keywords: C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d895c0dc40d94d6a8fcd567173e2d596e68e333
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3498"></a>C3498 błąd kompilatora
"var": nie można dokonać przechwytu zmiennej, która ma zarządzanego lub WinRTtype  
  
 Nie można dokonać przechwytu zmiennej, która ma typ zarządzany lub typem środowiska wykonawczego systemu Windows w wyrażeniu lambda.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przekaż zarządzanej lub zmiennej środowiska wykonawczego systemu Windows do listy parametrów wyrażenia lambda.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3498, ponieważ zmienna, która ma typ zarządzany pojawi się na liście przechwytywania wyrażenia lambda:  
  
```  
// C3498a.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [&s](String ^ r)   
      { return String::Concat(s, r); } (", World!"); // C3498  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa C3498 przez przekazanie zmiennej zarządzanych `s` do listy parametrów wyrażenia lambda:  
  
```  
// C3498b.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [](String ^ s, String ^ r)   
      { return String::Concat(s, r); } (s, ", World!");  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)