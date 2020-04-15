---
title: setlocale, _wsetlocale
description: W tym artykule opisano funkcje setlocale biblioteki środowiska wykonawczego języka Microsoft C (CRT) i _wsetlocaleprogram .
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 2834229839153c3154caadf71e5fb30d84ed2f1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353723"
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

*Kategorii*\
Kategoria, której dotyczą ustawienia regionalne.

*Ustawień regionalnych*\
Specyfikator ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Jeśli podano *prawidłowe ustawienia regionalne* i *kategorię,* zwraca wskaźnik do ciągu skojarzonego z *określonymi ustawieniami ustawieniami regionalnymi* i *kategorią*. Jeśli ustawienia regionalne lub *kategoria* nie są *prawidłowe,* zwraca wskaźnik zerowy, a bieżące ustawienia regionalne programu pozostają niezmienione.

Na przykład, wywołanie

```C
setlocale( LC_ALL, "en-US" );
```

ustawia wszystkie kategorie, zwracając tylko ciąg

```Output
en-US
```

Ciąg zwracany przez **setlocale** można skopiować, aby przywrócić tę część informacji o ustawieniach regionalnych programu. Magazyn lokalny globalny lub wątkowy jest używany dla ciągu zwracany przez **setlocale**. Późniejsze wywołania **setlocale** zastąpić ciąg, który unieważnia wskaźniki ciąg zwracany przez wcześniejsze wywołania.

## <a name="remarks"></a>Uwagi

Funkcja **setlocale** służy do ustawiania, zmieniania lub wykonywania zapytań o niektóre lub wszystkie bieżące informacje o ustawieniach regionalnych programu określone przez ustawienia regionalne i *kategorię* . *category* *ustawienia regionalne* odnoszą się do miejscowości (kraju/regionu i języka), dla której można dostosować niektóre aspekty programu. Niektóre kategorie zależne od ustawień regionalnych obejmują formatowanie dat i format wyświetlania wartości pieniężnych. Jeśli ustawisz *ustawienia regionalne* dla domyślnego ciągu dla języka, który ma wiele formularzy obsługiwanych na komputerze, należy sprawdzić wartość zwrotu **setlocale,** aby zobaczyć, który język jest w mocy. Na przykład jeśli ustawisz ustawienia regionalne na "chiński" wartość zwracana może być "chiński *uproszczony"* lub "chiński tradycyjny".

**_wsetlocale** jest szerokoznakową wersją **setlocale**; argument ustawień *regionalnych* i zwracana wartość **_wsetlocale** są ciągami znaków o szerokich znakach. **_wsetlocale** i **setlocale** zachowują się identycznie inaczej.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**Setlocale**|**Setlocale**|**_wsetlocale**|

Argument *kategoria* określa części informacji o ustawieniach regionalnych programu, których dotyczy problem. Makra używane dla *kategorii* i części programu, których dotyczą, są następujące:

|flaga *kategorii*|Wpływa|
|-|-|
| **LC_ALL** | Wszystkie kategorie, jak podano poniżej. |
| **LC_COLLATE** | **Strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**i **wcsxfrm** funkcji. |
| **Lc_ctype** | Funkcje obsługi znaków (z wyjątkiem **isdigit**, **isxdigit**, **mbstowcs**i **mbtowc**, które pozostają nienaruszone). |
| **LC_MONETARY** | Informacje o formacie monetaryskowym zwracane przez funkcję **localeconv.** |
| **LC_NUMERIC** | Znak dziesiętny dla sformatowanych procedur wyjściowych (takich jak **printf),** dla procedur konwersji danych i dla informacji o formatowaniu niepieniężnym zwracanych przez **localeconv**. Oprócz znaku dziesiętnego **LC_NUMERIC** ustawia separator tysięcy i ciąg kontrolny grupowania zwracany przez [localeconv](localeconv.md). |
| **LC_TIME** | **Strftime** i **wcsftime** funkcje. |

