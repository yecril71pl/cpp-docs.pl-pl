---
title: Korzystanie z nazwy funkcji bez () nie tworzy kodu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c03706be0b9853cbbdebe79b58e410f7237692ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-function-name-without--produces-no-code"></a>Korzystanie z nazwy funkcji bez () nie tworzy kodu
W przypadku zadeklarowany w programie nazwy funkcji bez nawiasów kompilator nie tworzy kodu. Dzieje się tak niezależnie od tego, czy funkcja przyjmuje parametry, ponieważ kompilator oblicza adresu funkcji; Jednak ponieważ operator wywołania funkcji (")" nie jest obecny, nie wywołanie. Ten wynik jest podobny do następującego:  
  
```  
// compile with /Wall to generate a warning  
int a;  
a;      // no code generated here either  
```  
  
 W programie Visual C++ nawet za pomocą ostrzeżenie poziom 4 generuje nie diagnostycznych danych wyjściowych. Ostrzeżenie nie jest generowane; żaden kod jest generowany.  
  
 Poniższy przykładowy kod kompiluje (za pomocą ostrzeżenie) i łączy poprawnie bez błędów, ale nie tworzy kodu reference do `funcn( )`. Dla tego działał prawidłowo należy dodać operator wywołania funkcji (")".  
  
```  
#include <stdio.h>  
void funcn();  
  
int main() {  
   funcn;      /* missing function call operator;   
                  call will fail.  Use funcn() */  
   }  
  
void funcn() {  
   printf("\nHello World\n");  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja kodu](../../build/reference/optimizing-your-code.md)