---
title: _findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64
ms.date: 11/04/2016
apiname:
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 47a1d7301b59a942a1af860f310e1f1f9da12ec7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333745"
---
# <a name="findfirst-findfirst32-findfirst32i64-findfirst64-findfirst64i32-findfirsti64-wfindfirst-wfindfirst32-wfindfirst32i64-wfindfirst64-wfindfirst64i32-wfindfirsti64"></a>_findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64

Zawierają informacje dotyczące pierwszego wystąpienia nazwy pliku, który pasuje do pliku określonego w *specyfikacja* argumentu.

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

*filespec*<br/>
Specyfikacja pliku docelowego (może zawierać symbole wieloznaczne).

*fileinfo*<br/>
Bufor informacje o pliku.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_findfirst** zwraca uchwyt wyszukiwania unikatowe identyfikowanie pliku lub grupy plików, które odpowiadają *specyfikacja* specyfikacja, która może służyć w następnym wywołaniu do metody [_ FindNext](findnext-functions.md) lub [_findclose —](findclose.md). W przeciwnym razie **_findfirst** zwraca wartość -1 i ustawia **errno** do jednej z następujących wartości.

| errno wartość | Warunek |
|-|-|
| **EINVAL** | Nieprawidłowy parametr: *specyfikacja* lub *fileinfo* został **NULL**. Lub system operacyjny zwrócił nieoczekiwany błąd. |
| **ENOENT** | Specyfikacja pliku nie jest zgodny. |
| **ENOMEM** | Za mało pamięci. |
| **EINVAL** | Nieprawidłowy plik specyfikacja nazwy lub nazwy pliku, biorąc pod uwagę był większy niż **MAX_PATH**. |

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Jeśli podano nieprawidłowy parametr jest przekazywany w, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

Należy wywołać [_findclose —](findclose.md) po zakończeniu albo **_findfirst** lub [_findnext](findnext-functions.md) — funkcja (lub warianty). To powoduje zwolnienie zasobów używanych przez te funkcje w aplikacji.

Zmiany te funkcje, które mają **w** prefiks są wersjami znaków dwubajtowych; w przeciwnym razie są identyczne z odpowiednimi funkcjami jednobajtowych.

Różnice te funkcje obsługuje 32-bitową lub 64-bitowych typów oraz godziny rozmiary plików 32-bitową lub 64-bitowych. Pierwszy sufiksu liczbowego (**32** lub **64**) wskazuje rozmiar typu time; drugi sufiks jest **i32** lub **i64**oraz wskazuje czy rozmiar pliku jest reprezentowany jako 32-bitowy lub 64-bitową liczbę całkowitą. Informacje o tym, które wersje obsługują czasu 32-bitowych i 64-bitowych typów i rozmiarów plików na ten temat można znaleźć w poniższej tabeli. **I32** lub **i64** sufiks jest pomijana, jeżeli jest taki sam jak rozmiar typu czasu, dlatego **_findfirst64 —** również obsługuje 64-bitowy plik długości i **_findfirst32 —**  obsługuje tylko 32-bitowy plik długości.

Te funkcje używają różne rodzaje **_finddata_t —** struktury dla *fileinfo* parametru. Aby uzyskać więcej informacji na temat struktury, zobacz [funkcje wyszukiwania nazwy pliku](../../c-runtime-library/filename-search-functions.md).

Zmiany, które używają typu czasu 64-bitowego Włącz daty tworzenia pliku do się wyraża się poprzez 23:59:59, 31 grudnia 3000, czasu UTC. Te, które używają typów 32-bitowych czasu reprezentują daty wyłącznie za pośrednictwem 23:59:59 18 stycznia 2038 r. UTC. Północy 1 stycznia 1970 r., to dolna granica zakresu dat dla tych funkcji.

Chyba że masz powód, aby użyć wersji, które jawnie określ rozmiar w czasie, użyj **_findfirst** lub **_wfindfirst —** lub, jeśli potrzebujesz do obsługi plików większych niż 3 GB, użyj **_ findfirsti64 —** lub **_wfindfirsti64 —**. Wszystkie te funkcje używają typu czasu 64-bitowych. We wcześniejszych wersjach te funkcje używane typem time 32-bitowych. Jeśli jest to istotną zmianę dla aplikacji, można zdefiniować **_USE_32BIT_TIME_T** można przywrócić poprzednie działanie. Jeśli **_USE_32BIT_TIME_T** jest zdefiniowany, **_findfirst**, **_finfirsti64**, i odpowiadające im wersje Unicode używają czasu 32-bitowych.

### <a name="time-type-and-file-length-type-variations-of-findfirst"></a>Typ czasu i zmian typu długość pliku _findfirst

|Funkcje|**_USE_32BIT_TIME_T** zdefiniowane?|Typ czasu|Typ długość pliku|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**, **_wfindfirst —**|Nie zdefiniowano|64-bitowy|32-bitowa|
|**_findfirst**, **_wfindfirst —**|Definicja|32-bitowa|32-bitowa|
|**_findfirst32**, **_wfindfirst32**|Nie dotyczy definicji makra|32-bitowa|32-bitowa|
|**_findfirst64**, **_wfindfirst64**|Nie dotyczy definicji makra|64-bitowy|64-bitowy|
|**_findfirsti64**, **_wfindfirsti64**|Nie zdefiniowano|64-bitowy|64-bitowy|
|**_findfirsti64**, **_wfindfirsti64**|Definicja|32-bitowa|64-bitowy|
|**_findfirst32i64**, **_wfindfirst32i64**|Nie dotyczy definicji makra|32-bitowa|64-bitowy|
|**_findfirst64i32**, **_wfindfirst64i32**|Nie dotyczy definicji makra|64-bitowy|32-bitowa|

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
|**_findfirst**|\<io.h>|
|**_findfirst32**|\<io.h>|
|**_findfirst64**|\<io.h>|
|**_findfirsti64**|\<io.h>|
|**_findfirst32i64**|\<io.h>|
|**_findfirst64i32**|\<io.h>|
|**_wfindfirst**|\<IO.h > lub \<wchar.h >|
|**_wfindfirst32**|\<IO.h > lub \<wchar.h >|
|**_wfindfirst64**|\<IO.h > lub \<wchar.h >|
|**_wfindfirsti64**|\<IO.h > lub \<wchar.h >|
|**_wfindfirst32i64**|\<IO.h > lub \<wchar.h >|
|**_wfindfirst64i32**|\<IO.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wywołania systemowe](../../c-runtime-library/system-calls.md)<br/>
[Funkcje wyszukiwania nazwy pliku](../../c-runtime-library/filename-search-functions.md)<br/>
