---
title: C3496 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3496
dev_langs:
- C++
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbc128c1e9a80c61ad42514827bbf8d47b693e84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3496"></a>C3496 błąd kompilatora
"this" jest zawsze przechwycone przez wartość: "&" ignorowane  
  
 Nie można przechwycić `this` wskaźnika przez odwołanie.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przechwyć `this` wskaźnika przez wartość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3496, ponieważ odwołanie do `this` wskaźnika jest wyświetlany na liście przechwytywania wyrażenia lambda:  
  
```  
// C3496.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      [&this] {}(); // C3496  
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)