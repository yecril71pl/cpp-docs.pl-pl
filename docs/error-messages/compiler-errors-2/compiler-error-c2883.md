---
title: "C2883 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2883
dev_langs: C++
helpviewer_keywords: C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 28c2031c3e659099507a8e59758e27f364dd29b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2883"></a>C2883 błąd kompilatora
"Nazwa": deklaracja funkcji powoduje konflikt z identyfikatorem"" wynikające z deklaracją using  
  
 Próbowano więcej niż raz zdefiniować funkcję. Pierwsza definicja została wprowadzona w obszarze nazw o `using` deklaracji. Drugi był lokalnej definicji.  
  
 Poniższy przykład generuje C2883:  
  
```  
// C2883.cpp  
namespace A {  
   void z(int);  
}  
  
int main() {  
   using A::z;  
   void z(int);   // C2883  z is already defined  
}  
```