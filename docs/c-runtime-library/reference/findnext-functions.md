---
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
ms.date: 11/04/2016
api_name:
- _wfindnext
- _findnext
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- findnext
- _wfindnext32i64
- _tfindnext64i32
- findnext32
- findnext32i64
- wfindnext64i32
- _wfindnext
- tfindnext64
- findnexti64
- _findnexti64
- _tfindnexti64
- _findnext64i32
- tfindnexti64
- tfindnext32
- _wfindnext64i32
- findnext64i32
- _findnext
- _tfindnext32i64
- _wfindnext64
- wfindnext
- wfindnext32
- tfindnext32i64
- _findnext64
- _tfindnext64
- _wfindnext32
- findnext64
- _findnext32i64
- tfindnext
- wfindnexti64
- tfindnext64i32
- _tfindnext32
- wfindnext32i64
- wfindnext64
- _wfindnexti64
- _tfindnext
- _findnext32
helpviewer_keywords:
- _wfindnexti64 function
- _tfindnext32 function
- wfindnexti64 function
- _wfindnext32i64 function
- findnext32i64 function
- tfindnext64i32 function
- _tfindnext64i32 function
- _findnext function
- findnext64i32 function
- _tfindnext function
- findnext32 function
- tfindnext32 function
- _findnext32 function
- _tfindnext32i64 function
- _wfindnext function
- tfindnext function
- _findnext64 function
- findnext64 function
- _findnext64i32 function
- wfindnext32i64 function
- findnext function
- wfindnext32 function
- _wfindnext64i32 function
- findnexti64 function
- _wfindnext64 function
- _findnext32i64 function
- _findnexti64 function
- _tfindnext64 function
- wfindnext64i32 function
- tfindnexti64 function
- wfindnext64 function
- wfindnext function
- tfindnext64 function
- _wfindnext32 function
- tfindnext32i64 function
- _tfindnexti64 function
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
ms.openlocfilehash: 083f0f1d383472c104a1e4fcb6f3139c7a9d9c88
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957248"
---
# <a name="_findnext-_findnext32-_findnext32i64-_findnext64-_findnext64i32-_findnexti64-_wfindnext-_wfindnext32-_wfindnext32i64-_wfindnext64-_wfindnext64i32-_wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Znajdź następną nazwę (jeśli istnieje), która pasuje do argumentu *Specyfikacja* w poprzednim wywołaniu [_findfirst](findfirst-functions.md), a następnie odpowiednio zmień zawartość struktury *FileInfo* .

## <a name="syntax"></a>Składnia

