---
title: _heapadd — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _heapadd
apilocation:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- heapadd
- _heapadd
dev_langs:
- C++
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce067dc000a681dfd1bfa9d3376131f86f5a73e1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086853"
---
# <a name="heapadd"></a>_heapadd

Dodaje pamięć do sterty.

> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do pamięci sterty.

*Rozmiar*<br/>
Rozmiar pamięci, aby dodać, w bajtach.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia `_heapadd` zwraca 0; w przeciwnym razie funkcja zwraca wartość -1 i ustawia `errno` do `ENOSYS`.

Aby uzyskać więcej informacji na temat tego i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Począwszy od Visual C++ w wersji 4.0, wewnętrzna struktura sterty został przeniesiony do biblioteki wykonawczej C o obsługę nowych funkcji debugowania. W rezultacie `_heapadd` nie jest już obsługiwany na dowolnej platformie, która jest oparta na Win32 API.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|`_heapadd`|\<malloc.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md) we wstępie.

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../c-runtime-library/memory-allocation.md)<br/>
[free](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)