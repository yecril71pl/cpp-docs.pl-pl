---
title: "wctomb_s —, _wctomb_s_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wctomb_s_l
- wctomb_s
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
f1_keywords:
- wctomb_s
- _wctomb_s_l
dev_langs: C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3c819f62f36966363f32eb16b7af758de274d3d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="wctombs-wctombsl"></a>wctomb_s, _wctomb_s_l
Konwertuje odpowiednich znaków wielobajtowych znaków dwubajtowych. Wersja [wctomb —, _wctomb_l —](../../c-runtime-library/reference/wctomb-wctomb-l.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t wctomb_s(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar   
);  
errno_t _wctomb_s_l(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pRetValue`  
 Liczba bajtów lub kod informujący o wyniku.  
  
 [out]`mbchar`  
 Adres znaków wielobajtowych.  
  
 [in]`sizeInBytes`  
 Rozmiar buforu `mbchar`.  
  
 [in]`wchar`  
 Znaków dwubajtowych.  
  
 [in]`locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie, kod błędu w przypadku awarii.  
  
 Warunki błędów  
  
|`mbchar`|`sizeInBytes`|Wartość zwracana|`pRetValue`|  
|--------------|-------------------|------------------|-----------------|  
|`NULL`|>0|`EINVAL`|Nie zmodyfikowano|  
|wszystkie|>`INT_MAX`|`EINVAL`|Nie zmodyfikowano|  
|wszystkie|za mały|`EINVAL`|Nie zmodyfikowano|  
  
 Jeśli dowolne z powyższych warunków błąd wystąpi, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `wctomb` zwraca `EINVAL` i ustawia `errno` do `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `wctomb_s` Funkcji konwertuje jego `wchar` argument odpowiednich znaków wielobajtowych i zapisuje wynik w `mbchar`. Funkcję można wywołać z dowolnego punktu w programach.  
  
 Jeśli `wctomb_s` konwertuje znaków dwubajtowych do znaków wielobajtowych, umieszcza liczba bajtów (który nigdy nie jest większa niż `MB_CUR_MAX`) w znaków dwubajtowych w całkowitą wskazywana przez `pRetValue`. Jeśli `wchar` jest znakiem pustym znaków dwubajtowych (L '\0'), `wctomb_s` wypełnia `pRetValue` o 1. Jeśli wskaźnika docelowej `mbchar` ma wartość NULL, `wctomb_s` umieszcza 0 `pRetValue`. Jeśli konwersja nie jest możliwe w bieżących ustawień regionalnych, `wctomb_s` umieszcza -1 `pRetValue`.  
  
 `wctomb_s`używa bieżące ustawienia regionalne dla informacji zależnych od ustawień regionalnych. `_wctomb_s_l` jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`wctomb_s`|\<stdlib.h >|  
|`_wctomb_s_l`|\<stdlib.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Ten program ilustruje zachowanie `wctomb` funkcji.  
  
```  
// crt_wctomb_s.cpp  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    int i;  
    wchar_t wc = L'a';  
    char *pmb = (char *)malloc( MB_CUR_MAX );  
  
    printf_s( "Convert a wide character:\n" );  
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );  
    printf_s( "   Characters converted: %u\n", i );  
    printf_s( "   Multibyte character: %.1s\n\n", pmb );  
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