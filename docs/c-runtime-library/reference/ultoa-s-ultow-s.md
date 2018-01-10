---
title: "_ultoa_s —, _ultow_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ultow_s
- _ultoa_s
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
- _ultow_s
- ultoa_s
- ultow_s
- _ultoa_s
dev_langs: C++
helpviewer_keywords:
- _ultoa_s function
- converting integers
- integers, converting
- _ultow_s function
- ultoa_s function
- converting numbers, to strings
- ultow_s function
ms.assetid: 606ce905-6752-46ac-a15a-bdc22920e1d4
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1785204bc6043973fac4eeb490b8e072e3ec4a95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ultoas-ultows"></a>_ultoa_s, _ultow_s
Konwertuj niepodpisane długich liczb całkowitych na ciąg. Są to wersje [_ultoa —, _ultow —](../../c-runtime-library/reference/ultoa-ultow.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _ultoa_s(  
    unsigned long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ultoa_s(  
    unsigned long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ultow_s(  
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
  
 `sizeOfstr`  
 Rozmiar `str` w bajtach dla `_ultoa_s` lub wyrazów dla `_ultow_s`.  
  
 `radix`  
 Podstawa `value`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli funkcja zakończyło się pomyślnie lub kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `_ultoa_s` Funkcja konwertuje cyfry `value` na ciąg znaków zakończony znakiem null i zapisuje wynik (w bajtach do 33) w `str`. `radix` Argument określa podstawą `value`, które muszą być w zakresie od 2 36. `_ultow_s`jest to wersja znaków typu wide `_ultoa_s`; drugi argument funkcji `_ultow_s` jest ciągów znaków dwubajtowych.  
  
 Jeśli `str` jest `NULL` wskaźnika, lub jeśli `sizeOfstr` jest mniejsza lub równa zero, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw `errno` do `EINVAL` lub, jeśli `value` lub `str` poza zakresem długich liczb całkowitych, te funkcje będą Zwróć -1 i ustaw `errno` do `ERANGE`.  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ultot_s`|`_ultoa_s`|`_ultoa_s`|`_ultow_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ultoa_s`|\<stdlib.h >|  
|`_ultow_s`|\<stdlib.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [_ultoa —, _ultow —](../../c-runtime-library/reference/ultoa-ultow.md)   
 [_ltoa —, _ltow —](../../c-runtime-library/reference/ltoa-ltow.md)   
 [_ltoa_s —, _ltow_s —](../../c-runtime-library/reference/ltoa-s-ltow-s.md)   
 [_ltoa_s, _ltow_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)