---
title: C2632 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3bc07c404a1f4d667045fdfea24009e7d20ad69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2632"></a>C2632 błąd kompilatora
"type1", po której następuje "type2" jest niedozwolony  
  
 Ten błąd może być spowodowany brakuje kodu między dwoma specyfikatorze typu.  
  
 Poniższy przykład generuje C2632:  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003. `bool` jest teraz odpowiedniego typu. W poprzednich wersjach `bool` był typem typedef i identyfikatory można utworzyć o tej nazwie.  
  
 Poniższy przykład generuje C2632:  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 Aby rozwiązać ten problem, dzięki czemu kod jest nieprawidłowy w wersji Visual Studio .NET 2003 i Visual Studio .NET programu Visual C++, zmień identyfikator.