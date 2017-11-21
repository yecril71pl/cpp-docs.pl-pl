---
title: "_strdate —, _wstrdate — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strdate
- _wstrdate
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tstrdate
- wstrdate
- _wstrdate
- _strdate
- strdate
dev_langs: C++
helpviewer_keywords:
- strdate function
- dates, copying
- tstrdate function
- _wstrdate function
- wstrdate function
- _strdate function
- _tstrdate function
- copying dates
ms.assetid: de8e4097-58f8-42ba-9dcd-cb4d9a9f1696
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e398363fd12853b06644019201028067cf10f7dd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="strdate-wstrdate"></a>_strdate, _wstrdate
Skopiuj bieżącą datę systemową w buforze. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_strdate_s —, _wstrdate_s —](../../c-runtime-library/reference/strdate-s-wstrdate-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *_strdate(  
   char *datestr   
);  
wchar_t *_wstrdate(  
   wchar_t *datestr   
);  
template <size_t size>  
char *_strdate(  
   char (&datestr)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wstrdate(  
   wchar_t (&datestr)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `datestr`  
 Wskaźnik do buforu zawierającą ciąg daty sformatowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wskaźnik do wynikowy ciąg znaków `datestr`.  
  
## <a name="remarks"></a>Uwagi  
 Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_strdate_s —, _wstrdate_s —](../../c-runtime-library/reference/strdate-s-wstrdate-s.md). Zaleca się, że bezpieczniejsze funkcji można używać, gdy jest to możliwe.  
  
 `_strdate` Funkcja kopiuje bieżącej systemowej daty do bufor wskazywany przez `datestr`, sformatowany `mm` / `dd` / `yy`, gdzie `mm` jest reprezentujący dwie cyfry miesiąc, `dd` to dwie cyfry reprezentującą dzień, a `yy` to dwa ostatnie cyfry roku. Na przykład ciąg `12/05/99` reprezentuje 5 grudnia 1999. Rozmiar buforu musi być co najmniej 9 bajtów.  
  
 Jeśli `datestr` jest `NULL` wskaźnika, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw `errno` do `EINVAL`.  
  
 `_wstrdate`jest to wersja znaków dwubajtowych `_strdate`; argumentów i wartości `_wstrdate` są ciągami znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.  
  
 W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstrdate`|`_strdate`|`_strdate`|`_wstrdate`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_strdate`|\<Time.h >|  
|`_wstrdate`|\<Time.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// strdate.c  
// compile with: /W3  
#include <time.h>  
#include <stdio.h>  
int main()  
{  
    char tmpbuf[9];  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    printf( "OS date: %s\n", _strdate(tmpbuf) ); // C4996  
    // Note: _strdate is deprecated; consider using _strdate_s instead  
}  
```  
  
```Output  
OS date: 04/25/03  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [asctime —, _wasctime —](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime —, _ctime32 —, _ctime64 —, _wctime — _wctime32 —, _wctime64 —](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime —, _gmtime32 —, _gmtime64 —](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [czas lokalny, _localtime32 —, _localtime64 —](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [mktime —, _mktime32 —, _mktime64 —](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [czas, _time32 —, _time64 —](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset —](../../c-runtime-library/reference/tzset.md)