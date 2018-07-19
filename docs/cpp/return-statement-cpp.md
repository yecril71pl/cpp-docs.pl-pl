---
title: Return — instrukcja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- return_cpp
dev_langs:
- C++
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aea9999adc7089499028850017a32245bba97db6
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947853"
---
# <a name="return-statement-c"></a>return — instrukcja (C++)
Kończy wykonywanie funkcji i przekazuje sterowanie do funkcji wywołującej (lub systemu operacyjnego w przypadku przenoszenia kontrolki z `main` funkcji). Wznawia wykonywanie w funkcji wywołującej w punkcie, w następującej natychmiast po wywołaniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
return [expression];  
```  
  
## <a name="remarks"></a>Uwagi  
 `expression` Klauzuli, jeśli jest obecny, jest konwertowany na typie określonym w deklaracji funkcji tak, jakby były wykonywane inicjowanie. Konwersja z typu wyrażenia do **zwracają** typ funkcji można tworzyć obiektów tymczasowych. Aby uzyskać więcej informacji na temat sposobu i czasu obiekty tymczasowe są tworzone, zobacz [obiekty tymczasowe](../cpp/temporary-objects.md).  
  
 Wartość `expression` klauzula jest zwracana do funkcji wywołującej. Jeśli wyrażenie jest pominięty, wartość zwracana funkcji jest niezdefiniowane. Konstruktory i destruktory i funkcji typu **void**, nie można określić wyrażenie w **zwracają** instrukcji. Funkcje wszystkich innych typów, należy określić wyrażenie w **zwracają** instrukcji.  
  
 Przepływ sterowania opuszcza blok otaczający definicji funkcji, wynik jest taka sama jak byłoby Jeśli **zwracają** miał została wykonana instrukcja bez wyrażenia. To ustawienie jest nieprawidłowe dla funkcji, które są zadeklarowane jako zwracanie wartości.  
  
 Funkcja może mieć dowolną liczbę **zwracają** instrukcji.  
  
 W poniższym przykładzie użyto wyrażenia z **zwracają** instrukcję, aby uzyskać największy dwóch liczb całkowitych.  
  
## <a name="example"></a>Przykład  
  
```cpp 
// return_statement2.cpp  
#include <stdio.h>  
  
int max ( int a, int b )  
{  
   return ( a > b ? a : b );  
}  
  
int main()  
{  
    int nOne = 5;  
    int nTwo = 7;  
  
    printf_s("\n%d is bigger\n", max( nOne, nTwo ));  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje skoku](../cpp/jump-statements-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)