---
title: "C3612 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3612
dev_langs: C++
helpviewer_keywords: C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dd430c7dbdfae88d80e073fa9e624f123c41f366
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3612"></a>C3612 błąd kompilatora
"type": klasy zapieczętowanej nie mogą być abstrakcyjne  
  
Typy definiowane przy użyciu `value` są zapieczętowane domyślnie i klasa jest abstrakcyjna, o ile nie implementuje metody wszystkich jego elementów bazowych. Zapieczętowana klasa abstrakcyjna nie może być klasą podstawową nie może zostać utworzona.  
  
Aby uzyskać więcej informacji, zobacz [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C3612:  
  
```  
// C3612.cpp  
// compile with: /clr /c  
value struct V: public System::ICloneable {};   // C3612  
  
// OK  
value struct V2: public System::ICloneable {  
   Object^ Clone();  
};  
```