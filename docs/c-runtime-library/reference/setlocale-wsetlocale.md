---
title: setlocale, _wsetlocale
description: Opisuje funkcje setlocale biblioteki środowiska uruchomieniowego języka Microsoft C (CRT _wsetlocale) i.
ms.date: 4/2/2020
api_name:
- _wsetlocale
- setlocale
- _o__wsetlocale
- _o_setlocale
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
no-loc:
- setlocale
- _wsetlocale
ms.openlocfilehash: 312fd8e9f794368d334ea353e2c92241d701ab0b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918853"
---
# <a name="setlocale-_wsetlocale"></a>setlocale, _wsetlocale

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

*kategorii*\
Kategoria, której dotyczą ustawienia regionalne.

*ustawienie*\
Specyfikator ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Jeśli podano prawidłowe *Ustawienia regionalne* i *Kategorie* , zwraca wskaźnik do ciągu skojarzonego z określonymi *ustawieniami regionalnymi* i *kategorią*. Jeśli *Ustawienia regionalne* lub *Kategorie* są nieprawidłowe, zwraca wskaźnik o wartości null, a bieżące ustawienia regionalne programu nie są zmieniane.

Na przykład, wywołanie

```C
setlocale( LC_ALL, "en-US" );
```

ustawia wszystkie kategorie, zwracając tylko ciąg

```Output
en-US
```

Można skopiować ciąg zwracany przez **setlocale** , aby przywrócić tę część informacji o ustawieniach regionalnych programu. Globalny lub lokalny magazyn wątków jest używany dla ciągu zwracanego przez **setlocale**. Późniejsze wywołania metody **setlocal** zastępują ciąg, który unieważnia wskaźniki ciągu zwracane przez wcześniejsze wywołania.

## <a name="remarks"></a>Uwagi

Funkcja **setlocals** służy do ustawiania, zmieniania lub wykonywania zapytań dotyczących niektórych lub wszystkich bieżących informacji o ustawieniach regionalnych programu określonych przez *Ustawienia regionalne* i *Kategorie*. *Ustawienia regionalne* odnoszą się do lokalizacji lokalnej (kraju/regionu i języka), dla którego można dostosować niektóre aspekty programu. Niektóre kategorie zależne od ustawień regionalnych obejmują formatowanie dat i format wyświetlania wartości pieniężnych. Jeśli ustawisz *Ustawienia regionalne* na domyślny ciąg dla języka, który ma wiele formularzy obsługiwanych na komputerze, sprawdź wartość zwracaną **setlocal** , aby zobaczyć, który język jest w działaniu. Jeśli na przykład ustawisz *Ustawienia regionalne* na "chiński", wartością zwracaną może być "chiński uproszczony" lub "chiński tradycyjny".

**_wsetlocale** to dwubajtowa wersja **setlocale**; argument *locale* i wartość zwracana **_wsetlocale** są ciągami znaków dwubajtowych. **_wsetlocale** i **setlocale** zachowują się identycznie w innym przypadku.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

Argument *kategorii* określa części informacji o ustawieniach regionalnych, których dotyczy ten program. Makra używane dla *kategorii* i części programu, których one dotyczą, są następujące:

|Flaga *kategorii*|Mową|
|-|-|
| **LC_ALL** | Wszystkie kategorie, jak wymieniono poniżej. |
| **LC_COLLATE** | Funkcje **strcoll —**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**i **wcsxfrm** . |
| **LC_CTYPE** | Funkcje obsługi znaków (z wyjątkiem **iscyfr**, **isxdigit**, **mbstowcs**i **mbtowc**, których nie dotyczy). |
| **LC_MONETARY** | Informacje o formatowaniu pieniężnym zwracane przez funkcję **localeconv** . |
| **LC_NUMERIC** | Znak dziesiętny dla sformatowanych procedur danych wyjściowych (takich jak **printf**), dla procedur konwersji danych i dla niepieniężnych informacji o formatowaniu zwracanych przez **localeconv**. Oprócz znaku dziesiętnego, **LC_NUMERIC** ustawia separator tysięcy i ciąg sterujący grupowania zwracanego przez [localeconv](localeconv.md). |
| **LC_TIME** | Funkcje **strftime** i **wcsftime** . |

