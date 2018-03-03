---
title: "Instrukcja return Kończenie działania programu (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a9e97c0ee52094cd3f0ccbb36c0da8b3b04c630
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="return-statement-in-program-termination-c"></a>return — instrukcja w zakończeniu działania programu (C++)
Wystawianie `return` instrukcji z **głównego** jest funkcjonalnym odpowiednikiem wywołania **zakończyć** funkcji. Rozważmy następujący przykład:  
  
```  
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 **Zakończyć** i `return` instrukcje w powyższym przykładzie są funkcjonalnie identyczne. C++ wymaga jednak funkcje, które mają inne niż zwracanych typów `void` zwracają wartość. `return` Umożliwia zwrócona wartość **głównego**.  
  
## <a name="see-also"></a>Zobacz też  
 [Kończenie działania programu](../cpp/program-termination.md)