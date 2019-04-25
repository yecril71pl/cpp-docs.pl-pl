---
title: _msize
ms.date: 11/04/2016
apiname:
- _msize
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
- msize
- _msize
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
ms.openlocfilehash: 0321e42face817a0a9f12d780f72c86c67ba308d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156294"
---
# <a name="msize"></a>_msize

Zwraca rozmiar bloku pamięci przydzielone w stosie.

## <a name="syntax"></a>Składnia

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci.

## <a name="return-value"></a>Wartość zwracana

**_msize —** zwraca rozmiar (w bajtach) jako liczbę całkowitą bez znaku.

## <a name="remarks"></a>Uwagi

**_Msize —** funkcja zwraca rozmiar w bajtach, blok pamięci przydzielonej przez wywołanie **calloc**, **— funkcja malloc**, lub **realloc**.

Gdy aplikacja jest połączona z wersji debugowania bibliotek uruchomieniowych C, **_msize —** jest rozpoznawana jako [_msize_dbg —](msize-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania stosem podczas debugowania, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja sprawdza poprawność swojego parametru. Jeśli *memblock* jest pustym wskaźnikiem, **_msize —** wywołuje program obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli obsługiwany jest błąd, funkcja ustawia **errno** do **EINVAL** i zwraca wartość -1.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [realloc](realloc.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
