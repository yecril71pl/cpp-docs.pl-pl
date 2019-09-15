---
title: _umask_s
ms.date: 11/04/2016
api_name:
- _umask_s
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
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: 21d9ba194f85e40c3c5a4d67d16ebca9721f68f8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945985"
---
# <a name="_umask_s"></a>_umask_s

Ustawia domyślną maskę dostępu do pliku. Wersja [_umask](umask.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Parametry

*wyst*<br/>
Domyślne ustawienie uprawnień.

*pOldMode*<br/>
Poprzednia wartość ustawienia uprawnienia.

## <a name="return-value"></a>Wartość zwracana

Zwraca kod błędu, jeśli w *trybie* nie określono prawidłowego trybu lub wskaźnik *POldMode* ma **wartość null**.

### <a name="error-conditions"></a>Warunki błędów

|*wyst*|*pOldMode*|Wartość zwracana|Zawartość *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|Ile|**NULL**|**EINVAL**|nie zmodyfikowano|
|Nieprawidłowy tryb|Ile|**EINVAL**|nie zmodyfikowano|

Jeśli wystąpi jeden z powyższych warunków, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja **_umask_s** zwraca **EINVAL** i ustawia **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_umask_s** Ustawia maskę uprawnień pliku bieżącego procesu do trybu określonego przez *tryb*. Maska uprawnień plików modyfikuje ustawienie uprawnień nowych plików utworzonych przez **_creat**, **_open**lub **_sopen**. Jeśli bit w masce wynosi 1, odpowiadający mu bit w wartości żądanego uprawnienia pliku jest ustawiony na 0 (niedozwolone). Jeśli bit w masce ma wartość 0, odpowiedni bit pozostaje niezmieniony. Ustawienie uprawnienia dla nowego pliku nie jest ustawione do momentu zamknięcia pliku po raz pierwszy.

Wyrażenie Integer *PMODE* zawiera jedną lub obie następujące stałe manifestu zdefiniowane w SYS\STAT. C

|*pmode*||
|-|-|
|**_S_IWRITE**|Dozwolone jest zapisanie.|
|**_S_IREAD**|Odczytywanie dozwolone.|
|**_S_IREAD** \| **_S_IWRITE**|Dozwolone odczytywanie i zapisywanie.|

Po otrzymaniu obu stałych są one przyłączone do operatora bitowego lub ( **|** ). Jeśli argument *mode* ma wartość **_S_IREAD**, odczytywanie jest niedozwolone (plik jest tylko do zapisu). Jeśli argument *mode* ma wartość **_S_IWRITE**, pisanie jest niedozwolone (plik jest tylko do odczytu). Na przykład jeśli bit zapisu jest ustawiony w masce, wszystkie nowe pliki będą tylko do odczytu. Należy pamiętać, że w systemach operacyjnych MS-DOS i Windows wszystkie pliki są odczytywane; nie można udzielić uprawnienia tylko do zapisu. W związku z tym ustawienie bitu odczytu z **_umask_s** nie ma wpływu na tryby pliku.

Jeśli *PMODE* nie jest kombinacją jednej z stałych manifestu ani nie zawiera alternatywnego zestawu stałych, funkcja zignoruje te elementy.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_umask_s**|\<IO. h > i \<sys/stat. h > i \<sys/Types. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
