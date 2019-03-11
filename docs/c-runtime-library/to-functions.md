---
title: do funkcji
ms.date: 11/04/2016
apilocation:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
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
ms.openlocfilehash: 17d80507462b3eb0fdfb5d9e41da6162947bd3de
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742532"
---
# <a name="to-functions"></a>do funkcji

Każdy z **do** funkcji i jej skojarzone — makro, konwertuje jeden znak inny znak.

|||
|-|-|
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[toupper _toupper —, towupper —](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|
|[tolower _tolower —, towlower —](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||

## <a name="remarks"></a>Uwagi

**Do** konwersje makra i funkcje są następujące.

|Procedura|Macro|Opis|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|Konwertuje `c` znak ASCII|
|`tolower`|`tolower`|Konwertuje `c` na małe litery, jeśli jest to odpowiednie|
|`_tolower`|`_tolower`|Konwertuje `c` na małe litery.|
|`towlower`|Brak|Konwertuje `c` do odpowiedniego znaku dwubajtowego mała litera|
|`toupper`|`toupper`|Konwertuje `c` na wielką, jeśli jest to odpowiednie|
|`_toupper`|`_toupper`|Konwertuje `c` na wielkie litery|
|`towupper`|Brak|Konwertuje c do odpowiedniego znaku dwubajtowego wielką literą.|

Do użycia funkcja wersje **do** procedur, które są również określone jako makra, albo usunięcie definicji makra z `#undef` dyrektywy lub nie dołączaj CTYPE. H. Jeśli używasz opcji kompilatora/za, kompilator używa funkcji wersję `toupper` lub `tolower`. Deklaracje `toupper` i `tolower` funkcji znajdują się w STDLIB. H.

`__toascii` Rutynowych Ustawia wszystkie, ale niskiego rzędu 7 bity `c` 0, dzięki czemu przekonwertowana wartość reprezentuje znak zestawu znaków ASCII. Jeśli `c` już reprezentuje znak ASCII `c` pozostaje niezmieniony.

`tolower` i `toupper` procedury:

- Są zależne od `LC_CTYPE` kategorii bieżących ustawień regionalnych (`tolower` wywołania `isupper` i `toupper` wywołania `islower`).

- Konwertuj `c` Jeśli `c` reprezentuje konwersję litery mają odpowiednią wielkość liter w bieżących ustawień regionalnych i w przeciwnym wypadku nie istnieje dla danego ustawienia regionalnego. W przeciwnym razie `c` pozostaje niezmieniony.

`_tolower` i `_toupper` procedury:

- Są niezależne od ustawień regionalnych, znacznie szybciej wersje `tolower` i **toupper.**

- Można użyć tylko wtedy, gdy **isascii — (**`c`**)** i **isupper (**`c`**)** lub **islower (**`c`**)**, odpowiednio, czy wartość różną od zera.

- Ma niezdefiniowane wyniki, jeśli `c` nie jest litery ASCII odpowiednią wielkość liter do konwersji.

`towlower` i `towupper` funkcje zwracają przekonwertowanego kopię `c` tylko wtedy, gdy oba poniższe warunki są wartość różną od zera. W przeciwnym razie `c` pozostaje niezmieniony.

- `c` jest znakiem dwubajtowym odpowiednią wielkość liter (oznacza to, dla którego `iswupper` lub **iswlower —,** odpowiednio jest różna od zera).

- Brak odpowiedniego znakiem dwubajtowym przypadek docelowego (oznacza to, dla którego `iswlower` lub **iswupper —,** odpowiednio jest różna od zera).

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
