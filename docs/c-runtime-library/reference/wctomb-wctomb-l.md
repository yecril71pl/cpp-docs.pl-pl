---
title: "wctomb —, _wctomb_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wctomb_l
- wctomb
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
f1_keywords: wctomb
dev_langs: C++
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cbba6a51a51720248667cf04738ad16203717db9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="wctomb-wctombl"></a>wctomb, _wctomb_l
Przekonwertować odpowiednich znaków wielobajtowych znaków dwubajtowych. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [wctomb_s —, _wctomb_s_l —](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int wctomb(  
   char *mbchar,  
   wchar_t wchar   
);  
int _wctomb_l(  
   char *mbchar,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mbchar`  
 Adres znaków wielobajtowych.  
  
 `wchar`  
 Znaków dwubajtowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli `wctomb` konwertuje znaków dwubajtowych do znaków wielobajtowych, zwraca liczbę bajtów (który nigdy nie jest większa niż `MB_CUR_MAX`) w znaków dwubajtowych. Jeśli `wchar` jest znakiem pustym znaków dwubajtowych (L '\0'), `wctomb` zwraca wartość 1. Jeśli wskaźnika docelowej `mbchar` ma wartość NULL, `wctomb` zwraca wartość 0. Jeśli konwersja nie jest możliwe w bieżących ustawień regionalnych, `wctomb` zwraca wartość -1 i `errno` ma ustawioną wartość `EILSEQ`.  
  
## <a name="remarks"></a>Uwagi  
 `wctomb` Funkcji konwertuje jego `wchar` argument odpowiednich znaków wielobajtowych i zapisuje wynik w `mbchar`. Funkcję można wywołać z dowolnego punktu w programach. `wctomb`używa bieżące ustawienia regionalne dla dowolnego zachowań zależnych od ustawień regionalnych. `_wctomb_l` jest taka sama jak `wctomb` z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 `wctomb`sprawdza poprawność parametrów. Jeśli `mbchar` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca wartość -1.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`wctomb`|\<stdlib.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Ten program ilustruje zachowanie wctomb — funkcja.  
  
```  
// crt_wctomb.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int i;  
   wchar_t wc = L'a';  
   char *pmb = (char *)malloc( MB_CUR_MAX );  
  
   printf( "Convert a wide character:\n" );  
   i = wctomb( pmb, wc ); // C4996  
   // Note: wctomb is deprecated; consider using wctomb_s  
   printf( "   Characters converted: %u\n", i );  
   printf( "   Multibyte character: %.1s\n\n", pmb );  
}  
```  
  
```Output  
Convert a wide character:  
   Characters converted: 1  
   Multibyte character: a  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [_mbclen —, mblen —, _mblen_l —](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs —, _mbstowcs_l —](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc —, _mbtowc_l —](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs —, _wcstombs_l —](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [Procedura WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)