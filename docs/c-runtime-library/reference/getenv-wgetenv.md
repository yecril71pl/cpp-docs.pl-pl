---
title: "getenv —, _wgetenv — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- getenv
- _wgetenv
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
- _wgetenv
- getenv
- _tgetenv
dev_langs:
- C++
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99d9104959dccf4a6879c4e929a1cdc281317171
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="getenv-wgetenv"></a>getenv, _wgetenv
Pobiera wartość po bieżącym środowisku. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [getenv_s —, _wgetenv_s —](../../c-runtime-library/reference/getenv-s-wgetenv-s.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *getenv(   
   const char *varname   
);  
wchar_t *_wgetenv(   
   const wchar_t *varname   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `varname`  
 Nazwa zmiennej środowiskowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do środowiska tabeli wpis zawierający `varname`. Nie jest bezpieczne zmodyfikować wartość zmiennej środowiskowej przy użyciu wskaźnika zwrócony. Użyj `_putenv` funkcji, aby zmodyfikować wartość zmiennej środowiskowej. Wartość zwracana jest `NULL` Jeśli `varname` nie można odnaleźć tabeli środowiska.  
  
## <a name="remarks"></a>Uwagi  
 `getenv` Funkcja wyszukuje listę zmiennych środowiskowych dla `varname`. `getenv` nie jest uwzględniana wielkość liter w systemie operacyjnym Windows. `getenv` i `_putenv` użyj kopii środowiska wskazywanej przez zmienną globalne `_environ` można uzyskiwać dostęp do środowiska. `getenv` działa tylko na dostęp do biblioteki wykonawczej struktury danych, a nie na środowisko "segmentu" tworzone przez system operacyjny dla procesu. W związku z tym programy używające `envp` argument [głównego](../../cpp/main-program-startup.md) lub [wmain](../../cpp/main-program-startup.md) może pobrać nieprawidłowe informacje.  
  
 Jeśli `varname` jest `NULL`, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `NULL`.  
  
 `_wgetenv` jest to wersja znaków dwubajtowych `getenv`; argumentów i wartości `_wgetenv` są ciągami znaków dwubajtowych. `_wenviron` — Zmienna globalna jest wersja znaków dwubajtowych `_environ`.  
  
 W programie MBCS (na przykład w programie SBCS ASCII) `_wenviron` jest początkowo `NULL` ponieważ środowisko składa się z ciągów znaków wielobajtowych. Następnie w pierwszym wywołaniu `_wputenv`, lub w pierwszym wywołaniu `_wgetenv` po środowisko (MBCS) już istnieje, odpowiednie środowisko ciąg znaków dwubajtowych tworzy, a następnie jest wskazywana przez `_wenviron`.  
  
 Podobnie w standardzie Unicode (`_wmain`) program, `_environ` jest początkowo `NULL` ponieważ środowisko składa się z ciągów znaków dwubajtowych. Następnie w pierwszym wywołaniu `_putenv`, lub w pierwszym wywołaniu `getenv` po środowiska (Unicode) już istnieje, odpowiednie środowisko MBCS tworzy, a następnie jest wskazywana przez `_environ`.  
  
 Gdy w programie jednocześnie istnieją dwie kopie środowiska (MBCS i Unicode), środowiska wykonawczego systemu muszą zachować obydwie kopie spowodować wolniejszy czasu wykonywania. Na przykład, gdy jest wywoływana `_putenv`, wywołanie `_wputenv` również jest wykonywane automatycznie, tak aby odpowiadały ciągów dwóch środowiska.  
  
> [!CAUTION]
>  W rzadkich przypadkach gdy system czasu wykonywania jest obsługę zarówno wersji Unicode, jak i wielobajtowe wersji środowiska, tych wersji środowiska dwóch mogą nie odpowiadać dokładnie. To dlatego, chociaż dowolny unikatowy ciąg znaków wielobajtowych mapuje z unikatowym ciągiem Unicode, mapowanie unikatowy ciąg Unicode na ciąg znaków wielobajtowych nie jest zawsze unikatowa. Aby uzyskać więcej informacji, zobacz [_environ —, _wenviron —](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  `_putenv` i `_getenv` rodzin funkcje nie są wątkowo. `_getenv` można zwracać wskaźnik ciągu podczas `_putenv` modyfikuje ciągu znaków powoduje losowe awarie. Upewnij się, że wywołania te funkcje są zsynchronizowane.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tgetenv`|`getenv`|`getenv`|`_wgetenv`|  
  
 Aby sprawdzić lub zmienić wartość `TZ` użycie zmiennej, środowisko `getenv`, `_putenv` i `_tzset` odpowiednio do potrzeb. Aby uzyskać więcej informacji na temat `TZ`, zobacz [_tzset —](../../c-runtime-library/reference/tzset.md) i [_daylight, strefa czasowa i _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`getenv`|\<stdlib.h>|  
|`_wgetenv`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_getenv.c  
// compile with: /W3  
// This program uses getenv to retrieve  
// the LIB environment variable and then uses  
// _putenv to change it to a new value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *libvar;  
  
   // Get the value of the LIB environment variable.  
   libvar = getenv( "LIB" ); // C4996  
   // Note: getenv is deprecated; consider using getenv_s instead  
  
   if( libvar != NULL )  
      printf( "Original LIB variable is: %s\n", libvar );  
  
   // Attempt to change path. Note that this only affects the environment  
   // variable of the current process. The command processor's  
   // environment is not changed.  
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996  
   // Note: _putenv is deprecated; consider using putenv_s instead  
  
   // Get new value.  
   libvar = getenv( "LIB" ); // C4996  
  
   if( libvar != NULL )  
      printf( "New LIB variable is: %s\n", libvar );  
}  
```  
  
```Output  
Original LIB variable is: C:\progra~1\devstu~1\vc\lib  
New LIB variable is: c:\mylib;c:\yourlib  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [_putenv —, _wputenv —](../../c-runtime-library/reference/putenv-wputenv.md)   
 [Stałe środowiska](../../c-runtime-library/environmental-constants.md)