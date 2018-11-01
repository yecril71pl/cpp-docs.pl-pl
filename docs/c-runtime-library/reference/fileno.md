---
title: _fileno
ms.date: 11/04/2016
apiname:
- _fileno
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
- _fileno
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
ms.openlocfilehash: 682ab4b01a663bd9a6314138aa692b1c05b7437a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646614"
---
# <a name="fileno"></a>_fileno

Pobiera deskryptor pliku skojarzone ze strumieniem.

## <a name="syntax"></a>Składnia

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**_fileno** zwroty deskryptora pliku. Nie będzie zwrotu błędu. Wynik jest niezdefiniowane, jeżeli *strumienia* nie określa otwartego pliku. Jeśli wartość strumienia wynosi **NULL**, **_fileno** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca wartość -1 i ustawia **errno** do **EINVAL**.

Aby uzyskać więcej informacji na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

> [!NOTE]
> Jeśli **stdout** lub **stderr** nie jest skojarzony ze strumienia wyjściowego (na przykład w aplikacji Windows bez okna konsoli), deskryptor pliku, zwracany jest -2. W poprzednich wersjach deskryptor pliku zwracane było -1. Ta zmiana umożliwia aplikacjom odróżnienia tego warunku wystąpił błąd.

## <a name="remarks"></a>Uwagi

**_Fileno** rutynowe zwroty deskryptora pliku aktualnie skojarzone z *strumienia*. Ta procedura jest implementowany jako funkcja i jak makra. Aby uzyskać informacji dotyczących wyboru każdej implementacji, zobacz [wybierania pomiędzy funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
