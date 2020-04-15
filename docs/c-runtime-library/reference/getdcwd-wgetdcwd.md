---
title: _getdcwd, _wgetdcwd
ms.date: 4/2/2020
api_name:
- _getdcwd
- _wgetdcwd
- _o__getdcwd
- _o__wgetdcwd
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3a4ca8ff3f1153893282c65bc4c2becd687138ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344399"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd, _wgetdcwd

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

*Dysku*<br/>
Nieujemna liczba całkowita określająca dysk (0 = dysk domyślny, 1 = A, 2 = B itd.).

Jeśli określony dysk nie jest dostępny lub nie można określić rodzaju dysku (na przykład wymiennego, stałego, cd-ROM, dysku RAM lub dysku sieciowego), wywoływany jest program obsługi nieprawidłowych parametrów. Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności parametrów](../../c-runtime-library/parameter-validation.md).

*Buforu*<br/>
Lokalizacja przechowywania ścieżki lub **NULL**.

Jeśli określono **wartość NULL,** ta funkcja przydziela bufor o co najmniej *maksymalnym* rozmiarze przy użyciu **malloc**, a zwracana wartość **_getdcwd** jest wskaźnikiem do przydzielonego buforu. Bufor można zwolnić, wywołując **free** i przekazując go wskaźnik.

*maxlen ( maxlen )*<br/>
Liczba całkowita niezerowa, która określa maksymalną długość ścieżki w znakach: **char** dla **_getdcwd** i **wchar_t** dla **_wgetdcwd**.

Jeśli *maxlen* jest mniejsza lub równa zero, wywoływany jest program obsługi nieprawidłowego parametru. Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności parametrów](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu, który reprezentuje pełną ścieżkę bieżącego katalogu roboczego na określonym dysku lub **NULL**, który wskazuje błąd.

Jeśli *bufor* jest określony jako **NULL** i nie ma wystarczającej ilości pamięci do przydzielenia znaków *maxlen,* występuje błąd i **errno** jest ustawiona na **ENOMEM**. Jeśli długość ścieżki, w tym kończący się znak null przekracza *maxlen,* występuje błąd, a **errno** jest ustawiona na **ERANGE**. Aby uzyskać więcej informacji na temat tych kodów błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_getdcwd** pobiera pełną ścieżkę bieżącego katalogu roboczego na określonym dysku i przechowuje go w *buforze*. Jeśli bieżący katalog roboczy jest ustawiony na katalog główny,\\ciąg kończy się ukośnikiem odwrotnym ( ). Jeśli bieżący katalog roboczy jest ustawiony na katalog inny niż katalog główny, ciąg kończy się nazwą katalogu, a nie ukośnikiem odwrotnym.

**_wgetdcwd** jest wersją _getdcwd o szerokim **znaku,** a jego parametr *buforu* i wartość zwracana są ciągami znaków o szerokich znakach. W przeciwnym razie **_wgetdcwd** i **_getdcwd** zachowywać się identycznie.

Ta funkcja jest bezpieczna dla wątków, nawet jeśli zależy od **GetFullPathName**, który sam nie jest bezpieczny dla wątków. Jednak można naruszyć bezpieczeństwo wątków, jeśli aplikacja wielowątkowa wywołuje zarówno tę funkcję, jak i [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew).

Wersja tej funkcji, która ma **_nolock** sufiks zachowuje się identycznie jak ta funkcja, z tą różnicą, że nie jest bezpieczna dla wątków i nie jest chroniona przed zakłóceniami przez inne wątki. Aby uzyskać więcej informacji, zobacz [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md).

Po zdefiniowaniu **_DEBUG** i **_CRTDBG_MAP_ALLOC** wywołania **_getdcwd** i **_wgetdcwd** są zastępowane wywołaniami **_getdcwd_dbg** i **_wgetdcwd_dbg,** dzięki czemu można debugować alokacje pamięci. Aby uzyskać więcej informacji, zobacz[_getdcwd_dbg _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_getdrive](getdrive.md).

## <a name="see-also"></a>Zobacz też

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
