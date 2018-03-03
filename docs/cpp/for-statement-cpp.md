---
title: "for — instrukcja (C++) | Dokumentacja firmy Microsoft"
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
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8358af0cd6784b1974767456602350a8ccf1c57f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="for-statement-c"></a>for — instrukcja (C++)
Wykonuje instrukcję wielokrotnie, dopóki warunek przestaje być prawdziwy. Aby uzyskać informacji na temat zakresu na podstawie instrukcji, zobacz [opartej na zakresie — instrukcja (C++)](../cpp/range-based-for-statement-cpp.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## <a name="remarks"></a>Uwagi  
 Użyj `for` instrukcji, aby utworzyć pętli, które należy wykonać określoną liczbę razy.  
  
 `for` Instrukcji składa się z trzech części opcjonalne, jak pokazano w poniższej tabeli.  
  
### <a name="for-loop-elements"></a>Elementy pętli for  
  
|Nazwa składni|Kiedy wykonywane|Opis|  
|-----------------|-------------------|-----------------|  
|`init-expression`|Przed wszystkie inne elementy **dla** instrukcji `init-expression` jest wykonywane tylko raz. Kontrola następnie przechodzi do `cond-expression`.|Często używane do zainicjowania indeksów pętli. Może zawierać wyrażenia lub deklaracje.|  
|`cond-expression`|Przed wykonaniem każdej iteracji `statement`, łącznie z pierwszej iteracji. `statement`jest wykonywane tylko wtedy, gdy `cond-expression` zwraca wartość true (różną od zera).|Wyrażenie obliczane do typu całkowitoliczbowego lub typu klasy, która ma jednoznaczną konwersję na typ całkowitoliczbowy. Normalnie używane do sprawdzania kryteriów zakończenia pętli for.|  
|`loop-expression`|Na koniec każdej iteracji `statement`. Po `loop-expression` jest wykonywane, `cond-expression` oceny.|Zwykle jest używane do zwiększania indeksów pętli.|  
  
 W poniższych przykładach pokazano różne sposoby stosowania `for` instrukcji.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main() {  
    // The counter variable can be declared in the init-expression.  
    for (int i = 0; i < 2; i++ ){   
       cout << i;  
    }  
    // Output: 01  
    // The counter variable can be declared outside the for loop.  
    int i;  
    for (i = 0; i < 2; i++){  
        cout << i;  
    }  
    // Output: 01  
    // These for loops are the equivalent of a while loop.  
    i = 0;  
    while (i < 2){  
        cout << i++;  
    }  
}  
    // Output: 012  
```  
  
 `init-expression`i `loop-expression` może zawierać wiele instrukcji rozdzielonych przecinkami. Na przykład:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
    int i, j;  
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {  
        cout << "i + j = " << (i + j) << '\n';  
    }  
}  
    // Output:  
    i + j = 15  
    i + j = 17  
    i + j = 19  
```  
  
 `loop-expression`może być zwiększany lub zmniejszany lub zmodyfikowany w inny sposób.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
for (int i = 10; i > 0; i--) {  
        cout << i << ' ';  
    }  
    // Output: 10 9 8 7 6 5 4 3 2 1  
    for (int i = 10; i < 20; i = i+2) {  
        cout << i << ' ';  
    }  
    // Output: 10 12 14 16 18  
```  
  
 A `for` kończy pętlę, gdy [podziału](../cpp/break-statement-cpp.md), [zwracać](../cpp/return-statement-cpp.md), lub [goto](../cpp/goto-statement-cpp.md) (etykietą instrukcji poza **dla** pętli) w `statement` jest wykonywana. A [kontynuować](../cpp/continue-statement-cpp.md) instrukcji w `for` pętli kończy bieżącą iterację.  
  
 Jeśli `cond-expression` jest pominięty, jest on uznawany za true i **dla** pętli nie zakończy się bez `break`, `return`, lub `goto` w `statement`.  
  
 Mimo że trzy pola `for` instrukcji są zwykle używane do inicjowania testowania dla zakończenia połączenia, i wzrastała, nie są ograniczone do tych zastosowań. Na przykład poniższy kod wyświetla cyfry od 0 do 4. W takim przypadku `statement` jest instrukcja o wartości null:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    int i;  
    for( i = 0; i < 5; cout << i << '\n', i++){  
        ;  
    }  
}  
```  
  
## <a name="for-loops-and-the-c-standard"></a>Pętle for i standard C++  
 C++ standard mówi, że zmiennej zadeklarowanej w `for` pętli stosuje się znaleźć poza zakresem po `for` kończy się w pętli. Na przykład:  
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 Domyślnie w obszarze [/Ze](../build/reference/za-ze-disable-language-extensions.md), Zmienna zadeklarowana w `for` pętli pozostaje w zakresie do `for` pętli do otaczającej kończy się w zakresie.  
  
 [/ Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) umożliwia standardowe zachowanie zmiennych zadeklarowanych na dla pętli, bez konieczności Określ /Za.  
  
 Istnieje również możliwość użycia zakresu różnic `for` pętli można ponownie zadeklarować zmienne w obszarze /Ze w następujący sposób:  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 Naśladuje to lepiej standardowe zachowanie zmiennej zadeklarowanej w `for` pętli, które wymaga zmiennych zadeklarowanych na `for` pętli po ukończeniu pętli się znaleźć poza zakresem. Jeśli zmienna jest zadeklarowana w `for` pętli, kompilator wewnętrznie wspiera go do zmiennej lokalnej w `for` pętli do otaczającej zakresu, nawet jeśli zmiennej lokalnej o takiej samej nazwie już istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [Iteracja — instrukcje](../cpp/iteration-statements-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [while — instrukcja (C++)](../cpp/while-statement-cpp.md)   
 [czy-while — instrukcja (C++)](../cpp/do-while-statement-cpp.md)   
 [Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)