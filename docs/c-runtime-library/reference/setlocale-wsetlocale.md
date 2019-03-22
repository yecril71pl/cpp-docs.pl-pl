---
title: setlocale, _wsetlocale
ms.date: 11/04/2016
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
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
ms.openlocfilehash: 618b3e58a52e89561439fe76bf1b30e3cbbce001
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356208"
---
# <a name="setlocale-wsetlocale"></a>setlocale, _wsetlocale

Ustawia lub pobiera ustawienia regionalne czasu wykonywania.

## <a name="syntax"></a>Składnia

```C
char *setlocale(
   int category,
   const char *locale
);
wchar_t *_wsetlocale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parametry

*category*<br/>
Kategoria, której dotyczą ustawienia regionalne.

*Ustawienia regionalne*<br/>
Specyfikator ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Jeśli jest to prawidłowy *ustawień regionalnych* i *kategorii* są podane, zwraca wskaźnik do ciągu skojarzonego z określonym *ustawień regionalnych* i *kategorii*. Jeśli *ustawień regionalnych* lub *kategorii* jest nieprawidłowe, zwraca pusty wskaźnik, a bieżące ustawienia regionalne programu nie są zmieniane.

Na przykład, wywołanie

```C
setlocale( LC_ALL, "en-US" );
```

ustawia wszystkie kategorie, zwracając tylko ciąg

```Output
en-US
```

Można skopiować ciąg zwracany przez **setlocale** Aby przywrócić tę część informacji o ustawieniach regionalnych programu. Magazyn lokalny globalny lub wątku jest używana dla ciągu zwracanego przez **setlocale**. Późniejsze wywołania **setlocale** zastępują ten ciąg, co unieważnia wskaźniki ciągu zwracane przez poprzednie wywołania.

## <a name="remarks"></a>Uwagi

Użyj **setlocale** funkcję, aby ustawić, zmienić lub sprawdzić niektóre lub wszystkie bieżące informacje o ustawieniach regionalnych programu określony przez *ustawień regionalnych* i *kategorii*. *Ustawienia regionalne* odwołuje się do tej lokalizacji (kraj/region i język), dla którego można dostosować niektóre aspekty programu. Niektóre kategorie zależne od ustawień regionalnych obejmują formatowanie dat i format wyświetlania wartości pieniężnych. Jeśli ustawisz *ustawień regionalnych* na domyślny ciąg języka, który ma wiele form obsługiwanych na komputerze, należy sprawdzić **setlocale** wartości zwracanej, aby zobaczyć, jaki język jest aktywna. Na przykład jeśli ustawisz *ustawień regionalnych* na "chiński", zwracana wartość może być "chiński uproszczony" lub "chiński tradycyjny".

**_wsetlocale** to wersja znaku dwubajtowego **setlocale**; *ustawień regionalnych* argument i wartość zwracana przez **_wsetlocale** są ciągami znaków dwubajtowych. **_wsetlocale** i **setlocale** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

*Kategorii* argument określa części informacji o ustawieniach regionalnych programu, których to dotyczy. Makra używane do *kategorii* i części programu, które wpływają, są następujące:

|*Kategoria* flagi|Dotyczy|
|-|-|
| **LC_ALL** | Wszystkie kategorie, wymienione poniżej. |
| **LC_COLLATE** | **Strcoll —**, **_stricoll —**, **wcscoll —**, **_wcsicoll —**, **strxfrm —**, **_ strncoll —**, **_strnicoll —**, **_wcsncoll —**, **_wcsnicoll —**, i **wcsxfrm —** funkcji. |
| **LC_CTYPE** | Funkcje obsługi znaków (z wyjątkiem **isdigit**, **isxdigit**, **mbstowcs**, i **mbtowc**, które są bez zmian). |
| **LC_MONETARY** | Informacje o formatowaniu walutowym zwracane przez **localeconv** funkcji. |
| **LC_NUMERIC** | Dziesiętny znak dla sformatowanych procedur danych wyjściowych (takich jak **printf**), dla procedur konwersji danych i dla niepieniężnych informacji formatowania zwracanych przez **localeconv**. Oprócz znaku dziesiętnego **LC_NUMERIC** ustawia separator tysięcy i sterujący grupowaniem zwracany przez ciąg [localeconv](localeconv.md). |
| **LC_TIME** | **Strftime** i **wcsftime** funkcji. |

Ta funkcja sprawdza poprawność parametru kategorii. Jeśli parametr kategorii nie jest jedną z wartości podanych w powyższej tabeli, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ustawia **errno** do **EINVAL** i zwraca **NULL**.

*Ustawień regionalnych* argument jest wskaźnikiem do ciągu, który określa ustawienia regionalne. Aby uzyskać informacje o formacie parametru *ustawień regionalnych* argumentów, zobacz [nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Jeśli *ustawień regionalnych* wskazuje na pusty ciąg, ustawienia regionalne są natywnym środowiskiem zdefiniowanych w implementacji. Wartość **C** określa minimalne środowisko odpowiadające ANSI dla translacji C. **C** ustawień regionalnych zakładają, że wszystkie **char** 1 bajt są typy danych i ich wartość jest zawsze mniejsza niż 256.

W momencie uruchamiania programu wykonywany jest odpowiednik następującej instrukcji:

`setlocale( LC_ALL, "C" );`

*Ustawień regionalnych* argument może przyjąć nazwy ustawień regionalnych, ciąg języka, ciąg języka i kraju/regionu, stronę kodową lub ciąg języka, kod kraju/regionu i stronę kodową. Zestaw dostępnych nazw ustawień regionalnych, języków, kodów krajów/regionów i stron kodowych zawiera wszystkie te opcje, które są obsługiwane przez API Windows NLS, z wyjątkiem stron kodowych, które wymagają więcej niż dwóch bajtów na znak, takich jak UTF-7 lub UTF-8. Jeśli podasz wartość strony kodowej UTF-7 lub UTF-8, **setlocale** zakończy się niepowodzeniem, zwracając **NULL**. Zestaw nazw ustawień regionalnych obsługiwanych przez **setlocale** są opisane w [nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Zestaw ciągów języka i kraju/regionu, obsługiwany przez **setlocale** są wymienione w [Language Strings](../../c-runtime-library/language-strings.md) i [ciągi Kraj/Region](../../c-runtime-library/country-region-strings.md). Firma Microsoft zaleca formę nazwy ustawień regionalnych ze względu na wydajność i łatwość konserwacji ciągów ustawień regionalnych, osadzonych w kodzie lub szeregowanych do pamięci. Zmiana ciągów nazw ustawień regionalnych przez aktualizację systemu operacyjnego jest mniej prawdopodobna niż zmiana formy nazwy języka i kraju/regionu.

Pusty wskaźnik, który jest przekazywany jako *ustawień regionalnych* argument nakazuje **setlocale** kwerendy zamiast ustawić środowisko międzynarodowe. Jeśli *ustawień regionalnych* argument jest wskaźnikiem typu null, bieżących ustawień regionalnych programu nie jest zmieniany. Zamiast tego **setlocale** zwraca wskaźnik do ciągu, który jest skojarzony z *kategorii* bieżących ustawień regionalnych dla wątku. Jeśli *kategorii* argument jest **LC_ALL**, funkcja zwraca ciąg, wskazujący bieżące ustawienie każdej kategorii, oddzielając je średnikami. Na przykład, sekwencja wywołań

```C
// Set all categories and return "en-US"
setlocale(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
setlocale(LC_MONETARY, "fr-FR");
printf("%s\n", setlocale(LC_ALL, NULL));
```

zwraca

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

który jest ciągiem, który jest skojarzony z **LC_ALL** kategorii.

Następujące przykłady odnoszą się do **LC_ALL** kategorii. Zamiast numeru strony kodowej można użyć jednego z ciągów „.OCP” lub „.ACP”, aby określić odpowiednio domyślną stronę kodową OEM użytkownika i domyślną stronę kodową ANSI użytkownika.

- `setlocale( LC_ALL, "" );`

   Ustawia ustawienia regionalne na domyślne, czyli domyślną stronę kodową ANSI użytkownika, uzyskaną z systemu operacyjnego.

- `setlocale( LC_ALL, ".OCP" );`

   Jawnie ustawia ustawienia regionalne na bieżącą stronę kodową OEM, uzyskaną od systemu operacyjnego.

- `setlocale( LC_ALL, ".ACP" );`

   Ustawia ustawienia regionalne na bieżącą stronę kodową ANSI, uzyskaną od systemu operacyjnego.

- `setlocale( LC_ALL, "<localename>" );`

   Ustawia ustawienia regionalne nazwy ustawień regionalnych, który jest wskazywany przez  *\<localename >*.

- `setlocale( LC_ALL, "<language>_<country>" );`

   Ustawia ustawienia regionalne na język i kraj/region, wskazane przez  *\<języka >* i  *\<kraju >*, wraz z domyślną stroną kodową uzyskany z hosta System operacyjny.

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Ustawia ustawienia regionalne na język, kraj/region i stronę kodową wskazane przez  *\<języka >*,  *\<kraju >*, i  *\<code_page >* ciągów. Można użyć różnych kombinacji języka, kraju/regionu i strony kodowej. Na przykład, to wywołanie ustawia ustawienia regionalne na francuski-Kanada ze stroną kodową 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   To wywołanie ustawia ustawienia regionalne na francuski-Kanada z domyślną stroną kodową ANSI:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   To wywołanie ustawia ustawienia regionalne na francuski-Kanada z domyślną stroną kodową OEM:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Ustawia ustawienia regionalne na język, który jest wskazywany przez  *\<języka >* i używa domyślnego kraju/regionu dla określonego języka i ANSI użytkownika domyślnej strony kodowej dla kraju/regionu uzyskany z hosta System operacyjny. Na przykład, następujące wywołania **setlocale** są funkcjonalnie równoważne:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Zaleca się pierwszą formę ze względu na wydajność oraz łatwość konserwacji.

- `setlocale( LC_ALL, ".<code_page>" );`

   Ustawia stronę kodową na wartość wskazaną przez *< code_page >*, wraz z domyślnym krajem/regionem i językiem (zdefiniowanym przez system operacyjny hosta) dla określonej strony kodowej.

Kategoria musi być albo **LC_ALL** lub **LC_CTYPE** aby strony kodowej. Na przykład, jeśli domyślny kraj/region i język systemu operacyjnego hosta "United States" i "English", następujące dwa wywołania **setlocale** są funkcjonalnie równoważne:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Aby uzyskać więcej informacji, zobacz [setlocale](../../preprocessor/setlocale.md) dyrektywa pragmy w [C/C++ Preprocessor Reference](../../preprocessor/c-cpp-preprocessor-reference.md).

Funkcja [_configthreadlocale](configthreadlocale.md) służy do sterowania czy **setlocale** wpływa na ustawienia regionalne wszystkich wątków w programie, czy tylko wątku wywołującego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setlocale**|\<locale.h>|
|**_wsetlocale**|\<Locale.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
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

## <a name="see-also"></a>Zobacz także

[Nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
