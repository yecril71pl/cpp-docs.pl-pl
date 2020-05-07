---
title: setbuf
ms.date: 4/2/2020
api_name:
- setbuf
- _o_setbuf
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: 40f23db88abf9733eada9e775aacda83cba5829a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910331"
---
# <a name="setbuf"></a>setbuf

Steruje buforowaniem strumienia. Ta funkcja jest przestarzała; Zamiast tego użyj [setvbuf —](setvbuf.md) .

## <a name="syntax"></a>Składnia

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>Parametry

*produkcyjne*<br/>
Wskaźnik do struktury **pliku** .

*buforu*<br/>
Bufor przydzielony przez użytkownika.

## <a name="remarks"></a>Uwagi

Funkcja **setbuf** kontroluje buforowanie dla *strumienia*. Argument *Stream* musi odwoływać się do otwartego pliku, który nie został odczytany lub zapisany. Jeśli argument *buforu* ma **wartość null**, strumień zostanie zbuforowany. W przeciwnym razie bufor musi wskazywać tablicę znaków o długości **bufsiz**, gdzie **bufsiz** jest rozmiar buforu, zgodnie z definicją w stdio. C. Bufor określony przez użytkownika, a nie domyślny bufor przypisywany przez system dla danego strumienia, jest używany dla buforowania we/wy. Strumień **stderr** jest domyślnie buforowany, ale do przypisywania buforów do obiektu **stderr**można użyć **setbuf** .

**setbuf** został zastąpiony przez [setvbuf —](setvbuf.md), który jest preferowaną procedurą dla nowego kodu. W przeciwieństwie do **setvbuf —**, **setbuf** nie ma żadnego sposobu raportowania błędów. **setvbuf —** umożliwia również sterowanie zarówno trybem buforowania, jak i rozmiarem buforu. **setbuf** istnieje na potrzeby zgodności z istniejącym kodem.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setbuf**|\<stdio. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
