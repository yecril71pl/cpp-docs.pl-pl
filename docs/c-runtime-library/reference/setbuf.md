---
title: setbuf
ms.date: 11/04/2016
apiname:
- setbuf
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
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: 3b5fbccd304d406131b0c4f7d16a289f80484642
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440499"
---
# <a name="setbuf"></a>setbuf

Formanty buforowanie strumienia. Ta funkcja jest przestarzała; Użyj [setvbuf —](setvbuf.md) zamiast tego.

## <a name="syntax"></a>Składnia

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

*buffer*<br/>
Bufor przydzielony przez użytkownika.

## <a name="remarks"></a>Uwagi

**Setbuf —** funkcji kontrolek buforowania *strumienia*. *Strumienia* argumentu musi odwoływać się do otwartego pliku, który nie odczytu lub zapisu. Jeśli *buforu* argument jest **NULL**, strumień jest niezaznaczone buforowanego. Jeśli nie, rozmiar buforu musi wskazywać na tablicy znaków o długości **BUFSIZ**, gdzie **BUFSIZ** jest rozmiar buforu, zgodnie z definicją w stdio —. H. Bufor określonych przez użytkownika, zamiast bufor przydzielony systemu domyślny dla danego strumienia jest używany dla we/wy buforowania. **Stderr** strumień jest niezaznaczone buforowanego domyślnie, ale można użyć **setbuf —** można przypisać buforów do **stderr**.

**setbuf —** został zastąpiony przez [setvbuf —](setvbuf.md), czyli preferowany procedury dla nowego kodu. **setbuf —** został zachowany na potrzeby utrzymywania zgodności z istniejącego kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
