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
ms.openlocfilehash: a54f20d6ae4dead5ba7c606fd28d456e96ff31d6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836081"
---
# <a name="to-functions"></a>do funkcji

Każda z funkcji **do** Functions i powiązane z nią makro (jeśli istnieją) konwertuje pojedynczy znak na inny znak.

[__toascii](../c-runtime-library/reference/toascii-toascii.md)\
[ToLower, _tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)\
[ToUpper, _toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)

## <a name="remarks"></a>Uwagi

Funkcje **do** i konwersje makr są następujące.

|Procedura|Makro|Opis|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|Konwertuje `c` na znak ASCII|
|`tolower`|`tolower`|Konwertuje `c` na małe litery, jeśli jest to konieczne|
|`_tolower`|`_tolower`|Konwertuje `c` na małe litery|
|`towlower`|Brak|Konwertuje `c` na odpowiadającą małą literę o szerokim znaku|
|`toupper`|`toupper`|Konwertuje `c` na wielkie litery, jeśli jest to konieczne|
|`_toupper`|`_toupper`|Konwertuje `c` na wielkie litery|
|`towupper`|Brak|Konwertuje znak c na odpowiadającą wielką literę litery|

Aby użyć wersji funkcji **do** procedur, które są również zdefiniowane jako makra, Usuń definicje makr z `#undef` dyrektywami lub nie dodawaj CType. C. Jeśli używasz opcji kompilatora/za, kompilator używa wersji funkcji `toupper` lub `tolower` . Deklaracje `toupper` i `tolower` funkcji są w STDLIB. C.

`__toascii`Procedura ustawia wszystkie poza kolejnością 7 bitów o wartości `c` 0, tak aby przekonwertowana wartość reprezentuje znak w zestawie znaków ASCII. Jeśli `c` już reprezentuje znak ASCII, `c` jest niezmieniony.

`tolower`Procedury i `toupper` :

- Są zależne od `LC_CTYPE` kategorii bieżących ustawień regionalnych ( `tolower` wywołań `isupper` i `toupper` wywołań `islower` ).

- Convert `c` if `c` reprezentuje literę do konwersji odpowiedniego przypadku w bieżących ustawieniach regionalnych i odwrotnie istnieje dla tych ustawień regionalnych. W przeciwnym razie `c` jest niezmienione.

`_tolower`Procedury i `_toupper` :

- Są niezależne od ustawień regionalnych, znacznie szybszymi wersjami `tolower` i **ToUpper.**

- Mogą być używane tylko wtedy, gdy **isascii (** `c` **)** i **IsUpper (** `c` **)** lub **IsLower (** `c` **)**, które są odpowiednio niezerowe.

- Mają niezdefiniowane wyniki `c` , jeśli nie jest literą ASCII odpowiedniej wielkości dla konwersji.

`towlower`Funkcje i `towupper` zwracają przekonwertowane kopie `c` if i tylko wtedy, gdy oba poniższe warunki są inne niż zero. W przeciwnym razie `c` jest niezmienione.

- `c` jest znakiem dwubajtowym odpowiedniego przypadku (to jest, dla którego `iswupper` odpowiednio lub **iswlower** jest różna od zera).

- Istnieje odpowiedni znak dwubajtowy przypadku docelowego (to jest, dla którego `iswlower` odpowiednio lub **iswupper,** jest różny od zera).

## <a name="example"></a>Przykład

```c
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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../c-runtime-library/data-conversion.md)<br/>
[Regionalne](../c-runtime-library/locale.md)<br/>
[to, ISW, procedury](../c-runtime-library/is-isw-routines.md)
