---
title: 'Prefiksów inkrementacji i dekrementacji: ++ i--| Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc5ef28f7119316f0c42302d4fd1583a53e53140
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069732"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Operatory prefiksów inkrementacji i dekrementacji: ++ i --

## <a name="syntax"></a>Składnia

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Uwagi

Operator inkrementacji prefiksu (**++**) dodaje je do swojego operandu; Ta zwiększona wartość jest wynikiem wyrażenia. Argument musi być l wartością nie jest typu **const**. Wynik jest l wartością tego samego typu jako argumentu operacji.

Operator dekrementacji prefiksu (**--**) jest odpowiednikiem operator inkrementacji prefiksu, z tą różnicą, że argument jest zmniejszana o jeden, a wynik jest ta zmniejszona wartość.

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): operand operatora inkrementacji lub dekrementacji nie może być typu **bool**.

Prefiks i przyrostka inkrementacji i dekrementacji operatory mają wpływ na ich argumentów. Główną różnicą między nimi jest kolejność, w którym inkrementacyjna lub dekrementacyjna odbywa się w wyniku obliczenia wyrażenia. (Aby uzyskać więcej informacji, zobacz [operatory przyrostka inkrementacji i dekrementacji](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) W formularzu prefiks inkrementacyjna lub dekrementacyjna odbywa się przed zostanie użyta wartość obliczania wyrażeń, więc wartość wyrażenia jest inny niż wartość operandu. W formularzu przyrostka inkrementacji lub dekrementacji odbywa się po zostanie użyta wartość obliczania wyrażeń, więc wartość wyrażenia jest taka sama jak wartość operandu. Na przykład, poniższy program odbitek "`++i = 6`":

```cpp
// expre_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   int i = 5;
   cout << "++i = " << ++i << endl;
}
```

Argument operacji typu całkowitego lub zmiennoprzecinkowego jest zwiększone lub zmniejszone wartość całkowita 1. Typ wyniku jest taki sam jak typ operandu. Argument operacji typu wskaźnika jest zwiększone lub zmniejszone rozmiar obiektu, które ona rozwiązuje. Wskazuje zwiększona wskaźnik do następnego obiektu. zmniejszony wskaźnik wskazuje poprzedniego obiektu.

Ponieważ operatory inkrementacji i dekrementacji mają skutki uboczne, za pomocą wyrażenia z operatorami inkrementacyjna lub dekrementacyjna w [makro preprocesora](../preprocessor/macros-c-cpp.md) może mieć niepożądane wyniki. Rozważmy następujący przykład:

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

Makro rozszerza się, aby:

```cpp
k = ((++i)<(j))?(j):(++i);
```

Jeśli `i` jest większa niż lub równa `j` lub mniej niż `j` o 1, jego jest zwiększany dwa razy.

> [!NOTE]
>  Funkcji śródwierszowych języka C++ są preferowane w porównaniu do makr w wielu przypadkach, ponieważ eliminuje efekty uboczne, takich jak te opisane w tym miejscu i Zezwalaj na język do wykonywania bardziej szczegółowy sprawdzania typu.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory prefiksów inkrementacji i dekrementacji](../c-language/prefix-increment-and-decrement-operators.md)