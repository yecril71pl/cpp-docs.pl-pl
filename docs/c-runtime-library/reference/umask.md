---
title: _umask — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce3053bfb19cc81dff15d41d1b5bc6d405da619f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="umask"></a>_umask

Ustawia domyślną maskę uprawnień do pliku. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [_umask_s —](umask-s.md).

## <a name="syntax"></a>Składnia

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Domyślne ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

**_umask —** zwraca poprzednią wartość *pmode*. Nie ma żadnych zwracany błąd.

## <a name="remarks"></a>Uwagi

**_Umask —** funkcja ustawia maski uprawnienia pliku bieżącego procesu do trybu określonego przez *pmode*. Maska uprawnienia pliku Modyfikuje ustawienia uprawnień nowych plików utworzonych przez **_creat —**, **_otwórz**, lub **_sopen —**. Jeśli bit maski to 1, odpowiadający mu bit pliku żądane uprawnienie wartość jest równa 0 (niedopuszczalne). Jeśli bit maski to 0, odpowiadający mu bit pozostanie bez zmian. Ustawienie uprawnień dla nowego pliku nie jest ustawiona, dopóki ten plik będzie zamknięty po raz pierwszy.

Wyrażenie całkowite *pmode* zawiera co najmniej jednej z następujących stałych manifestu, zdefiniowane w SYS\STAT. H:

|*pmode*||
|-|-|
**_S_IWRITE —**|Zapisywanie dozwolone.
**_S_IREAD —**|Odczytywanie dozwolone.
**_S_IREAD —** \| **_S_IWRITE —**|Odczytywanie i zapisywanie dozwolone.

Gdy zarówno stałe są podane, są połączone z operator Alternatywy ( **|** ). Jeśli *pmode* argument jest **_s_iread —**, odczytu jest niedozwolony (plik jest tylko do zapisu). Jeśli *pmode* argument jest **_s_iwrite —**, zapis nie jest dozwolone. (plik jest tylko do odczytu). Na przykład jeśli ustawiono bit zapisu maski, nowe pliki będą tylko do odczytu. Pamiętaj, że wszystkie pliki z systemu MS-DOS i systemów operacyjnych Windows, jest do odczytu; nie jest możliwe nadaj uprawnienia tylko do zapisu. W związku z tym ustawienie odczytu bit z **_umask —** nie ma wpływu na tryby pliku.

Jeśli *pmode* nie jest kombinacją jednego z manifestu stałe lub zawiera inny zestaw stałych, funkcja będzie ignorować te.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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
[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
