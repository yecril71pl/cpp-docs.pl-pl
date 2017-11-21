---
title: "C3765 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3765
dev_langs: C++
helpviewer_keywords: C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 44311ab210a85b05d86eb48aebe8294c95bfb5ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3765"></a>C3765 błąd kompilatora
"event": nie można definiować zdarzenia w klasie/strukturze "type" oznaczonej jako event_receiver  
  
 Jeśli klasa jest oznaczona przy [event_receiver](../../windows/event-receiver.md) atrybut klasy nie może zawierać [__event](../../cpp/event.md) deklaracji.  
  
 Poniższy przykład generuje C3765:  
  
```  
// C3765.cpp  
[event_receiver(native)]  
struct ER2 {  
   __event void f();   // C3765  
   __event void b(int);   // C3765  
};  
```