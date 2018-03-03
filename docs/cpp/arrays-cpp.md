---
title: Tablice (C++) | Dokumentacja firmy Microsoft
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
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b23727d7f6f5e8adcc220d57907a1d61f430bde3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="arrays-c"></a>Tablice (C++)
Tablica jest kolekcją jak w przypadku obiektów. Najprostszym przypadku tablicy jest wektorem, który może być deklarowana przez następująca sekwencja:  
  
```  
  
      decl-specifier identifier [ constant-expression ]  
decl-specifier identifier []  
decl-specifier identifer [][ constant-expression] . . .  
decl-specifier identifier [ constant-expression ]  
[ constant-expression ] . . .  
```  
  
 1. Specyfikator deklaracji:  
  
-   Specyfikator klasy magazynu opcjonalne.  
  
-   Opcjonalne **const** i/lub `volatile` specyfikatory.  
  
-   Nazwa typu elementu tablicy.  
  
 2. Deklarator:  
  
-   Identyfikator.  
  
-   Wyrażenie stałe typu całkowitego w nawiasach, **[].** Jeśli wiele wymiarów zadeklarowane za pomocą dodatkowe nawiasy, można pominąć stałego wyrażenia na pierwszy zestaw nawiasów.  
  
-   Opcjonalne dodatkowe nawiasy otaczające wyrażenia stałe.  
  
 3. Opcjonalne inicjatora.  Zobacz [inicjatory](../cpp/initializers.md).  
  
 Liczba elementów w tablicy jest podawany przez wyrażenie stałe. Pierwszy element w tablicy jest 0th element i jest ostatnim elementem (*n*-1) elementu, gdzie  *n*  jest liczba elementów tablicy może zawierać. *Wyrażenia* musi być typem całkowitym i musi być większa niż 0. Zerowy rozmiar tablicy jest dozwolony tylko wtedy, gdy tablica jest ostatnim polu `struct` lub **Unii** oraz gdy są włączone rozszerzenia Microsoft (/Ze).  
  
 Poniższy przykład przedstawia sposób definiowania tablicy w czasie wykonywania:  
  
```  
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
  
 Tablice typów pochodnych i w związku z tym mogą zostać utworzone na podstawie żadnego innego typu pochodnego lub podstawowych z wyjątkiem funkcji, odwołań, oraz `void`.  
  
 Tablice utworzone na podstawie tablic są tablice wielowymiarowe. Te tablice wielowymiarowe są określane przez umieszczenie wiele stałych wyrażeń w nawiasach kwadratowych w sekwencji. Rozważmy na przykład tej deklaracji:  
  
```  
int i2[5][7];  
```  
  
 Określa tablicę typu `int`, koncepcyjnie uszeregowanych w macierzy dwuwymiarowa pięć wierszy i kolumn siedmiu, jak pokazano na poniższej ilustracji:  
  
 ![Układ pojęć związanych z wieloma &#45; tablicą wielowymiarową](../cpp/media/vc38rc1.gif "vc38RC1")  
Koncepcyjny układ tablicy wielowymiarowej  
  
 W deklaracjach multidimensioned tablic, których listy inicjatorów (zgodnie z opisem w [inicjatory](../cpp/initializers.md)), można pominąć wyrażenie stałe, który określa granice wymiar. Na przykład:  
  
```  
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
  
 Poprzedniej deklaracji definiuje tablicę, która jest trzy wiersze przez cztery kolumny. Fabryki reprezentują wiersze i kolumny reprezentują rynkach, do których wysłać fabryk. Wartości są kosztów transportu z fabryki na rynku. Pierwszy wymiar tablicy pozostało, ale kompilator wypełnia ją znaleźć, sprawdzając inicjatora.  
  
 Tematy w tej sekcji:  
  
-   [Używanie tablic](../cpp/using-arrays-cpp.md)  
  
-   [Tablice w wyrażeniach](../cpp/arrays-in-expressions.md)  
  
-   [Interpretacja operatora indeksu dolnego](../cpp/interpretation-of-subscript-operator.md)  
  
-   [Pośrednie w typach tablic](../cpp/indirection-on-array-types.md)  
  
-   [Porządkowanie tablic C++](../cpp/ordering-of-cpp-arrays.md)  
  
## <a name="example"></a>Przykład  
 Techniki pominięcie specyfikacji granice wymiar tablicy wielowymiarowej można także w deklaracji funkcji w następujący sposób:  
  
```  
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
 Funkcja `FindMinToMkt` są zapisywane w taki sposób, że dodawanie nowych fabryki nie wymaga żadnych zmian kodu, po prostu ponownej kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 