---
title: while — instrukcja (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 0dfbbb2865c9cf0a23b04ce213a0e739e29c27da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187326"
---
# <a name="while-statement-c"></a>while — instrukcja (C++)

Wykonuje *instrukcję* wielokrotnie, dopóki *wyrażenie* zwróci wartość zero.

## <a name="syntax"></a>Składnia

```
while ( expression )
   statement
```

## <a name="remarks"></a>Uwagi

Test *wyrażenia* odbywa się przed każdym wykonaniem pętli; w związku z tym pętla **while** wykonuje zero lub więcej razy. *wyrażenie* musi być typu całkowitego, typu wskaźnika lub typu klasy z nieniejednoznaczną konwersją na typ całkowitego lub typu wskaźnika.

Pętla **while** można także przerwać, gdy zostanie wykonane [przerwanie](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md)lub [Return](../cpp/return-statement-cpp.md) w treści instrukcji. Użyj [Kontynuuj](../cpp/continue-statement-cpp.md) , aby zakończyć bieżącą iterację bez kończenia pętli **while** . **Kontynuuj** przekazuje kontrolę do następnej iteracji pętli **while** .

Poniższy kod używa pętli **while** do przycinania końcowego podkreślenia z ciągu:

```cpp
// while_statement.cpp

#include <string.h>
#include <stdio.h>
char *trim( char *szSource )
{
    char *pszEOS = 0;

    //  Set pointer to character before terminating NULL
    pszEOS = szSource + strlen( szSource ) - 1;

    //  iterate backwards until non '_' is found
    while( (pszEOS >= szSource) && (*pszEOS == '_') )
        *pszEOS-- = '\0';

    return szSource;
}
int main()
{
    char szbuf[] = "12345_____";

    printf_s("\nBefore trim: %s", szbuf);
    printf_s("\nAfter trim: %s\n", trim(szbuf));
}
```

Warunek zakończenia jest oceniany w górnej części pętli. Jeśli nie ma żadnych końcowych podkreśleń, pętla nigdy nie jest wykonywana.

## <a name="see-also"></a>Zobacz też

[Instrukcje iteracji](../cpp/iteration-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[do-while, instrukcja (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for, instrukcja (C++)](../cpp/for-statement-cpp.md)<br/>
[Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)
