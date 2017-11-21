---
title: "_ultoa —, _ultow — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ultoa
- _ultow
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
- ultot
- ultow
- _ultoa
- _ultow
- _ultot
dev_langs: C++
helpviewer_keywords:
- ultot function
- converting integers
- _ultot function
- ultow function
- integers, converting
- _ultow function
- _ultoa function
- converting numbers, to strings
ms.assetid: 7a472dc4-5652-4513-93c3-3358522c23be
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 05a79538edf1e39b26ad38f365b5fc52bb713f61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ultoa-ultow"></a>_ultoa, _ultow
Konwertuj niepodpisane długich liczb całkowitych na ciąg. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_ultoa_s —, _ultow_s —](../../c-runtime-library/reference/ultoa-s-ultow-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *_ultoa(  
   unsigned long value,  
   char *str,  
   int radix   
);  
wchar_t *_ultow(  
   unsigned long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ultoa(  
   unsigned long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ultow(  
   unsigned long value,  
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
 `_ultoa` Funkcji konwertuje `value` na ciąg znaków zakończony znakiem null i zapisuje wynik (w bajtach do 33) w `str`. Sprawdzanie przepełnienia nie jest wykonywane. `radix`Określa podstawą `value`; `radix` musi należeć do zakresu 2 36. `_ultow`jest to wersja znaków dwubajtowych `_ultoa`.  
  
> [!IMPORTANT]
>  Aby uniknąć przepełnienia buforu, upewnij się, że `str` bufor jest wystarczająco duży, aby pomieścić przekonwertowanego cyfry oraz końcowego znaku null.  
  
 W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ultot`|`_ultoa`|`_ultoa`|`_ultow`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ultoa`|\<stdlib.h >|  
|`_ultow`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_itoa —](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [_itoa —, _i64toa —, _ui64toa —, _itow — _i64tow —, _ui64tow —](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)