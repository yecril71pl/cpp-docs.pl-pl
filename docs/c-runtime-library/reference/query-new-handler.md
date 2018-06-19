---
title: _query_new_handler — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _query_new_handler
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _query_new_handler
- query_new_handler
dev_langs:
- C++
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 340574a57bf1e6309ac9a5e1aa59b7e28632ae59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401002"
---
# <a name="querynewhandler"></a>_query_new_handler

Zwraca adres bieżącej nowe procedury obsługi.

## <a name="syntax"></a>Składnia

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca adres bieżącej nowe procedury obsługi zgodnie z ustawieniami **_set_new_handler —**.

## <a name="remarks"></a>Uwagi

C++ **_query_new_handler —** funkcja zwraca adres bieżącej funkcji obsługi wyjątków, ustawione przez C++ [_set_new_handler —](set-new-handler.md) funkcji. **_set_new_handler —** służy do określania funkcji obsługi wyjątków, która jest przejęcie kontroli, jeśli **nowe** operator nie może przydzielić pamięci. Aby uzyskać więcej informacji, zobacz Omówienie [nowy i delete — operatory](../../cpp/new-and-delete-operators.md) w dokumentacja języka C++.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
