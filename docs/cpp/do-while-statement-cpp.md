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
ms.openlocfilehash: f52c065210a8861dc065508248a506770b039b1d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189276"
---
# <a name="do-while-statement-c"></a>do-while — instrukcja (C++)

Wykonuje *instrukcję* wielokrotnie, dopóki określony warunek zakończenia ( *wyrażenie*) zwróci wartość zero.

## <a name="syntax"></a>Składnia

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Uwagi

Test warunku zakończenia jest wykonywany po każdym wykonaniu pętli; w związku z tym pętla **do-while** wykonuje jeden lub więcej razy, w zależności od wartości wyrażenia zakończenia. Instrukcja **do-while** może również kończyć się, gdy instrukcja [Break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md)lub [Return](../cpp/return-statement-cpp.md) jest wykonywana w treści instrukcji.

*Wyrażenie* musi mieć typ arytmetyczny lub wskaźnikowy. Wykonanie przebiega w następujący sposób:

1. Treść instrukcji jest wykonywana.

1. Następnie *wyrażenie* jest oceniane. Jeśli *wyrażenie* ma wartość false, instrukcja **do-while** kończy działanie i kontrola przechodzi do następnej instrukcji w programie. Jeśli *wyrażenie* jest prawdziwe (niezerowe), proces jest powtarzany, zaczynając od kroku 1.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano instrukcję **do-while** :

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

## <a name="see-also"></a>Zobacz też

[Instrukcje iteracji](../cpp/iteration-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[while, instrukcja (C++)](../cpp/while-statement-cpp.md)<br/>
[for, instrukcja (C++)](../cpp/for-statement-cpp.md)<br/>
[Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)
