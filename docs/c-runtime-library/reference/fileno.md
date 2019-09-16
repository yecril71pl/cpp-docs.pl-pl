---
title: _fileno
ms.date: 11/04/2016
api_name:
- _fileno
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
ms.openlocfilehash: 586e390e100f5dc46a49b99c007016cf23ac68f0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957206"
---
# <a name="_fileno"></a>_fileno

Pobiera deskryptor pliku skojarzony ze strumieniem.

## <a name="syntax"></a>Składnia

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

**_fileno** zwraca deskryptor pliku. Brak powrotu błędu. Wynik jest niezdefiniowany, jeśli *strumień* nie określa otwartego pliku. Jeśli strumień ma **wartość null**, **_fileno** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1 i ustawia **errno** na **EINVAL**.

Aby uzyskać więcej informacji o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

> [!NOTE]
> Jeśli **stdout** lub **stderr** nie jest skojarzony ze strumieniem wyjściowym (na przykład w aplikacji systemu Windows bez okna konsoli), zwracany deskryptor pliku to-2. W poprzednich wersjach zwrócony deskryptor pliku miał wartość-1. Ta zmiana umożliwia aplikacjom odróżnienie tego stanu od błędu.

## <a name="remarks"></a>Uwagi

Procedura **_fileno** zwraca deskryptor pliku aktualnie skojarzony ze *strumieniem*. Ta procedura jest zaimplementowana zarówno jako funkcja, jak i jako makro. Aby uzyskać informacje na temat wybierania dowolnej implementacji, zobacz [Wybieranie między funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
