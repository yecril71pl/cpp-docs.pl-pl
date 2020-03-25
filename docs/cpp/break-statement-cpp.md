---
title: break — instrukcja (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 23d31e1456106d5f82c4a13079c72c231b8477bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190485"
---
# <a name="break-statement-c"></a>break — instrukcja (C++)

Instrukcja **Break** zatrzymuje wykonywanie najbliższej otaczającej pętli lub instrukcji warunkowej, w której występuje. Jeśli po końcu przerwanej instrukcji występuje kolejna, sterowanie przechodzi do niej.

## <a name="syntax"></a>Składnia

```
break;
```

## <a name="remarks"></a>Uwagi

Instrukcja **Break** jest używana z instrukcją [Switch](../cpp/switch-statement-cpp.md) warunkowego [i z instrukcjami pętli do,](../cpp/do-while-statement-cpp.md) [for](../cpp/for-statement-cpp.md)i [while](../cpp/while-statement-cpp.md) .

W instrukcji **Switch** instrukcja **Break** powoduje, że program wykonuje następną instrukcję poza instrukcją **Switch** . Bez instrukcji **Break** wszystkie instrukcje od dopasowanej etykiety **Case** do końca instrukcji **Switch** , łącznie z klauzulą **default** , są wykonywane.

W pętlach instrukcja **Break** zatrzymuje wykonywanie najbliższej otaczającej instrukcji **Zrób**, **for**lub **while** . Sterowanie przechodzi do instrukcji następującej po zakończonej, jeśli taka istnieje.

W zagnieżdżonych instrukcjach **instrukcja break** przerywa tylko instrukcję do, **for**, **Switch**lub **while** **, która**bezpośrednio ją ujmuje. Można użyć instrukcji **Return** lub **goto** , aby przetransferować kontrolę z bardziej głęboko zagnieżdżonych struktur.

## <a name="example"></a>Przykład

Poniższy kod ilustruje sposób używania instrukcji **Break** w pętli **for** .

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

Poniższy kod ilustruje sposób używania instrukcji **Break** w pętli **while** **i pętli do** .

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

Poniższy kod pokazuje, jak używać **Break** w instrukcji switch. Należy używać **przerwy** w każdym przypadku, jeśli chcesz osobno obsługiwać poszczególne przypadki; Jeśli nie używasz **przerwy**, wykonanie kodu przechodzi do następnego przypadku.

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

## <a name="see-also"></a>Zobacz też

[Instrukcje skoku](../cpp/jump-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[continue, instrukcja](../cpp/continue-statement-cpp.md)
