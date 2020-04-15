---
title: _heapadd
ms.date: 11/04/2016
api_name:
- _heapadd
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapadd
- _heapadd
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
ms.openlocfilehash: c5eeb66ff0e6fb05063ec395e12cd97106ad724d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351323"
---
# <a name="_heapadd"></a>_heapadd

Dodaje pamięć do sterty.

> [!IMPORTANT]
> Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Wskaźnik do pamięci sterty.

*Rozmiar*<br/>
Rozmiar pamięci do dodania w bajtach.

## <a name="return-value"></a>Wartość zwracana

Jeśli się `_heapadd` powiedzie, zwraca wartość 0; w przeciwnym razie funkcja zwraca `errno` wartość `ENOSYS`-1 i ustawia na .

Aby uzyskać więcej informacji na temat tego i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual C++ w wersji 4.0, podstawowa struktura sterty została przeniesiona do bibliotek w czasie wykonywania języka C w celu obsługi nowych funkcji debugowania. W rezultacie `_heapadd` nie jest już obsługiwana na żadnej platformie, która jest oparta na interfejsie API Win32.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|`_heapadd`|\<> malloc.h|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../c-runtime-library/compatibility.md) we wstępie.

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../c-runtime-library/memory-allocation.md)<br/>
[Wolna](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)
