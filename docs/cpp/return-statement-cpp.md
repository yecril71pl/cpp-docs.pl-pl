---
title: "Return — instrukcja (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: return_cpp
dev_langs: C++
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: db65a7762659bfc71f7ef33dc9f8b9b732fda091
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="return-statement-c"></a>return — instrukcja (C++)
Kończy wykonywanie funkcji i zwraca sterowania do wywoływania funkcji (lub systemu operacyjnego w przypadku przenoszenia formantu z `main` funkcji). Wznawia wykonywanie w funkcji wywołującej w momencie bezpośrednio po wywołaniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
return [expression];  
```  
  
## <a name="remarks"></a>Uwagi  
 `expression` Klauzuli, jeśli istnieje, jest konwertowana na typ określony w deklaracji funkcji tak, jakby były wykonywane inicjowania. Konwersja z typu wyrażenia, aby `return` typu funkcji można utworzyć obiekty tymczasowe. Aby uzyskać więcej informacji dotyczących sposobu i czasu obiekty tymczasowe są tworzone, zobacz [obiekty tymczasowe](../cpp/temporary-objects.md).  
  
 Wartość `expression` klauzuli jest zwracana do wywoływania funkcji. Jeśli wyrażenie jest pominięty, zwracana wartość funkcji jest niezdefiniowany. Konstruktory i destruktory i funkcji typu `void`, nie można określić wyrażenie w `return` instrukcji. Funkcje innych typów musi określić wyrażenie w `return` instrukcji.  
  
 Podczas przepływu sterowania opuszcza blok, w definicji funkcji otaczającej, wynik jest taki sam, jak gdyby Jeśli `return` instrukcję bez wyrażenie ma zostało wykonane. To ustawienie jest nieprawidłowe dla funkcji, które są zadeklarowane jako zwracanie wartości.  
  
 Funkcja może mieć dowolną liczbę `return` instrukcje.  
  
 W poniższym przykładzie użyto wyrażenia z `return` instrukcji, aby uzyskać największy dwóch liczb całkowitych.  
  
## <a name="example"></a>Przykład  
  
```  
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