---
title: _umask
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b451f979f2925a31f5baaac52351c5d2c0a76da0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362020"
---
# <a name="_umask"></a>_umask

Ustawia domyślną maskę uprawnień do plików. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [_umask_s](umask-s.md).

## <a name="syntax"></a>Składnia

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Domyślne ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

**_umask** zwraca poprzednią wartość *pmode*. Nie ma zwracania błędów.

## <a name="remarks"></a>Uwagi

Funkcja **_umask** ustawia maskę uprawnień do plików bieżącego procesu na tryb określony przez *pmode*. Maska uprawnień do plików modyfikuje ustawienie uprawnień nowych plików utworzonych przez **_creat** **, _open**lub **_sopen**. Jeśli bit w masce wynosi 1, odpowiedni bit w żądanej wartości uprawnień pliku jest ustawiony na 0 (niedozwolone). Jeśli nieco w masce wynosi 0, odpowiedni bit pozostaje niezmieniony. Ustawienie uprawnień dla nowego pliku nie jest ustawiane, dopóki plik nie zostanie zamknięty po raz pierwszy.

*Pmode* wyrażenia liczby całkowitej zawiera jedną lub obie z następujących stałych manifestu, zdefiniowane w SYS\STAT. H:

|*pmode*| |
|-|-|
| **_S_IWRITE** | Pisanie dozwolone. |
| **_S_IREAD** | Odczyt dozwolony. |
| **_S_IREAD _S_IWRITE** &#124; **&#124;** | Czytanie i pisanie dozwolone. |

Gdy obie stałe są podane, są one połączone z operatorem bitowym OR **(&#124;** ). Jeśli argument *pmode* jest **_S_IREAD**, odczyt jest niedozwolony (plik jest tylko do zapisu). Jeśli argument *pmode* jest **_S_IWRITE,** zapisywanie jest niedozwolone (plik jest tylko do odczytu). Na przykład jeśli bit zapisu jest ustawiony w masce, wszystkie nowe pliki będą tylko do odczytu. Należy pamiętać, że w systemach MS-DOS i systemach operacyjnych Windows wszystkie pliki są czytelne; nie można udzielić uprawnień tylko do zapisu. W związku z tym ustawienie bitu odczytu z **_umask** nie ma wpływu na tryby pliku.

Jeśli *pmode* nie jest kombinacją jednej ze stałych manifestu lub zawiera alternatywny zestaw stałych, funkcja po prostu je zignoruje.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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
[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
