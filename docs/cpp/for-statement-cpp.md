---
title: for — instrukcja (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: e3dfdb45bdf8a508eca9d29e90b3f7c05e7b147d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179917"
---
# <a name="for-statement-c"></a>for — instrukcja (C++)

Wykonuje instrukcję wielokrotnie, dopóki warunek przestaje być prawdziwy. Aby uzyskać informacje na temat instrukcji for opartej na zakresie, zobacz [zakres na podstawie instrukcjiC++for ()](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Składnia

```
for ( init-expression ; cond-expression ; loop-expression )
    statement;
```

## <a name="remarks"></a>Uwagi

Użyj instrukcji **for** , aby utworzyć pętle, które muszą wykonać określoną liczbę razy.

Instrukcja **for** zawiera trzy opcjonalne części, jak pokazano w poniższej tabeli.

### <a name="for-loop-elements"></a>Elementy pętli for

|Nazwa składni|Kiedy wykonywane|Opis|
|-----------------|-------------------|-----------------|
|`init-expression`|Przed jakimkolwiek innym elementem instrukcji **for** `init-expression` jest wykonywane tylko raz. Następnie kontrolka przechodzi do `cond-expression`.|Często używane do zainicjowania indeksów pętli. Może zawierać wyrażenia lub deklaracje.|
|`cond-expression`|Przed wykonaniem każdej iteracji `statement`, łącznie z pierwszą iteracją. `statement` jest wykonywane tylko wtedy, gdy `cond-expression` ma wartość true (niezerowa).|Wyrażenie obliczane do typu całkowitoliczbowego lub typu klasy, która ma jednoznaczną konwersję na typ całkowitoliczbowy. Normalnie używane do sprawdzania kryteriów zakończenia pętli for.|
|`loop-expression`|Na końcu każdej iteracji `statement`. Po wykonaniu `loop-expression` `cond-expression` jest oceniane.|Zwykle jest używane do zwiększania indeksów pętli.|

W poniższych przykładach przedstawiono różne sposoby używania instrukcji **for** .

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

`init-expression` i `loop-expression` mogą zawierać wiele instrukcji oddzielonych przecinkami. Na przykład:

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

`loop-expression` można zwiększyć lub zmniejszyć lub zmodyfikować w inny sposób.

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

Pętla **for** kończy się po wykonaniu instrukcji [Break](../cpp/break-statement-cpp.md), [Return](../cpp/return-statement-cpp.md)lub [goto](../cpp/goto-statement-cpp.md) (do etykiety oznaczonej poza pętlą **for** ) w ramach `statement`. Instrukcja [Continue](../cpp/continue-statement-cpp.md) w pętli **for** kończy tylko bieżącą iterację.

W przypadku pominięcia `cond-expression` jest uznawana za true, a pętla **for** nie zostanie zakończona bez **przerw**, **Return**lub **goto** w `statement`.

Chociaż trzy pola instrukcji **for** są zwykle używane do inicjowania, testowania do zakończenia i zwiększania, nie są ograniczone do tych celów. Na przykład poniższy kod wyświetla cyfry od 0 do 4. W tym przypadku `statement` jest instrukcją o wartości null:

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

C++ Standard mówi, że zmienna zadeklarowana w pętli **for** nie należy do zakresu po zakończeniu pętli **for** . Na przykład:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

Domyślnie, w obszarze [/ze](../build/reference/za-ze-disable-language-extensions.md), zmienna zadeklarowana w pętli **for** pozostaje w zakresie do momentu zakończenia otaczającego zakresu pętli **for** .

[/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) włącza standardowe zachowanie zmiennych zadeklarowanych w pętli for, bez konieczności określania `/Za`.

Istnieje również możliwość użycia różnic między zakresami **dla pętli for** , aby ponownie zadeklarować zmienne w `/Ze` w następujący sposób:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

Pozwala to dokładniej naśladować standardowe zachowanie zmiennej zadeklarowanej w pętli **for** , co wymaga, aby zmienne zadeklarowane w pętli **for** wychodzą poza zakres po zakończeniu pętli. Gdy zmienna jest zadeklarowana w pętli **for** , kompilator wewnętrznie promuje go do zmiennej lokalnej w otaczającym zakresie pętli **for** , nawet jeśli istnieje już zmienna lokalna o tej samej nazwie.

## <a name="see-also"></a>Zobacz też

[Instrukcje iteracji](../cpp/iteration-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[while, instrukcja (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while, instrukcja (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)
