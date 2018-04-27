---
title: _getdcwd —, _wgetdcwd — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
dev_langs:
- C++
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3572f629a6ca9df44fb4c571e2712894d89b257
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
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

*Dysk*<br/>
Nieujemną liczbą całkowitą, która określa dysk (0 = dysk domyślny, 1 = A, 2 = B i tak dalej).

Jeśli określony dysk nie jest dostępny, lub typ dysku (na przykład wymiennego, stały, dysku CD, pamięci RAM dysku lub dysku sieciowego) nie można ustalić, obsługi nieprawidłowy parametr, który jest opisany w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md), jest wywoływane.

*buffer*<br/>
Lokalizacja magazynu dla ścieżki lub **NULL**.

Jeśli **NULL** jest określony, ta funkcja przydziela buforu z co najmniej *maxlen* rozmiarze przy użyciu **— funkcja malloc**i wartość zwracaną **_getdcwd —**wskaźnik do przydzielonego buforu. Bufor zwolniona, wywołując **wolnego** i przekazanie jej przez wskaźnik.

*maxlen*<br/>
Niezerowe dodatnią liczbą całkowitą, która określa maksymalną długość ścieżki w znakach: **char** dla **_getdcwd —** i **wchar_t** dla **_wgetdcwd —**.

Jeśli *maxlen* nie jest większa niż zero, obsługi nieprawidłowy parametr, który jest opisany w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md), jest wywoływana.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciąg, który reprezentuje pełną ścieżkę bieżącego katalogu roboczego na określonym dysku, lub **NULL**, co wskazuje błąd.

Jeśli *buforu* jest określony jako **NULL** i ma za mało pamięci do przydzielenia *maxlen* znaków, wystąpi błąd i **errno** jest Ustaw **enomem —**. Jeśli długość ścieżki, która zawiera znak końcowy null, przekracza *maxlen*, wystąpi błąd i **errno** ustawiono **erange —**. Aby uzyskać więcej informacji na temat kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Getdcwd —** funkcja pobiera pełną ścieżkę bieżącego katalogu roboczego na określonym dysku i zapisuje go w *buforu*. Jeśli bieżący katalog roboczy jest ustawiany na katalog główny, ciąg kończy się znakiem kreski ułamkowej odwróconej (\\). Jeśli bieżący katalog roboczy jest ustawiona w katalogu innym niż katalog główny, ciąg kończy się nazwą katalogu i nie kreski ułamkowej odwróconej.

**_wgetdcwd —** jest wersja znaków dwubajtowych **_getdcwd —**, a jego *buforu* parametrów i wartości zwracanej są ciągami znaków dwubajtowych. W przeciwnym razie **_wgetdcwd —** i **_getdcwd —** zachowują się tak samo.

Ta funkcja jest bezpieczne wątkowo, nawet jeśli zależy od **GetFullPathName**, które jest nie wątkowo. Jednak jeśli funkcja ta wymaga aplikacji wielowątkowych może naruszyć bezpieczeństwo wątków i **GetFullPathName**. Aby uzyskać więcej informacji, przejdź do [biblioteki MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) , a następnie wyszukaj **GetFullPathName**.

Wersja tej funkcji, która ma **_nolock —** sufiks zachowuje się tak samo do tej funkcji z tą różnicą, że nie jest bezpieczne wątkowo i nie jest chroniony przez inne wątki zakłóceń. Aby uzyskać więcej informacji, zobacz [_getdcwd_nolock —, _wgetdcwd_nolock —](getdcwd-nolock-wgetdcwd-nolock.md).

Gdy **_DEBUG** i **_crtdbg_map_alloc —** są zdefiniowane, wywołań **_getdcwd —** i **_wgetdcwd —** zastępuje wywołań **_getdcwd_dbg —** i **_wgetdcwd_dbg —** tak, aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz[_getdcwd_dbg —, _wgetdcwd_dbg —](getdcwd-dbg-wgetdcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<Direct.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [_getdrive —](getdrive.md).

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