Ta funkcja sprawdza poprawność parametru kategorii. Jeśli parametr kategorii nie jest jedną z wartości podanej w poprzedniej tabeli, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ustawia **errno** na **EINVAL** i zwraca **wartość null**.

Argument *locale* jest wskaźnikiem do ciągu, który określa ustawienia regionalne. Aby uzyskać informacje na temat formatu argumentu *ustawień regionalnych* , zobacz [nazwy ustawień regionalnych, Języki i ciągi kraj/region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Jeśli *Ustawienia regionalne* wskazują pusty ciąg, ustawienia regionalne to środowisko natywne zdefiniowane w implementacji. Wartość **C** określa minimalne środowisko zgodne ze standardem ANSI dla translacji C. Ustawienia regionalne **C** zakładają, że wszystkie typy danych **char** są 1 bajty, a ich wartość jest zawsze mniejsza niż 256.

W momencie uruchamiania programu wykonywany jest odpowiednik następującej instrukcji:

`setlocale( LC_ALL, "C" );`

Argument *locale* może przyjmować nazwę ustawień regionalnych, ciąg języka, ciąg języka i kod kraju/regionu, stronę kodową lub ciąg języka, kod kraju/regionu i stronę kodową. Zestaw dostępnych nazw ustawień regionalnych, języków, kodów krajów/regionów i stron kodowych zawiera wszystkie obsługiwane przez NLS API systemu Windows. Zestaw nazw ustawień regionalnych obsługiwanych przez **setlocale** jest opisany w temacie [nazwy regionalne, Języki i ciągi kraj/region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Zestaw ciągów języka i kraju/regionu obsługiwanych przez **setlocale** znajduje się w [ciągach języka](../../c-runtime-library/language-strings.md) i w [ciągach kraju/regionu](../../c-runtime-library/country-region-strings.md). Firma Microsoft zaleca formę nazwy ustawień regionalnych ze względu na wydajność i łatwość konserwacji ciągów ustawień regionalnych, osadzonych w kodzie lub szeregowanych do pamięci. Zmiana ciągów nazw ustawień regionalnych przez aktualizację systemu operacyjnego jest mniej prawdopodobna niż zmiana formy nazwy języka i kraju/regionu.

Wskaźnik o wartości null, który jest przesyłany jako argument *ustawień regionalnych* , mówi **setlocaling** to Query zamiast ustawiać środowisko międzynarodowe. Jeśli argument *locale* jest wskaźnikiem o wartości null, bieżące ustawienie regionalne programu nie zostanie zmienione. Zamiast tego, funkcja **setlocale** zwraca wskaźnik do ciągu, który jest skojarzony z *kategorią* bieżących ustawień regionalnych wątku. Jeśli argument *kategorii* jest **LC_ALL**, funkcja zwraca ciąg, który wskazuje bieżące ustawienie każdej kategorii, oddzielone średnikami. Na przykład, sekwencja wywołań

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

jest to ciąg, który jest skojarzony z kategorią **LC_ALL** .

Poniższe przykłady odnoszą się do kategorii **LC_ALL** . Jeden z ciągów ". OCP "i". AKP "można użyć zamiast numeru strony kodowej, aby określić użycie domyślnej strony kodowej OEM i domyślnej strony kodowej ANSI użytkownika dla tej nazwy ustawień regionalnych.

- `setlocale( LC_ALL, "" );`

   Ustawia ustawienia regionalne na domyślne, czyli domyślną stronę kodową ANSI użytkownika, uzyskaną z systemu operacyjnego. Nazwa ustawień regionalnych jest ustawiona na wartość zwróconą przez [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Strona kodowa jest ustawiona na wartość zwróconą przez [GetACP](/windows/win32/api/winnls/nf-winnls-getacp).

- `setlocale( LC_ALL, ".OCP" );`

   Ustawia ustawienia regionalne na bieżącą stronę kodową OEM uzyskaną od systemu operacyjnego. Nazwa ustawień regionalnych jest ustawiona na wartość zwróconą przez [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Na stronie kodowej jest ustawiona wartość [LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) domyślna nazwa ustawień regionalnych użytkownika [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, ".ACP" );`

   Ustawia ustawienia regionalne na bieżącą stronę kodową ANSI, uzyskaną od systemu operacyjnego. Nazwa ustawień regionalnych jest ustawiona na wartość zwróconą przez [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Na stronie kodowej jest ustawiona wartość [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) domyślna nazwa ustawień regionalnych użytkownika [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<localename>" );`

   Ustawia ustawienia regionalne na nazwę ustawień regionalnych, która jest wskazywana przez * \<LocalName>*. Strona kodowa jest ustawiona na wartość [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) dla określonej nazwy ustawień regionalnych przez [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>" );`

   Ustawia ustawienia regionalne dla języka i kraju/regionu wskazywanego przez * \<język>* i * \<>kraju *, wraz z domyślną stroną kodową uzyskaną z systemu operacyjnego hosta. Strona kodowa jest ustawiona na wartość [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) dla określonej nazwy ustawień regionalnych przez [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Ustawia ustawienia regionalne na język, kraj/region i stronę kodową wskazywaną przez * \<>języka *, * \<>kraju *i * \<code_page>* ciągi. Można użyć różnych kombinacji języka, kraju/regionu i strony kodowej. Na przykład, to wywołanie ustawia ustawienia regionalne na francuski-Kanada ze stroną kodową 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   To wywołanie ustawia ustawienia regionalne na francuski-Kanada z domyślną stroną kodową ANSI:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   To wywołanie ustawia ustawienia regionalne na francuski-Kanada z domyślną stroną kodową OEM:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Ustawia ustawienia regionalne na język, który jest wskazywany przez * \<język>*, i używa domyślnego kraju/regionu dla określonego języka i strony kodowej ANSI użytkownika dla tego kraju/regionu uzyskanych z systemu operacyjnego hosta. Na przykład następujące wywołania metody **setlocal** są równoważne funkcjonalnie:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Zaleca się pierwszą formę ze względu na wydajność oraz łatwość konserwacji.

- `setlocale( LC_ALL, ".<code_page>" );`

   Ustawia stronę kodową na wartość wskazywaną przez *<code_page>* oraz domyślny kraj/region i język (zgodnie z definicją w systemie operacyjnym hosta) dla określonej strony kodowej.

Kategoria musi mieć wartość **LC_ALL** lub **LC_CTYPE** , aby można było zmienić stronę kodową. Na przykład jeśli domyślny kraj/region i język systemu operacyjnego hosta to "Stany Zjednoczone" i "angielski", następujące dwa wywołania metody **setlocaling** są funkcjonalnie równoważne:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Aby uzyskać więcej informacji, zobacz Dyrektywa " [setlocales](../../preprocessor/setlocale.md) pragma" w [dokumentacji preprocesora C/C++](../../preprocessor/c-cpp-preprocessor-reference.md).

Funkcja [_configthreadlocale](configthreadlocale.md) służy do kontrolowania, czy **setlocal** ma wpływ na ustawienia regionalne wszystkich wątków w programie, czy tylko ustawienia regionalne wątku wywołującego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setlocale**|\<locale. h>|
|**_wsetlocale**|\<locale. h> \<lub WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Nazwy lokalne, Języki i ciągi kraj/region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)\
[Ustawienie](../../c-runtime-library/locale.md)\
[localeconv](localeconv.md)\
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[Funkcje strcoll —](../../c-runtime-library/strcoll-functions.md)\
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb, _wctomb_l](wctomb-wctomb-l.md)
