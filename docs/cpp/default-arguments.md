---
title: "Domyślne argumenty | Dokumentacja firmy Microsoft"
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
- arguments [C++], function
- function declarators
- functions [C++], default arguments
- declaring functions [C++], declarators
- default arguments
- arguments [C++], default
- defaults [C++], arguments
ms.assetid: d32cf516-05cb-4d4d-b169-92f5649fdfa2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88c341abab34595da58d435be28f50e86cb47403
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="default-arguments"></a>Argumenty domyślne
W wielu przypadkach funkcje mają argumenty, które są używane sporadycznie, który będzie wystarczająca wartość domyślną. Aby rozwiązać ten problem, funkcji domyślnego argumentu umożliwia określenie tylko te argumenty do funkcji, które powinny być opisowe w danym wywołania. W celu zilustrowania koncepcji, należy wziąć pod uwagę przedstawione w przykładzie [przeciążanie funkcji](../cpp/function-overloading.md).  
  
```  
// Prototype three print functions.  
int print( char *s );                  // Print a string.  
int print( double dvalue );            // Print a double.  
int print( double dvalue, int prec );  // Print a double with a  
//  given precision.  
```  
  
 W wielu aplikacjach uzasadnione domyślne można podać dla `prec`, eliminując konieczność dwie funkcje:  
  
```  
// Prototype two print functions.  
int print( char *s );                    // Print a string.  
int print( double dvalue, int prec=2 );  // Print a double with a  
//  given precision.  
```  
  
 Implementacja `print` funkcji jest nieco zmienione w celu uwzględnienia faktów dla typu istnieje tylko jeden taki funkcja **podwójne**:  
  
```  
// default_arguments.cpp  
// compile with: /EHsc /c  
  
// Print a double in specified precision.  
//  Positive numbers for precision indicate how many digits  
//  precision after the decimal point to show. Negative  
//  numbers for precision indicate where to round the number  
//  to the left of the decimal point.  
  
#include <iostream>  
#include <math.h>  
using namespace std;  
  
int print( double dvalue, int prec ) {  
   // Use table-lookup for rounding/truncation.  
   static const double rgPow10[] = {   
      10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 10E0,  
         10E1,  10E2,  10E3,  10E4, 10E5,  10E6  
   };  
   const int iPowZero = 6;  
   // If precision out of range, just print the number.  
   if( prec >= -6 && prec <= 7 )  
      // Scale, truncate, then rescale.  
      dvalue = floor( dvalue / rgPow10[iPowZero - prec] ) *  
      rgPow10[iPowZero - prec];  
   cout << dvalue << endl;  
   return cout.good();  
}  
```  
  
 Aby wywołać nowe `print` funkcji, należy użyć następującego kodu:  
  
```  
print( d );    // Precision of 2 supplied by default argument.  
print( d, 0 ); // Override default argument to achieve other  
//  results.  
```  
  
 Podczas korzystania z argumenty domyślne, należy uwzględnić następujące punkty:  
  
-   Argumenty domyślne są używane tylko w przypadku wywołania funkcji gdzie końcowe argumenty zostały pominięte — muszą być ostatnim argumentów. W związku z tym następujący kod jest niedozwolony:  
  
    ```  
    int print( double dvalue = 0.0, int prec );  
    ```  
  
-   Argument domyślny nie można ponownie zdefiniować w deklaracjach nowsze, nawet jeśli ponowna definicja jest identyczna jak oryginalne. W związku z tym poniższy kod tworzy błąd:  
  
    ```  
    // Prototype for print function.  
    int print( double dvalue, int prec = 2 );  
  
    ...  
  
    // Definition for print function.  
    int print( double dvalue, int prec = 2 )  
    {  
    ...  
    }  
    ```  
  
     Problem z tym kodem jest, że deklaracji funkcji w definicji ponownie definiuje domyślnego argumentu dla `prec`.  
  
-   Można dodać argumenty domyślne dodatkowe, nowsze deklaracji.  
  
-   Argumenty domyślne można podać dla wskaźników do funkcji. Na przykład:  
  
    ```  
    int (*pShowIntVal)( int i = 0 );  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 