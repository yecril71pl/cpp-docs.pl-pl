---
title: "C3533 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3533
dev_langs: C++
helpviewer_keywords: C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b519a08080edb8dda37760bd826224657365afae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Auto — słowo kluczowe](../../cpp/auto-keyword.md)   
 [/ Zc: Auto (dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)