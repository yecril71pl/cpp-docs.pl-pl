---
title: Return, instrukcja w zakończeniu programu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb594eb10e8068d5f5b3ed124d5e77b48ced728e
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947742"
---
# <a name="return-statement-in-program-termination-c"></a>return — instrukcja w zakończeniu działania programu (C++)
Wystawianie `return` instrukcji z **głównego** jest funkcjonalnym odpowiednikiem wywołania **wyjść** funkcji. Rozważmy następujący przykład:  
  
```cpp 
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 **Wyjść** i **zwracają** instrukcji w powyższym przykładzie są funkcjonalnie identyczny. Jednak C++ wymaga funkcji, które mają inne niż zwracane typy **void** zwracają wartość. **Zwracają** instrukcji umożliwia zwracanie wartości z `main`.  
  
## <a name="see-also"></a>Zobacz też  
 [Kończenie działania programu](../cpp/program-termination.md)