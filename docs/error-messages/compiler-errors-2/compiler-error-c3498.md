---
title: C3498 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3498
dev_langs:
- C++
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 913caa8fc73e5fe325a9d17a48b6c2b9ba641546
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254458"
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