```C
int _findnext(
   intptr_t handle,
   struct _finddata_t *fileinfo
);
int _findnext32(
   intptr_t handle,
   struct _finddata32_t *fileinfo
);
int _findnext64(
   intptr_t handle,
   struct __finddata64_t *fileinfo
);
int _findnexti64(
   intptr_t handle,
   struct __finddatai64_t *fileinfo
);
int _findnext32i64(
   intptr_t handle,
   struct _finddata32i64_t *fileinfo
);
int _findnext64i32(
   intptr_t handle,
   struct _finddata64i32_t *fileinfo
);
int _wfindnext(
   intptr_t handle,
   struct _wfinddata_t *fileinfo
);
int _wfindnext32(
   intptr_t handle,
   struct _wfinddata32_t *fileinfo
);
int _wfindnext64(
   intptr_t handle,
   struct _wfinddata64_t *fileinfo
);
int _wfindnexti64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext32i64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext64i32(
   intptr_t handle,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>Parametry

*uchwyty*<br/>
Dojście wyszukiwania zwrócone przez poprzednie wywołanie do **_findfirst**.

*FileInfo*<br/>
Bufor informacji o plikach.

## <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca wartość 0. W przeciwnym razie zwraca-1 i ustawia **errno** na wartość wskazującą charakter błędu. W poniższej tabeli przedstawiono możliwe kody błędów.

|errno wartość|Warunek|
|-|-|
| **EINVAL** | Nieprawidłowy parametr: *FileInfo* miał **wartość null**. System operacyjny zwrócił nieoczekiwany błąd. |
| **ENOENT** | Nie znaleziono więcej pasujących plików. |
| **ENOMEM** | Za mało pamięci lub długość nazwy pliku przekroczyła wartość **MAX_PATH**. |

Jeśli przeszedł nieprawidłowy parametr, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

Musisz wywołać [_findclose](findclose.md) po zakończeniu korzystania z funkcji **_findfirst** lub **_findnext** (lub dowolnego wariantu). Spowoduje to zwolnienie zasobów używanych przez te funkcje w aplikacji.

Różnice tych funkcji **z prefiksem** a są wersjami znaków dwubajtowych; w przeciwnym razie są identyczne z odpowiednimi funkcjami jednobajtowymi.

Różnice tych funkcji obsługują 32-bitowe lub 64-bitowe typy czasu i 32-bitowe lub 64-bitowe rozmiary plików. Pierwszy sufiks numeryczny (**32** lub **64**) wskazuje rozmiar używanego typu czasu; drugi sufiks jest **I32** lub **I64**, wskazując, czy rozmiar pliku jest reprezentowany jako 32-bitowa czy 64-bitowa liczba całkowita. Aby uzyskać informacje o tym, które wersje obsługują 32-bitowe i 64-bitowe typy czasu i rozmiary plików, zobacz poniższą tabelę. Różnice korzystające z typu czasu 64-bitowego zezwalają na wyrażanie dat tworzenia plików do 23:59:59, 31 grudnia 3000, UTC; te, które używają 32-bitowego typu czasu, reprezentują daty tylko do 23:59:59 stycznia 18, 2038, UTC. Północ, 1 stycznia 1970, to Dolna granica zakresu dat dla wszystkich tych funkcji.

O ile nie masz konkretnej przyczyny używania wersji, które jawnie określają rozmiar czasu, użyj **_findnext** lub **_wfindnext** lub, jeśli potrzebujesz obsługiwać rozmiary plików większe niż 3 GB, użyj **_findnexti64** lub **_wfindnexti64**. Wszystkie te funkcje korzystają z 64-bitowego typu czasu. W poprzednich wersjach te funkcje używały typu czasu 32-bitowego. Jeśli jest to istotna zmiana dla aplikacji, można zdefiniować **_USE_32BIT_TIME_T** , aby uzyskać stare zachowanie. Jeśli **_USE_32BIT_TIME_T** jest zdefiniowany, **_findnext**, **_finnexti64** i odpowiadające im wersje Unicode używają czasu 32-bitowego.

### <a name="time-type-and-file-length-type-variations-of-_findnext"></a>Typ czasu i typ długości pliku odmiany _findnext

|Funkcje|Zdefiniowano **_USE_32BIT_TIME_T** ?|Typ czasu|Typ długości pliku|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext**, **_wfindnext**|Nie zdefiniowano|64-bitowy|32-bitowa|
|**_findnext**, **_wfindnext**|Określonych|32-bitowa|32-bitowa|
|**_findnext32**, **_wfindnext32**|Nie dotyczy definicji makra|32-bitowa|32-bitowa|
|**_findnext64**, **_wfindnext64**|Nie dotyczy definicji makra|64-bitowy|64-bitowy|
|**_findnexti64**, **_wfindnexti64**|Nie zdefiniowano|64-bitowy|64-bitowy|
|**_findnexti64**, **_wfindnexti64**|Określonych|32-bitowa|64-bitowy|
|**_findnext32i64**, **_wfindnext32i64**|Nie dotyczy definicji makra|32-bitowa|64-bitowy|
|**_findnext64i32**, **_wfindnext64i32**|Nie dotyczy definicji makra|64-bitowy|32-bitowa|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_findnext**|\<io.h>|
|**_findnext32**|\<io.h>|
|**_findnext64**|\<io.h>|
|**_findnexti64**|\<io.h>|
|**_findnext32i64**|\<io.h>|
|**_findnext64i32**|\<io.h>|
|**_wfindnext**|\<IO. h > lub \<WCHAR. h >|
|**_wfindnext32**|\<IO. h > lub \<WCHAR. h >|
|**_wfindnext64**|\<IO. h > lub \<WCHAR. h >|
|**_wfindnexti64**|\<IO. h > lub \<WCHAR. h >|
|**_wfindnext32i64**|\<IO. h > lub \<WCHAR. h >|
|**_wfindnext64i32**|\<IO. h > lub \<WCHAR. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Wywołania systemowe](../../c-runtime-library/system-calls.md)<br/>
[Funkcje wyszukiwania nazwy pliku](../../c-runtime-library/filename-search-functions.md)<br/>
