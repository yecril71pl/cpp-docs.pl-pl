---
title: _umask_s
ms.date: 11/04/2016
apiname:
- _umask_s
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
ms.openlocfilehash: 878a22cb2884c36e792ff8dead1453582addb5b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480674"
---
# <a name="umasks"></a>_umask_s

Ustawia domyślną maskę uprawnień do pliku. Wersja [_umask —](umask.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Parametry

*Tryb*<br/>
Domyślne ustawienie uprawnień.

*pOldMode*<br/>
Poprzedniej wartości ustawienia uprawnień.

## <a name="return-value"></a>Wartość zwracana

Zwraca kod błędu, jeśli *tryb* nie określa prawidłowego trybu lub *pOldMode* wskaźnik jest **NULL**.

### <a name="error-conditions"></a>Warunki błędów

|*Tryb*|*pOldMode*|Wartość zwracana|Zawartość *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|Wszystkie|**NULL**|**EINVAL**|Nie zmodyfikowano|
|Nieprawidłowy element mode|Wszystkie|**EINVAL**|Nie zmodyfikowano|

Jeśli wystąpi jedno z powyższych warunków, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_umask_s —** zwraca **EINVAL** i ustawia **errno** do **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Umask_s —** funkcja Ustawia maskę uprawnień pliku bieżącego procesu przekładają się na określonej przez *tryb*. Maskę uprawnień pliku Modyfikuje ustawienia uprawnień dla nowych plików utworzonych przez **_creat —**, **_otwórz**, lub **_sopen**. Jeśli bit maski to 1, odpowiadający mu bit w pliku żądane uprawnienie wartość jest równa 0 (niedozwolone). Jeśli bit maski to 0, odpowiadający mu bit pozostanie bez zmian. Ustawienie uprawnienia dla nowego pliku nie jest ustawiona, dopóki ten plik będzie zamknięty po raz pierwszy.

Wyrażenia typu całkowitego *pmode* zawiera jeden lub oba z następujących stałych manifestu, określonych w SYS\STAT. GODZ.:

|*pmode*||
|-|-|
|**_S_IWRITE**|Zapisywanie jest dozwolone.|
|**_S_IREAD**|Odczytywanie dozwolone.|
|**_S_IREAD** \| **_S_IWRITE**|Odczyt i zapis dozwolone.|

Gdy oba stałe są podane, są połączone za pomocą operatora bitowego OR ( **|** ). Jeśli *tryb* argument jest **_S_IREAD**, odczytu, nie jest dozwolona (plik jest tylko do zapisu). Jeśli *tryb* argument jest **_S_IWRITE**, nie jest dozwolone zapisywanie (plik jest tylko do odczytu). Na przykład jeśli maska jest ustawiony bit zapisu, nowe pliki będą tylko do odczytu. Należy zauważyć, że MS-DOS i systemów operacyjnych Windows, wszystkie pliki do odczytu; nie jest możliwe przyznać uprawnienia tylko do zapisu. W związku z tym, ustawienie odczytu bit z **_umask_s —** nie ma wpływu na tryby plików.

Jeśli *pmode* nie jest kombinacją jednej ze stałych manifestu lub inny zestaw zawiera stałych, funkcja będzie ignorować te.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_umask_s**|\<IO.h > i \<sys/stat.h > i \<sys/types.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
[Niskiego poziomu operacji We/Wy](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
