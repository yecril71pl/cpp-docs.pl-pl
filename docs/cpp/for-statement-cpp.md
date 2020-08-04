---
title: for — instrukcja (C++)
description: Odwołanie do standardowej instrukcji C++ for w Microsoft Visual Studio C++.
f1_keywords:
- for_cpp
ms.date: 07/31/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: b32a50e376113f9f9d550d4984d05fc8c675f14d
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520852"
---
# <a name="for-statement-c"></a>`for`Instrukcja (C++)

Wykonuje instrukcję wielokrotnie, dopóki warunek przestaje być prawdziwy. Aby uzyskać informacje na temat instrukcji opartych na zakresie **`for`** , zobacz [instrukcje oparte na zakresie `for` (C++)](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Składnia

> **`for (`** *`init-expression`* **`;`** *`cond-expression`* **`;`** *`loop-expression`* **`)`**\
> &emsp;*`statement`*

## <a name="remarks"></a>Uwagi

Użyj **`for`** instrukcji, aby skonstruować pętle, które muszą wykonać określoną liczbę razy.

**`for`** Instrukcja składa się z trzech opcjonalnych części, jak pokazano w poniższej tabeli.

### <a name="for-loop-elements"></a>dla elementów pętli

| Nazwa składni | Gdy wykonywane | Opis |
|--|--|--|
| *`init-expression`* | Przed jakimkolwiek innym elementem **`for`** instrukcji *`init-expression`* jest wykonywane tylko raz. Następnie formant przekazuje do *`cond-expression`* . | Często używane do zainicjowania indeksów pętli. Może zawierać wyrażenia lub deklaracje. |
| *`cond-expression`* | Przed wykonaniem każdej iteracji *`statement`* , łącznie z pierwszą iteracją. *`statement`* jest wykonywany tylko wtedy *`cond-expression`* , gdy wynikiem jest wartość true (niezerowa). | Wyrażenie obliczane do typu całkowitoliczbowego lub typu klasy, która ma jednoznaczną konwersję na typ całkowitoliczbowy. Normalnie używane do sprawdzania kryteriów zakończenia pętli for. |
| *`loop-expression`* | Na końcu każdej iteracji *`statement`* . Po *`loop-expression`* wykonaniu jest *`cond-expression`* oceniane. | Zwykle jest używane do zwiększania indeksów pętli. |

W poniższych przykładach przedstawiono różne sposoby używania **`for`** instrukcji.

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
    // Output: 01
}
```

*`init-expression`* i *`loop-expression`* mogą zawierać wiele instrukcji oddzielonych przecinkami. Na przykład:

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

*`loop-expression`* można zwiększyć lub zmniejszyć lub zmodyfikować w inny sposób.

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

**`for`** Pętla kończy się w trakcie [`break`](../cpp/break-statement-cpp.md) wykonywania, [Return](../cpp/return-statement-cpp.md)lub [`goto`](../cpp/goto-statement-cpp.md) (do instrukcji oznaczonej poza **`for`** pętlą) *`statement`* . [`continue`](../cpp/continue-statement-cpp.md)Instrukcja w **`for`** pętli kończy tylko bieżącą iterację.

Jeśli *`cond-expression`* parametr zostanie pominięty, zostanie on uwzględniony **`true`** , a **`for`** pętla nie zostanie zakończona bez **`break`** , **`return`** , lub **`goto`** wewnątrz *`statement`* .

Chociaż trzy pola **`for`** instrukcji są zwykle używane do inicjowania, testowania do zakończenia i zwiększania, nie są ograniczone do tych celów. Na przykład poniższy kod wyświetla cyfry od 0 do 4. W tym przypadku *`statement`* jest instrukcją o wartości null:

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

## <a name="for-loops-and-the-c-standard"></a>`for`pętle i standard C++

Standard C++ wskazuje, że zmienna zadeklarowana w **`for`** pętli nie należy do zakresu po **`for`** zakończeniu pętli. Na przykład:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

Domyślnie, w obszarze [/ze](../build/reference/za-ze-disable-language-extensions.md), zmienna zadeklarowana w **`for`** pętli pozostaje w zakresie do momentu **`for`** zakończenia otaczającego zakresu pętli.

[/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) włącza standardowe zachowanie zmiennych zadeklarowanych w pętli for, bez konieczności określania `/Za` .

Istnieje również możliwość użycia różnic dotyczących określania zakresu **`for`** pętli, aby ponownie zadeklarować zmienne w `/Ze` następujący sposób:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

To zachowanie bardziej ściśle naśladuje standardowe zachowanie zmiennej zadeklarowanej w **`for`** pętli, co wymaga, aby zmienne zadeklarowane w **`for`** pętli przechodzą poza zakres po zakończeniu pętli. Gdy zmienna jest zadeklarowana w **`for`** pętli, kompilator wewnętrznie promuje ją do zmiennej lokalnej w **`for`** zasięgu otaczającym pętli. Jest to promowane, nawet jeśli istnieje już zmienna lokalna o tej samej nazwie.

## <a name="see-also"></a>Zobacz także

[Instrukcje iteracji](../cpp/iteration-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[While — Instrukcja (C++)](../cpp/while-statement-cpp.md)<br/>
[do-While — Instrukcja (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Oparta na zakresie for — instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)