Ta funkcja sprawdza poprawność parametru kategorii. Jeśli parametr kategorii nie jest jedną z wartości podanych w poprzedniej tabeli, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w polu [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja ustawia **errno** na **Wartość EINVAL** i zwraca **wartość NULL**.

Argument *ustawień regionalnych* jest wskaźnikiem do ciągu, który określa ustawienia regionalne. Aby uzyskać informacje o formacie argumentu *ustawień regionalnych,* zobacz [Nazwy ustawień regionalnych, języki i ciągi kraju/regionu](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Jeśli *ustawienia regionalne* wskazują na pusty ciąg, ustawienia regionalne są środowiskiem macierzystym zdefiniowanym przez implementację. Wartość **C** określa minimalne środowisko zgodne z ANSI dla tłumaczenia C. Ustawienia regionalne **języka C** przyjęto założenie, że wszystkie typy danych **char** są 1 bajt i że ich wartość jest zawsze mniejsza niż 256.

W momencie uruchamiania programu wykonywany jest odpowiednik następującej instrukcji:

`setlocale( LC_ALL, "C" );`

Argument *ustawień regionalnych* może mieć nazwę ustawień regionalnych, ciąg języka, ciąg języka i kod kraju/regionu, stronę kodową lub ciąg języka, kod kraju/regionu i stronę kodową. Zestaw dostępnych nazw ustawień regionalnych, języków, kodów krajów/regionów i stron kodowych zawiera wszystkie te obsługiwane przez interfejs API systemu Windows NLS. Zestaw nazw ustawień regionalnych obsługiwanych przez **setlocale** są opisane w [ustawieniach regionalnych nazwy, języki i kraj/region ciągi](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Zestaw ciągów języka i kraju/regionu obsługiwanych przez **setlocale** są wymienione w [ciągach językowych](../../c-runtime-library/language-strings.md) i [ciągach kraju/regionu](../../c-runtime-library/country-region-strings.md). Firma Microsoft zaleca formę nazwy ustawień regionalnych ze względu na wydajność i łatwość konserwacji ciągów ustawień regionalnych, osadzonych w kodzie lub szeregowanych do pamięci. Zmiana ciągów nazw ustawień regionalnych przez aktualizację systemu operacyjnego jest mniej prawdopodobna niż zmiana formy nazwy języka i kraju/regionu.

Wskaźnik null, który jest przekazywany jako argument *ustawień regionalnych* mówi **setlocale** do kwerendy zamiast ustawić środowisko międzynarodowe. Jeśli argument *ustawień regionalnych* jest wskaźnikiem zerowym, bieżące ustawienie ustawień regionalnych programu nie zostanie zmienione. Zamiast tego **setlocale** zwraca wskaźnik do ciągu, który jest skojarzony z *kategorią* bieżących ustawień regionalnych wątku. Jeśli argument *kategorii* jest **LC_ALL,** funkcja zwraca ciąg wskazujący bieżące ustawienie każdej kategorii, oddzielone średnikami. Na przykład, sekwencja wywołań

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

który jest ciągiem skojarzonym z **kategorią LC_ALL.**

Poniższe przykłady odnoszą się do **kategorii LC_ALL.** Jeden z ciągów ". OCP" i ". ACP" może służyć zamiast numeru strony kodowej, aby określić użycie domyślnej strony kodowej OEM użytkownika i domyślnej strony kodowej ANSI dla tej nazwy ustawień regionalnych, odpowiednio.

- `setlocale( LC_ALL, "" );`

   Ustawia ustawienia regionalne na domyślne, czyli domyślną stronę kodową ANSI użytkownika, uzyskaną z systemu operacyjnego. Nazwa ustawień regionalnych jest ustawiona na wartość zwracaną przez [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Strona kodowa jest ustawiona na wartość zwracaną przez [GetACP](/windows/win32/api/winnls/nf-winnls-getacp).

- `setlocale( LC_ALL, ".OCP" );`

   Ustawia ustawienia regionalne na bieżącą stronę kodową OEM uzyskaną z systemu operacyjnego. Nazwa ustawień regionalnych jest ustawiona na wartość zwracaną przez [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Strona kodowa jest ustawiona na [wartość LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) dla domyślnej nazwy ustawień regionalnych użytkownika przez [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, ".ACP" );`

   Ustawia ustawienia regionalne na bieżącą stronę kodową ANSI, uzyskaną od systemu operacyjnego. Nazwa ustawień regionalnych jest ustawiona na wartość zwracaną przez [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Strona kodowa jest ustawiona na [wartość LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) dla domyślnej nazwy ustawień regionalnych użytkownika przez [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<localename>" );`

   Ustawia ustawienia regionalne na nazwę ustawień regionalnych, która jest wskazywana przez * \<>. * Strona kodowa jest ustawiona na [wartość LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) dla określonej nazwy ustawień regionalnych przez [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>" );`

   Ustawia ustawienia regionalne na język i kraj/region wskazywany przez * \<>języka* i * \<>kraju, *wraz z domyślną stroną kodową uzyskaną z systemu operacyjnego hosta. Strona kodowa jest ustawiona na [wartość LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) dla określonej nazwy ustawień regionalnych przez [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Ustawia ustawienia regionalne na język, kraj/region i stronę kodową wskazywany przez * \<>języka *, * \<>kraju *i * \<code_page>* ciągi. Można użyć różnych kombinacji języka, kraju/regionu i strony kodowej. Na przykład, to wywołanie ustawia ustawienia regionalne na francuski-Kanada ze stroną kodową 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   To wywołanie ustawia ustawienia regionalne na francuski-Kanada z domyślną stroną kodową ANSI:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   To wywołanie ustawia ustawienia regionalne na francuski-Kanada z domyślną stroną kodową OEM:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Ustawia ustawienia regionalne na język, który * \< *jest wskazywany przez>języka i używa domyślnego kraju/regionu dla określonego języka i domyślnej strony kodowej ANSI dla tego kraju/regionu, uzyskanej z systemu operacyjnego hosta. Na przykład następujące wywołania **setlocale** są funkcjonalnie równoważne:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Zaleca się pierwszą formę ze względu na wydajność oraz łatwość konserwacji.

- `setlocale( LC_ALL, ".<code_page>" );`

   Ustawia stronę kodową na wartość wskazywana przez *<code_page>, *wraz z domyślnym krajem/regionem i językiem (zdefiniowanym przez system operacyjny hosta) dla określonej strony kodowej.

Kategoria musi być **LC_ALL** lub **LC_CTYPE,** aby dokonać zmiany strony kodowej. Na przykład jeśli domyślnym krajem/regionem i językiem systemu operacyjnego hosta są "Stany Zjednoczone" i "Angielski", następujące dwa wywołania **setlocale** są funkcjonalnie równoważne:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Aby uzyskać więcej informacji, zobacz [dyrektywę setlocale](../../preprocessor/setlocale.md) pragma w [odwołaniu preprocesora C/C++](../../preprocessor/c-cpp-preprocessor-reference.md).

Funkcja [_configthreadlocale](configthreadlocale.md) służy do kontrolowania, czy **setlocale** wpływa na ustawienia regionalne wszystkich wątków w programie lub tylko ustawienia regionalne wątku wywołującego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setlocale**|\<>|
|**_wsetlocale**|\<>> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

[Nazwy ustawień regionalnych, języki i ciągi kraju/regionu](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)\
[Ustawień regionalnych](../../c-runtime-library/locale.md)\
[lokalizacja konw.](localeconv.md)\
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)\
[wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[funkcje strcoll](../../c-runtime-library/strcoll-functions.md)\
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb, _wctomb_l](wctomb-wctomb-l.md)
