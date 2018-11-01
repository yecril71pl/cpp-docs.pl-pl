---
title: __max
ms.date: 04/05/2018
apiname:
- __max
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
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 32e1207ea4bb030ac5303de32c0566f98e0596a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613762"
---
# <a name="max"></a>__max

Makro preprocesora, które zwraca większy z dwóch wartości.

## <a name="syntax"></a>Składnia

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parametry

*a*, *b*<br/>
Wartości dowolnego typu liczbowego, który można porównać.

## <a name="return-value"></a>Wartość zwracana

**__max** zwraca większy z jej argumentów.

## <a name="remarks"></a>Uwagi

**__Max** — makro porównuje dwie wartości i zwraca wartość większy z nich. Argumenty mogą być wszelkie wartości numeryczne, typ danych, podpisane lub niepodpisane. Argumenty i wartość zwracana musi być tego samego typu danych.

Argument, zwracany jest oceniany dwukrotnie przez makra. Może to prowadzić do nieoczekiwanych wyników, jeśli argument jest wyrażeniem, które zmienia jego wartość, gdy zostanie ono ocenione, takich jak `*p++`.

## <a name="requirements"></a>Wymagania

|Macro|Wymagany nagłówek|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz przykład [__min](min.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>