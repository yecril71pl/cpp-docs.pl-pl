---
title: Tablice (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 176e358bd0217ac914eb4ee6079126d3f429b6dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184519"
---
# <a name="arrays-c"></a>Tablice (C++)

Tablica jest zbiorem podobnych obiektów. Najprostszym przypadku tablicy jest wektor, który może być zdeklarowany przez poniższą sekwencję:

> *Decl-specifier* *identyfikator* **\[** *wyrażenie_stałe* **]**<br/>
> *Decl-specifier* *identyfikator*  **\[]**<br/>
> *Decl-specifier* *identyfikator* **\[]\[** *wyrażenie_stałe* **]** . . .<br/>
> *Decl-specifier* *identyfikator* **\[** *wyrażenie_stałe* **]** **\[** *wyrażenie_stałe* **]** . . .

1. Specyfikator deklaracji:

   - Specyfikator klasy magazynowania opcjonalne.

   - Opcjonalnie **const** i/lub **volatile** specyfikatorów.

   - Nazwa typu elementów tablicy.

1. Specyfikator:

   - Identyfikator.

   - Wyrażenie stałe typu Liczba całkowita ujęte w nawiasy kwadratowe,  **\[]**. Jeśli wiele wymiarów są deklarowane przy użyciu dodatkowe nawiasy, można pominąć wyrażenie stałe na pierwszy zestaw nawiasów.

   - Opcjonalne dodatkowe nawiasy zamykające stałe wyrażenia.

1. Opcjonalny inicjator. Aby uzyskać więcej informacji, zobacz [inicjatory](../cpp/initializers.md).

Liczba elementów w tablicy jest podana przez *wyrażenie_stałe*. Pierwszy element w tablicy jest elementem 0, a wartość ostatniego elementu wynosi (*n*-1) elementu, gdzie *n* jest liczba elementów tablicy mogą zawierać. *Wyrażenie_stałe* musi być typu całkowitego i musi być większa niż 0. Tablicą o rozmiarze zero jest legalna tylko wtedy, gdy tablica jest ostatnim polu **struktury** lub **Unii** i jeżeli są włączone rozszerzenia Microsoft (/Ze).

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

![Koncepcyjny układ wielu&#45;tablicą wielowymiarową](../cpp/media/vc38rc1.gif "koncepcyjny układ wielu&#45;tablicą wielowymiarową") <br/>
Koncepcyjny układ tablicy wielowymiarowej

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
