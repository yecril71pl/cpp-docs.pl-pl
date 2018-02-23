---
title: "mbstowcs_s —, _mbstowcs_s_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- _mbstowcs_s_l
- mbstowcs_s
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28f038c1529c2f7fb7bbc28127ee5b528474e0f0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l
Konwertuje sekwencji znaków wielobajtowych sekwencji odpowiednie znaki dwubajtowe. Wersje [mbstowcs —, _mbstowcs_l —](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count   
);  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `pReturnValue`  
 Liczba znaków konwersji.  
  
 [out] `wcstr`  
 Adres buforu dla wynikowy ciąg przekonwertowany znaków dwubajtowych.  
  
 [in] `sizeInWords`  
 Rozmiar `wcstr` buforu w wyrazy.  
  
 [in] `mbstr`  
 Adres sekwencji null zakończone znaki wielobajtowe.  
  
 [in] `count`  
 Maksymalna liczba znaki dwubajtowe, które mają być przechowywane w `wcstr` buforu Trwa przerywanie działania wartość null, z wyłączeniem lub [_truncate —](../../c-runtime-library/truncate.md).  
  
 [in] `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie, kod błędu w przypadku awarii.  
  
|Warunek błędu|Wartość zwracana i `errno`|  
|---------------------|------------------------------|  
|`wcstr` jest `NULL` i `sizeInWords` > 0.|`EINVAL`|  
|`mbstr` jest `NULL`|`EINVAL`|  
|Bufor docelowy jest zbyt mały, aby pomieścił skonwertowany ciąg (chyba że `count` jest `_TRUNCATE`; zobacz uwagi poniżej)|`ERANGE`|  
|`wcstr` nie jest `NULL` i `sizeInWords` == 0|`EINVAL`|  
  
 Jeśli występuje którykolwiek z tych warunków, zgodnie z opisem w wywołaniu wyjątek nieprawidłowy parametr [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, funkcja zwraca błąd o kodzie i ustawia `errno` wymienione w tabeli.  
  
## <a name="remarks"></a>Uwagi  
 `mbstowcs_s` Funkcja konwertuje ciąg znaków wielobajtowych wskazywana przez `mbstr` w znaki dwubajtowe są przechowywane w buforze wskazywana przez `wcstr`. Konwersja będzie kontynuowane dla każdego znaku, dopóki spełniony jest jeden z następujących warunków:  
  
-   Napotkano znak null wielobajtowe  
  
-   Napotkano nieprawidłowy znaków wielobajtowych  
  
-   Liczba znaki dwubajtowe są przechowywane w `wcstr` buforu equals `count`.  
  
 Ciąg docelowego jest zawsze zerem (nawet w przypadku błędu).  
  
 Jeśli `count` jest specjalna wartość [_truncate —](../../c-runtime-library/truncate.md), następnie `mbstowcs_s` konwertuje tyle ciągu jako spowoduje mieści się w bufor docelowy pozostawiając nadal miejsca dla terminatora o wartości null.  
  
 Jeśli `mbstowcs_s` pomyślnie konwertuje ciąg źródłowy umieszcza w znaki dwubajtowe przekonwertowanego ciągu, włącznie z terminatorem null do rozmiaru `*pReturnValue` (pod warunkiem `pReturnValue` nie jest `NULL`). Dzieje się tak nawet wtedy, gdy `wcstr` argument jest `NULL` i zapewnia możliwość określenia wymagany rozmiar buforu. Należy pamiętać, że jeśli `wcstr` jest `NULL`, `count` jest ignorowany i `sizeInWords` musi być równa 0.  
  
 Jeśli `mbstowcs_s` napotkał nieprawidłowy znaków wielobajtowych umieszcza 0 w `*pReturnValue`, ustawia bufor docelowy na pusty ciąg, ustawia `errno` do `EILSEQ`i zwraca `EILSEQ`.  
  
 Jeśli sekwencje wskazywana przez `mbstr` i `wcstr` nakładają się zachowanie `mbstowcs_s` jest niezdefiniowana.  
  
> [!IMPORTANT]
>  Upewnij się, że `wcstr` i `mbstr` nie pokrywają oraz że `count` poprawnie odzwierciedla liczbę znaków wielobajtowych do konwersji.  
  
 `mbstowcs_s` używa bieżące ustawienia regionalne dla dowolnego zachowań zależnych od ustawień regionalnych. `_mbstowcs_s_l` jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`mbstowcs_s`|\<stdlib.h>|  
|`_mbstowcs_s_l`|\<stdlib.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs —, _wcstombs_l —](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)