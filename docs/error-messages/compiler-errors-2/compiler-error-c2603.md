---
title: "C2603 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2603
dev_langs: C++
helpviewer_keywords: C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0df12c25b1da2d28c2a6a2a9340817c989ae4b54
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2603"></a>C2603 błąd kompilatora  
  
> "*funkcja*": zbyt wiele bloku zakresem statycznych obiektów z konstruktorem/destruktorami w funkcji  
  
W wersji kompilatora Visual C++ przed Visual Studio 2015 lub gdy [/Zc:threadSafeInit-](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) określono opcję kompilatora, jest ograniczona do 31 liczby statycznych obiektów, które mogą mieć w widocznej zewnętrznie wbudowanej funkcji .  
  
Aby rozwiązać ten problem, zalecamy przyjęcie nowszą wersję zestawu narzędzi kompilatora Visual C++, lub jeśli to możliwe, Usuń /Zc:threadSafeInit-— opcja kompilatora. Jeśli nie jest to możliwe, należy wziąć pod uwagę łączenie statycznych obiektów. Jeśli obiekty są tego samego typu, rozważ użycie pojedynczą tablicę statycznych danego typu i odwołań do poszczególnych elementów członkowskich zgodnie z wymaganiami.
  
## <a name="example"></a>Przykład  
  
Poniższy kod generuje C2603 i przedstawia sposób rozwiązywanie problemu:  
  
```cpp  
// C2603.cpp  
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };  
extern inline void f1() {  
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;  
    static C C32;   // C2603 Comment this line out to avoid error  
}  
```
