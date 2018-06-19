---
title: _Static_assert — makro | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbbab8314a038d796ebd1a13342f3054e59f3e68
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407369"
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT — Makro

Oceń wyrażenia w czasie kompilacji i generuje błąd, gdy wynik jest **FALSE**.

## <a name="syntax"></a>Składnia

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Parametry

*booleanExpression* wyrażenia (w tym wskaźników), którego wynikiem do różną od zera (**TRUE**) lub równa 0 (**FALSE**).

## <a name="remarks"></a>Uwagi

Przypomina to makro [_ASSERT i _asserte — makra](assert-asserte-assert-expr-macros.md), ale *booleanExpression* jest oceniane w czasie kompilacji zamiast w czasie wykonywania. Jeśli *booleanExpression* daje w wyniku **FALSE** (0), [C2466 błąd kompilatora](../../error-messages/compiler-errors-1/compiler-error-c2466.md) jest generowany.

## <a name="example"></a>Przykład

W tym przykładzie, musimy sprawdzić czy [sizeof](../../c-language/sizeof-operator-c.md) **int** jest większa niż lub równa 2 bajty oraz tego, czy [sizeof](../../c-language/sizeof-operator-c.md) **długi** jest 1 bajt. Program nie zostanie skompilowany i będzie generować [C2466 błąd kompilatora](../../error-messages/compiler-errors-1/compiler-error-c2466.md) ponieważ **długi** jest większy niż 1 bajt.

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
