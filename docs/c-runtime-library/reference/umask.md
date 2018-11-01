---
title: _umask
ms.date: 11/04/2016
apiname:
- _umask
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
- _umask
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: f51e2c19933953eb4910cdeb5e1ec50b7387bd59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677165"
---
# <a name="umask"></a>_umask

Ustawia domyślną maskę uprawnień do pliku. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [_umask_s —](umask-s.md).

## <a name="syntax"></a>Składnia

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Domyślne ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

**_umask —** zwraca poprzednią wartość *pmode*. Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

**_Umask —** funkcja Ustawia maskę uprawnień pliku bieżącego procesu przekładają się na określonej przez *pmode*. Maskę uprawnień pliku Modyfikuje ustawienia uprawnień dla nowych plików utworzonych przez **_creat —**, **_otwórz**, lub **_sopen**. Jeśli bit maski to 1, odpowiadający mu bit w pliku żądane uprawnienie wartość jest równa 0 (niedozwolone). Jeśli bit maski to 0, odpowiadający mu bit pozostanie bez zmian. Ustawienie uprawnienia dla nowego pliku nie jest ustawiona, dopóki ten plik będzie zamknięty po raz pierwszy.

Wyrażenia typu całkowitego *pmode* zawiera jeden lub oba z następujących stałych manifestu, określonych w SYS\STAT. GODZ.:

|*pmode*||
|-|-|
**_S_IWRITE**|Zapisywanie jest dozwolone.
**_S_IREAD**|Odczytywanie dozwolone.
**_S_IREAD** \| **_S_IWRITE**|Odczyt i zapis dozwolone.

Gdy oba stałe są podane, są połączone za pomocą operatora bitowego OR ( **|** ). Jeśli *pmode* argument jest **_S_IREAD**, odczytu, nie jest dozwolona (plik jest tylko do zapisu). Jeśli *pmode* argument jest **_S_IWRITE**, nie jest dozwolone zapisywanie (plik jest tylko do odczytu). Na przykład jeśli maska jest ustawiony bit zapisu, nowe pliki będą tylko do odczytu. Należy zauważyć, że MS-DOS i systemów operacyjnych Windows, wszystkie pliki do odczytu; nie jest możliwe przyznać uprawnienia tylko do zapisu. W związku z tym, ustawienie odczytu bit z **_umask —** nie ma wpływu na tryby plików.

Jeśli *pmode* nie jest kombinacją jednej ze stałych manifestu lub inny zestaw zawiera stałych, funkcja będzie ignorować te.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_umask.c
// compile with: /W3
// This program uses _umask to set
// the file-permission mask so that all future
// files will be created as read-only files.
// It also displays the old mask.
#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask;

   /* Create read-only files: */
   oldmask = _umask( _S_IWRITE ); // C4996
   // Note: _umask is deprecated; consider using _umask_s instead
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
