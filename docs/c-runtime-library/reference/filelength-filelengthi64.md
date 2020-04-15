---
title: _filelength, _filelengthi64
ms.date: 4/2/2020
api_name:
- _filelengthi64
- _filelength
- _o__filelength
- _o__filelengthi64
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _filelength
- _filelengthi64
- filelengthi64
helpviewer_keywords:
- filelengthi64 function
- lengths, file
- filelength function
- _filelength function
- files [C++], length
- _filelengthi64 function
ms.assetid: 3ab83d5a-543c-4079-b9d9-0abfc7da0275
ms.openlocfilehash: 1a830bedc8dca65410a2df49b96c6e3bf6e11b4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346881"
---
# <a name="_filelength-_filelengthi64"></a>_filelength, _filelengthi64

Pobiera długość pliku.

## <a name="syntax"></a>Składnia

```C
long _filelength(
   int fd
);
__int64 _filelengthi64(
   int fd
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Kieruj do deskryptora plików.

## <a name="return-value"></a>Wartość zwracana

Zarówno **_filelength,** jak i **_filelengthi64** zwracają długość pliku w bajtach pliku docelowego skojarzonego z *fd*. Jeśli *fd* jest nieprawidłowym deskryptorem plików, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [polu Sprawdzanie poprawności parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, obie funkcje zwracają -1L, aby wskazać błąd i ustawić **errno** na **EBADF**.

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_filelength**|\<> io.h|
|**_filelengthi64**|\<> io.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_chsize](chsize.md).

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_fileno](fileno.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_stat, funkcje _wstat](stat-functions.md)<br/>
