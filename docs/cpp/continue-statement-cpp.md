---
title: continue — instrukcja (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: b3790ecfde0af958b3244cfdaa61524ba78d6267
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180280"
---
# <a name="continue-statement-c"></a>continue — instrukcja (C++)

Wymusza przeniesienie kontroli do wyrażenia sterującego najmniejszej otaczającej pętli [Zrób](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)lub [while](../cpp/while-statement-cpp.md) .

## <a name="syntax"></a>Składnia

```
continue;
```

## <a name="remarks"></a>Uwagi

Wszystkie pozostałe instrukcje w bieżącej iteracji nie są wykonywane. Następna iteracja pętli jest określana w następujący sposób:

- W pętli **do** lub **while** następna iteracja jest uruchamiana przez ponowną ocenę wyrażenia sterującego instrukcji **do** lub **while** .

- W pętli **for** (przy użyciu składni `for`(`init-expr`; `cond-expr`; `loop-expr`)) jest wykonywana klauzula `loop-expr`. Następnie klauzula `cond-expr` jest ponownie Szacowana i, w zależności od wyniku, pętla lub jest wykonywana inna iteracja.

Poniższy przykład pokazuje, jak można użyć instrukcji **Continue** , aby pominąć sekcje kodu i rozpocząć następną iterację pętli.

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

## <a name="see-also"></a>Zobacz też

[Instrukcje skoku](../cpp/jump-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
