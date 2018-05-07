---
title: C3536 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f88e656b0d63b6a7a4d60ace2f4cd5e2347d188
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3536"></a>C3536 błąd kompilatora
"symbol": nie można użyć, zanim zostanie zainicjowany  
  
 Nie można używać symboli wskazanych, przed zainicjowaniem. W praktyce oznacza to, że zmienna nie może służyć do zainicjowania.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Można zainicjować zmiennej z samym sobą.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3536, ponieważ każda zmienna jest zainicjowana z samym sobą.  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Auto, słowo kluczowe](../../cpp/auto-keyword.md)