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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: f96cffb8770cda78ebff8d873b441ddc288bc41f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332075"
---
# <a name="setbuf"></a>setbuf

Steruje buforowaniem strumienia. Ta funkcja jest przestarzała; zamiast tego użyj [setvbuf.](setvbuf.md)

## <a name="syntax"></a>Składnia

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

*Buforu*<br/>
Bufor przydzielony przez użytkownika.

## <a name="remarks"></a>Uwagi

Funkcja **setbuf** steruje buforowaniem *strumienia*. Argument *strumienia* musi odwoływać się do otwartego pliku, który nie został odczytany lub zapisany. Jeśli argument *bufora* ma **wartość NULL**, strumień jest niebuforowany. Jeśli nie, bufor musi wskazywać tablicę znaków o długości **BUFSIZ**, gdzie **BUFSIZ** jest rozmiar buforu, jak zdefiniowano w STDIO. H. Bufor określony przez użytkownika, zamiast domyślnego buforu przydzielonego systemowi dla danego strumienia, jest używany do buforowania we/wy. Strumień **stderr** jest domyślnie niebuforowany, ale można użyć **setbuf,** aby przypisać bufory do **stderr**.

**setbuf** został zastąpiony przez [setvbuf](setvbuf.md), który jest preferowaną procedurą dla nowego kodu. W przeciwieństwie do **setvbuf**, **setbuf** nie ma możliwości zgłaszania błędów. **setvbuf** pozwala również kontrolować zarówno tryb buforowania, jak i rozmiar bufora. **setbuf** istnieje dla zgodności z istniejącym kodem.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
