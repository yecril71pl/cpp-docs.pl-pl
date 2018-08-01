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
ms.openlocfilehash: 30910f6850fc3728ee101ab0662638fdebcd3775
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405447"
---
# <a name="break-statement-c"></a>break — instrukcja (C++)
**Podziału** instrukcja kończy wykonywanie najbliższej otaczającej pętli lub instrukcji warunkowej, w której występuje. Jeśli po końcu przerwanej instrukcji występuje kolejna, sterowanie przechodzi do niej.  
  
## <a name="syntax"></a>Składnia  
  
```  
break;  
```  
  
## <a name="remarks"></a>Uwagi  
 **Podziału** instrukcja jest używane z zasad dostępu [Przełącz](../cpp/switch-statement-cpp.md) instrukcji i [czy](../cpp/do-while-statement-cpp.md), [dla](../cpp/for-statement-cpp.md), i [podczas](../cpp/while-statement-cpp.md) instrukcje pętli.  
  
 W **Przełącz** instrukcji **podziału** instrukcji powoduje, że program do uruchomienia następnej instrukcji poza **Przełącz** instrukcji. Bez **podziału** instrukcji, każda instrukcja z dopasowanej **przypadek** etykiet na końcu **Przełącz** instrukcji, w tym **domyślne**klauzuli, jest wykonywany.  
  
 W pętlach **podziału** instrukcja kończy wykonywanie najbliższej otaczającej **czy**, **dla**, lub **podczas** instrukcji. Sterowanie przechodzi do instrukcji następującej po zakończonej, jeśli taka istnieje.  
  
 W obrębie zagnieżdżonych instrukcji **podziału** kończy tylko instrukcję instrukcji **czy**, **dla**, **Przełącz**, lub **podczas**instrukcja, która bezpośrednio ją obejmuje. Możesz użyć **zwracają** lub **goto** instrukcję, aby przekazać sterowanie z głęboko zagnieżdżonych struktur.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia **podziału** instrukcji w **dla** pętli.  
  
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
  
 Poniższy kod przedstawia sposób użycia **podziału** w **podczas** pętli i **czy** pętli.  
  
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
  
 Poniższy kod przedstawia sposób użycia **podziału** w instrukcji switch. Należy użyć **podziału** w każdym przypadku, jeśli chcesz obsługiwać każde wystąpienie case oddzielnie; Jeśli nie używasz **podziału**, wykonanie kodu przejdzie do następnego wystąpienia case.  
  
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
 [Instrukcje skoku](../cpp/jump-statements-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [continue, instrukcja](../cpp/continue-statement-cpp.md)