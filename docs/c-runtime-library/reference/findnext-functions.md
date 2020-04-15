---
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
ms.date: 4/2/2020
api_name:
- _findnext
- _findnext32
- _findnext32i64
- _findnext64
- _findnext64i32
- _findnexti64
- _wfindnext
- _wfindnext32
- _wfindnext32i64
- _wfindnext64
- _wfindnext64i32
- _wfindnexti64
- _o__findnext32
- _o__findnext32i64
- _o__findnext64
- _o__findnext64i32
- _o__wfindnext32
- _o__wfindnext32i64
- _o__wfindnext64
- _o__wfindnext64i32
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
ms.openlocfilehash: 38243b48a97c038f36ada85e3ca2cda814f43fa8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346738"
---
# <a name="_findnext-_findnext32-_findnext32i64-_findnext64-_findnext64i32-_findnexti64-_wfindnext-_wfindnext32-_wfindnext32i64-_wfindnext64-_wfindnext64i32-_wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Znajdź następną nazwę, jeśli istnieje, która pasuje do argumentu *filespec* w poprzednim wywołaniu [_findfirst](findfirst-functions.md), a następnie odpowiednio zmień zawartość struktury *fileinfo.*

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

*Obsługi*<br/>
Uchwyt wyszukiwania zwrócony przez poprzednie wywołanie **_findfirst**.

*fileinfo*<br/>
Bufor informacji o pliku.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca wartość 0. W przeciwnym razie zwraca wartość -1 i ustawia **errno** na wartość wskazującą charakter błędu. Możliwe kody błędów są pokazane w poniższej tabeli.

|wartość errno|Warunek|
|-|-|
| **Einval** | Nieprawidłowy parametr: *fileinfo* miał **wartość NULL**. Lub system operacyjny zwrócił nieoczekiwany błąd. |
| **Enoent** | Nie można było znaleźć więcej pasujących plików. |
| **ENOMEM ( ENOMEM )** | Za mało pamięci lub długość nazwy pliku przekroczyła **MAX_PATH**. |

Jeśli nieprawidłowy parametr jest przekazywany, te funkcje wywołają nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

Należy wywołać [_findclose](findclose.md) po zakończeniu korzystania **z funkcji _findfirst** lub **_findnext** (lub dowolnych wariantów). Zwalnia to zasoby używane przez te funkcje w aplikacji.

Odmiany tych funkcji z prefiksem **w** są wersjami szerokoznakowymi; w przeciwnym razie są one identyczne z odpowiednimi funkcjami jedno bajtowymi.

Odmiany tych funkcji obsługują 32-bitowe lub 64-bitowe typy czasu oraz 32-bitowe lub 64-bitowe rozmiary plików. Pierwszy przyrostek numeryczny (**32** lub **64**) wskazuje rozmiar używanego typu czasu; drugi sufiks to **i32** lub **i64**, wskazujący, czy rozmiar pliku jest reprezentowany jako 32-bitowa czy 64-bitowa liczba całkowita. Aby uzyskać informacje o wersjach obsługujących 32-bitowe i 64-bitowe typy i rozmiary plików, zobacz poniższą tabelę. Odmiany, które używają 64-bitowego typu czasu, umożliwiają wyrażenie dat tworzenia plików do 23:59:59, 31 grudnia 3000, UTC; mając na uwadze, że te przy użyciu typów czasu 32-bitowego reprezentują tylko daty do 23:59:59 18 stycznia 2038, UTC. Północ, 1 stycznia 1970 r., jest dolną granicą zakresu dat dla wszystkich tych funkcji.

Jeśli nie masz określonego powodu, aby użyć wersji, które określają rozmiar czasu jawnie, użyj **_findnext** lub **_wfindnext** lub, jeśli chcesz obsługiwać rozmiary plików większe niż 3 GB, użyj **_findnexti64** lub **_wfindnexti64**. Wszystkie te funkcje używają typu czasu 64-bitowego. W poprzednich wersjach te funkcje używane typu czasu 32-bitowego. Jeśli jest to zmiana podziału dla aplikacji, można zdefiniować **_USE_32BIT_TIME_T,** aby uzyskać stare zachowanie. Jeśli **zdefiniowano _USE_32BIT_TIME_T,** **_findnext** **, _finnexti64** i odpowiadające im wersje Unicode używają czasu 32-bitowego.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findnext"></a>Zmiany typu i długości pliku _findnext

|Funkcje|**_USE_32BIT_TIME_T** zdefiniowane?|Typ czasu|Typ długości pliku|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext**, **_wfindnext**|Nieokreślona|64-bitowy|32-bitowa|
|**_findnext**, **_wfindnext**|Zdefiniowane|32-bitowa|32-bitowa|
|**_findnext32** **, _wfindnext32**|Definicja makra nie ma na nie wpływu|32-bitowa|32-bitowa|
|**_findnext64** **, _wfindnext64**|Definicja makra nie ma na nie wpływu|64-bitowy|64-bitowy|
|**_findnexti64** **, _wfindnexti64**|Nieokreślona|64-bitowy|64-bitowy|
|**_findnexti64** **, _wfindnexti64**|Zdefiniowane|32-bitowa|64-bitowy|
|**_findnext32i64** **, _wfindnext32i64**|Definicja makra nie ma na nie wpływu|32-bitowa|64-bitowy|
|**_findnext64i32** **, _wfindnext64i32**|Definicja makra nie ma na nie wpływu|64-bitowy|32-bitowa|

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
|**_findnext**|\<> io.h|
|**_findnext32**|\<> io.h|
|**_findnext64**|\<> io.h|
|**_findnexti64**|\<> io.h|
|**_findnext32i64**|\<> io.h|
|**_findnext64i32**|\<> io.h|
|**_wfindnext**|\<io.h> lub \<wchar.h>|
|**_wfindnext32**|\<io.h> lub \<wchar.h>|
|**_wfindnext64**|\<io.h> lub \<wchar.h>|
|**_wfindnexti64**|\<io.h> lub \<wchar.h>|
|**_wfindnext32i64**|\<io.h> lub \<wchar.h>|
|**_wfindnext64i32**|\<io.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[Wywołania systemowe](../../c-runtime-library/system-calls.md)<br/>
[Funkcje wyszukiwania nazwy plików](../../c-runtime-library/filename-search-functions.md)<br/>
