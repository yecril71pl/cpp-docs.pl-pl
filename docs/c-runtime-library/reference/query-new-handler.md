---
title: _query_new_handler
ms.date: 11/04/2016
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
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
ms.openlocfilehash: febefbe46d95b7e5c8de026806a20d7eff74e7cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357881"
---
# <a name="querynewhandler"></a>_query_new_handler

Zwraca adres bieżącej nową procedurę obsługi.

## <a name="syntax"></a>Składnia

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca adres bieżącej nową procedurę obsługi zgodnie z ustawieniem **_set_new_handler**.

## <a name="remarks"></a>Uwagi

C++ **_Query_new_handler —** funkcja zwraca adres bieżącej funkcji obsługi wyjątków, ustawiane przez C++ [_set_new_handler](set-new-handler.md) funkcji. **_set_new_handler** służy do określania funkcji obsługi wyjątków, która jest przejęcie kontroli, jeśli **nowe** operator nie może przydzielić pamięci. Aby uzyskać więcej informacji, zobacz Omówienie [nowych i delete — operatory](../../cpp/new-and-delete-operators.md) w dokumentacji języka C++.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
