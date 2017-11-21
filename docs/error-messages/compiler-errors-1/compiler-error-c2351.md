---
title: "C2351 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2351
dev_langs: C++
helpviewer_keywords: C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 954b610ede6d00e1f9f4d0b3630c67566534355a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2351"></a>C2351 błąd kompilatora
przestarzała Inicjalizacja składni konstruktora C++  
  
 Na liście nowy styl inicjowania dla konstruktora musi jawnie nazwę każdego bezpośredniej klasie podstawowej, nawet jeśli jest ona tylko podstawowe klasy.  
  
 Poniższy przykład generuje C2351:  
  
```  
// C2351.cpp  
// compile with: /c  
class B {  
public:   
   B() : () {}   // C2351  
   B() {}   // OK  
};  
```