---
title: "C3210 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3210
dev_langs: C++
helpviewer_keywords: C3210
ms.assetid: c6e9d309-fabc-4e7d-b526-be20d9fe3f6a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f4825abf58b7c0277b3e7f00ce16bcd0d5b1df64
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3210"></a>C3210 błąd kompilatora
"type": deklaracja dostępu można stosować tylko do elementu członkowskiego klasy podstawowej  
  
 A [za pomocą deklaracji](../../cpp/using-declaration.md) została określona nieprawidłowo.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3210.  
  
```  
// C3210.cpp  
// compile with: /c  
struct A {  
protected:  
   int i;  
};  
  
struct B {  
   using A::i;   // C3210  
};  
  
struct C : public A {  
   using A::i;   // OK  
};  
```