---
title: setbuf | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f8592e8008fa78402ced307b60188ea8610960a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407317"
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

*strumień* wskaźnik do **pliku** struktury.

*Bufor* buforu przydzielone przez użytkownika.

## <a name="remarks"></a>Uwagi

**Setbuf** funkcji buforowania dla formantów *strumienia*. *Strumienia* argumentu musi odwoływać się do otwartego pliku, który nie odczytu lub zapisu. Jeśli *buforu* argument jest **NULL**, jest cofanie buforowanego strumienia. Jeśli nie, rozmiar buforu musi wskazywać do tablicy znaków o długości **bufsiz —**, gdzie **bufsiz —** jest zdefiniowany w stdio — rozmiar buforu. H. Określony użytkownik buforu, zamiast domyślnej przydzielone systemu bufor dla danego strumienia jest używany dla operacji We/Wy buforowania. **Stderr** strumień jest nie buforowanego domyślnie, ale można użyć **setbuf** można przypisać buforów do **stderr**.

**setbuf** została zastąpiona przez [setvbuf —](setvbuf.md), która jest preferowanym procedury dla nowego kodu. **setbuf** został zachowany na potrzeby zgodności z istniejącego kodu.

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
