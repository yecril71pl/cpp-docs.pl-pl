---
title: "asctime_s —, _wasctime_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wasctime_s
- asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
dev_langs: C++
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30a48101ea2db80f7c8a37434c1fd73c9c535286
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="asctimes-wasctimes"></a>asctime_s, _wasctime_s
Konwertuj `tm` czasu struktury do ciągu znaków. Te funkcje są wersje [asctime —, _wasctime —](../../c-runtime-library/reference/asctime-wasctime.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t asctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const struct tm *_tm   
);  
errno_t _wasctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements  
   const struct tm *_tm   
);  
template <size_t size>  
errno_t asctime_s(   
   char (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
template <size_t size>  
errno_t _wasctime_s(   
   wchar_t (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 [out] Wskaźnik do buforu do przechowywania wyników ciąg znaków. Ta funkcja zakłada wskaźnik do lokalizacji w pamięci prawidłowy o rozmiarze określonym przez `numberOfElements`.  
  
 `numberOfElements`  
 [in] Rozmiar buforu używany do przechowywania wyniku.  
  
 `_tm`  
 [in] Godzina i Data struktury. Ta funkcja przyjmuje wskaźnik do prawidłowej `struct tm` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie. W przypadku awarii, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, wartość zwracana jest kod błędu. Kody błędów są definiowane w numer błędu. H. Aby uzyskać więcej informacji, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md). Kody błędów rzeczywiste zwrócony dla każdego warunku błędu przedstawiono w poniższej tabeli.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`buffer`|`numberOfElements`|`tm`|Zwraca|Wartość w`buffer`|  
|--------------|------------------------|----------|------------|-----------------------|  
|`NULL`|wszystkie|wszystkie|`EINVAL`|Nie zmodyfikowano|  
|nie `NULL` (wskazuje prawidłowy pamięci)|0|wszystkie|`EINVAL`|Nie zmodyfikowano|  
|nie`NULL`|0 < < 26 rozmiaru|wszystkie|`EINVAL`|Pusty ciąg|  
|nie`NULL`|>= 26|`NULL`|`EINVAL`|Pusty ciąg|  
|nie`NULL`|>= 26|Struktura nieprawidłową wartość czas lub wartości spoza zakresu dla składników czasu|`EINVAL`|Pusty ciąg|  
  
> [!NOTE]
>  Błąd warunki dotyczące `wasctime_s` są podobne do `asctime_s` z wyjątkiem, że limit rozmiaru jest mierzony w wyrazy.  
  
## <a name="remarks"></a>Uwagi  
 `asctime` Funkcja konwertuje godzinę przechowywane jako struktura na ciąg znaków. `_tm` Wartość zazwyczaj jest uzyskiwana w wyniku wywołania `gmtime` lub `localtime`. Funkcjami może służyć do wypełnienia `tm` struktury, zgodnie z definicją w czasie. H.  
  
|element członkowski timeptr|Wartość|  
|--------------------|-----------|  
|`tm_hour`|Godziny od północy (0-23)|  
|`tm_isdst`|Dodatnie, jeśli czas letni są włączone; 0, jeśli czas letni nie jest włączone; ujemna, jeśli stan okresu obowiązywania czasu letniego jest nieznany. Biblioteki wykonawcze języka C zakłada Stanów Zjednoczonych zasady wykonywania obliczeń czasu (DST).|  
|`tm_mday`|Dzień miesiąca (1-31)|  
|`tm_min`|Minut po godziny (0-59)|  
|`tm_mon`|Miesiąc (0-11; Stycznia = 0)|  
|`tm_sec`|Sekund po minucie (0-59)|  
|`tm_wday`|Dzień tygodnia (0 – 6; Niedziela = 0)|  
|`tm_yday`|Dzień roku (0-365; 1 stycznia = 0)|  
|`tm_year`|Roku (bieżącego roku minus 1900)|  
  
 Ciąg przekonwertowany znaków jest również dostosowywana zgodnie z ustawieniami strefy czasu lokalnego. Zobacz [czas, _time32 —, _time64 —](../../c-runtime-library/reference/time-time32-time64.md), [_ftime —, _ftime32 —, _ftime64 —](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), i [localtime_s —, _localtime32_s —, _localtime64_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) funkcje informacji o konfigurowaniu czas lokalny i [_tzset —](../../c-runtime-library/reference/tzset.md) funkcja dla informacji na temat definiowania strefy czasowej środowiska i zmiennych globalnych.  
  
 Wynik ciąg utworzony przez `asctime_s` zawiera dokładnie 26 znaków i ma postać `Wed Jan 02 02:03:55 1980\n\0`. 24-godzinnym jest używany. Wszystkie pola mają stałej szerokości. Znaku nowego wiersza i znaku null zajmują ostatnich dwóch pozycji w ciągu. Wartość przekazany jako drugi parametr należy co najmniej tym duży. Jeśli jest mniejsza ilość kodu błędu, `EINVAL`, zostaną zwrócone.  
  
 `_wasctime_s`jest to wersja znaków dwubajtowych `asctime_s`. `_wasctime_s`i `asctime_s` zachowują się tak samo w przeciwnym razie wartość.  
  
### <a name="generic-text-routine-mapping"></a>Rutynowe mapowanie — zwykły tekst  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tasctime_s`|`asctime_s`|`asctime_s`|`_wasctime_s`|  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie, co eliminuje konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`asctime_s`|\<Time.h >|  
|`_wasctime_s`|\<Time.h > lub \<wchar.h >|  
  
## <a name="security"></a>Zabezpieczenia  
 Jeśli nie jest wskaźnika buforu `NULL` i wskaźnik nie wskazuje prawidłowego buforu, funkcja spowoduje zastąpienie, niezależnie od znajduje się w tej lokalizacji. Ponadto może to spowodować naruszenie zasad dostępu.  
  
 A [przepełnienie buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795) może wystąpić, jeśli przekazany argument rozmiar jest większy niż rzeczywisty rozmiar buforu.  
  
## <a name="example"></a>Przykład  
 Ten program umieszcza czasu systemowego w długich liczb całkowitych `aclock`, tłumaczy go do struktury `newtime` i konwertuje ją do postaci ciągu dla danych wyjściowych, używając `asctime_s` funkcji.  
  
```  
// crt_asctime_s.c  
#include <time.h>  
#include <stdio.h>  
  
struct tm newtime;  
__time32_t aclock;  
  
int main( void )  
{  
   char buffer[32];  
   errno_t errNum;  
   _time32( &aclock );   // Get time in seconds.  
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.  
  
   // Print local time as a string.  
  
   errNum = asctime_s(buffer, 32, &newtime);  
   if (errNum)  
   {  
       printf("Error code: %d", (int)errNum);  
       return 1;  
   }  
   printf( "Current date and time: %s", buffer );  
   return 0;  
}  
```  
  
```Output  
Current date and time: Wed May 14 15:30:17 2003  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [ctime_s —, _ctime32_s —, _ctime64_s —, _wctime_s — _wctime32_s —, _wctime64_s —](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [_ftime —, _ftime32 —, _ftime64 —](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s —, _gmtime32_s —, _gmtime64_s —](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s —, _localtime32_s —, _localtime64_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [czas, _time32 —, _time64 —](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)