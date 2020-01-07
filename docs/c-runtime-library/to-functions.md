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
ms.openlocfilehash: df8f59088cd402503fe31f768557e3ed936b31ec
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301694"
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
|`toupper`|`toupper`|Konwertuje `c` na wielkie litery, jeśli są odpowiednie|
|`_toupper`|`_toupper`|Konwertuje `c` na wielkie litery|
|`towupper`|Brak|Konwertuje znak c na odpowiadającą wielką literę litery|

Aby użyć wersji funkcji **do** procedur, które są również zdefiniowane jako makra, Usuń definicje makr z dyrektywami `#undef` lub nie dodawaj CType. C. Jeśli używasz opcji kompilatora/za, kompilator używa wersji funkcji `toupper` lub `tolower`. Deklaracje `toupper` i `tolower` funkcje są w STDLIB. C.

Procedura `__toascii` ustawia wszystkie, ale minimalna liczba 7 bitów z `c` na 0, tak że przekonwertowana wartość reprezentuje znak w zestawie znaków ASCII. Jeśli `c` już reprezentuje znak ASCII, `c` nie zmieni się.

Procedury `tolower` i `toupper`:

- Są zależne od kategorii `LC_CTYPE` bieżących ustawień regionalnych (`tolower` wywołań `isupper` i `toupper` wywołań `islower`).

- Konwertuj `c`, jeśli `c` reprezentuje literę do przekonwertowania odpowiedniego przypadku w bieżących ustawieniach regionalnych i odwrotnym przypadku dla tych ustawień regionalnych. W przeciwnym razie `c` nie zmieni się.

Procedury `_tolower` i `_toupper`:

- Są niezależne od ustawień regionalnych, znacznie szybsze wersje `tolower` i **ToUpper.**

- Mogą być używane tylko wtedy, gdy **isascii (** `c` **)** i **IsUpper (** `c` **)** lub **IsLower (** `c` **)** , które są odpowiednio niezerowe.

- Mają niezdefiniowane wyniki, jeśli `c` nie jest literą ASCII odpowiedniej wielkości dla konwersji.

Funkcje `towlower` i `towupper` zwracają przekonwertowane kopie `c` Jeśli i tylko wtedy, gdy oba poniższe warunki mają wartość różną od zera. W przeciwnym razie `c` nie zmieni się.

- `c` jest znakiem dwubajtowym odpowiedniego przypadku (czyli dla którego `iswupper` lub **iswlower,** odpowiednio, jest różna od zera).

- Istnieje odpowiedni znak dwubajtowy przypadku docelowego (to jest, dla którego odpowiednio `iswlower` lub **iswupper,** jest różna od zera).

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

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../c-runtime-library/is-isw-routines.md)
