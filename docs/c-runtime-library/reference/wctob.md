---
title: "wctob — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: wctob
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords: wctob
dev_langs: C++
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e52046f648d3a2d5ca1e80dba861afda8e79f34
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="wctob"></a>wctob
Określa, czy znaków dwubajtowych odpowiada znaków wielobajtowych i zwraca jego reprezentacja znaków wielobajtowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
int wctob(  
   wint_t wchar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wchar`  
 Wartość do tłumaczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli `wctob` pomyślnie konwertuje znaków dwubajtowych, zwraca jej reprezentacji znaków wielobajtowych tylko wtedy, gdy znaków wielobajtowych dokładnie jednego bajtu. Jeśli `wctob` napotka znaków dwubajtowych nie można konwertować znaków wielobajtowych lub znaków wielobajtowych nie jest dokładnie jeden długi, zwraca -1 bajt.  
  
## <a name="remarks"></a>Uwagi  
 `wctob` Funkcja konwertuje znaków dwubajtowych zawarte w `wchar` do odpowiednich znaków wielobajtowych przekazany przez zwracany `int` wartość, jeśli znaków wielobajtowych jest dokładnie jeden bajt.  
  
 Jeśli `wctob` nie powiodła się i nie odpowiednich znaków wielobajtowych znaleziono funkcja ustawia `errno` do `EILSEQ` i zwraca wartość -1.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`wctob`|\<WChar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Ten program ilustruje zachowanie `wcstombs` funkcji.  
  
```  
// crt_wctob.c  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    int     bChar = 0;  
    wint_t  wChar = 0;  
  
    // Set the corresponding wide character to exactly one byte.  
    wChar = (wint_t)'A';  
  
    bChar = wctob( wChar );  
    if (bChar == WEOF)  
    {  
        printf( "No corresponding multibyte character was found.\n");  
    }  
    else  
    {  
        printf( "Determined the corresponding multibyte character to"  
                " be \"%c\".\n", bChar);  
    }  
}  
  
```  
  
```Output  
Determined the corresponding multibyte character to be "A".  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [_mbclen —, mblen —, _mblen_l —](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs —, _mbstowcs_l —](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc —, _mbtowc_l —](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb —, _wctomb_l —](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [Procedura WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)