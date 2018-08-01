---
title: for — instrukcja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: feb14056e3054cdf0e802b16ce9ff20f67da43fe
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401577"
---
# <a name="for-statement-c"></a>for — instrukcja (C++)
Wykonuje instrukcję wielokrotnie, dopóki warunek przestaje być prawdziwy. Informacje na temat bazująca na zakresie dla instrukcji można zobaczyć [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## <a name="remarks"></a>Uwagi  
 Użyj **dla** instrukcji do konstruowania pętli, które muszą być wykonywane określoną liczbę razy.  
  
 **Dla** instrukcji składa się z trzech opcjonalnych części, jak pokazano w poniższej tabeli.  
  
### <a name="for-loop-elements"></a>Elementy pętli for  
  
|Nazwa składni|Kiedy wykonywane|Opis|  
|-----------------|-------------------|-----------------|  
|`init-expression`|Przed innym elementem z **dla** instrukcji `init-expression` jest wykonywane tylko raz. Następnie sterowanie przechodzi do `cond-expression`.|Często używane do zainicjowania indeksów pętli. Może zawierać wyrażenia lub deklaracje.|  
|`cond-expression`|Przed wykonaniem każdej iteracji `statement`, łącznie z pierwszą iteracją. `statement` jest wykonywane tylko wtedy, gdy `cond-expression` zwraca wartość true (niezerową).|Wyrażenie obliczane do typu całkowitoliczbowego lub typu klasy, która ma jednoznaczną konwersję na typ całkowitoliczbowy. Normalnie używane do sprawdzania kryteriów zakończenia pętli for.|  
|`loop-expression`|Na koniec każdej iteracji `statement`. Po `loop-expression` jest wykonywane, `cond-expression` jest oceniany.|Zwykle jest używane do zwiększania indeksów pętli.|  
  
 W poniższych przykładach pokazano różne sposoby stosowania **dla** instrukcji.  
  
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
  
 `init-expression` i `loop-expression` mogą zawierać wiele instrukcji, oddzielonych przecinkami. Na przykład:  
  
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
  
 `loop-expression` może być zwiększona lub zmniejszona lub modyfikować w inny sposób.  
  
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
  
 A **dla** pętli skończy się, gdy [podziału](../cpp/break-statement-cpp.md), [zwracają](../cpp/return-statement-cpp.md), lub [goto](../cpp/goto-statement-cpp.md) (do oznaczonej instrukcji poza **dla**pętli) w ramach `statement` jest wykonywany. A [nadal](../cpp/continue-statement-cpp.md) instrukcji w **dla** pętli kończy tylko bieżącą iterację.  
  
 Jeśli `cond-expression` jest pominięty, jest uznawane za true i **dla** pętli nie zostanie zakończona bez **podziału**, **zwracają**, lub **przejdź do** w ramach `statement`.  
  
 Chociaż trzy pola **dla** instrukcji są zwykle używane do inicjowania i testowania rozwiązania, i inkrementacji, nie są ograniczone do tych zastosowań. Na przykład poniższy kod wyświetla cyfry od 0 do 4. W tym przypadku `statement` jest pustą instrukcją:  
  
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
 C++ standard mówi, że Zmienna zadeklarowana w **dla** pętla powinna wyjść poza zakres po **dla** zakończeniu pętli. Na przykład:  
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 Domyślnie w ramach [/Ze](../build/reference/za-ze-disable-language-extensions.md), Zmienna zadeklarowana w **dla** pętli pozostaje w zakresie aż do zakończenia **dla** pętli otaczającego zakresu.  
  
 [/ Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) włącza standardowe zachowanie zmiennych zadeklarowanych w pętlach for bez konieczności określania `/Za`.  
  
 Istnieje również możliwość użycia różnic zakresu **dla** pętli do ponownego zadeklarowania zmiennych pod `/Ze` w następujący sposób:  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 To bardziej ścisłe naśladowanie standardowego zachowania zmiennej zadeklarowanej w **dla** pętli, która wymaga, aby zmienne zadeklarowane w **dla** pętli wykraczają poza zakres po zakończeniu pętli. Gdy zmienna jest zadeklarowana w **dla** pętli, kompilator wewnętrznie Awansuje ją do zmiennej lokalnej w **dla** otaczającym zakresie pętli, nawet jeśli zmienna lokalna o takiej samej nazwie już istnieje.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje iteracji](../cpp/iteration-statements-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [while — instrukcja (C++)](../cpp/while-statement-cpp.md)   
 [czy-while — instrukcja (C++)](../cpp/do-while-statement-cpp.md)   
 [Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)