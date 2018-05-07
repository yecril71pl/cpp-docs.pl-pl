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
ms.openlocfilehash: f184f0459e7ec2251d6ff34e2ee76559fe0dea42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3533"></a>C3533 błąd kompilatora
'type': parametr nie może mieć typu zawierającego "auto"  
  
 Nie można zadeklarować parametru metody lub szablonu ze `auto` — słowo kluczowe Jeśli domyślna [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) — opcja kompilatora jest włączona.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń `auto` — słowo kluczowe z deklaracji parametru.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3535, ponieważ deklaruje on parametr funkcji z `auto` — słowo kluczowe i jest skompilowana przy użyciu **/Zc: Auto**.  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3535, ponieważ deklaruje on parametr szablonu z `auto` — słowo kluczowe i jest skompilowana przy użyciu **/Zc: Auto**.  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## <a name="see-also"></a>Zobacz też  
 [auto Keyword](../../cpp/auto-keyword.md)   
 [/Zc:auto (Dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)