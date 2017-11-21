---
title: "C3704 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3704
dev_langs: C++
helpviewer_keywords: C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae48bc886aab0211063cc7a9c2e73f3c7bbdd368
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3704"></a>C3704 błąd kompilatora
"Funkcja": metoda vararg nie może wyzwalać zdarzeń  
  
 Podjęto próbę użycia [__event](../../cpp/event.md) na metoda vararg. Aby naprawić ten błąd, należy zastąpić `fireEvent(int i, ...)` wywołania z `fireEvent(int i)` wywołanie, jak pokazano w poniższym przykładzie kodu.  
  
 Poniższy przykład generuje C3704:  
  
```  
// C3704.cpp  
[ event_source(native) ]  
class CEventSrc {  
   public:  
      __event void fireEvent(int i, ...);   // C3704  
      // try the following line instead:  
      // __event void fireEvent(int i);  
};  
  
int main() {  
}  
```