---
title: "C2575 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2575
dev_langs: C++
helpviewer_keywords: C2575
ms.assetid: 9eb45706-37ef-4481-b373-6d193ba13634
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63e31d1cb3b6ebe7129510464732a37ae416da82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2575"></a>C2575 błąd kompilatora
"identyfikator": tylko funkcje Członkowskie i typy podstawowe mogą być wirtualne  
  
 Zadeklarowano globalnej funkcji lub klasy `virtual`. Jest to niedozwolone.  
  
 Poniższy przykład generuje C2575:  
  
```  
// C2575.cpp  
// compile with: /c  
virtual void func() {}   // C2575  
  
void func2() {}  
struct A {  
   virtual void func2(){}  
};  
```