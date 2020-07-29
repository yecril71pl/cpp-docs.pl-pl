---
title: break — instrukcja (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 30ca602ecc65099adff7300f730c500a31fe0ed5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227611"
---
# <a name="break-statement-c"></a>break — instrukcja (C++)

**`break`** Instrukcja przerywa wykonywanie najbliższej otaczającej pętli lub instrukcji warunkowej, w której występuje. Jeśli po końcu przerwanej instrukcji występuje kolejna, sterowanie przechodzi do niej.

## <a name="syntax"></a>Składnia

```
break;
```

## <a name="remarks"></a>Uwagi

**`break`** Instrukcja jest używana z instrukcją warunkowego [Switch](../cpp/switch-statement-cpp.md) oraz z instrukcjami [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)i [while](../cpp/while-statement-cpp.md) .

W **`switch`** instrukcji instrukcja powoduje, **`break`** że program wykonuje następną instrukcję poza **`switch`** instrukcją. Bez **`break`** instrukcji wszystkie instrukcje od dopasowanej **`case`** etykiety do końca **`switch`** instrukcji, łącznie z **`default`** klauzulą, są wykonywane.

W pętlach **`break`** instrukcja przerywa wykonywanie najbliższej otaczającej **`do`** **`for`** instrukcji,, lub **`while`** . Sterowanie przechodzi do instrukcji następującej po zakończonej, jeśli taka istnieje.

W zagnieżdżonych instrukcjach **`break`** instrukcja zatrzymuje tylko **`do`** instrukcję, **`for`** , **`switch`** , lub, **`while`** która bezpośrednio należy do niej. Można użyć **`return`** instrukcji lub, **`goto`** Aby przetransferować kontrolę z bardziej głęboko zagnieżdżonych struktur.

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak używać **`break`** instrukcji w **`for`** pętli.

```cpp
#include <iostream>
using namespace std;

int main()
{
    // An example of a standard for loop
    for (int i = 1; i < 10; i++)
    {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }

    // An example of a range-based for loop
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

    for (int i : nums) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }
}
```

```Output
In each case:
1
2
3
```

Poniższy kod pokazuje, jak używać **`break`** w **`while`** pętli i **`do`** pętli.

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;

    while (i < 10) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    }

    i = 0;
    do {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    } while (i < 10);
}
```

```Output
In each case:
0123
```

Poniższy kod pokazuje, jak używać **`break`** w instrukcji switch. Należy używać **`break`** w każdym przypadku, jeśli chcesz osobno obsługiwać poszczególne przypadki; Jeśli nie używasz **`break`** , wykonanie kodu przechodzi do następnego przypadku.

```cpp
#include <iostream>
using namespace std;

enum Suit{ Diamonds, Hearts, Clubs, Spades };

int main() {

    Suit hand;
    . . .
    // Assume that some enum value is set for hand
    // In this example, each case is handled separately
    switch (hand)
    {
    case Diamonds:
        cout << "got Diamonds \n";
        break;
    case Hearts:
        cout << "got Hearts \n";
        break;
    case Clubs:
        cout << "got Clubs \n";
        break;
    case Spades:
        cout << "got Spades \n";
        break;
    default:
          cout << "didn't get card \n";
    }
    // In this example, Diamonds and Hearts are handled one way, and
    // Clubs, Spades, and the default value are handled another way
    switch (hand)
    {
    case Diamonds:
    case Hearts:
        cout << "got a red card \n";
        break;
    case Clubs:
    case Spades:
    default:
        cout << "didn't get a red card \n";
    }
}
```

## <a name="see-also"></a>Zobacz także

[Instrukcje skoku](../cpp/jump-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Continue — instrukcja](../cpp/continue-statement-cpp.md)
