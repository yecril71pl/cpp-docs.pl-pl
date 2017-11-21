---
title: "C3231 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3231
dev_langs: C++
helpviewer_keywords: C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5d3cf8747f25fdccda1467e894f95d8bcfb3525c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3231"></a>C3231 błąd kompilatora
"argument": argument typu szablonu nie można użyć parametru typu ogólnego  
  
 Szablony są tworzone w czasie kompilacji, ale typy ogólne są tworzone w czasie wykonywania. W związku z tym nie jest możliwe do generowania kodu ogólnego, który można wywołać szablonu, ponieważ szablon nie można utworzyć wystąpienia w czasie wykonywania, gdy finally jest znany typu ogólnego.  
  
 Poniższy przykład generuje C3231:  
  
```  
// C3231.cpp  
// compile with: /clr /LD  
template <class T> class A;  
  
generic <class T>  
ref class C {  
   void f() {  
      A<T> a;   // C3231  
   }  
};  
```