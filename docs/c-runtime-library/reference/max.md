---
title: __max
ms.date: 04/05/2018
api_name:
- __max
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
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 4cdfd99ec344cd357900d76dfc7f9400046e448a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170192"
---
# <a name="__max"></a>__max

Makro preprocesora, które zwraca większe z dwóch wartości.

## <a name="syntax"></a>Składnia

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parametry

*a*, *b*<br/>
Wartości dowolnego typu liczbowego do porównania.

## <a name="return-value"></a>Wartość zwracana

**__max** zwraca większą liczbę argumentów.

## <a name="remarks"></a>Uwagi

Makro **__max** porównuje dwie wartości i zwraca wartość większą. Argumenty mogą być dowolnego typu danych liczbowych, podpisane lub niepodpisane. Oba argumenty i wartość zwracana muszą być tego samego typu danych.

Zwracany argument jest obliczany dwukrotnie przez makro. Może to prowadzić do nieoczekiwanych wyników, jeśli argument jest wyrażeniem, które zmienia jego wartość podczas oceniania, np. `*p++`.

## <a name="requirements"></a>Wymagania

|Macro|Wymagany nagłówek|
|-------------|---------------------|
|**__max**|\<STDLIB. h >|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz przykład dla [__min](min.md).

## <a name="see-also"></a>Zobacz też

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>
