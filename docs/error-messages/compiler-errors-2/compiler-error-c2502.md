---
title: "C2502 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2502
dev_langs: C++
helpviewer_keywords: C2502
ms.assetid: affa0b86-15fc-4e17-b7f2-6aad4a3771c4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 396ec843c03843b506174308a5b548f50379c06f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2502"></a>C2502 błąd kompilatora
"identyfikator": zbyt wiele modyfikatorów dostępu dla klasy podstawowej  
  
 Klasa podstawowa ma więcej niż jeden modyfikator dostępu. Modyfikator dostępu tylko jeden (`public`, `private`, lub `protected`) jest dozwolone.  
  
 Poniższy przykład generuje C2502:  
  
```  
// C2502.cpp  
// compile with: /c  
class A { };  
class B { };  
class C : private public A { };   // C2502  
  
// OK  
class D : private A {};  
class E : public A, private B {};  
```