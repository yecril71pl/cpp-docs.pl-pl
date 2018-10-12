---
title: _abnormal_termination | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 053fa3559672e4b314d209184c076e8ced2018db
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162155"
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

## <a name="see-also"></a>Zobacz też

[try-finally, instrukcja](../cpp/try-finally-statement.md)