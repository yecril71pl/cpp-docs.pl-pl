---
title: "C2632 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2632
dev_langs: C++
helpviewer_keywords: C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c1af198d4949da112792c2bbddfac68a80d0daf4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2632"></a>C2632 błąd kompilatora
"type1", po której następuje "type2" jest niedozwolony  
  
 Ten błąd może być spowodowany brakuje kodu między dwoma specyfikatorze typu.  
  
 Poniższy przykład generuje C2632:  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003. `bool`jest teraz odpowiedniego typu. W poprzednich wersjach `bool` był typem typedef i identyfikatory można utworzyć o tej nazwie.  
  
 Poniższy przykład generuje C2632:  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 Aby rozwiązać ten problem, dzięki czemu kod jest nieprawidłowy w wersji Visual Studio .NET 2003 i Visual Studio .NET programu Visual C++, zmień identyfikator.