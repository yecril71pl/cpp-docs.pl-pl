---
title: C3533 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3533
dev_langs:
- C++
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faaf53d08512559b86c95148bc93e7b3367d2b01
ms.sourcegitcommit: 3bb7c1c0ceeb8012418e2fff9ae5a7db0fff3877
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="compiler-error-c3533"></a>C3533 błąd kompilatora
'type': parametr nie może mieć typu zawierającego "auto"  
  
 Nie można zadeklarować parametru metody lub szablonu ze `auto` — słowo kluczowe Jeśli domyślna [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) — opcja kompilatora jest włączona.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń `auto` — słowo kluczowe z deklaracji parametru.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3533, ponieważ deklaruje on parametr funkcji z `auto` — słowo kluczowe i jest skompilowana przy użyciu **/Zc: Auto**.  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j) {} // C3533  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3533 w tryb C ++ 14, ponieważ deklaruje on parametr szablonu z `auto` — słowo kluczowe i jest skompilowana przy użyciu **/Zc: Auto**. (W języku C ++ 17, jest to prawidłowej definicji szablonu klasy z parametrem jednego szablonu bez typu, którego typ jest ustalane).
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C {}; // C3533  
```  
  
## <a name="see-also"></a>Zobacz też  
 [auto Keyword](../../cpp/auto-keyword.md)   
 [/Zc:auto (Dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)
