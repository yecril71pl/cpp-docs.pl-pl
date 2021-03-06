---
title: 'Operatory prefiksów inkrementacji i dekrementacji: ++ i --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
ms.openlocfilehash: 0b84360f41c665707a03ad453909c054ac741405
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231159"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Operatory prefiksów inkrementacji i dekrementacji: ++ i --

## <a name="syntax"></a>Składnia

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Uwagi

Operator przyrostu prefiksu ( **++** ) dodaje jeden do operandu; ta wartość przyrostowa jest wynikiem wyrażenia. Argument operacji musi być l-wartością typu nie **`const`** . Wynik jest l-wartością tego samego typu co operand.

Operator zmniejszania prefiksu ( **--** ) jest analogiczny do operatora przyrostu prefiksu, z tą różnicą, że argument operacji jest zmniejszany o jeden, a wynikiem jest wartość tego zmniejszenia.

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): operand operatora Increment lub zmniejszania nie może być typu **`bool`** .

Operatory prefix i Increment przyrostu i zmniejszania wpływają na ich operandy. Kluczową różnicą między nimi jest kolejność, w której zwiększenie lub zmniejszenie odbywa się podczas obliczania wyrażenia. (Aby uzyskać więcej informacji, zobacz [Operatory przyrostu i zmniejszania](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)). W formie prefiksu, przyrost lub zmniejszenie odbywa się przed użyciem wartości podczas obliczania wyrażenia, więc wartość wyrażenia jest inna niż wartość operandu. W formie przyrostkowej przyrost lub zmniejszenie odbywa się po użyciu wartości podczas obliczania wyrażenia, więc wartość wyrażenia jest taka sama jak wartość operandu. Na przykład następujący program drukuje " `++i = 6` ":

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

Operand typu całkowitego lub zmiennoprzecinkowego jest zwiększany lub zmniejszany przez wartość całkowitą 1. Typ wyniku jest taki sam jak typ argumentu operacji. Operand typu wskaźnika jest zwiększany lub zmniejszany o rozmiar obiektu, do którego się odnosi. Przyrostowy wskaźnik wskazuje na następny obiekt; zmniejszający wskaźnik wskazuje na poprzedni obiekt.

Ze względu na to, że operatory zwiększania i zmniejszania mają efekty uboczne, Używanie wyrażeń z operatorami przyrostu lub zmniejszania w [makrze preprocesora](../preprocessor/macros-c-cpp.md) może mieć niepożądane wyniki. Rozważmy następujący przykład:

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

Makro powiększa się do:

```cpp
k = ((++i)<(j))?(j):(++i);
```

Jeśli `i` jest większa lub równa `j` lub mniejsza niż `j` 1, zostanie dwukrotnie zwiększona.

> [!NOTE]
> Wbudowane funkcje języka C++ są preferowane dla makr w wielu przypadkach, ponieważ eliminują efekty uboczne, takie jak opisane tutaj, i zezwalają na wykonywanie dokładniejszego sprawdzania typu przez język.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory przyrostu i zmniejszania prefiksu](../c-language/prefix-increment-and-decrement-operators.md)
