---
title: BREAK — instrukcja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- break_cpp
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3679ad27683e5f7ff9a13f5b5021710f7894c04
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="break-statement-c"></a>break — instrukcja (C++)
`break` Instrukcji kończy wykonywanie najbliższej otaczającej pętli lub instrukcji warunkowej, w których występuje. Jeśli po końcu przerwanej instrukcji występuje kolejna, sterowanie przechodzi do niej.  
  
## <a name="syntax"></a>Składnia  
  
```  
break;  
```  
  
## <a name="remarks"></a>Uwagi  
 `break` z warunkowej używana jest instrukcja [przełącznika](../cpp/switch-statement-cpp.md) instrukcji i [czy](../cpp/do-while-statement-cpp.md), [dla](../cpp/for-statement-cpp.md), i [podczas](../cpp/while-statement-cpp.md) pętli instrukcje.  
  
 W `switch` instrukcji, `break` instrukcja powoduje, że program do uruchomienia następnej instrukcji poza `switch` instrukcji. Bez `break` instrukcji, co instrukcji z dopasowanej `case` etykiet na końcu `switch` instrukcji, w tym `default` klauzuli jest wykonywana.  
  
 W pętli `break` instrukcji kończy wykonywanie najbliższej otaczającej `do`, `for`, lub `while` instrukcji. Sterowanie przechodzi do instrukcji następującej po zakończonej, jeśli taka istnieje.  
  
 W zagnieżdżonych instrukcjach `break` instrukcji kończy się tylko `do`, `for`, `switch`, lub `while` instrukcji ograniczający natychmiast go. Można użyć `return` lub `goto` instrukcji do przekazywania kontroli z więcej głęboko zagnieżdżone struktury.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `break` instrukcji w `for` pętli.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    // An example of a standard for loop  
    for (int i = 1; i < 10; i++)  
    {  
        cout << i << '\n';  
        if (i == 4)  
            break;  
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
  
 Poniższy kod przedstawia sposób użycia `break` w `while` pętli i `do` pętli.  
  
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
  
 Poniższy kod przedstawia sposób użycia `break` w instrukcji switch. Należy użyć `break` w każdym przypadku, jeśli chcesz obsługiwać każdego przypadku oddzielnie; Jeśli nie używasz `break`, wykonanie kodu znajduje się za pośrednictwem dalej wielkość liter.  
  
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
 [Instrukcje skoku](../cpp/jump-statements-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [continue, instrukcja](../cpp/continue-statement-cpp.md)