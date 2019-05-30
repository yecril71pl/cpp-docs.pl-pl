---
title: memcmp, wmemcmp
ms.date: 11/04/2016
apiname:
- memcmp
- wmemcmp
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
topictype: APIRef
f1_keywords:
- memcmp
- wmemcmp
helpviewer_keywords:
- wmemcmp function
- memcmp function
ms.assetid: 0c21c3e3-8ee4-40e5-add1-eb26d225fd8d
ms.openlocfilehash: 228a74ac8cc83bca169779f1afd6936f5be59bee
ms.sourcegitcommit: 010ecc2bb9a15deea192a34975176ec0426aa3d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265632"
---
# <a name="memcmp-wmemcmp"></a>memcmp, wmemcmp

Porównanie znaków w dwóch buforów.

## <a name="syntax"></a>Składnia

```C
int memcmp(
   const void *buffer1,
   const void *buffer2,
   size_t count
);
int wmemcmp(
   const wchar_t * buffer1,
   const wchar_t * buffer2,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*buffer1*<br/>
Pierwszy buforu.

*buffer2*<br/>
Drugi buforu.

*Liczba*<br/>
Liczba znaków do porównania. (Porównuje bajty dla **memcmp**, znaki dwubajtowe dla **wmemcmp —**).

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana określa relację pomiędzy buforów.

|Wartość zwracana|Relacja między pierwszym *liczba* znaków buf1 i buf2|
|------------------|---------------------------------------------------------------|
|< 0|*buffer1* mniej niż *buffer2*|
|0|*buffer1* taka sama jak *buffer2*|
|> 0|*buffer1* większa *buffer2*|

## <a name="remarks"></a>Uwagi

Porównuje pierwszy *liczba* znaków *buffer1* i *buffer2* i zwraca wartość wskazującą, ich relacje. Znak różna od zera zwracana wartość jest znak różnica między pierwszej pary różne wartości w buforów. Wartości są interpretowane jako **niepodpisane** **char** dla **memcmp**i **wchar_t** dla **wmemcmp —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memcmp**|\<Memory.h > lub \<string.h >|
|**wmemcmp**|\<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_memcmp.c
/* This program uses memcmp to compare
* the strings named first and second. If the first
* 19 bytes of the strings are equal, the program
* considers the strings to be equal.
*/

#include <string.h>
#include <stdio.h>

int main( void )
{
   char first[]  = "12345678901234567890";
   char second[] = "12345678901234567891";
   int int_arr1[] = {1,2,3,4};
   int int_arr2[] = {1,2,3,4};
   int result;

   printf( "Compare '%.19s' to '%.19s':\n", first, second );
   result = memcmp( first, second, 19 );
   if( result < 0 )
      printf( "First is less than second.\n" );
   else if( result == 0 )
      printf( "First is equal to second.\n" );
   else
      printf( "First is greater than second.\n" );

   printf( "Compare '%d,%d' to '%d,%d':\n", int_arr1[0], int_arr1[1], int_arr2[0], int_arr2[1]);
   result = memcmp( int_arr1, int_arr2, sizeof(int) * 2 );
   if( result < 0 )
      printf( "int_arr1 is less than int_arr2.\n" );
   else if( result == 0 )
      printf( "int_arr1 is equal to int_arr2.\n" );
   else
      printf( "int_arr1 is greater than int_arr2.\n" );
}
```

```Output
Compare '1234567890123456789' to '1234567890123456789':
First is equal to second.
Compare '1,2' to '1,2':
int_arr1 is equal to int_arr2.
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
