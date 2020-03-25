---
title: Argumenty domyślne
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function declarators
- functions [C++], default arguments
- declaring functions [C++], declarators
- default arguments
- arguments [C++], default
- defaults [C++], arguments
ms.assetid: d32cf516-05cb-4d4d-b169-92f5649fdfa2
ms.openlocfilehash: 0202aaca47964f8923aa57d84515dc70ae8c8a2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189549"
---
# <a name="default-arguments"></a>Argumenty domyślne

W wielu przypadkach funkcje mają argumenty, które są używane tak rzadko, że wystarcza wartość domyślna. Aby rozwiązać ten scenariusz, funkcja domyślnego argumentu zezwala na określenie tylko tych argumentów funkcji, które mają znaczenie w danym wywołaniu. Aby zilustrować to pojęcie, rozważmy przykład zaprezentowany w [przeciążeniu funkcji](../cpp/function-overloading.md).

```cpp
// Prototype three print functions.
int print( char *s );                  // Print a string.
int print( double dvalue );            // Print a double.
int print( double dvalue, int prec );  // Print a double with a
//  given precision.
```

W wielu aplikacjach można dostarczyć rozsądną wartość domyślną dla `prec`, eliminując konieczność stosowania dwóch funkcji:

```cpp
// Prototype two print functions.
int print( char *s );                    // Print a string.
int print( double dvalue, int prec=2 );  // Print a double with a
//  given precision.
```

Implementacja funkcji `print` jest nieco zmieniana w celu odzwierciedlenia faktu, że tylko jedna taka funkcja istnieje dla typu **Double**:

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

Aby wywołać nową funkcję `print`, należy użyć następującego kodu:

```cpp
print( d );    // Precision of 2 supplied by default argument.
print( d, 0 ); // Override default argument to achieve other
//  results.
```

Należy pamiętać o tych punktach przy użyciu domyślnych argumentów:

- Argumenty domyślne są używane tylko w wywołaniach funkcji, w których końcowe argumenty są pomijane — muszą być ostatnimi argumentami. W związku z tym następujący kod jest niedozwolony:

    ```cpp
    int print( double dvalue = 0.0, int prec );
    ```

- Nie można ponownie zdefiniować argumentu domyślnego w późniejszych deklaracjach, nawet jeśli zmiana definicji jest taka sama jak oryginalna. W związku z tym Poniższy kod generuje błąd:

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

   Problem z tym kodem polega na tym, że deklaracja funkcji w definicji ponownie definiuje domyślny argument dla `prec`.

- Dodatkowe argumenty domyślne mogą być dodawane przez późniejsze deklaracje.

- Dla wskaźników do funkcji można podać argumenty domyślne. Na przykład:

    ```cpp
    int (*pShowIntVal)( int i = 0 );
    ```
