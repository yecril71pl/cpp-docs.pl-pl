---
title: _findnext —, _findnext32 —, _findnext32i64 —, _findnext64 —, _findnext64i32 —, _findnexti64 —, _wfindnext —, _wfindnext32 —, _wfindnext32i64 —, _wfindnext64 —, _wfindnext64i32 —, _wfindnexti64 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfindnext
- _findnext
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 540ec2aae5e13df68438c74e0371e91326e9bb0a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405565"
---
# <a name="findnext-findnext32-findnext32i64-findnext64-findnext64i32-findnexti64-wfindnext-wfindnext32-wfindnext32i64-wfindnext64-wfindnext64i32-wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Znaleźć nazwę Dalej, jeśli istnieje, odpowiadający *Specyfikacja pliku* argument poprzednie wywołanie [_findfirst —](findfirst-functions.md), a następnie zmienić *fileinfo* odpowiednio struktury zawartości.

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

*Dojście*<br/>
Dojście wyszukiwania zwrócony przez poprzednie wywołanie **_findfirst —**.

*fileinfo*<br/>
Bufor informacji o pliku.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wartość 0. W przeciwnym razie zwraca wartość -1 i ustawia **errno** wartość wskazującą naturę niepowodzenia. W poniższej tabeli przedstawiono możliwych kodów błędów.

|errno wartość|Warunek|
|-|-|
**EINVAL —**|Nieprawidłowy parametr: *fileinfo* został **NULL**. Lub system operacyjny zwrócił nieoczekiwany błąd.
**ENOENT —**|Brak pasujących plików można znaleźć.
**ENOMEM —**|Za mało pamięci lub długość nazwy pliku **MAX_PATH**.

Jeśli przekazano nieprawidłowy parametr tych funkcji Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

Należy wywołać [_findclose —](findclose.md) po zakończeniu za pomocą **_findfirst —** lub **_findnext —** — funkcja (lub warianty). Zwalnia zasoby używane przez te funkcje w aplikacji.

Zmiany te funkcje za pomocą **w** prefiks są wersje znaków dwubajtowych; w przeciwnym razie są one takie same jak odpowiednie funkcje jednobajtowe.

Zmiany tych funkcji obsługuje typy czasu 32-bitowy lub 64-bitowej i rozmiary plików 32-bitowy lub 64-bitowej. Pierwszy liczbowego sufiksu (**32** lub **64**) wskazuje rozmiar czasu używany typ; jest drugi sufiks **i32** lub **komputerach 64**, wskazującą, czy rozmiar pliku jest reprezentowany jako 32-bitowy lub 64-bitowej liczby całkowitej. Aby uzyskać informacje o tym, które wersje obsługują typy czasu 32-bitowe i 64-bitowe i rozmiary plików Zobacz poniższą tabelę. Zezwalaj na zmiany, używające typu czasu 64-bitowych daty utworzenia pliku wyrażane się za pośrednictwem 23:59:59 31 grudnia 3000 UTC; te przy użyciu tylko typy czasu 32-bitowych stanowią dat za pośrednictwem 23:59:59 18 stycznia 2038 r., UTC. Północy, 1 stycznia 1970 jest dolna granica zakresu dat dla tych funkcji.

Jeśli nie masz powód, aby użyć wersji, które jawnie określ rozmiar w czasie, użyj **_findnext —** lub **_wfindnext —** lub, jeśli zachodzi potrzeba obsługi plików o rozmiarze przekraczającym 3 GB, użyj **_ findnexti64 —** lub **_wfindnexti64 —**. Wszystkie te funkcje Użyj typu czasu 64-bitowych. W poprzednich wersjach typem time 32-bitowych używać tych funkcji. Jeśli jest to istotne zmiany dla aplikacji, można zdefiniować **_USE_32BIT_TIME_T** uzyskać poprzednie działanie. Jeśli **_USE_32BIT_TIME_T** jest zdefiniowany, **_findnext —**, **_finnexti64** i odpowiadające im wersje Unicode, użyj czasu 32-bitowych.

### <a name="time-type-and-file-length-type-variations-of-findnext"></a>Typ czasu i zmian typu długość pliku _findnext —

|Funkcje|**_USE_32BIT_TIME_T** zdefiniowane?|Typu czasu|Typ długość pliku|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext —**, **_wfindnext —**|Nie zdefiniowano|64-bitowy|32-bitowa|
|**_findnext —**, **_wfindnext —**|Definicja|32-bitowa|32-bitowa|
|**_findnext32 —**, **_wfindnext32 —**|Nie dotyczy definicji makra|32-bitowa|32-bitowa|
|**_findnext64 —**, **_wfindnext64 —**|Nie dotyczy definicji makra|64-bitowy|64-bitowy|
|**_findnexti64 —**, **_wfindnexti64 —**|Nie zdefiniowano|64-bitowy|64-bitowy|
|**_findnexti64 —**, **_wfindnexti64 —**|Definicja|32-bitowa|64-bitowy|
|**_findnext32i64 —**, **_wfindnext32i64 —**|Nie dotyczy definicji makra|32-bitowa|64-bitowy|
|**_findnext64i32 —**, **_wfindnext64i32 —**|Nie dotyczy definicji makra|64-bitowy|32-bitowa|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext —**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32 —**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64 —**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64 —**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64 —**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32 —**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_findnext**|\<io.h>|
|**_findnext32**|\<io.h>|
|**_findnext64**|\<io.h>|
|**_findnexti64**|\<io.h>|
|**_findnext32i64**|\<io.h>|
|**_findnext64i32**|\<io.h>|
|**_wfindnext**|\<IO.h > lub \<wchar.h >|
|**_wfindnext32**|\<IO.h > lub \<wchar.h >|
|**_wfindnext64**|\<IO.h > lub \<wchar.h >|
|**_wfindnexti64**|\<IO.h > lub \<wchar.h >|
|**_wfindnext32i64**|\<IO.h > lub \<wchar.h >|
|**_wfindnext64i32**|\<IO.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Wywołania systemowe](../../c-runtime-library/system-calls.md)<br/>
[Funkcje wyszukiwania nazwy pliku](../../c-runtime-library/filename-search-functions.md)<br/>
