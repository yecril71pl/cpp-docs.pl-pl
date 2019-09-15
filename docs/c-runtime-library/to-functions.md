---
title: do funkcji
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- To
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
ms.openlocfilehash: f7a898d70e506ed4707ea718faa0ed618682c2c7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944822"
---
# <a name="to-functions"></a>do funkcji

Każda z funkcji **do** Functions i powiązane z nią makro (jeśli istnieją) konwertuje pojedynczy znak na inny znak.

|||
|-|-|
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[ToUpper, _toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|
|[ToLower, _tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||

## <a name="remarks"></a>Uwagi

Funkcje **do** i konwersje makr są następujące.

|Procedura|Macro|Opis|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|Konwertuje `c` na znak ASCII|
|`tolower`|`tolower`|Konwertuje `c` na małe litery, jeśli jest to konieczne|
|`_tolower`|`_tolower`|Konwertuje `c` na małe litery|
|`towlower`|Brak|Konwertuje `c` na odpowiadającą małą literę o szerokim znaku|
|`toupper`|`toupper`|Konwertuje `c` na wielkie litery, jeśli jest to konieczne|
|`_toupper`|`_toupper`|Konwertuje `c` na wielkie litery|
|`towupper`|Brak|Konwertuje znak c na odpowiadającą wielką literę litery|

Aby użyć wersji funkcji **do** procedur, które są również zdefiniowane jako makra, Usuń definicje makr z `#undef` dyrektywami lub nie dodawaj CType. C. Jeśli używasz opcji kompilatora/za, kompilator używa wersji `toupper` funkcji lub. `tolower` Deklaracje `tolower` i funkcji są w STDLIB. `toupper` C.

Procedura ustawia wszystkie poza kolejnością 7 bitów o wartości `c` 0, tak aby przekonwertowana wartość reprezentuje znak w zestawie znaków ASCII. `__toascii` Jeśli `c` już reprezentuje znak ASCII, `c` jest niezmieniony.

Procedury `tolower` i `toupper` :

- Są `LC_CTYPE` zależne od kategorii bieżących ustawień regionalnych (`tolower` wywołań `isupper` i `toupper` wywołań `islower`).

- Convert `c` if`c` reprezentuje literę do konwersji odpowiedniego przypadku w bieżących ustawieniach regionalnych i odwrotnie istnieje dla tych ustawień regionalnych. W przeciwnym razie jest niezmienione. `c`

Procedury `_tolower` i `_toupper` :

- Są niezależne od ustawień regionalnych, znacznie szybszymi `tolower` wersjami i **ToUpper.**

- Mogą być używane tylko wtedy, gdy **isascii (** `c` **)** i **IsUpper (** `c` **)** lub **IsLower (** `c` **)** , które są odpowiednio niezerowe.

- Mają niezdefiniowane wyniki `c` , jeśli nie jest literą ASCII odpowiedniej wielkości dla konwersji.

Funkcje `towlower` i `towupper` zwracająprzekonwertowanekopieifitylkowtedy,gdyobaponiższewarunkisą`c` inne niż zero. W przeciwnym razie jest niezmienione. `c`

- `c`jest znakiem dwubajtowym odpowiedniego przypadku (to jest, dla którego `iswupper` odpowiednio lub **iswlower** jest różna od zera).

- Istnieje odpowiedni znak dwubajtowy przypadku docelowego (to jest, dla którego `iswlower` odpowiednio lub **iswupper,** jest różny od zera).

## <a name="example"></a>Przykład

```
// crt_toupper.c
/* This program uses toupper and tolower to
 * analyze all characters between 0x0 and 0x7F. It also
 * applies _toupper and _tolower to any code in this
 * range for which these functions make sense.
 */

#include <ctype.h>
#include <string.h>

char msg[] = "Some of THESE letters are Capitals.";
char *p;

int main( void )
{
   printf( "%s\n", msg );

   /* Reverse case of message. */
   for( p = msg; p < msg + strlen( msg ); p++ )
   {
      if( islower( *p ) )
         putchar( _toupper( *p ) );
      else if( isupper( *p ) )
         putchar( _tolower( *p ) );
      else
         putchar( *p );
   }
}
```

```Output
Some of THESE letters are Capitals.
sOME OF these LETTERS ARE cAPITALS.
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../c-runtime-library/is-isw-routines.md)
