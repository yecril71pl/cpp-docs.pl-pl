---
title: _isatty
ms.date: 11/04/2016
apiname:
- _isatty
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
- _isatty
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
ms.openlocfilehash: ef0df5f859779c081df47ef4bfe938ec2601d524
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545590"
---
# <a name="isatty"></a>_isatty

Określa, czy deskryptor pliku jest skojarzony z urządzeniem znaku.

## <a name="syntax"></a>Składnia

```C
int _isatty( int fd );
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptor pliku, który odwołuje się do urządzenia, które ma zostać przetestowana.

## <a name="return-value"></a>Wartość zwracana

**_isatty —** zwraca wartość różną od zera, jeśli deskryptor jest skojarzony z urządzeniem znaku. W przeciwnym razie **_isatty —** zwraca wartość 0.

## <a name="remarks"></a>Uwagi

**_Isatty —** funkcja sprawdza, czy *fd* jest skojarzony z urządzeniem znaku (terminal, konsola, drukarka lub port szeregowy).

Ta funkcja sprawdza poprawność *fd* parametru. Jeśli *fd* jest złym wskaźnikiem pliku, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca 0 i ustawia **errno** do **EBADF**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_isatty**|\<io.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_isatty.c
/* This program checks to see whether
* stdout has been redirected to a file.
*/

#include <stdio.h>
#include <io.h>

int main( void )
{
   if( _isatty( _fileno( stdout ) ) )
      printf( "stdout has not been redirected to a file\n" );
   else
      printf( "stdout has been redirected to a file\n");
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
stdout has not been redirected to a file
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
