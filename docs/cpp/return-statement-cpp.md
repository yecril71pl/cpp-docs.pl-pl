---
title: return — instrukcja (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: 6a1ed4f374f133abd0233826d1b58896d49576cf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225868"
---
# <a name="return-statement-c"></a>return — instrukcja (C++)

Kończy wykonywanie funkcji i zwraca kontrolę do funkcji wywołującej (lub systemu operacyjnego, Jeśli przeniesiesz kontrolę z `main` funkcji). Wykonanie wznowione w funkcji wywołującej w punkcie bezpośrednio po wywołaniu.

## <a name="syntax"></a>Składnia

```
return [expression];
```

## <a name="remarks"></a>Uwagi

`expression`Klauzula, jeśli jest obecna, jest konwertowana na typ określony w deklaracji funkcji, tak jak w przypadku wykonywania inicjalizacji. Konwersja z typu wyrażenia na **`return`** Typ funkcji może tworzyć obiekty tymczasowe. Aby uzyskać więcej informacji o tym, jak i kiedy obiekty tymczasowe są tworzone, zobacz [obiekty tymczasowe](../cpp/temporary-objects.md).

Wartość `expression` klauzuli jest zwracana do funkcji wywołującej. Jeśli wyrażenie zostanie pominięte, zwracana wartość funkcji jest niezdefiniowana. Konstruktory i destruktory oraz funkcje typu **`void`** nie mogą określać wyrażenia w **`return`** instrukcji. Funkcje wszystkich innych typów muszą określać wyrażenie w **`return`** instrukcji.

Gdy przepływ sterowania opuszcza blok zawierający definicję funkcji, wynik jest taki sam, jak gdyby **`return`** instrukcja bez wyrażenia została wykonana. Jest to nieprawidłowe dla funkcji, które są zadeklarowane jako zwracające wartość.

Funkcja może zawierać dowolną liczbę **`return`** instrukcji.

Poniższy przykład używa wyrażenia z **`return`** instrukcją, aby uzyskać największą z dwóch liczb całkowitych.

## <a name="example"></a>Przykład

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>Zobacz także

[Instrukcje skoku](../cpp/jump-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
