---
title: _fileno — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9bc03bcd92eb8040b7eefadd0c109e4e887f7304
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398868"
---
# <a name="fileno"></a>_fileno

Pobiera deskryptor pliku skojarzone z strumienia.

## <a name="syntax"></a>Składnia

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**_fileno —** zwraca deskryptorów plików. Nie ma żadnych zwracany błąd. Wynik jest niezdefiniowana, jeśli *strumienia* nie określa plik. W przypadku strumienia **NULL**, **_fileno —** wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca wartość -1 i zestawy **errno** do **einval —**.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

> [!NOTE]
> Jeśli **stdout** lub **stderr** nie jest skojarzony z strumienia wyjściowego (na przykład w aplikacji systemu Windows bez okna konsoli), deskryptorów plików, zwracana jest -2. W poprzednich wersjach deskryptorów plików, zwracana jest wartość -1. Ta zmiana umożliwia aplikacjom odróżnienia tego warunku błędu.

## <a name="remarks"></a>Uwagi

**_Fileno —** procedury zwraca deskryptorów plików, w obecnie skojarzony z *strumienia*. Ta procedura zaimplementowano funkcji oraz w makrze. Aby uzyskać informacje o wybieraniu albo implementacji, zobacz [wybierania pomiędzy funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
