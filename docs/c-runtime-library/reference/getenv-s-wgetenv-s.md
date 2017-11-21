---
title: "getenv_s —, _wgetenv_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getenv_s
- _wgetenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- getenv_s
- _tgetenv_s
- _wgetenv_s
dev_langs: C++
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
caps.latest.revision: "42"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d391e24a5b14bd015b43f88b2a687011d84d35fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="getenvs-wgetenvs"></a>getenv_s, _wgetenv_s
Pobiera wartość po bieżącym środowisku. Te wersje programu [getenv —, _wgetenv —](../../c-runtime-library/reference/getenv-wgetenv.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t getenv_s(   
   size_t *pReturnValue,  
   char* buffer,  
   size_t numberOfElements,  
   const char *varname   
);  
errno_t _wgetenv_s(   
   size_t *pReturnValue,  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *varname   
);  
template <size_t size>  
errno_t getenv_s(   
   size_t *pReturnValue,  
   char (&buffer)[size],  
   const char *varname   
); // C++ only  
template <size_t size>  
errno_t _wgetenv_s(   
   size_t *pReturnValue,  
   wchar_t (&buffer)[size],  
   const wchar_t *varname   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `pReturnValue`  
 Rozmiar buforu, które są wymagane, lub 0, jeśli nie można odnaleźć zmiennej.  
  
 `buffer`  
 Bufor do przechowywania wartości zmiennej środowiskowej.  
  
 `numberOfElements`  
 Rozmiar `buffer`.  
  
 `varname`  
 Nazwa zmiennej środowiskowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia; w przeciwnym razie błąd kodu w przypadku awarii.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`pReturnValue`|`buffer`|`numberOfElements`|`varname`|Wartość zwracana|  
|--------------------|--------------|------------------------|---------------|------------------|  
|`NULL`|wszystkie|wszystkie|wszystkie|`EINVAL`|  
|wszystkie|`NULL`|>0|wszystkie|`EINVAL`|  
|wszystkie|wszystkie|wszystkie|`NULL`|`EINVAL`|  
  
 Jeden z następujących warunków błędów wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, Ustaw funkcje `errno` do `EINVAL` i zwracać `EINVAL`.  
  
 Ponadto jeśli bufor jest za mały, funkcje zwracają `ERANGE`. Nie wywołuj one program obsługi nieprawidłowych parametrów. Zapisują limit wymagany rozmiar buforu w `pReturnValue`i tym samym Włącz programy do wywołania funkcji ponownie, podając większy bufor.  
  
## <a name="remarks"></a>Uwagi  
 `getenv_s` Funkcja wyszukuje listę zmiennych środowiskowych dla `varname`. `getenv_s`nie jest uwzględniana wielkość liter w systemie operacyjnym Windows. `getenv_s`i `_putenv_s` użyj kopii w środowisku, które jest wskazywana przez zmiennej globalnej `_environ` można uzyskiwać dostęp do środowiska. `getenv_s`działa tylko dla struktury danych, które są dostępne do biblioteki czasu wykonywania, a nie na środowisko "segment", który jest tworzone przez system operacyjny dla procesu. W związku z tym programy używające `envp` argument [głównego](../../cpp/main-program-startup.md) lub [wmain](../../cpp/main-program-startup.md) może pobrać nieprawidłowe informacje.  
  
 `_wgetenv_s`jest to wersja znaków dwubajtowych `getenv_s`; argumentów i wartości `_wgetenv_s` są ciągami znaków dwubajtowych. `_wenviron` — Zmienna globalna jest wersja znaków dwubajtowych `_environ`.  
  
 W programie MBCS (na przykład w programie SBCS ASCII) `_wenviron` jest początkowo `NULL` ponieważ środowisko składa się z ciągów znaków wielobajtowych. Następnie w pierwszym wywołaniu `_wputenv`, lub w pierwszym wywołaniu `_wgetenv_s`, jeśli środowisko (MBCS) już istnieje, odpowiednie środowisko ciąg znaków dwubajtowych jest tworzony i następnie jest wskazywana przez `_wenviron`.  
  
 Podobnie w standardzie Unicode `(_wmain`) program, `_environ` jest początkowo `NULL` ponieważ środowisko składa się z ciągów znaków dwubajtowych. Następnie w pierwszym wywołaniu `_putenv`, lub w pierwszym wywołaniu `getenv_s` po środowiska (Unicode) już istnieje, odpowiednie środowisko MBCS tworzy, a następnie jest wskazywana przez `_environ`.  
  
 Gdy w programie jednocześnie istnieją dwie kopie środowiska (MBCS i Unicode), system czasu wykonywania muszą zachować obydwie kopie i powoduje wolniejsze czasu wykonywania. Na przykład podczas wywoływania `_putenv`, wywołanie `_wputenv` również jest wykonywane automatycznie, aby odpowiadać ciągów dwóch środowiska.  
  
> [!CAUTION]
>  W rzadkich przypadkach gdy system czasu wykonywania jest obsługę zarówno wersji Unicode, jak i wielobajtowe wersji środowiska, środowisko dwie wersje mogą nie odpowiadać dokładnie. Dzieje się tak, ponieważ, mimo że dowolny unikatowy ciąg znaków wielobajtowych mapuje z unikatowym ciągiem Unicode, mapowanie unikatowy ciąg Unicode na ciąg znaków wielobajtowych nie jest zawsze unikatowa. Aby uzyskać więcej informacji, zobacz [_environ —, _wenviron —](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  `_putenv_s` i `_getenv_s` rodzin funkcje nie są wątkowo. `_getenv_s`można zwracać wskaźnik ciągu podczas `_putenv_s` modyfikuje ciągu i spowodować losowe awarie. Upewnij się, że wywołania te funkcje są zsynchronizowane.  
  
 W języku C++ użycia tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu i tym samym, eliminując konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tgetenv_s`|`getenv_s`|`getenv_s`|`_wgetenv_s`|  
  
 Aby sprawdzić lub zmienić wartość `TZ` użycie zmiennej, środowisko `getenv_s`, `_putenv`, i `_tzset`, co jest wymagane. Aby uzyskać więcej informacji na temat `TZ`, zobacz [_tzset —](../../c-runtime-library/reference/tzset.md) i [_daylight, _dstbias, _timezone i _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`getenv_s`|\<stdlib.h >|  
|`_wgetenv_s`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_getenv_s.c  
// This program uses getenv_s to retrieve  
// the LIB environment variable and then uses  
// _putenv to change it to a new value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* libvar;  
   size_t requiredSize;  
  
   getenv_s( &requiredSize, NULL, 0, "LIB");  
   if (requiredSize == 0)  
   {  
      printf("LIB doesn't exist!\n");  
      exit(1);  
   }  
  
   libvar = (char*) malloc(requiredSize * sizeof(char));  
   if (!libvar)  
   {  
      printf("Failed to allocate memory!\n");  
      exit(1);  
   }  
  
   // Get the value of the LIB environment variable.  
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );  
  
   printf( "Original LIB variable is: %s\n", libvar );  
  
   // Attempt to change path. Note that this only affects  
   // the environment variable of the current process. The command  
   // processor's environment is not changed.  
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );  
  
   getenv_s( &requiredSize, NULL, 0, "LIB");  
  
   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));  
   if (!libvar)  
   {  
      printf("Failed to allocate memory!\n");  
      exit(1);  
   }  
  
   // Get the new value of the LIB environment variable.   
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );  
  
   printf( "New LIB variable is: %s\n", libvar );  
  
   free(libvar);  
}  
```  
  
```Output  
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib  
New LIB variable is: c:\mylib;c:\yourlib  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [Stałe środowiska](../../c-runtime-library/environmental-constants.md)   
 [_putenv —, _wputenv —](../../c-runtime-library/reference/putenv-wputenv.md)   
 [_dupenv_s —, _wdupenv_s —](../../c-runtime-library/reference/dupenv-s-wdupenv-s.md)