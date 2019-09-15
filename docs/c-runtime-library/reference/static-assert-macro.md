---
title: _STATIC_ASSERT — Makro
ms.date: 11/04/2016
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: ac609fc7af937b6f56cd5b310341409187df7de4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957930"
---
# <a name="_static_assert-macro"></a>_STATIC_ASSERT — Makro

Oceń wyrażenie w czasie kompilacji i Wygeneruj błąd, gdy wynik ma **wartość false**.

## <a name="syntax"></a>Składnia

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Wyrażenie (w tym wskaźniki), które ma wartość różną od zera (**true**) lub 0 (**false**).

## <a name="remarks"></a>Uwagi

To makro przypomina [makra _ASSERT i _ASSERTE](assert-asserte-assert-expr-macros.md), z tą różnicą, że *booleanExpression* jest oceniane w czasie kompilacji, a nie w czasie wykonywania. Jeśli *booleanExpression* zwraca **wartość false** (0), generowany jest [błąd kompilatora C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) .

## <a name="example"></a>Przykład

W tym przykładzie sprawdzimy, czy wartość [sizeof](../../c-language/sizeof-operator-c.md) jest **liczbą całkowitą** większą niż lub równą 2 bajty oraz czy [](../../c-language/sizeof-operator-c.md) wartość sizeof **to 1** bajt. Program nie zostanie skompilowany i zostanie wygenerowany [błąd kompilatora C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) , ponieważ **Long** jest większy niż 1 bajt.

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
