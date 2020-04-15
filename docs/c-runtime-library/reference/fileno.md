---
title: _fileno
ms.date: 4/2/2020
api_name:
- _fileno
- _o__fileno
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
- _fileno
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
ms.openlocfilehash: ec4f08e499efe82b0ee35235e6e2d86dbb9bab66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346843"
---
# <a name="_fileno"></a>_fileno

Pobiera deskryptora pliku skojarzone ze strumieniem.

## <a name="syntax"></a>Składnia

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

**_fileno** zwraca deskryptor pliku. Nie ma zwracania błędów. Wynik jest niezdefiniowany, jeśli *strumień* nie określa otwartego pliku. Jeśli strumień ma **wartość NULL**, **_fileno** wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja zwraca wartość -1 i ustawia **errno** na **EINVAL**.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

> [!NOTE]
> Jeśli **stdout** lub **stderr** nie jest skojarzony ze strumieniem danych wyjściowych (na przykład w aplikacji systemu Windows bez okna konsoli), zwrócony deskryptor pliku wynosi -2. W poprzednich wersjach zwrócony deskryptor pliku wynosił -1. Ta zmiana umożliwia aplikacjom odróżnienie tego warunku od błędu.

## <a name="remarks"></a>Uwagi

Procedura **_fileno** zwraca deskryptor pliku aktualnie skojarzony ze *strumieniem*. Ta procedura jest implementowana zarówno jako funkcja, jak i jako makro. Aby uzyskać informacje na temat wybierania jednej z implementacji, zobacz [Wybieranie między funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fileno.c
// This program uses _fileno to obtain
// the file descriptor for some standard C streams.
//

#include <stdio.h>

int main( void )
{
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );
}
```

```Output
The file descriptor for stdin is 0
The file descriptor for stdout is 1
The file descriptor for stderr is 2
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
