---
title: __noop | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __noop_cpp
- __noop
dev_langs: C++
helpviewer_keywords: __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7bdd595ac7fb70ef00865485a38e9d11cfd0181c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="noop"></a>__noop
**Dotyczące firmy Microsoft**  
  
 `__noop` Określa wewnętrzna funkcja należy ją ignorować i przeanalizowania listy argumentów, ale żaden kod można wygenerować dla argumentów. Jest on przeznaczone do użytku w funkcje globalne debugowania, w których zmienną liczbę argumentów.  
  
 Konwertuje kompilator `__noop` wewnętrznej na 0 w czasie kompilacji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `__noop`.  
  
```  
// compiler_intrinsics__noop.cpp  
// compile with or without /DDEBUG  
#include <stdio.h>  
  
#if DEBUG  
   #define PRINT   printf_s  
#else  
   #define PRINT   __noop  
#endif  
  
int main() {  
   PRINT("\nhello\n");  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)