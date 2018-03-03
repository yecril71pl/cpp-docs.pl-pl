---
title: "C3532 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3532
dev_langs:
- C++
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b85baf8e2e53885b07758772d3328f70fe93b35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3532"></a>C3532 błąd kompilatora
'type': nieprawidłowe użycie słowa kluczowego "Auto"  
  
 Nie można zadeklarować wskazany typ z `auto` — słowo kluczowe. Na przykład nie można użyć `auto` typ zwracany — słowo kluczowe, aby zadeklarować tablicy lub metody.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że wyrażenie inicjujące daje prawidłowego typu.  
  
2.  Upewnij się, że użytkownik nie deklaruj tablicy lub typ zwrotny metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3532, ponieważ `auto` — słowo kluczowe nie mogą deklarować zwracanego typu metody.  
  
```  
// C3532a.cpp  
// Compile with /Zc:auto  
auto f(){}   // C3532  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3532, ponieważ `auto` — słowo kluczowe nie można zadeklarować tablicy.  
  
```  
// C3532b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int x[5];  
   auto a[5];            // C3532  
   auto b[1][2];         // C3532  
   auto y[5] = x;        // C3532  
   auto z[] = {1, 2, 3}; // C3532  
   auto w[] = x;         // C3532  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Auto, słowo kluczowe](../../cpp/auto-keyword.md)