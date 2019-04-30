---
title: Operator reinterpret_cast
ms.date: 11/04/2016
f1_keywords:
- reinterpret_cast_cpp
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
ms.openlocfilehash: 421a1fdce6834f800cd33a55d75c9dc4f88ffc93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403428"
---
# <a name="reinterpretcast-operator"></a>Operator reinterpret_cast

Umożliwia dowolny wskaźnik do przekonwertowania na dowolny inny typ wskaźnika. Umożliwia również dowolnego typu całkowitoliczbowego ma zostać przekonwertowany na dowolny typ wskaźnika i odwrotnie.

## <a name="syntax"></a>Składnia

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>Uwagi

Nieprawidłowe użycie **reinterpret_cast** łatwo operator może być niebezpieczne. Chyba że żądany konwersji jest natury niskiego poziomu, należy użyć jednego z innych operatorów rzutowania.

**Reinterpret_cast** operator może służyć do konwersji takich jak `char*` do `int*`, lub `One_class*` do `Unrelated_class*`, które są założenia niebezpieczne.

Wynik **reinterpret_cast** bezpiecznie nie można używać do coś innego niż rzutowany powrót do oryginalnego typu. Inne zastosowania to, co najlepiej nonportable.

**Reinterpret_cast** operator nie może oddać **const**, **volatile**, lub **__unaligned** atrybutów. Zobacz [const_cast Operator](../cpp/const-cast-operator.md) informacji na temat usuwania tych atrybutów.

**Reinterpret_cast** operator konwertuje wartość pustego wskaźnika do wartości pustego wskaźnika typu miejsca docelowego.

Jednym z zastosowań praktycznych **reinterpret_cast** znajduje się w funkcji mieszania, mapująca wartość do indeksu w taki sposób, że dwóch odrębnych wartości rzadko zakończenia się przy użyciu tego samego indeksu.

```cpp
#include <iostream>
using namespace std;

// Returns a hash code based on an address
unsigned short Hash( void *p ) {
   unsigned int val = reinterpret_cast<unsigned int>( p );
   return ( unsigned short )( val ^ (val >> 16));
}

using namespace std;
int main() {
   int a[20];
   for ( int i = 0; i < 20; i++ )
      cout << Hash( a + i ) << endl;
}

Output:
64641
64645
64889
64893
64881
64885
64873
64877
64865
64869
64857
64861
64849
64853
64841
64845
64833
64837
64825
64829
```

**Reinterpret_cast** umożliwia wskaźnika, który powinien być traktowany jako typ całkowitoliczbowy. Wynik jest następnie bit przesunięte i XORed z samym sobą, aby wygenerować unikatowego indeksu (unikatowe wysokiego stopnia prawdopodobieństwa). Indeks jest następnie obcięte przez standard C rzutowania w stylu zwracany typ funkcji.

## <a name="see-also"></a>Zobacz także

[Operatory rzutowania](../cpp/casting-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)