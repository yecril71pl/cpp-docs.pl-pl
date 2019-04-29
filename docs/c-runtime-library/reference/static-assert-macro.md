---
title: _STATIC_ASSERT — Makro
ms.date: 11/04/2016
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: 5d3aa1d9665b48a0690d8eb62353fc98c5a550f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62354701"
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT — Makro

Ocena wyrażenia w czasie kompilacji i wygenerują błąd, jeśli wynik to **FALSE**.

## <a name="syntax"></a>Składnia

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Wyrażenie (w tym wskaźniki) obliczane na wartość różną od zera (**TRUE**) lub równa 0 (**FALSE**).

## <a name="remarks"></a>Uwagi

Przypomina to makro [_ASSERT i _asserte — makra](assert-asserte-assert-expr-macros.md), chyba że *booleanExpression* jest obliczane w czasie kompilacji, a nie w czasie wykonywania. Jeśli *booleanExpression* daje w wyniku **FALSE** (0), [błąd kompilatora C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) jest generowany.

## <a name="example"></a>Przykład

W tym przykładzie, możemy sprawdzić, czy [sizeof](../../c-language/sizeof-operator-c.md) **int** jest większy niż lub równa 2 bajty oraz tego, czy [sizeof](../../c-language/sizeof-operator-c.md) **długie** jest 1 bajt. Program nie zostanie skompilowany i będzie generować [błąd kompilatora C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) ponieważ **długie** jest większy niż 1 bajt.

```C
// crt__static_assert.c

#include <crtdbg.h>
#include <stdio.h>

_STATIC_ASSERT(sizeof(int) >= 2);
_STATIC_ASSERT(sizeof(long) == 1);  // C2466

int main()
{
    printf("I am sure that sizeof(int) will be >= 2: %d\n",
        sizeof(int));
    printf("I am not so sure that sizeof(long) == 1: %d\n",
        sizeof(long));
}
```

## <a name="requirements"></a>Wymagania

|Macro|Wymagany nagłówek|
|-----------|---------------------|
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](assert-asserte-assert-expr-macros.md)<br/>
