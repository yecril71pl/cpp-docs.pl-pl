---
title: __uncaught_exception
ms.date: 11/04/2016
api_name:
- __uncaught_exception
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
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 1eb06abbda7978acf578555f966f0857dff02053
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211635"
---
# <a name="__uncaught_exception"></a>__uncaught_exception

Wskazuje, czy zgłoszono co najmniej jeden wyjątek, ale nie został jeszcze obsłużony przez odpowiedni **`catch`** blok instrukcji [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) .

## <a name="syntax"></a>Składnia

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>Wartość zwracana

**`true`** od momentu, gdy wyjątek jest zgłaszany w **`try`** bloku do momentu **`catch`** zainicjowania pasującego bloku; w przeciwnym razie **`false`** .

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__uncaught_exception|eh. h|

## <a name="see-also"></a>Zobacz także

[Instrukcje try, throw i catch (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
