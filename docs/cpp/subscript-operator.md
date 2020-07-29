---
title: Operator indeksu dolnego []
ms.date: 11/04/2016
f1_keywords:
- '[]'
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
ms.openlocfilehash: a4eb878a18aa38b7047104903d10d96d66cc6720
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231094"
---
# <a name="subscript-operator-"></a>Operator indeksu dolnego []

## <a name="syntax"></a>Składnia

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>Uwagi

Wyrażenie przyrostkowe (które może również być wyrażeniem podstawowym), po którym następuje Operator indeksu dolnego **[]**, określa indeksowanie tablicy.

Informacje o zarządzanych tablicach w języku C++/CLI można znaleźć w temacie [Arrays](../extensions/arrays-cpp-component-extensions.md).

Zazwyczaj wartość reprezentowana przez *wyrażenie przyrostkowe* jest wartością wskaźnika, taką jak identyfikator tablicy, a *wyrażenie* jest wartością całkowitą (w tym typy wyliczeniowe). Jednakże wszystkie wymagane syntaktycznie to, że jedno z wyrażeń jest typu wskaźnika, a drugi jako typ całkowity. W ten sposób wartość całkowita może znajdować się w pozycji *wyrażenia przyrostkowego* , a wartość wskaźnika może znajdować się w nawiasach w położeniu *wyrażenia* lub indeksu dolnego. Rozważmy następujący fragment kodu:

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

W poprzednim przykładzie wyrażenie `nArray[2]` jest identyczne z `2[nArray]` . Przyczyną jest to, że wynik wyrażenia indeksu dolnego `e1[e2]` jest określony przez:

`*((e2) + (e1))`

Adres objęty wyrażeniem nie jest bajtem *E2* z adresu *E1*. Zamiast tego adres jest skalowany w celu uzyskania następnego obiektu w tablicy *E2*. Na przykład:

```cpp
double aDbl[2];
```

Adresy `aDb[0]` i `aDb[1]` są 8-bajtowe niezależnie od siebie — rozmiar obiektu typu **`double`** . Skalowanie zależne od typu obiektu jest wykonywane automatycznie przez język C++ i zdefiniowane w [operatorach dodatków](../cpp/additive-operators-plus-and.md) , w których jest omówiona Dodawanie i odejmowanie operandów typu wskaźnika.

Wyrażenie indeksu dolnego może mieć wiele indeksów dolnych, jak pokazano poniżej:

*wyrażenie1* **[** *wyrażenie2* **] [** *expression3* **]** ...

Wyrażenia indeksu dolnego są skojarzone od lewej do prawej. Pierwszy wyrażenie indeksu dolnego, *wyrażenie1* **[** *wyrażenie2* **]**, jest oceniane jako pierwsze. Adres, który wynika z dodania elementu *wyrażenie1* i *wyrażenie2* tworzą wyrażenie wskaźnika; następnie *expression3* jest dodawany do tego wyrażenia wskaźnika, aby utworzyć nowe wyrażenie wskaźnika i tak dalej, aż do ostatniego wyrażenia indeksu dolnego. Operator pośredni ( <strong>\*</strong> ) jest stosowany po obliczeniu ostatniego wyrażenia indeksu dolnego, chyba że końcowa wartość wskaźnika odnosi się do typu tablicy.

Wyrażenia z wieloma indeksami dolnymi odnoszą się do elementów tablic wielowymiarowych. Tablica wielowymiarowa jest tablicą, której elementy są tablicami. Na przykład, pierwszy element tablicy trójwymiarowej jest tablicą z dwoma wymiarami. Poniższy przykład deklaruje i inicjuje prostą dwuwymiarową tablicę znaków:

```cpp
// expre_Subscript_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
#define MAX_ROWS 2
#define MAX_COLS 2

int main() {
  char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };
  for ( int i = 0; i < MAX_ROWS; i++ )
     for ( int j = 0; j < MAX_COLS; j++ )
        cout << c[ i ][ j ] << endl;
}
```

## <a name="positive-and-negative-subscripts"></a>Dodatnie i ujemne indeksy dolne

Pierwszy element tablicy to element 0. Zakres tablicy C++ pochodzi z *tablicy*[0] do *tablicy*[*size* -1]. Jednak język C++ obsługuje pozytywne i ujemne indeksy dolne. Ujemne indeksy dolne muszą być ujęte w granice tablicy; Jeśli tak nie jest, wyniki są nieprzewidywalne. Poniższy kod przedstawia pozytywne i negatywne indeksy tablicowe:

```cpp
#include <iostream>
using namespace std;

int main() {
    int intArray[1024];
    for (int i = 0, j = 0; i < 1024; i++)
    {
        intArray[i] = j++;
    }

    cout << intArray[512] << endl;   // 512

    cout << 257[intArray] << endl;   // 257

    int *midArray = &intArray[512];  // pointer to the middle of the array

    cout << midArray[-256] << endl;  // 256

    cout << intArray[-256] << endl;  // unpredictable, may crash
}
```

Ujemny indeks dolny w ostatnim wierszu może generować błąd czasu wykonywania, ponieważ wskazuje na adres 256 **`int`** pozycji niższych niż wartość początkowa tablicy. Wskaźnik `midArray` jest inicjowany do środka; z `intArray` tego względu jest możliwe (ale niebezpieczne), aby używać na nim indeksów tablicowych z wynikami negatywnymi i ujemnymi. Błędy w indeksie tablicy nie generują błędów czasu kompilacji, ale zwracają nieprzewidywalne wyniki.

Operator indeksu dolnego to komutatywna. W związku z tym operatory *Array*[*index*] i *index*[*Array*] są gwarantowane jako równoważne, tak długo, jak operator indeksu dolnego nie jest przeciążony (zobacz [operator przeciążony](../cpp/operator-overloading.md)). Pierwszy formularz jest najbardziej typowym sposobem kodowania, ale działa.

## <a name="see-also"></a>Zobacz także

[Wyrażenia przyrostkowe](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Macierze](../cpp/arrays-cpp.md)<br/>
[Tablice jednowymiarowe](../c-language/one-dimensional-arrays.md)<br/>
[Tablice wielowymiarowe](../c-language/multidimensional-arrays-c.md)<br/>
