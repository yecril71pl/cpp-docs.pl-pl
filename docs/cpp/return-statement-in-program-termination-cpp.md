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
ms.openlocfilehash: 6c08edff8237462cbc2c55dc5541e3da663ed0a3
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461116"
---
# <a name="return-statement-in-program-termination-c"></a>return — instrukcja w zakończeniu działania programu (C++)
Wystawianie **zwracają** instrukcji z `main` jest funkcjonalnym odpowiednikiem wywołania `exit` funkcji. Rozważmy następujący przykład:  
  
```cpp 
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 `exit` i **zwracają** instrukcji w powyższym przykładzie są funkcjonalnie identyczny. Jednak C++ wymaga funkcji, które mają inne niż zwracane typy **void** zwracają wartość. **Zwracają** instrukcji umożliwia zwracanie wartości z `main`.  
  
## <a name="see-also"></a>Zobacz także  
 [Kończenie działania programu](../cpp/program-termination.md)