---
title: _getdcwd, _wgetdcwd
ms.date: 11/04/2016
apiname:
- _getdcwd
- _wgetdcwd
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
ms.openlocfilehash: 464a254775d9a1d2488247d6dafb4b85cd763f10
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702937"
---
# <a name="getdcwd-wgetdcwd"></a>_getdcwd, _wgetdcwd

Pobiera pełną ścieżkę bieżącego katalogu roboczego na określonym dysku.

## <a name="syntax"></a>Składnia

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parametry

*drive*<br/>
Nieujemna liczba całkowita, określająca dysk (0 = dysk domyślny, 1 = A, 2 = B i tak dalej).

Jeśli określony dysk nie jest dostępny, lub rodzaju dysku (na przykład, wymienny, stały, CD-ROM, dysk RAM lub dysk sieciowy) nie można ustalić, zostanie wywołany nieprawidłowy parametr uchwytu. Aby uzyskać więcej informacji, zobacz [Parameter Validation](../../c-runtime-library/parameter-validation.md).

*buffer*<br/>
Lokalizacja magazynu dla ścieżki, lub **NULL**.

Jeśli **NULL** jest określona, ta funkcja przydziela bufor o co najmniej *maxlen* rozmiar przy użyciu **— funkcja malloc**i wartość zwracana przez **_getdcwd —** jest wskaźnikiem do przydzielonego buforu. Bufor może zostać uwolniony przez wywołanie metody **bezpłatne** i przekazywania jemu wskaźnika.

*maxlen*<br/>
Wartość różną od zera dodatnia liczba całkowita, określająca maksymalną długość ścieżki w znakach: **char** dla **_getdcwd —** i **wchar_t** dla **_wgetdcwd —**.

Jeśli *maxlen* jest mniejszy niż lub równy zero, obsługi parametru zostanie wywołana. Aby uzyskać więcej informacji, zobacz [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu, który reprezentuje pełną ścieżkę bieżącego katalogu roboczego na określonym dysku lub **NULL**, który wskazuje na błąd.

Jeśli *buforu* jest określony jako **NULL** i ma za mało pamięci do przydzielenia *maxlen* znaków, wystąpi błąd i **errno** jest Ustaw **ENOMEM**. Jeśli długość ścieżki, w tym kończącego znaku null przekroczy *maxlen*, wystąpi błąd, i **errno** ustawiono **ERANGE**. Aby uzyskać więcej informacji na temat tych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Getdcwd —** funkcja pobiera pełną ścieżkę bieżącego katalogu roboczego na określonym dysku i zapisuje go w *buforu*. Jeśli bieżący katalog roboczy jest ustawiony na katalog główny, ciąg kończy się znakiem kreski ułamkowej odwróconej (\\). Jeśli bieżący katalog roboczy jest ustawiony na katalog inny niż katalog główny, ciąg kończy się nazwą katalogu, a nie znakiem kreski ułamkowej odwróconej.

**_wgetdcwd —** to wersja znaku dwubajtowego **_getdcwd —**, a jego *buforu* parametru i wartości zwracane to ciągi znaków dwubajtowych. W przeciwnym razie **_wgetdcwd —** i **_getdcwd —** zachowują się identycznie.

Ta funkcja jest bezpieczna dla wątków, mimo że jest to uzależnione od **GetFullPathName**, które jest nie metodą o bezpiecznych wątkach. Jednakże można naruszyć bezpieczeństwo wątków, jeśli wielowątkowa aplikacja wywoła tę funkcję i [GetFullPathNameA](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).

Wersja tej funkcji, która ma **_nolock** sufiks działa identycznie do tej funkcji z tą różnicą, że nie jest metodą o bezpiecznych wątkach i nie jest chronione przed ingerencją przez inne wątki. Aby uzyskać więcej informacji, zobacz [_getdcwd_nolock —, _wgetdcwd_nolock —](getdcwd-nolock-wgetdcwd-nolock.md).

Gdy **_DEBUG** i **_CRTDBG_MAP_ALLOC** są zdefiniowane, wzywa do **_getdcwd —** i **_wgetdcwd —** są zastępowane przez wywołania **_getdcwd_dbg —** i **_wgetdcwd_dbg —** tak, aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz[_getdcwd_dbg —, _wgetdcwd_dbg —](getdcwd-dbg-wgetdcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<Direct.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_getdrive —](getdrive.md).

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
