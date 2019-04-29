---
title: _query_new_mode
ms.date: 11/04/2016
apiname:
- _query_new_mode
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
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 327f22c847793316bd126721b4a66846d7da84dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358076"
---
# <a name="querynewmode"></a>_query_new_mode

Zwraca liczbę całkowitą wskazującą nowy tryb obsługi ustawione przez **_set_new_mode** dla **— funkcja malloc**.

## <a name="syntax"></a>Składnia

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca bieżący nowy tryb obsługi, a mianowicie 0 lub 1, **— funkcja malloc**. Zwracana wartość 1 oznacza, że, w przypadku niepowodzenia, można przydzielić pamięci, **— funkcja malloc** wywoła nową procedurę obsługi; zwracana wartość wynosząca 0 wskazuje, czy nie.

## <a name="remarks"></a>Uwagi

C++ **_Query_new_mode —** funkcji zwraca liczbę całkowitą, wskazującą nowy tryb obsługi, który jest uporządkowany według C++ [_set_new_mode](set-new-mode.md) działać w ramach [— funkcja malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku awarii można przydzielić pamięci, **— funkcja malloc** ma wywoływać nową procedurę obsługi zgodnie z ustawieniem [_set_new_handler](set-new-handler.md). Domyślnie **— funkcja malloc** nie wywołuje nowej procedury obsługi w przypadku niepowodzenia. Możesz użyć **_set_new_mode** zastąpienia tego zachowania, więc, w przypadku niepowodzenia **— funkcja malloc** wywoła nową procedurę obsługi w taki sam sposób **nowe** operator nie, gdy nie jest on Przydzielanie pamięci. Aby uzyskać więcej informacji, zobacz Omówienie [nowych i delete — operatory](../../cpp/new-and-delete-operators.md) w dokumentacji języka C++.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
