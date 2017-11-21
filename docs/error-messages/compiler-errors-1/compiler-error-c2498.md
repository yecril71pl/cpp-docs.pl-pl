---
title: "C2498 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2498
dev_langs: C++
helpviewer_keywords: C2498
ms.assetid: 0839f12c-aaa4-4a02-bb33-7f072715dd14
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0324ebd2cb27e1d48221b72bec2caaea5c4fc698
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2498"></a>C2498 błąd kompilatora
"Funkcja": "novtable" można stosować do deklaracji lub definicji klasy  
  
 Ten błąd może być spowodowany za pomocą `__declspec(novtable)` przy użyciu funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2498:  
  
```  
// C2498.cpp  
// compile with: /c  
void __declspec(novtable) f() {}   // C2498  
class __declspec(novtable) A {};   // OK  
```