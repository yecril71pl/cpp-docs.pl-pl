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
ms.openlocfilehash: ce066a3349d56b278739f586fe851b020da78885
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366219"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Operatory prefiksów inkrementacji i dekrementacji: ++ i --

## <a name="syntax"></a>Składnia

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Uwagi

Operator przyrostu prefiksu (**++**) dodaje jeden do jego operand; ta przyrostowa wartość jest wynikiem wyrażenia. Operand musi być wartością l, a nie **typem const**. Wynik jest wartością l tego samego typu co operand.

Operator dekrementacji prefiksu (**--**) jest analogiczny do operatora przyrostu prefiksu, z tą różnicą, że operand jest zmniejszany o jeden, a wynikiem jest ta wartość zmniejszana.

**Visual Studio 2017 w wersji 15.3 i nowszej** (dostępne z [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Operand operatora przyrostu lub dekrementacji może nie być typu **bool**.

Zarówno prefiks i przyrost postfix i dekrementacji operatorów wpływa na ich operands. Kluczową różnicą między nimi jest kolejność, w której przyrost lub dekrementowanie odbywa się w ocenie wyrażenia. (Aby uzyskać więcej informacji, zobacz [Postfix Increment and Decrement Operators](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) W formularzu prefiksu przyrost lub dekrementacja odbywa się przed użyciem wartości w ocenie wyrażenia, więc wartość wyrażenia różni się od wartości operandu. W formularzu postfix przyrost lub dekrementacja odbywa się po użyciu wartości w ocenie wyrażenia, więc wartość wyrażenia jest taka sama jak wartość operandu. Na przykład następujący program drukuje "`++i = 6`":

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

Operand typu integralnego lub pływającego jest zwiększany lub zmniejszany o wartość całkowitą 1. Typ wyniku jest taki sam jak typ operandu. Operand typu wskaźnika jest zwiększany lub zmniejszany o rozmiar obiektu, który adresuje. Przyrostowy wskaźnik wskazuje na następny obiekt; zdymisjonowany wskaźnik wskazuje poprzedni obiekt.

Ponieważ operatory przyrostu i dekrementacji mają skutki uboczne, używanie wyrażeń z operatorami przyrostu lub dekrementacji w [makrze preprocesora](../preprocessor/macros-c-cpp.md) może mieć niepożądane wyniki. Rozważmy następujący przykład:

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

Makro rozszerza się do:

```cpp
k = ((++i)<(j))?(j):(++i);
```

Jeśli `i` jest większa lub `j` równa `j` lub mniejsza niż o 1, zostanie dwukrotnie wzmocniona.

> [!NOTE]
> Funkcje wbudowane języka C++ są preferowane dla makr w wielu przypadkach, ponieważ eliminują skutki uboczne, takie jak opisane w tym miejscu, i umożliwiają językowi bardziej kompletne sprawdzanie typu.

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory prefiksów inkrementacji i dekrementacji](../c-language/prefix-increment-and-decrement-operators.md)
