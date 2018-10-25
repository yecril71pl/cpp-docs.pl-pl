---
title: Domyślne argumenty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48261d545737215ff44b1b56bb3b2d48839b6eb4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067062"
---
# <a name="default-arguments"></a>Argumenty domyślne

W wielu przypadkach funkcje mają argumenty, które są używane sporadycznie, który może wystarczyć wartość domyślną. Aby rozwiązać ten problem, funkcji argument domyślny umożliwia określenie tylko te argumenty funkcji powinny być opisowe w danym wywołania. Aby zilustrować to pojęcie, rozważmy przykład przedstawiony w [przeciążanie funkcji](../cpp/function-overloading.md).

```cpp
// Prototype three print functions.
int print( char *s );                  // Print a string.
int print( double dvalue );            // Print a double.
int print( double dvalue, int prec );  // Print a double with a
//  given precision.
```

W wielu aplikacjach uzasadnione domyślne mogą być podawane dla `prec`, eliminując konieczność łączenia się dwie funkcje:

```cpp
// Prototype two print functions.
int print( char *s );                    // Print a string.
int print( double dvalue, int prec=2 );  // Print a double with a
//  given precision.
```

Implementacja `print` funkcji jest nieznacznie zmienione w celu uwzględnienia faktów dla typu istnieje tylko jeden taki funkcja **double**:

```cpp
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

Aby wywołać nową `print` funkcji, użyj następującego kodu:

```cpp
print( d );    // Precision of 2 supplied by default argument.
print( d, 0 ); // Override default argument to achieve other
//  results.
```

Należy zwrócić uwagę te punkty, korzystając z domyślnych argumentów:

- Argumenty domyślne są używane tylko w przypadku wywołania funkcji, gdzie Opuszczono końcowe argumenty — muszą być ostatnie argumenty. W związku z tym poniższy kod jest niedozwolone:

    ```cpp
    int print( double dvalue = 0.0, int prec );
    ```

- Argument domyślny nie można ponownie zdefiniować w deklaracjach nowsze, nawet jeśli ponowne zdefiniowanie jest taka sama jak oryginalne. W związku z tym poniższy kod generuje błąd:

    ```cpp
    // Prototype for print function.
    int print( double dvalue, int prec = 2 );

    ...

    // Definition for print function.
    int print( double dvalue, int prec = 2 )
    {
    ...
    }
    ```

   Problem z tym kodem jest, że deklaracji funkcji w definicji redefiniuje argument domyślny dla `prec`.

- Argumenty domyślne dodatkowych można dodawać przez nowszy deklaracji.

- Argumenty domyślne można podać dla wskaźników do funkcji. Na przykład:

    ```cpp
    int (*pShowIntVal)( int i = 0 );
    ```