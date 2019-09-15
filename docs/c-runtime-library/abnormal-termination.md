---
title: _abnormal_termination
ms.date: 11/04/2016
api_name:
- _abnormal_termination
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: b66cf0df998b4e33a9f3425fdf0f260d163f423b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944710"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

Wskazuje, `__finally` czy blok [instrukcji try-finally](../cpp/try-finally-statement.md) jest wprowadzany, gdy system wykonuje wewnętrzną listę programów obsługi zakończenia.

## <a name="syntax"></a>Składnia

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli system nie powoduje *odwinięcia* stosu; w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

Jest to wewnętrzna funkcja używana do zarządzania wyjątkami, która nie jest przeznaczona do wywoływania z kodu użytkownika.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>Zobacz także

[try-finally, instrukcja](../cpp/try-finally-statement.md)
