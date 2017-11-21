---
title: "C2267 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2267
dev_langs: C++
helpviewer_keywords: C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42385c64119acfb669c7420ad9d3ba18d6daf60b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2267"></a>C2267 błąd kompilatora
"Funkcja": funkcje statyczne w zakresie bloku są niedozwolone  
  
 Funkcja lokalna jest zadeklarowany jako `static`. Statyczne funkcje musi mieć zakresu globalnego.  
  
 Poniższy przykład generuje C2267:  
  
```  
// C2267.cpp  
static int func2();   // OK  
int main() {  
    static int func1();   // C2267  
}  
```