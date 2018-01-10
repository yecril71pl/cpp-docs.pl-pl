---
title: do funkcji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords: To
dev_langs: C++
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ef97b5e5ab2c21b375814cf117d6155b4a502795
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="to-functions"></a>do funkcji
Każdy z **do** funkcji i jej skojarzone makra, konwertuje pojedynczy znak do innego znaku.  
  
|||  
|-|-|  
|[__toascii —](../c-runtime-library/reference/toascii-toascii.md)|[toupper _toupper —, towupper —](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|  
|[tolower _tolower —, towlower —](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||  
  
## <a name="remarks"></a>Uwagi  
 **Do** konwersje makra i funkcje są następujące.  
  
|Procedura|Makra|Opis|  
|-------------|-----------|-----------------|  
|`__toascii`|`__toascii`|Konwertuje `c` do znaków ASCII|  
|`tolower`|`tolower`|Konwertuje `c` na małe litery w razie potrzeby|  
|`_tolower`|`_tolower`|Konwertuje `c` na małe litery.|  
|`towlower`|Brak|Konwertuje `c` do odpowiednich znaków dwubajtowych małą literę|  
|`toupper`|`toupper`|Konwertuje `c` na wielkie litery w razie potrzeby|  
|`_toupper`|`_toupper`|Konwertuje `c` na wielkie litery|  
|`towupper`|Brak|Konwertuje c do odpowiednich znaków dwubajtowych wielką literę.|  
  
 Aby użyć wersji funkcji **do** procedur, które także są zdefiniowane jako makra, Usuń definicje makr z `#undef` dyrektywy lub nie dołączaj CTYPE. H. Jeśli używasz /Za — opcja kompilatora, kompilator używa wersji funkcji `toupper` lub `tolower`. Deklaracje `toupper` i `tolower` funkcji znajdują się w STDLIB. H.  
  
 `__toascii` Rutynowych wszystkie zestawy, ale znaczącymi bitami 7 usługi bits `c` 0, dzięki czemu skonwertowana wartość reprezentuje znak zestawu znaków ASCII. Jeśli `c` już reprezentuje znaków ASCII `c` niezmieniona.  
  
 `tolower` i `toupper` procedury:  
  
-   Są zależne od `LC_CTYPE` kategorii bieżące ustawienia regionalne (`tolower` wywołania `isupper` i `toupper` wywołania `islower`).  
  
-   Konwertuj `c` Jeśli `c` reprezentuje przekonwertowania litery w przypadku odpowiednie bieżące ustawienia regionalne i przeciwnym wypadku istnieje dla ustawień regionalnych. W przeciwnym razie `c` jest bez zmian.  
  
 `_tolower` i `_toupper` procedury:  
  
-   Niezależne od ustawień regionalnych, znacznie szybsze wersji `tolower` i **toupper.**  
  
-   Mogą być używane tylko wtedy, gdy **isascii — (**`c`**)** i **isupper — (**`c`**)** lub **islower — (**`c`**)**odpowiednio jest różna od zera.  
  
-   Ma niezdefiniowane wyniki, jeśli `c` nie jest odpowiednie w przypadku konwertowania litery ASCII.  
  
 `towlower` i `towupper` zwracają przekonwertowanego kopię `c` tylko wtedy, gdy oba poniższe warunki są różną od zera. W przeciwnym razie `c` jest bez zmian.  
  
-   `c`jest szerokie odpowiednim przypadku (to znaczy, dla którego `iswupper` lub **iswlower —,** odpowiednio jest różna od zera).  
  
-   Brak odpowiedniego szerokie w przypadku docelowej (oznacza to, dla którego `iswlower` lub **iswupper —,** odpowiednio jest różna od zera).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../c-runtime-library/locale.md)   
 [is, isw, procedury](../c-runtime-library/is-isw-routines.md)