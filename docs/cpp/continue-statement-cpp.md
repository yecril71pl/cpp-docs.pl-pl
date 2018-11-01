---
title: continue — instrukcja (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 6fbc4af6a9a56f3406582ea9ba59f4d5759b88a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607483"
---
# <a name="continue-statement-c"></a>continue — instrukcja (C++)

Wymusza transfer kontroli do kontrolowania wyrażenia najmniejszy otaczający [czy](../cpp/do-while-statement-cpp.md), [dla](../cpp/for-statement-cpp.md), lub [podczas](../cpp/while-statement-cpp.md) pętli.

## <a name="syntax"></a>Składnia

```
continue;
```

## <a name="remarks"></a>Uwagi

Wszystkie pozostałe instrukcje w bieżącej iteracji nie zostaną wykonane. Następnej iteracji pętli jest określane w następujący sposób:

- W **czy** lub **podczas** pętli, następnej iteracji należy zacząć od reevaluating kontrolowanie wyrażenia **czy** lub **podczas** instrukcji.

- W **dla** pętli (przy użyciu składni `for`(`init-expr`; `cond-expr`; `loop-expr`)), `loop-expr` klauzula jest wykonywany. A następnie `cond-expr` klauzula jest ponownie oceniane i, w zależności od wyniku pętli albo kończy się lub występuje innej iteracji.

W poniższym przykładzie pokazano sposób, w jaki **nadal** instrukcja może być używana do obejścia sekcje kodu i rozpocząć kolejnej iteracji pętli.

## <a name="example"></a>Przykład

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>Zobacz także

[Instrukcje skoku](../cpp/jump-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)