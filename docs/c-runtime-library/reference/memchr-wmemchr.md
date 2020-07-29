---
title: memchr, wmemchr
ms.date: 03/31/2019
api_name:
- wmemchr
- memchr
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- memchr
- wmemchr
helpviewer_keywords:
- memchr function
- wmemchr function
ms.assetid: 5a348581-28f1-4256-8434-687245f7fc9f
ms.openlocfilehash: b4640004526eda4ff26e9601e15298bcb8ba3c79
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232472"
---
# <a name="memchr-wmemchr"></a>memchr, wmemchr

Znajdź znaki w buforze.

## <a name="syntax"></a>Składnia

```C
void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C only
void *memchr(
   void *buffer,
   int c,
   size_t count
); // C++ only
const void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C++ only
wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C only
wchar_t *wmemchr(
   wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
const wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
```

### <a name="parameters"></a>Parametry

*buforu*<br/>
Wskaźnik do buforu.

*s*<br/>
Znak, który ma być wyszukiwany.

*liczbą*<br/>
Liczba znaków do sprawdzenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wskaźnik do pierwszej lokalizacji *c* w *buforze*. W przeciwnym razie zwraca wartość NULL.

## <a name="remarks"></a>Uwagi

`memchr`i `wmemchr` poszukaj pierwszego wystąpienia *c* w pierwszej *liczbie* znaków w *buforze*. Kończy się po znalezieniu *c* lub po sprawdzeniu pierwszej *liczby* znaków.

W języku C te funkcje przyjmują **`const`** wskaźnik dla pierwszego argumentu. W języku C++ dostępne są dwa przeciążenia. Przeciążenie pobierające wskaźnik do **`const`** zwraca wskaźnik do **`const`** ; wersja, która przyjmuje wskaźnik do **`const`** niezwracanego wskaźnika do niebędącego elementem **`const`** . W \_ przypadku, \_ \_ \_ gdy obie **`const`** **`const`** te funkcje są dostępne, są zdefiniowane poprawne przeciążenia w ramach monitora. Jeśli wymagane jest **`const`** niezachowanie w przypadku przeciążeń c++ w języku c++, zdefiniuj \_ zwracaną wartość symbolu const \_ .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`memchr`|\<memory.h> lub \<string.h>|
|`wmemchr`|\<wchar.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_memchr.c

#include <memory.h>
#include <stdio.h>

int  ch = 'r';
char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int result;
   printf( "String to be searched:\n             %s\n", string );
   printf( "             %s\n             %s\n\n", fmt1, fmt2 );

   printf( "Search char: %c\n", ch );
   pdest = memchr( string, ch, sizeof( string ) );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "Result:      %c found at position %d\n", ch, result );
   else
      printf( "Result:      %c not found\n" );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
String to be searched:
             The quick brown dog jumps over the lazy fox
                      1         2         3         4         5
             12345678901234567890123456789012345678901234567890

Search char: r
Result:      r found at position 12
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
