---
title: _abnormal_termination
ms.date: 11/04/2016
apiname:
- _abnormal_termination
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: 213938fa830f0a924fa954d4a36a39b544473dd4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290875"
---
# <a name="abnormaltermination"></a>_abnormal_termination

Wskazuje, czy `__finally` bloku [try-finally — instrukcja](../cpp/try-finally-statement.md) zostanie wprowadzona podczas, gdy system wykonuje wewnętrzną listę obsługi zakończenia.

## <a name="syntax"></a>Składnia

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Wartość zwracana

**wartość true,** w przypadku systemu *odwijania* stosu; w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

Jest używany do zarządzania odwijania wyjątków funkcji wewnętrznej, a nie jest przeznaczona do wywoływania z kodu użytkownika.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>Zobacz także

[try-finally, instrukcja](../cpp/try-finally-statement.md)
