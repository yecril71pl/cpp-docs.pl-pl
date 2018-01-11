---
title: "wcsrtombs_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: wcsrtombs_s
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
f1_keywords: wcsrtombs_s
dev_langs: C++
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 025acdf18d0e5322ef43de800e3577233a93cb86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="wcsrtombss"></a>wcsrtombs_s
Konwertowanie ciągu znaków typu wide reprezentacji ciągu znaków wielobajtowych. Wersja [wcsrtombs —](../../c-runtime-library/reference/wcsrtombs.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pReturnValue`  
 Liczba znaków konwersji.  
  
 [out]`mbstr`  
 Adres buforu dla wynikowy ciąg znaków wielobajtowych przekonwertowany.  
  
 [out]`sizeInBytes`  
 Wyrażony w bajtach rozmiar `mbstr` buforu.  
  
 [in]`wcstr`  
 Wskazuje ciąg znaków typu wide do skonwertowania.  
  
 [in]`count`  
 Maksymalna liczba bajtów do zapisania w `mbstr` buforu, lub [_truncate —](../../c-runtime-library/truncate.md).  
  
 [in]`mbstate`  
 Wskaźnik do `mbstate_t` konwersji stanu obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie, kod błędu w przypadku awarii.  
  
|Warunek błędu|Wartość zwracana i`errno`|  
|---------------------|------------------------------|  
|`mbstr`jest `NULL` i `sizeInBytes` > 0.|`EINVAL`|  
|`wcstr`jest`NULL`|`EINVAL`|  
|Bufor docelowy jest zbyt mały, aby pomieścił skonwertowany ciąg (chyba że `count` jest `_TRUNCATE`; zobacz uwagi poniżej)|`ERANGE`|  
  
 Jeśli występuje którykolwiek z tych warunków, zgodnie z opisem w wywołaniu wyjątek nieprawidłowy parametr [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, funkcja zwraca błąd o kodzie i ustawia `errno` wymienione w tabeli.  
  
## <a name="remarks"></a>Uwagi  
 `wcsrtombs_s` Funkcja konwertuje ciąg znaki dwubajtowe wskazywana przez `wcstr` do znaków wielobajtowych przechowywane w buforze wskazywana przez `mbstr`, za pomocą konwersji stanie zawartymi w `mbstate`. Konwersja będzie kontynuowane dla każdego znaku, dopóki spełniony jest jeden z następujących warunków:  
  
-   Napotkano pusty znaków dwubajtowych  
  
-   Napotkano znaków dwubajtowych, której nie można przekonwertować  
  
-   Liczba bajtów przechowywanych w `mbstr` buforu equals `count`.  
  
 Ciąg docelowego jest zawsze zerem (nawet w przypadku błędu).  
  
 Jeśli `count` jest specjalna wartość [_truncate —](../../c-runtime-library/truncate.md), następnie `wcsrtombs_s` konwertuje tyle ciągu jako spowoduje mieści się w bufor docelowy pozostawiając nadal miejsca dla terminatora o wartości null.  
  
 Jeśli `wcsrtombs_s` pomyślnie konwertuje ciąg źródłowy umieszcza rozmiar w bajtach skonwertowany ciąg, włącznie z terminatorem null do `*pReturnValue` (pod warunkiem `pReturnValue` nie jest `NULL`). Dzieje się tak nawet wtedy, gdy `mbstr` argument jest `NULL` i zapewnia możliwość określenia wymagany rozmiar buforu. Należy pamiętać, że jeśli `mbstr` jest `NULL`, `count` jest ignorowana.  
  
 Jeśli `wcsrtombs_s` napotka znaków dwubajtowych nie można przekonwertować znaków wielobajtowych, umieszcza -1 w `*pReturnValue`, ustawia bufor docelowy na pusty ciąg, ustawia `errno` do `EILSEQ`i zwraca `EILSEQ`.  
  
 Jeśli sekwencje wskazywana przez `wcstr` i `mbstr` nakładają się zachowanie `wcsrtombs_s` jest niezdefiniowana. `wcsrtombs_s`ma to wpływ na poszczególnych kategorii LC_TYPE bieżące ustawienia regionalne.  
  
> [!IMPORTANT]
>  Upewnij się, że `wcstr` i `mbstr` nie nakładają oraz że `count` poprawnie odzwierciedla liczbę znaki dwubajtowe do konwersji.  
  
 `wcsrtombs_s` Funkcja różni się od [wcstombs_s —, _wcstombs_s_l —](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md) przez jego restartability. Stan konwersji jest przechowywany w `mbstate` dla kolejnych wywołań w tej samej lub innych funkcji ponownego uruchamiania. Wyniki są niezdefiniowane, gdy mieszanie korzystanie z funkcji ponownego uruchamiania i nonrestartable. Na przykład aplikacja może użyć `wcsrlen` zamiast `wcslen`, jeśli kolejne wywołanie `wcsrtombs_s` użyto zamiast`wcstombs_s.`  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Wyjątki  
 `wcsrtombs_s` Funkcji jest bezpieczne wielowątkowe tak długo, jak wywołuje żadnej funkcji w bieżącym wątku `setlocale` podczas wykonywania tej funkcji i `mbstate` ma wartość null.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_wcsrtombs_s.cpp  
//   
// This code example converts a wide  
// character string into a multibyte  
// character string.  
//  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
void main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    errno_t         err;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,  
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);  
    if (err == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfully converted.\n" );  
    }  
}  
```  
  
```Output  
The string was successfully converted.  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`wcsrtombs_s`|\<WChar.h >|  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb —](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s —](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb —, _wctomb_l —](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs —, _wcstombs_l —](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)