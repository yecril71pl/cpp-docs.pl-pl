---
title: do-while — instrukcja (C++)
ms.date: 11/04/2016
f1_keywords:
- do_cpp
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
ms.openlocfilehash: 014012166f3a659d71b2e3212d63a523f2b87b8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656158"
---
# <a name="do-while-statement-c"></a>do-while — instrukcja (C++)

Wykonuje *instrukcji* wielokrotnie, aż określony warunek kończący ( *wyrażenie*) osiągnie wartość zero.

## <a name="syntax"></a>Składnia

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Uwagi

Test warunku zakończenia jest przeprowadzany po każdym wykonaniu pętli. w związku z tym **czy — gdy** pętla jest wykonywana raz lub więcej razy, w zależności od wartości wyrażenia ukończenia. **Czy — podczas** instrukcji można także zakończyć, gdy [podziału](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), lub [zwracają](../cpp/return-statement-cpp.md) instrukcja jest wykonywana w treści instrukcji.

*Wyrażenie* musi mieć typ arytmetyczny lub wskaźnika. Wykonanie działa w następujący sposób:

1. Instrukcja zostaje wykonana.

1. Następnie *wyrażenie* jest oceniany. Jeśli *wyrażenie* ma wartość FAŁSZ, **czy — gdy** kończy się i przekazuje kontrolę do następnej instrukcji w programie. Jeśli *wyrażenie* jest prawdziwe (niezerowe), proces jest powtarzany, zaczynając od kroku 1.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano **czy — gdy** instrukcji:

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>Zobacz także

[Instrukcje iteracji](../cpp/iteration-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[while, instrukcja (C++)](../cpp/while-statement-cpp.md)<br/>
[for, instrukcja (C++)](../cpp/for-statement-cpp.md)<br/>
[Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)