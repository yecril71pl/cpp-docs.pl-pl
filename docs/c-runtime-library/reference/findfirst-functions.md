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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 879a84b14f612992ae7ed3a96211637aaf5c4783
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911738"
---
# <a name="_findfirst-_findfirst32-_findfirst32i64-_findfirst64-_findfirst64i32-_findfirsti64-_wfindfirst-_wfindfirst32-_wfindfirst32i64-_wfindfirst64-_wfindfirst64i32-_wfindfirsti64"></a>_findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64

Podaj informacje o pierwszym wystąpieniu nazwy pliku, która jest zgodna z plikiem określonym w argumencie *Specyfikacja* .

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

*Specyfikacja*<br/>
Specyfikacja pliku docelowego (może zawierać symbole wieloznaczne).

*fileinfo*<br/>
Bufor informacji o plikach.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, **_findfirst** zwraca unikatowy uchwyt wyszukiwania identyfikujący plik lub grupę plików zgodnych ze specyfikacją *Specyfikacja* , która może być używana w kolejnym wywołaniu [_findnext](findnext-functions.md) lub do [_findclose](findclose.md). W przeciwnym razie **_findfirst** zwraca wartość-1 i ustawia **errno** na jedną z następujących wartości.

| errno wartość | Warunek |
|-|-|
| **EINVAL** | Nieprawidłowy parametr: *Specyfikacja* lub *FileInfo* miał **wartość null**. System operacyjny zwrócił nieoczekiwany błąd. |
| **ENOENT** | Specyfikacja pliku, którego nie można dopasować. |
| **ENOMEM** | Za mało pamięci. |
| **EINVAL** | Nieprawidłowa specyfikacja nazwy pliku lub określona nazwa pliku jest większa niż **MAX_PATH**. |

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Jeśli przeszedł nieprawidłowy parametr, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

Musisz wywołać [_findclose](findclose.md) po zakończeniu pracy z funkcją **_findfirst** lub [_findnext](findnext-functions.md) (lub dowolnym wariantem). Spowoduje to zwolnienie zasobów używanych przez te funkcje w aplikacji.

Różnice tych funkcji, które mają prefiks **w** , są wersjami znaków dwubajtowych; w przeciwnym razie są identyczne z odpowiednimi funkcjami jednobajtowymi.

Różnice tych funkcji obsługują 32-bitowe lub 64-bitowe typy czasu i 32-bitowe lub 64-bitowe rozmiary plików. Pierwszy sufiks liczbowy (**32** lub **64**) wskazuje rozmiar typu czasu; drugi sufiks jest **I32** lub **I64**i wskazuje, czy rozmiar pliku jest reprezentowany jako 32-bitowa czy 64-bitowa liczba całkowita. Aby uzyskać informacje o tym, które wersje obsługują 32-bitowe i 64-bitowe typy czasu i rozmiary plików, zobacz poniższą tabelę. Sufiks **I32** lub **I64** jest pomijany, jeśli jest taki sam jak rozmiar typu czasu, więc **_findfirst64** również obsługuje 64-bitowe długości plików, a **_findfirst32** obsługuje tylko 32-bitowe długości plików.

Te funkcje używają różnych form struktury **_finddata_t** dla parametru *FileInfo* . Aby uzyskać więcej informacji na temat struktury, zobacz [funkcje wyszukiwania filename](../../c-runtime-library/filename-search-functions.md).

Różnice, które korzystają z 64-bitowego typu czasu, umożliwiają, że daty tworzenia plików są wyrażane do 23:59:59, 31 grudnia 3000, UTC. Te, które używają 32-bitowego typu czasu reprezentują daty tylko do 23:59:59 stycznia 18, 2038, UTC. Północ, 1 stycznia 1970, to Dolna granica zakresu dat dla wszystkich tych funkcji.

O ile nie masz konkretnej przyczyny używania wersji, które jawnie określają rozmiar czasu, użyj **_findfirst** lub **_wfindfirst** lub, jeśli potrzebujesz obsługiwać rozmiary plików większe niż 3 GB, użyj **_findfirsti64** lub **_wfindfirsti64**. Wszystkie te funkcje korzystają z 64-bitowego typu czasu. We wcześniejszych wersjach te funkcje używały typu czasu 32-bitowego. Jeśli jest to istotna zmiana dla aplikacji, można zdefiniować **_USE_32BIT_TIME_T** , aby przywrócić stare zachowanie. Jeśli **_USE_32BIT_TIME_T** jest zdefiniowany, **_findfirst**, **_finfirsti64**i odpowiadające im wersje Unicode używają czasu 32-bitowego.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findfirst"></a>Typ czasu i typ długości pliku wariacje _findfirst

|Funkcje|**_USE_32BIT_TIME_T** zdefiniowane?|Typ czasu|Typ długości pliku|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**, **_wfindfirst**|Nieokreślona|64-bitowa|32-bitowa|
|**_findfirst**, **_wfindfirst**|Określonych|32-bitowa|32-bitowa|
|**_findfirst32**, **_wfindfirst32**|Nie dotyczy definicji makra|32-bitowa|32-bitowa|
|**_findfirst64**, **_wfindfirst64**|Nie dotyczy definicji makra|64-bitowa|64-bitowa|
|**_findfirsti64**, **_wfindfirsti64**|Nieokreślona|64-bitowa|64-bitowa|
|**_findfirsti64**, **_wfindfirsti64**|Określonych|32-bitowa|64-bitowa|
|**_findfirst32i64**, **_wfindfirst32i64**|Nie dotyczy definicji makra|32-bitowa|64-bitowa|
|**_findfirst64i32**, **_wfindfirst64i32**|Nie dotyczy definicji makra|64-bitowa|32-bitowa|

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
|**_findfirst**|\<IO. h>|
|**_findfirst32**|\<IO. h>|
|**_findfirst64**|\<IO. h>|
|**_findfirsti64**|\<IO. h>|
|**_findfirst32i64**|\<IO. h>|
|**_findfirst64i32**|\<IO. h>|
|**_wfindfirst**|\<IO. h> lub \<WCHAR. h>|
|**_wfindfirst32**|\<IO. h> lub \<WCHAR. h>|
|**_wfindfirst64**|\<IO. h> lub \<WCHAR. h>|
|**_wfindfirsti64**|\<IO. h> lub \<WCHAR. h>|
|**_wfindfirst32i64**|\<IO. h> lub \<WCHAR. h>|
|**_wfindfirst64i32**|\<IO. h> lub \<WCHAR. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Wywołania systemowe](../../c-runtime-library/system-calls.md)<br/>
[Funkcje wyszukiwania nazw plików](../../c-runtime-library/filename-search-functions.md)<br/>
