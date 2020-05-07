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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 69e9d0b0eaa3a62d95ea602b68b5d1ad0df99e4a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919216"
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

*litera*<br/>
Nieujemna liczba całkowita określająca dysk (0 = dysk domyślny, 1 = A, 2 = B itd.).

Jeśli określony dysk nie jest dostępny lub nie można ustalić rodzaju dysku (na przykład wymienny, stały, CD-ROM, dysku pamięci RAM lub dysku sieciowego), zostanie wywołana procedura obsługi nieprawidłowego parametru. Aby uzyskać więcej informacji, zobacz [Walidacja parametrów](../../c-runtime-library/parameter-validation.md).

*buforu*<br/>
Lokalizacja przechowywania dla ścieżki lub **wartość null**.

Jeśli określono **wartość null** , ta funkcja przydziela bufor o rozmiarze co najmniej *MaxLen* przy użyciu wartości **malloc**, a zwracana wartość **_getdcwd** jest wskaźnikiem do przydzielonego buforu. Bufor może zostać zwolniony przez wywołanie **bezpłatnej** i przekazanie jej wskaźnika.

*MaxLen*<br/>
Niezerowy dodatnia liczba całkowita, która określa maksymalną długość ścieżki, w znakach: **char** dla **_getdcwd** i **wchar_t** dla **_wgetdcwd**.

Jeśli *MaxLen* jest mniejsza lub równa zero, zostanie wywołana procedura obsługi nieprawidłowego parametru. Aby uzyskać więcej informacji, zobacz [Walidacja parametrów](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Wartość zwracana

Wskaźnik na ciąg, który reprezentuje pełną ścieżkę bieżącego katalogu roboczego na określonym dysku lub **wartość null**, co wskazuje na błąd.

Jeśli *bufor* jest określony jako **null** , a za mało pamięci do przydzielenia znaków *MaxLen* , wystąpi błąd i **errno** jest ustawiony na **ENOMEM**. Jeśli długość ścieżki włącznie z końcowym znakiem null przekracza *MaxLen*, wystąpi błąd, a **errno** jest ustawiona na **ERANGE**. Aby uzyskać więcej informacji o tych kodach błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_getdcwd** pobiera pełną ścieżkę bieżącego katalogu roboczego na określonym dysku i zapisuje ją w *buforze*. Jeśli bieżący katalog roboczy jest ustawiony na katalog główny, ciąg kończący się ukośnikiem odwrotnym (\\). Jeśli bieżący katalog roboczy jest ustawiony na katalog inny niż główny, ciąg zostanie zakończony nazwą katalogu, a nie ukośnikiem odwrotnym.

**_wgetdcwd** to wersja znaku dwubajtowego **_getdcwd**, a jej parametr *buforu* i wartość zwracana są ciągami znaków dwubajtowych. W przeciwnym razie **_wgetdcwd** i **_getdcwd** zachowują się identycznie.

Ta funkcja jest bezpieczna wątkowo, chociaż zależy od **GetFullPathName**, która sama nie jest bezpieczna wątkowo. Można jednak naruszyć bezpieczeństwo wątku, jeśli aplikacja wielowątkowa wywoła tę funkcję i [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew).

Wersja tej funkcji, która ma sufiks **_nolock** zachowuje się identycznie z tą funkcją, z tą różnicą, że nie jest bezpieczna wątkowo i nie jest chroniona przed ingerencją przez inne wątki. Aby uzyskać więcej informacji, zobacz [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md).

Po zdefiniowaniu **_DEBUG** i **_CRTDBG_MAP_ALLOC** , wywołania **_getdcwd** i **_wgetdcwd** są zastępowane przez wywołania **_getdcwd_dbg** i **_wgetdcwd_dbg** , aby można było debugować alokacje pamięci. Aby uzyskać więcej informacji, zobacz[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getdcwd**|\<> Direct. h|
|**_wgetdcwd**|\<Direct. h> lub \<WCHAR. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_getdrive](getdrive.md).

## <a name="see-also"></a>Zobacz też

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
