---
title: _query_new_mode
ms.date: 11/04/2016
api_name:
- _query_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 59724dafdc6488596478d0b44b254c4f498fce99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950113"
---
# <a name="_query_new_mode"></a>_query_new_mode

Zwraca liczbę całkowitą wskazującą nowy tryb obsługi ustawiony przez **_set_new_mode** dla **malloc**.

## <a name="syntax"></a>Składnia

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca bieżący nowy tryb obsługi, czyli 0 lub 1, dla **malloc**. Zwracana wartość 1 oznacza, że w przypadku niepowodzenia przydzielenia pamięci, **malloc** wywołuje nową procedurę obsługi; wartość zwracana przez 0 wskazuje, że nie.

## <a name="remarks"></a>Uwagi

C++ Funkcja **_query_new_mode** zwraca liczbę całkowitą, która wskazuje nowy tryb obsługi ustawiony C++ przez funkcję [_set_new_mode](set-new-mode.md) dla opcji [malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku niemożności przydzielenia pamięci, **malloc** ma wywołać nową procedurę obsługi jako ustawioną przez [_set_new_handler](set-new-handler.md). Domyślnie funkcja **malloc** nie wywołuje nowej procedury obsługi w przypadku niepowodzenia. Możesz użyć **_set_new_mode** , aby zastąpić to zachowanie, tak aby w przypadku niepowodzenia **malloc** wywołuje nową procedurę obsługi w taki sam sposób, jak w przypadku niepowodzenia przydzielenia pamięci przez operatora **New** . Aby uzyskać więcej informacji, zobacz Omówienie [operatorów New i DELETE](../../cpp/new-and-delete-operators.md) w dokumentacji C++ języka.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
