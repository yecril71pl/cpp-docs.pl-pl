---
title: "_ltoa —, _ltow — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ltoa
- _ltow
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
apitype: DLLExport
f1_keywords:
- ltow
- _ltot
- _ltoa
- _ltow
dev_langs: C++
helpviewer_keywords:
- converting integers
- _ltoa function
- _ltow function
- ltow function
- ltoa function
- long integer conversion to string
- converting numbers, to strings
ms.assetid: 14036104-2c25-4759-87c0-918ed8521e47
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 135c082e4d972b18af057bf22a718ac9c4170718
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltoa-ltow"></a>_ltoa, _ltow
Konwertuje długich liczb całkowitych na ciąg. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_ltoa_s —, _ltow_s —](../../c-runtime-library/reference/ltoa-s-ltow-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *_ltoa(  
   long value,  
   char *str,  
   int radix   
);  
wchar_t *_ltow(  
   long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ltoa(  
   long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ltow(  
   long value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Numer do skonwertowania.  
  
 `str`  
 Ciąg wyniku.  
  
 `radix`  
 Podstawa `value`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji, zwraca wskaźnik do `str`. Nie ma żadnych zwracany błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_ltoa` Funkcja konwertuje cyfry `value` na ciąg znaków zakończony znakiem null i zapisuje wynik (w bajtach do 33) w `str`. `radix` Argument określa podstawą `value`, które muszą być w zakresie od 2 36. Jeśli `radix` równa 10 i `value` jest ujemna, pierwszego znaku ciągu przechowywanych jest znak minus (-). `_ltow`jest to wersja znaków dwubajtowych `_ltoa`; druga argumentów i wartość `_ltow` są ciągami znaków dwubajtowych. Każda z tych funkcji jest specyficzne dla firmy Microsoft.  
  
> [!IMPORTANT]
>  Aby uniknąć przepełnienia buforu, upewnij się, że `str` bufor jest wystarczająco duży, aby pomieścić przekonwertowanego cyfr oraz końcowego znaku null i znak.  
  
 W języku C++ te funkcje mają przeciążenia szablonu. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_ltot`|`_ltoa`|`_ltoa`|`_ltow`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ltoa`|\<stdlib.h >|  
|`_ltow`|\<stdlib.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_itoa —](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [_itoa —, _i64toa —, _ui64toa —, _itow — _i64tow —, _ui64tow —](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [_ultoa —, _ultow —](../../c-runtime-library/reference/ultoa-ultow.md)