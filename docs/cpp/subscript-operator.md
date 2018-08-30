---
title: Operator indeksu dolnego [] | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '[]'
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb54752efb23db7599538e6dc2b71ea3bf5eb3a3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197338"
---
# <a name="subscript-operator-"></a>Operator indeksu dolnego]

## <a name="syntax"></a>Składnia

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>Uwagi

Wyrażenie przyrostkowe (który również może być wyrażeniem podstawowym) następuje operator indeksu dolnego **[**, określa indeksowanie tablicy.

Aby uzyskać informacje o zarządzanych tablic, zobacz [tablic](../windows/arrays-cpp-component-extensions.md).

Zwykle reprezentowany przez wartość *wyrażeniem przyrostkowym* jest wartością wskaźnika, takich jak identyfikator tablicy, a *wyrażenie* jest wartością całkowitą (w tym typy wyliczone). Jednakże, wszystko co jest wymagane składniowo tego jednego z wyrażeń jest typu wskaźnika i innych być typu całkowitego. Ten sposób może być wartością typu całkowitego *wyrażeniem przyrostkowym* położenie i wartość wskaźnika można w nawiasach w *wyrażenie* lub indeksu dolnego pozycji. Rozważmy następujący fragment kodu:

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

W powyższym przykładzie wyrażenie `nArray[2]` jest taka sama jak `2[nArray]`. Przyczyną jest to, że wynik wyrażenia indeksu dolnego `e1[e2]` jest nadawana przez:

`*((e2) + (e1))`

Adres uzyskane przez wyrażenie nie jest *e2* bajtów z adresu *e1*. Zamiast skalowania adres umożliwiające uzyskanie następny obiekt w tablicy *e2*. Na przykład:

```cpp
double aDbl[2];
```

Adresy `aDb[0]` i `aDb[1]` są od siebie 8 bajtów — rozmiar obiektu typu **double**. To skalowanie zgodnie z typem obiektu odbywa się automatycznie za pomocą języka C++ i jest zdefiniowany w [operatory addytywne](../cpp/additive-operators-plus-and.md) gdzie omówiono Dodawanie i odejmowanie argumentów operacji typu wskaźnika.

Wyrażenie indeksu dolnego może mieć wiele indeksów dolnych, jak pokazano poniżej:

*wyrażenie1* **[** *wyrażenie2* **] [** *expression3* **]** ...

Wyrażenia indeksu dolnego są skojarzone od lewej do prawej. Skrajnie po lewej stronie wyrażenia indeksu dolnego, *wyrażenie1* **[** *wyrażenie2* **]**, jest stosowana jako pierwsza. Adres, który jest wynikiem dodawania *wyrażenie1* i *wyrażenie2* stanowi wyrażenie wskaźnika; następnie *expression3* jest dodawany do tego wyrażenia wskaźnika w celu utworzenia nowego wyrażenia wskaźnika, i tak dalej, aż ostatniego wyrażenia indeksu dolnego został dodany. Operator pośredni (<strong>\*</strong>) są stosowane po ostatnim indeksem wyrażenie jest obliczane, chyba że wartość końcowego wskaźnika adresuje typ tablicowy.

Wyrażenia zawierające wiele indeksów dolnych odwołują się do elementów tablic wielowymiarowych. Tablica wielowymiarowa jest tablicą, której elementy są tablicami. Na przykład, pierwszy element tablicy trójwymiarowej jest tablicą z dwoma wymiarami. Poniższy przykład deklaruje i inicjuje proste dwuwymiarową tablicę znaków:

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

Pierwszy element tablicy jest element 0. Zakres tablicy C++ znajduje się w *tablicy*[0] Aby *tablicy*[*rozmiar* - 1]. Jednak język C++ obsługuje dodatnie i ujemne indeksy dolne. Ujemne indeksy dolne muszą mieścić się w granicach tablicy Jeśli tak się nie stanie, wyniki są nieprzewidywalne. Poniższy kod pokazuje indeksy dolne tablicy pozytywne i negatywne:

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

Ujemny indeks dolny w ostatnim wierszu może spowodować błąd czasu wykonywania, ponieważ wskazuje adres 256 **int** pozycji niższe pamięci niż punkt początkowy tablicy. Wskaźnik `midArray` jest inicjowany w środku `intArray`; jest zatem możliwe (ale niebezpiecznego) do użycia zarówno indeksy tablicy dodatnie i ujemne w nim. Błędy indeksu dolnego tablicy nie generują błędy czasu kompilacji, ale mogą przynieść nieprzewidywalne rezultaty.

Operator indeksu dolnego jest przemiennego. W związku z tym, wyrażenia *tablicy*[*indeksu*] i *indeksu*[*tablicy*] są gwarantowane jako równoważne, tak długo, jak indeks dolny nie jest przeciążony operator (zobacz [przeciążone operatory](../cpp/operator-overloading.md)). Pierwszy formularz jest najbardziej powszechną praktyką programowania, ale albo działa.

## <a name="see-also"></a>Zobacz także

[Wyrażenia przyrostków](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Tablice](../cpp/arrays-cpp.md)
[tablice jednowymiarowe](../c-language/one-dimensional-arrays.md)<br/>
[Tablice wielowymiarowe](../c-language/multidimensional-arrays-c.md)<br/>
