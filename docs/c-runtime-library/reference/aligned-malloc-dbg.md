---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_malloc_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: 49278c2282698478ad96cc1c7b1ad27add0a6787
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170943"
---
# <a name="_aligned_malloc_dbg"></a>_aligned_malloc_dbg

Przydziela pamięć na określonej granicy wyrównania z dodatkowym miejscem dla nagłówka debugowania i buforów zastąpień (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Rozmiar żądanego przydziału pamięci.

*struktury*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub NULL.

*LineNumber*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub NULL.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, który został przydzielony lub ma wartość NULL, jeśli operacja nie powiodła się.

## <a name="remarks"></a>Uwagi

**_aligned_malloc_dbg** jest wersją debugowania funkcji [_aligned_malloc](aligned-malloc.md) . Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_aligned_malloc_dbg** zostanie zredukowane do wywołania `_aligned_malloc`. Zarówno `_aligned_malloc`, jak i **_aligned_malloc_dbg** przydzielą blok pamięci w stercie podstawowej, ale **_aligned_malloc_dbg** oferuje kilka funkcji debugowania: bufory po obu stronach części bloku, aby przetestować pod kątem przecieków, a *Nazwa pliku*/informacje *LineNumber* do określenia pochodzenia żądań alokacji. Śledzenie określonych typów alokacji przy użyciu parametru typu bloku nie jest obsługiwaną funkcją debugowania dla wyrównanych przydziałów. Wyrównane alokacje będą wyświetlane jako _NORMAL_BLOCK typ bloku.

**_aligned_malloc_dbg** przydziela blok pamięci z nieco większym miejscem niż żądany *rozmiar*. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Gdy blok zostanie przydzielony, część użytkownika bloku jest wypełniania wartościami 0xCD a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.

**_aligned_malloc_dbg** ustawia `errno` do `ENOMEM`, jeśli alokacja pamięci nie powiedzie się lub jeśli wymagana ilość pamięci (łącznie z powyższym obciążeniem) przekracza `_HEAP_MAXREQ`. Aby uzyskać informacje o tym i innych kodach błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_malloc_dbg** sprawdza poprawność jego parametrów. Jeśli *wyrównanie* *nie jest potęgą 2 lub ma* wartość zero, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca wartość NULL i ustawia `errno` na `EINVAL`.

Aby uzyskać informacje o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o typach bloków alokacji i sposobach ich użycia, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywołaniem standardowej funkcji sterty i jej wersji debugowania w kompilacji debugowania aplikacji, zobacz [debugowanie wersji funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<CRTDBG. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Zobacz też

[Procedury debugowania](../../c-runtime-library/debug-routines.md)
