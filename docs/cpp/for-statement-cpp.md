---
title: for — instrukcja (C++)
description: Odwołanie do standardu C++ dla instrukcji w programie Microsoft Visual Studio C++.
f1_keywords:
- for_cpp
ms.date: 04/14/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: 92f7ae4b1f2fbaaf710cd5a8739b78cb98a0accb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375386"
---
# <a name="for-statement-c"></a>for — instrukcja (C++)

Wykonuje instrukcję wielokrotnie, dopóki warunek przestaje być prawdziwy. Aby uzyskać informacje na temat zakresu opartego na instrukcji, zobacz [oparte na zakresie dla instrukcji (C++)](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Składnia

> **`for (`***init-expression* **`;`** *cond-expression* **`;`** *wyrażenie pętli wyrażenie***`)`**\
> &nbsp;&nbsp;&nbsp;&nbsp;_Instrukcja_**`;`**

## <a name="remarks"></a>Uwagi

Użyj **for** instrukcji do konstruowania pętli, które muszą wykonać określoną liczbę razy.

**Instrukcja for** składa się z trzech opcjonalnych części, jak pokazano w poniższej tabeli.

### <a name="for-loop-elements"></a>Elementy pętli for

|Nazwa składni|Kiedy wykonywane|Opis|
|-----------------|-------------------|-----------------|
|`init-expression`|Przed innym elementem **for** `init-expression` instrukcji, jest wykonywany tylko raz. Kontrola następnie `cond-expression`przechodzi do .|Często używane do zainicjowania indeksów pętli. Może zawierać wyrażenia lub deklaracje.|
|`cond-expression`|Przed wykonaniem każdej iteracji `statement`, w tym pierwszej iteracji. `statement`jest wykonywany `cond-expression` tylko wtedy, gdy jest oblicza true (nonzero).|Wyrażenie obliczane do typu całkowitoliczbowego lub typu klasy, która ma jednoznaczną konwersję na typ całkowitoliczbowy. Normalnie używane do sprawdzania kryteriów zakończenia pętli for.|
|`loop-expression`|Na końcu każdej iteracji `statement`pliku . Po `loop-expression` wykonaniu `cond-expression` jest oceniane.|Zwykle jest używane do zwiększania indeksów pętli.|

Poniższe przykłady pokazują różne sposoby użycia **instrukcji for.**

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

`init-expression`i `loop-expression` może zawierać wiele instrukcji oddzielonych przecinkami. Przykład:

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

`loop-expression`mogą być zwiększane lub zmniejszane lub modyfikowane w inny sposób.

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

A **for** pętli kończy się, gdy [break](../cpp/break-statement-cpp.md), [return](../cpp/return-statement-cpp.md), lub [goto](../cpp/goto-statement-cpp.md) `statement` (do instrukcji oznaczone poza **for** pętli) wewnątrz jest wykonywana. Instrukcja [continue](../cpp/continue-statement-cpp.md) w **for** pętli kończy tylko bieżącą iterację.

Jeśli `cond-expression` zostanie pominięty, jest `true`uważany , a **pętla for** nie zakończy się bez `statement` **przerwy,** **powrotu**lub **goto** w obrębie .

Mimo że trzy pola **for** instrukcji są zwykle używane do inicjowania, testowania zakończenia i zwiększania, nie są one ograniczone do tych zastosowań. Na przykład poniższy kod wyświetla cyfry od 0 do 4. W takim `statement` przypadku jest null instrukcji:

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

Standard C++ mówi, że zmienna zadeklarowana w **for** pętli wykracza poza zakres po zakończeniu pętli **for.** Przykład:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

Domyślnie w [obszarze /Ze](../build/reference/za-ze-disable-language-extensions.md)zmienna zadeklarowana w pętli **for** pozostaje w zakresie, dopóki zakres otaczającej pętli **for** nie zakończy się.

[/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) umożliwia standardowe zachowanie zmiennych zadeklarowanych w pętlach bez konieczności określania `/Za`.

Istnieje również możliwość użycia różnic zakresu **for** pętli do ponownego deklarowania zmiennych w następujący sposób: `/Ze`

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

To zachowanie bardziej naśladuje standardowe zachowanie zmiennej zadeklarowanej w **for** pętli, która wymaga zmiennych zadeklarowanych w **for** pętli, aby wyjść poza zakres po wykonaniu pętli. Gdy zmienna jest zadeklarowana w **for** pętli, kompilator wewnętrznie promuje go do zmiennej lokalnej w **for** pętli otaczającego zakresu. Jest promowany, nawet jeśli istnieje już zmienna lokalna o tej samej nazwie.

## <a name="see-also"></a>Zobacz też

[Instrukcje iteracji](../cpp/iteration-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[while Statement (C++)](../cpp/while-statement-cpp.md)<br/>
[Instrukcja do-while (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)
