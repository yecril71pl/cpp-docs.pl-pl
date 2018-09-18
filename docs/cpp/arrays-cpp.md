---
title: Tablice (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7c88c1d0f4096017b8ffc48a92143a63d229c5e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017914"
---
# <a name="arrays-c"></a>Tablice (C++)

Tablica jest zbiorem podobnych obiektów. Najprostszym przypadku tablicy jest wektor, który może być zdeklarowany przez poniższą sekwencję:

```
decl-specifier identifier [ constant-expression ]
decl-specifier identifier []
decl-specifier identifer [][ constant-expression] . . .
decl-specifier identifier [ constant-expression ]
[ constant-expression ] . . .
```

1. Specyfikator deklaracji:

- Specyfikator klasy magazynowania opcjonalne.

- Opcjonalnie **const** i/lub **volatile** specyfikatorów.

- Nazwa typu elementów tablicy.

2. Specyfikator:

- Identyfikator.

- Wyrażenie stałe typu Liczba całkowita ujęte w nawiasy kwadratowe, **[]**. Jeśli wiele wymiarów są deklarowane przy użyciu dodatkowe nawiasy, można pominąć wyrażenie stałe na pierwszy zestaw nawiasów.

- Opcjonalne dodatkowe nawiasy zamykające stałe wyrażenia.

3. Opcjonalny inicjator.  Zobacz [inicjatory](../cpp/initializers.md).

Liczba elementów w tablicy jest podana przez wyrażenie stałe. Pierwszy element w tablicy jest elementem 0, a wartość ostatniego elementu wynosi (*n*-1) elementu, gdzie *n* jest liczba elementów tablicy mogą zawierać. *Wyrażenie_stałe* musi być typu całkowitego i musi być większa niż 0. Tablicą o rozmiarze zero jest legalna tylko wtedy, gdy tablica jest ostatnim polu **struktury** lub **Unii** i jeżeli są włączone rozszerzenia Microsoft (/Ze).

Poniższy przykład pokazuje, jak zdefiniować tablicę w czasie wykonywania:

```cpp
// arrays.cpp
// compile with: /EHsc
#include <iostream>

int main() {
   using namespace std;
   int size = 3, i = 0;

   int* myarr = new int[size];

   for (i = 0 ; i < size ; i++)
      myarr[i] = 10;

   for (i = 0 ; i < size ; i++)
      printf_s("myarr[%d] = %d\n", i, myarr[i]);

   delete [] myarr;
}
```

Tablice są typami pochodnymi i dlatego mogą być wykonany z żadnych innych pochodnego lub typu podstawowegoz wyjątkiem funkcji, odwołań, a **void**.

Tablice wykonane z innych tablic są tablicami wielowymiarowymi. Te Wielowymiarowe tablice są określone poprzez umieszczenie wielu stałych wyrażeń w nawiasach kwadratowych w sekwencji. Na przykład rozważmy tę deklarację:

```cpp
int i2[5][7];
```

Określa on tablicę typu **int**, koncepcyjnie ułożoną w dwuwymiarowej macierzy pięciu wierszy i siedmiu kolumn, jak pokazano na poniższej ilustracji:

![Koncepcyjny układ wielu&#45;tablicą wielowymiarową](../cpp/media/vc38rc1.gif "vc38RC1") koncepcyjny układ wielowymiarowej tablicy

W deklaracjach inicjującą tablic, które posiadają listę (zgodnie z opisem w [inicjatory](../cpp/initializers.md)), można pominąć wyrażenie stałe, które określają granice dla pierwszego wymiaru. Na przykład:

```cpp
// arrays2.cpp
// compile with: /c
const int cMarkets = 4;
// Declare a float that represents the transportation costs.
double TransportCosts[][cMarkets] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};
```

Poprzedzająca deklaracja określa tablicę składającą się z trzech wierszy i czterech kolumn. Wiersze reprezentują fabryki, a kolumny reprezentują rynki, na które fabryki dostarczają. Dopuszczalne wartości to koszt transportu z fabryk na rynki. Pierwszy wymiar tablicy jest wykluczony, ale kompilator wypełnia go poprzez zbadanie inicjatora.

Tematy w tej sekcji:

- [Używanie tablic](../cpp/using-arrays-cpp.md)

- [Tablice w wyrażeniach](../cpp/arrays-in-expressions.md)

- [Interpretacja operatora indeksu dolnego](../cpp/interpretation-of-subscript-operator.md)

- [Pośrednie w typach tablic](../cpp/indirection-on-array-types.md)

- [Porządkowanie tablic C++](../cpp/ordering-of-cpp-arrays.md)

## <a name="example"></a>Przykład

Technika pomijania specyfikacji powiązań dla pierwszego wymiaru wielowymiarowej tablicy może również służyć w deklaracjach funkcji w następujący sposób:

```cpp
// multidimensional_arrays.cpp
// compile with: /EHsc
// arguments: 3
#include <limits>   // Includes DBL_MAX
#include <iostream>

const int cMkts = 4, cFacts = 2;

// Declare a float that represents the transportation costs
double TransportCosts[][cMkts] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};

// Calculate size of unspecified dimension
const int cFactories = sizeof TransportCosts /
                  sizeof( double[cMkts] );

double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);

using namespace std;

int main( int argc, char *argv[] ) {
   double MinCost;

   if (argv[1] == 0) {
      cout << "You must specify the number of markets." << endl;
      exit(0);
   }
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);
   cout << "The minimum cost to Market " << argv[1] << " is: "
       << MinCost << "\n";
}

double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {
   double MinCost = DBL_MAX;

   for( int i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

## <a name="comments"></a>Komentarze

Funkcja `FindMinToMkt` są zapisywane w taki sposób, że dodanie nowych fabryk nie wymaga żadnych zmian w kodzie, tylko ponownej kompilacji.