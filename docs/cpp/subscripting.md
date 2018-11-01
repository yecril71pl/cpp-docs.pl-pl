---
title: Tworzenie indeksów dolnych
ms.date: 11/04/2016
helpviewer_keywords:
- subscript operator [C++], overloaded
- arrays [C++], subscripting
- subscripting [C++]
- operators [C++], overloading
- operator overloading [C++], examples
- subscript operator
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
ms.openlocfilehash: 376cacc3f70995c271a29b741ad266049da45785
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527325"
---
# <a name="subscripting"></a>Tworzenie indeksów dolnych

Operator indeksu dolnego (**[**), takiej jak operator wywołania funkcji jest uznawany za operatora binarnego. Operator indeksu dolnego, musi być funkcją niestatycznej składowej, która przyjmuje jeden argument. Ten argument może być dowolnego typu i wyznacza indeks dolny tablicy żądaną.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób tworzenia wektorów typu **int** implementującej sprawdzanie granic:

```cpp
// subscripting.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class IntVector {
public:
   IntVector( int cElements );
   ~IntVector() { delete [] _iElements; }
   int& operator[](int nSubscript);
private:
   int *_iElements;
   int _iUpperBound;
};

// Construct an IntVector.
IntVector::IntVector( int cElements ) {
   _iElements = new int[cElements];
   _iUpperBound = cElements;
}

// Subscript operator for IntVector.
int& IntVector::operator[](int nSubscript) {
   static int iErr = -1;

   if( nSubscript >= 0 && nSubscript < _iUpperBound )
      return _iElements[nSubscript];
   else {
      clog << "Array bounds violation." << endl;
      return iErr;
   }
}

// Test the IntVector class.
int main() {
   IntVector v( 10 );
   int i;

   for( i = 0; i <= 10; ++i )
      v[i] = i;

   v[3] = v[9];

   for ( i = 0; i <= 10; ++i )
      cout << "Element: [" << i << "] = " << v[i] << endl;
}
```

```Output
Array bounds violation.
Element: [0] = 0
Element: [1] = 1
Element: [2] = 2
Element: [3] = 9
Element: [4] = 4
Element: [5] = 5
Element: [6] = 6
Element: [7] = 7
Element: [8] = 8
Element: [9] = 9
Array bounds violation.
Element: [10] = 10
```

## <a name="comments"></a>Komentarze

Gdy `i` osiągnie 10 poprzedni program **— operator []** wykryje, że liczbach indeksu jest używana i wysyła komunikat o błędzie.

Należy pamiętać, że funkcja **— operator []** zwraca typ odwołania. To powoduje, że do l wartością, co pozwala na korzystanie z indeksem wyrażeń po obu stronach operatory przypisania.

## <a name="see-also"></a>Zobacz także

[Przeładowanie operatora](../cpp/operator-overloading.md)