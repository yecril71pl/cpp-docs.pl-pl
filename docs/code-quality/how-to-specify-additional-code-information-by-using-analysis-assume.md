---
title: Użyj _Analysis_assume na potrzeby wskazówek dotyczących analizy kodu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
ms.openlocfilehash: f427afdcab07b41430a5d4b5fc7f300aa671e30b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503299"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Instrukcje: Określanie dodatkowych informacji o kodzie przy użyciu _Analysis_assume

Możesz dostarczyć wskazówki do narzędzia analizy kodu dla kodu C/C++, które ułatwią proces analizy i zmniejszają ostrzeżenia. Aby podać dodatkowe informacje, użyj następującej funkcji:

`_Analysis_assume(`  `expr`  `)`

`expr` — Dowolne wyrażenie, które ma zostać obliczone na wartość true.

Narzędzie do analizy kodu zakłada, że warunek reprezentowany przez wyrażenie ma wartość true w punkcie, w którym funkcja jest wyświetlana i pozostaje prawdziwa do momentu zmiany wyrażenia, na przykład przez przypisanie do zmiennej.

> [!NOTE]
> `_Analysis_assume` nie ma wpływu na optymalizację kodu. Poza narzędzia do analizy kodu, `_Analysis_assume` jest definiowana jako No-op.

## <a name="example"></a>Przykład

Poniższy kod używa `_Analysis_assume` do korygowania ostrzeżenia analizy kodu [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Zobacz też

- [__assume](../intrinsics/assume.md)
