---
title: "setLocale, _wsetlocale — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wsetlocale
- setlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsetlocale
- _tsetlocale
- setlocale
dev_langs: C++
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0610dff5366f72010de965b7b9df0cd4e02c1e5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setlocale-wsetlocale"></a>setlocale, _wsetlocale
Ustawia lub pobiera ustawienia regionalne czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
char *setlocale(  
   int category,  
   const char *locale   
);  
wchar_t *_wsetlocale(  
   int category,  
   const wchar_t *locale   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `category`  
 Kategoria, której dotyczą ustawienia regionalne.  
  
 `locale`  
 Specyfikator ustawień regionalnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli jest to prawidłowy `locale` i `category` podano, zwraca wskaźnik do ciągu skojarzonego z określonym `locale` i `category`. Jeśli `locale` lub `category` jest nieprawidłowa, zwraca wskaźnik null i bieżące ustawienia regionalne programu nie są zmieniane.  
  
 Na przykład, wywołanie  
  
 `setlocale( LC_ALL, "en-US" );`  
  
 ustawia wszystkie kategorie, zwracając tylko ciąg  
  
 `en-US`  
  
 Możesz skopiować długość ciągu zwróconego przez `setlocale` Aby przywrócić tę część informacji o ustawieniach regionalnych programu. Magazyn lokalny globalny lub wątku jest używana do ciągu zwróconego przez `setlocale`. Później wywołań `setlocale` zastąpić ciąg, co spowoduje unieważnienie wskaźniki ciąg zwrócony przez wcześniejszą wywołania.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `setlocale` funkcji, aby ustawić, zmienianie lub zapytania niektórych lub wszystkich aktualnych informacji ustawień regionalnych program określony przez `locale` i `category`. `locale`odnosi się do tej lokalizacji (kraj/region i język), dla którego można dostosować niektórych aspektów programu. Niektóre kategorie zależne od ustawień regionalnych obejmują formatowanie dat i format wyświetlania wartości pieniężnych. Jeśli ustawisz `locale` do domyślnego ciągu dla języka, który ma wiele formularzy obsługiwane na komputerze, należy sprawdzić `setlocale` zwrócić wartość języka, w którym znajduje się w celu. Na przykład jeśli ustawisz `locale` na "chiński" zwracana wartość może być "chiński uproszczony" lub "chiński tradycyjny".  
  
 `_wsetlocale`jest to wersja znaków dwubajtowych `setlocale`; `locale` argumentów i wartości `_wsetlocale` są ciągami znaków dwubajtowych. `_wsetlocale`i `setlocale` zachowują się tak samo w przeciwnym razie wartość.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsetlocale`|`setlocale`|`setlocale`|`_wsetlocale`|  
  
 `category` Argument określa części informacji o ustawieniach regionalnych programu, których dotyczy problem. Makra używane dla `category` i części programu wpływają na są następujące:  
  
 `LC_ALL`  
 Wszystkie kategorie z poniższej listy.  
  
 `LC_COLLATE`  
 `strcoll`, `_stricoll`, `wcscoll`, `_wcsicoll`, `strxfrm`, `_strncoll`, `_strnicoll`, `_wcsncoll`, `_wcsnicoll`, I `wcsxfrm` funkcji.  
  
 `LC_CTYPE`  
 Funkcje obsługi znaków (z wyjątkiem `isdigit`, `isxdigit`, `mbstowcs`, i `mbtowc`, którego dotyczy to).  
  
 `LC_MONETARY`  
 Formatowanie walutowa informacje zwracane przez `localeconv` funkcji.  
  
 `LC_NUMERIC`  
 Dziesiętnego znak dla procedury sformatowane dane wyjściowe (takich jak `printf`) dla procedury konwersji danych i -pieniężnego formatowania informacje zwracane przez `localeconv`. Oprócz znaku dziesiętnego `LC_NUMERIC` również ciągu zwróconego przez kontrolę separator tysięcy zestawów i grupowanie [localeconv —](../../c-runtime-library/reference/localeconv.md).  
  
 `LC_TIME`  
 `strftime` i `wcsftime` funkcji.  
  
 Ta funkcja sprawdza poprawność parametru kategorii. Jeśli parametr kategorii nie jest jedną z wartości podane w poprzedniej tabeli, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, funkcja ustawia `errno` do `EINVAL` i zwraca `NULL`.  
  
 `locale` Argument jest wskaźnikiem do ciągu, który określa ustawienia regionalne. Informacje o formacie `locale` argumentu, zobacz [nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Jeśli `locale` punktów na pusty ciąg, ustawienia regionalne są zdefiniowane w implementacji środowiska macierzystego. Wartość `C` określa minimalne środowisko zgodnych ANSI C tłumaczenia. `C` Ustawień regionalnych przy założeniu, że wszystkie `char` typy danych są 1 bajt i ich wartość jest zawsze mniej niż 256.  
  
 W momencie uruchamiania programu wykonywany jest odpowiednik następującej instrukcji:  
  
 `setlocale( LC_ALL, "C" );`  
  
 `locale` Argument może zająć Nazwa ustawień regionalnych, ciąg języka ciąg języka i kod kraju/regionu, stronę kodową lub ciąg języka, kod kraju/regionu i strony kodowej. Zestaw dostępnych nazw ustawień regionalnych, języków, kodów krajów/regionów i stron kodowych zawiera wszystkie te opcje, które są obsługiwane przez API Windows NLS, z wyjątkiem stron kodowych, które wymagają więcej niż dwóch bajtów na znak, takich jak UTF-7 lub UTF-8. Jeśli podasz strony kodowej, UTF-7 lub UTF-8, `setlocale` zakończy się niepowodzeniem, zwracając wartość NULL. Zestaw nazw ustawień regionalnych obsługiwane przez `setlocale` opisanym w [nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Ciągi kraj/region i język obsługiwany przez zestaw `setlocale` są wymienione w [ciągi języka](../../c-runtime-library/language-strings.md) i [ciągi Kraj/Region](../../c-runtime-library/country-region-strings.md). Firma Microsoft zaleca formę nazwy ustawień regionalnych ze względu na wydajność i łatwość konserwacji ciągów ustawień regionalnych, osadzonych w kodzie lub szeregowanych do pamięci. Zmiana ciągów nazw ustawień regionalnych przez aktualizację systemu operacyjnego jest mniej prawdopodobna niż zmiana formy nazwy języka i kraju/regionu.  
  
 Pustego wskaźnika, który jest przekazywany jako `locale` argument nakazuje `setlocale` zbadać zamiast można ustawić międzynarodowe środowiska. Jeśli `locale` argument jest pusty wskaźnik, bieżących ustawień regionalnych programu nie zostanie zmieniona. Zamiast tego `setlocale` zwraca wskaźnik na ciąg, z którym skojarzony jest `category` o bieżące ustawienia regionalne wątku. Jeśli `category` argument jest `LC_ALL`, funkcja zwraca ciąg, który wskazuje bieżące ustawienie każdej kategorii, oddzielając je średnikami. Na przykład, sekwencja wywołań  
  
 `// Set all categories and return "en-US"`  
  
 `setlocale(LC_ALL, "en-US");`  
  
 `// Set only the LC_MONETARY category and return "fr-FR"`  
  
 `setlocale(LC_MONETARY, "fr-FR");`  
  
 `printf("%s\n", setlocale(LC_ALL, NULL));`  
  
 zwraca  
  
 `LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US`  
  
 czyli ciąg, z którym skojarzony jest `LC_ALL` kategorii.  
  
 Poniższe przykłady dotyczą `LC_ALL` kategorii. Zamiast numeru strony kodowej można użyć jednego z ciągów „.OCP” lub „.ACP”, aby określić odpowiednio domyślną stronę kodową OEM użytkownika i domyślną stronę kodową ANSI użytkownika.  
  
 `setlocale( LC_ALL, "" );`  
 Ustawia ustawienia regionalne na domyślne, czyli domyślną stronę kodową ANSI użytkownika, uzyskaną z systemu operacyjnego.  
  
 `setlocale( LC_ALL, ".OCP" );`  
 Jawnie ustawia ustawienia regionalne na bieżącą stronę kodową OEM, uzyskaną od systemu operacyjnego.  
  
 `setlocale( LC_ALL, ".ACP" );`  
 Ustawia ustawienia regionalne na bieżącą stronę kodową ANSI, uzyskaną od systemu operacyjnego.  
  
 `setlocale( LC_ALL, "<localename>" );`  
 Ustawia ustawienia regionalne Nazwa ustawień regionalnych, które jest określane przez  *\<localename >*.  
  
 `setlocale( LC_ALL, "<language>_<country>" );`  
 Ustawia ustawień regionalnych na język i kraj/region wskazywanym przez  *\<języka >* i  *\<kraju >*, wraz z domyślną stronę kodową uzyskany z hosta System operacyjny.  
  
 `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`  
 Ustawia wskazuje ustawienia regionalne do języka, kraju/regionu i strona kodowa  *\<języka >*,  *\<kraju >*, i *< code_page >* ciągów. Można użyć różnych kombinacji języka, kraju/regionu i strony kodowej. Na przykład, to wywołanie ustawia ustawienia regionalne na francuski-Kanada ze stroną kodową 1252:  
  
 `setlocale( LC_ALL, "French_Canada.1252" );`  
  
 To wywołanie ustawia ustawienia regionalne na francuski-Kanada z domyślną stroną kodową ANSI:  
  
 `setlocale( LC_ALL, "French_Canada.ACP" );`  
  
 To wywołanie ustawia ustawienia regionalne na francuski-Kanada z domyślną stroną kodową OEM:  
  
 `setlocale( LC_ALL, "French_Canada.OCP" );`  
  
 `setlocale( LC_ALL, "<language>" );`  
 Ustawia ustawień regionalnych na język, w którym jest określane przez  *\<języka >*i używa domyślnego kraju/regionu, dla określonego języka i ANSI użytkownika domyślna strona kodowa w danym kraju/regionie uzyskany z hosta System operacyjny. Na przykład następujące wywołań `setlocale` działają tak samo:  
  
 `setlocale( LC_ALL, "en-US" );`  
  
 `setlocale( LC_ALL, "English" );`  
  
 `setlocale( LC_ALL, "English_United States.1252" );`  
  
 Zaleca się pierwszą formę ze względu na wydajność oraz łatwość konserwacji.  
  
 `setlocale( LC_ALL, ".<code_page>" );`  
 Ustawia wartość wskazywana przez stronę kodową *< code_page >*, jak również domyślny kraj/region i język (zgodnie z definicją według systemu operacyjnego hosta) dla określonej strony kodowej.  
  
 Kategoria musi być równa albo `LC_ALL` lub `LC_CTYPE` dokonanie zmiany strony kodowej. Na przykład jeśli domyślny kraj/region i język systemu operacyjnego hosta "Stanów Zjednoczonych" i "Angielski", dwa wywołań `setlocale` działają tak samo:  
  
 `setlocale( LC_ALL, ".1252" );`  
  
 `setlocale( LC_ALL, "English_United States.1252");`  
  
 Aby uzyskać więcej informacji, zobacz [setlocale](../../preprocessor/setlocale.md) dyrektywa pragma w [odwołania preprocesora języka C/C++](../../preprocessor/c-cpp-preprocessor-reference.md).  
  
 Funkcja [_configthreadlocale —](../../c-runtime-library/reference/configthreadlocale.md) służy do sterowania czy `setlocale` wpływa na ustawieniach regionalnych wszystkie wątki w programie lub tylko ustawienia regionalne wątku.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`setlocale`|\<Locale.h >|  
|`_wsetlocale`|\<Locale.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_setlocale.c  
//   
// This program demonstrates the use of setlocale when  
// using two independent threads.  
//  
  
#include <locale.h>  
#include <process.h>  
#include <windows.h>  
#include <stdio.h>  
#include <time.h>  
  
#define BUFF_SIZE 100  
  
// Retrieve the date in the current  
// locale's format.  
int get_date(unsigned char* str)  
{  
    __time64_t ltime;  
    struct tm  thetime;  
  
    // Retrieve the current time  
    _time64(&ltime);  
    _gmtime64_s(&thetime, &ltime);  
  
    // Format the current time structure into a string  
    // "%#x" is the long date representation in the  
    // current locale  
    if (!strftime((char *)str, BUFF_SIZE, "%#x",   
                  (const struct tm *)&thetime))  
    {  
        printf("strftime failed!\n");  
        return -1;  
    }  
    return 0;  
}  
  
// This thread sets its locale to the argument  
// and prints the date.  
uintptr_t __stdcall SecondThreadFunc( void* pArguments )  
{  
    unsigned char str[BUFF_SIZE];  
    char * locale = (char *)pArguments;  
  
    // Set the thread locale  
    printf("The thread locale is now set to %s.\n",  
           setlocale(LC_ALL, locale));  
  
    // Retrieve the date string from the helper function  
    if (get_date(str) == 0)  
    {  
        printf("The date in %s locale is: '%s'\n", locale, str);  
    }  
  
    _endthreadex( 0 );  
    return 0;  
}   
  
// The main thread sets the locale to English   
// and then spawns a second thread (above) and prints the date.  
int main()  
{   
    HANDLE          hThread;  
    unsigned        threadID;  
    unsigned char   str[BUFF_SIZE];  
  
    // Configure per-thread locale to cause all subsequently created   
    // threads to have their own locale.  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
  
    // Set the locale of the main thread to US English.  
    printf("The thread locale is now set to %s.\n",  
           setlocale(LC_ALL, "en-US"));  
  
    // Create the second thread with a German locale.  
    // Our thread function takes an argument of the locale to use.  
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,  
                                      "de-DE", 0, &threadID );  
  
    if (get_date(str) == 0)  
    {  
        // Retrieve the date string from the helper function  
        printf("The date in en-US locale is: '%s'\n\n", str);  
    }  
  
    // Wait for the created thread to finish.  
    WaitForSingleObject( hThread, INFINITE );  
  
    // Destroy the thread object.  
    CloseHandle( hThread );  
}  
```  
  
```Output  
The thread locale is now set to en-US.  
The time in en-US locale is: 'Wednesday, May 12, 2004'  
  
The thread locale is now set to de-DE.  
The time in de-DE locale is: 'Mittwoch, 12. Mai 2004'  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [_configthreadlocale —](../../c-runtime-library/reference/configthreadlocale.md)   
 [_create_locale, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [localeconv —](../../c-runtime-library/reference/localeconv.md)   
 [_mbclen —, mblen —, _mblen_l —](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [strlen —, wcslen —, _mbslen —, _mbslen_l — _mbstrlen —, _mbstrlen_l —](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)   
 [mbstowcs —, _mbstowcs_l —](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc —, _mbtowc_l —](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [_setmbcp —](../../c-runtime-library/reference/setmbcp.md)   
 [strcoll — funkcje](../../c-runtime-library/strcoll-functions.md)   
 [strftime —, wcsftime —, _strftime_l — _wcsftime_l —](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm —, wcsxfrm —, _strxfrm_l — _wcsxfrm_l —](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [wcstombs —, _wcstombs_l —](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)