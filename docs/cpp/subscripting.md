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
ms.openlocfilehash: 8974f6619af462050fc8a02798fe44007ea928e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160895"
---
# <a name="subscripting"></a>Tworzenie indeksów dolnych

Operator indeksu dolnego ( **[]** ), podobnie jak operator wywołania funkcji, jest traktowany jako operator binarny. Operator indeksu dolnego musi być niestatyczną funkcją składową, która przyjmuje jeden argument. Ten argument może być dowolnego typu i wyznacza żądany indeks dolny tablicy.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak utworzyć wektor typu **int** , który implementuje sprawdzanie granic:

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

Gdy `i` osiągnie 10 w poprzednim programie, **operator []** wykryje, że jest używany indeks dolny z ograniczeniami i wygeneruje komunikat o błędzie.

Należy zauważyć, że **operator funkcji []** zwraca typ referencyjny. Powoduje to, że jest to wartość l, co pozwala na korzystanie z wyrażeń w indeksach po obu stronach operatorów przypisania.

## <a name="see-also"></a>Zobacz też

[Przeładowanie operatora](../cpp/operator-overloading.md)
