---
title: "C2681 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2681
dev_langs: C++
helpviewer_keywords: C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9978a520b4682e4e2c7c4856d4e42675be0ab901
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2681"></a>C2681 błąd kompilatora
'type': nieprawidłowy typ wyrażenia dla nazwy  
  
 Operator rzutowania próbował przekonwertować z nieprawidłowego typu. Na przykład, jeśli używasz [dynamic_cast](../../cpp/dynamic-cast-operator.md) operator można przekonwertować wyrażenia na typ wskaźnika, wyrażenie źródłowe musi być wskaźnikiem.  
  
 Poniższy przykład generuje C2681:  
  
```  
// C2681.cpp  
class A { virtual void f(); };  
  
void g(int i) {  
    A* pa;  
    pa = dynamic_cast<A*>(i);  // C2681  
}  
```