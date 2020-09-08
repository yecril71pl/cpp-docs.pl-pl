---
title: _umask
description: Dokumentacja interfejsu API dla _umask; Ustawia domyślną maskę uprawnień plików.
ms.date: 4/2/2020
api_name:
- _umask
- _o__umask
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3735ecd7ba194009945d3717982d7828ecee3c1e
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554932"
---
# <a name="_umask"></a>_umask

Ustawia domyślną maskę dostępu do pliku. Aby uzyskać bardziej bezpieczną wersję tej funkcji, zobacz [_umask_s](umask-s.md) . "

## <a name="syntax"></a>Składnia

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Domyślne ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

**_umask** zwraca poprzednią wartość *PMODE*. Nie ma żadnego powrotu błędu.

## <a name="remarks"></a>Uwagi

Funkcja **_umask** Ustawia maskę uprawnień pliku bieżącego procesu do trybu określonego przez *PMODE*. Maska uprawnień plików modyfikuje ustawienie uprawnień nowych plików utworzonych przez **_creat**, **_open**lub **_sopen**. Jeśli bit w masce wynosi 1, odpowiadający mu bit w wartości żądanego uprawnienia pliku jest ustawiony na 0 (niedozwolone). Jeśli bit w masce ma wartość 0, odpowiedni bit pozostaje niezmieniony. Ustawienie uprawnienia dla nowego pliku nie jest ustawione do momentu zamknięcia pliku po raz pierwszy.

Wyrażenie Integer *PMODE* zawiera jedną lub obie następujące stałe manifestu zdefiniowane w SYS\STAT. C

|*pmode*| |
|-|-|
| **_S_IWRITE** | Dozwolone jest zapisanie. |
| **_S_IREAD** | Odczytywanie dozwolone. |
| **_S_IREAD** &#124; **_S_IWRITE** | Dozwolone odczytywanie i zapisywanie. |

Po otrzymaniu obu stałych są one przyłączone do operatora bitowego lub ( **&#124;** ). Jeśli argument *PMODE* jest **_S_IREAD**, odczytywanie jest niedozwolone (plik jest tylko do zapisu). Jeśli argument *PMODE* jest **_S_IWRITE**, pisanie nie jest dozwolone (plik jest tylko do odczytu). Na przykład jeśli bit zapisu jest ustawiony w masce, wszystkie nowe pliki będą tylko do odczytu. Należy pamiętać, że w systemach operacyjnych MS-DOS i Windows wszystkie pliki są odczytywane; nie można udzielić uprawnienia tylko do zapisu. W związku z tym ustawienie bitu odczytu z **_umask** nie ma wpływu na tryby pliku.

Jeśli *PMODE* nie jest kombinacją jednej z stałych manifestu ani nie zawiera alternatywnego zestawu stałych, funkcja zignoruje te elementy.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
