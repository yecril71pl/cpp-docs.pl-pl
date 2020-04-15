---
title: _findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64
ms.date: 4/2/2020
api_name:
- _findfirst
- _wfindfirst
- _findfirst32
- _wfindfirst32
- _findfirst32i64
- _wfindfirst32i64
- _findfirst64
- _wfindfirst64
- _findfirst64i32
- _wfindfirst64i32
- _findfirsti64
- _wfindfirsti64
- _o__findfirst32
- _o__findfirst32i64
- _o__findfirst64
- _o__findfirst64i32
- _o__wfindfirst32
- _o__wfindfirst32i64
- _o__wfindfirst64
- _o__wfindfirst64i32
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
ms.openlocfilehash: d83cc0913584618897cbc4aec45cb137388674b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346810"
---
# <a name="_findfirst-_findfirst32-_findfirst32i64-_findfirst64-_findfirst64i32-_findfirsti64-_wfindfirst-_wfindfirst32-_wfindfirst32i64-_wfindfirst64-_wfindfirst64i32-_wfindfirsti64"></a>_findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64

Podaj informacje o pierwszym wystąpieniu nazwy pliku, która pasuje do pliku określonego w argurze *filespec.*

## <a name="syntax"></a>Składnia

```C
intptr_t _findfirst(
   const char *filespec,
   struct _finddata_t *fileinfo
);
intptr_t _findfirst32(
   const char *filespec,
   struct _finddata32_t *fileinfo
);
intptr_t _findfirst64(
   const char *filespec,
   struct _finddata64_t *fileinfo
);
intptr_t _findfirsti64(
   const char *filespec,
   struct _finddatai64_t *fileinfo
);
intptr_t _findfirst32i64(
   const char *filespec,
   struct _finddata32i64_t *fileinfo
);
intptr_t _findfirst64i32(
   const char *filespec,
   struct _finddata64i32_t *fileinfo
);
intptr_t _wfindfirst(
   const wchar_t *filespec,
   struct _wfinddata_t *fileinfo
);
intptr_t _wfindfirst32(
   const wchar_t *filespec,
   struct _wfinddata32_t *fileinfo
);
intptr_t _wfindfirst64(
   const wchar_t *filespec,
   struct _wfinddata64_t *fileinfo
);
intptr_t _wfindfirsti64(
   const wchar_t *filespec,
   struct _wfinddatai64_t *fileinfo
);
intptr_t _wfindfirst32i64(
   const wchar_t *filespec,
   struct _wfinddata32i64_t *fileinfo
);
intptr_t _wfindfirst64i32(
   const wchar_t *filespec,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>Parametry

*Filespec*<br/>
Specyfikacja pliku docelowego (może zawierać symbole wieloznaczne).

*fileinfo*<br/>
Bufor informacji o pliku.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **_findfirst** zwraca unikatowy uchwyt wyszukiwania identyfikujący plik lub grupę plików, które odpowiadają specyfikacji *filespec,* która może być użyta w kolejnym wywołaniu [do _findnext](findnext-functions.md) lub [_findclose](findclose.md). W przeciwnym razie **_findfirst** zwraca wartość -1 i ustawia **errno** na jedną z następujących wartości.

| wartość errno | Warunek |
|-|-|
| **Einval** | Nieprawidłowy parametr: *filespec* lub *fileinfo* miał **wartość NULL**. Lub system operacyjny zwrócił nieoczekiwany błąd. |
| **Enoent** | Specyfikacja pliku, których nie można dopasować. |
| **ENOMEM ( ENOMEM )** | Za mało pamięci. |
| **Einval** | Nieprawidłowa specyfikacja nazwy pliku lub podana nazwa pliku była większa niż **MAX_PATH**. |

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Jeśli nieprawidłowy parametr jest przekazywany, te funkcje wywołają nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

Należy wywołać [_findclose](findclose.md) po zakończeniu funkcji **_findfirst** lub [_findnext](findnext-functions.md) (lub dowolnych wariantów). Zwalnia to zasoby używane przez te funkcje w aplikacji.

Odmiany tych funkcji, które mają prefiks **w** są wersje szerokoznakowe; w przeciwnym razie są one identyczne z odpowiednimi funkcjami jedno bajtowymi.

Odmiany tych funkcji obsługują 32-bitowe lub 64-bitowe typy czasu oraz 32-bitowe lub 64-bitowe rozmiary plików. Pierwszy przyrostek liczbowy (**32** lub **64**) wskazuje rozmiar typu czasu; drugi sufiks to **i32** lub **i64**i wskazuje, czy rozmiar pliku jest reprezentowany jako 32-bitowa czy 64-bitowa liczba całkowita. Aby uzyskać informacje o wersjach obsługujących 32-bitowe i 64-bitowe typy i rozmiary plików, zobacz poniższą tabelę. Sufiks **i32** lub **i64** jest pomijany, jeśli jest taki sam jak rozmiar typu czasu, więc **_findfirst64** obsługuje również 64-bitowe długości plików i **_findfirst32** obsługuje tylko 32-bitowe długości plików.

Funkcje te używają różnych form struktury **_finddata_t** dla parametru *fileinfo.* Aby uzyskać więcej informacji na temat struktury, zobacz [Funkcje wyszukiwania nazwy pliku](../../c-runtime-library/filename-search-functions.md).

Odmiany, które używają 64-bitowego typu czasu umożliwiają daty tworzenia plików do wyrażania w górę przez 23:59:59, 31 grudnia 3000, UTC. Te, które używają 32-bitowych typów czasu reprezentują daty tylko do 23:59:59 18 stycznia 2038, UTC. Północ, 1 stycznia 1970 r., jest dolną granicą zakresu dat dla wszystkich tych funkcji.

Jeśli nie masz określonego powodu, aby użyć wersji, które określają rozmiar czasu jawnie, użyj **_findfirst** lub **_wfindfirst** lub, jeśli chcesz obsługiwać rozmiary plików większych niż 3 GB, użyj **_findfirsti64** lub **_wfindfirsti64**. Wszystkie te funkcje używają typu czasu 64-bitowego. We wcześniejszych wersjach te funkcje używane typu czasu 32-bitowego. Jeśli jest to zmiana podziału dla aplikacji, można zdefiniować **_USE_32BIT_TIME_T,** aby powrócić do starego zachowania. Jeśli **zdefiniowano _USE_32BIT_TIME_T,** **_findfirst**, **_finfirsti64**, a ich odpowiednie wersje Unicode używają czasu 32-bitowego.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findfirst"></a>Zmiany typu i długości pliku _findfirst

|Funkcje|**_USE_32BIT_TIME_T** zdefiniowane?|Typ czasu|Typ długości pliku|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst** **, _wfindfirst**|Nieokreślona|64-bitowy|32-bitowa|
|**_findfirst** **, _wfindfirst**|Zdefiniowane|32-bitowa|32-bitowa|
|**_findfirst32** **, _wfindfirst32**|Definicja makra nie ma na nie wpływu|32-bitowa|32-bitowa|
|**_findfirst64** **, _wfindfirst64**|Definicja makra nie ma na nie wpływu|64-bitowy|64-bitowy|
|**_findfirsti64** **, _wfindfirsti64**|Nieokreślona|64-bitowy|64-bitowy|
|**_findfirsti64** **, _wfindfirsti64**|Zdefiniowane|32-bitowa|64-bitowy|
|**_findfirst32i64**, **_wfindfirst32i64**|Definicja makra nie ma na nie wpływu|32-bitowa|64-bitowy|
|**_findfirst64i32** **, _wfindfirst64i32**|Definicja makra nie ma na nie wpływu|64-bitowy|32-bitowa|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindfirst**|**_findfirst**|**_findfirst**|**_wfindfirst**|
|**_tfindfirst32**|**_findfirst32**|**_findfirst32**|**_wfindfirst32**|
|**_tfindfirst64**|**_findfirst64**|**_findfirst64**|**_wfindfirst64**|
|**_tfindfirsti64**|**_findfirsti64**|**_findfirsti64**|**_wfindfirsti64**|
|**_tfindfirst32i64**|**_findfirst32i64**|**_findfirst32i64**|**_wfindfirst32i64**|
|**_tfindfirst64i32**|**_findfirst64i32**|**_findfirst64i32**|**_wfindfirst64i32**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_findfirst**|\<> io.h|
|**_findfirst32**|\<> io.h|
|**_findfirst64**|\<> io.h|
|**_findfirsti64**|\<> io.h|
|**_findfirst32i64**|\<> io.h|
|**_findfirst64i32**|\<> io.h|
|**_wfindfirst**|\<io.h> lub \<wchar.h>|
|**_wfindfirst32**|\<io.h> lub \<wchar.h>|
|**_wfindfirst64**|\<io.h> lub \<wchar.h>|
|**_wfindfirsti64**|\<io.h> lub \<wchar.h>|
|**_wfindfirst32i64**|\<io.h> lub \<wchar.h>|
|**_wfindfirst64i32**|\<io.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Wywołania systemowe](../../c-runtime-library/system-calls.md)<br/>
[Funkcje wyszukiwania nazwy plików](../../c-runtime-library/filename-search-functions.md)<br/>
