---
title: _isatty
ms.date: 4/2/2020
api_name:
- _isatty
- _o__isatty
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
- _isatty
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
ms.openlocfilehash: c9611c2bd55ebc1602a73e4c71518716ea100420
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343902"
---
# <a name="_isatty"></a>_isatty

Określa, czy deskryptor pliku jest skojarzony z urządzeniem znakowym.

## <a name="syntax"></a>Składnia

```C
int _isatty( int fd );
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Deskryptor pliku, który odwołuje się do urządzenia, które ma być testowane.

## <a name="return-value"></a>Wartość zwracana

**_isatty** zwraca wartość niezerową, jeśli deskryptor jest skojarzony z urządzeniem znakowym. W przeciwnym razie **_isatty** zwraca wartość 0.

## <a name="remarks"></a>Uwagi

Funkcja **_isatty** określa, czy *fd* jest skojarzony z urządzeniem znakowym (terminalem, konsolą, drukarką lub portem szeregowym).

Ta funkcja sprawdza poprawność parametru *fd.* Jeśli *fd* jest złym wskaźnikiem pliku, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [polu Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja zwraca 0 i ustawia **errno** na **EBADF**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_isatty**|\<> io.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
