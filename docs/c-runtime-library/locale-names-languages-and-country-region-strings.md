---
title: Nazwy lokalne, Języki i ciągi krajów i regionów
ms.date: 12/10/2018
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
ms.openlocfilehash: 512eb589d964da9ef8e87f4193362c739b39b4b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500059"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>UCRT nazwy ustawień regionalnych, Języki i ciągi kraj/region

Argument *locale* dla funkcji [setlocals, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md), [ \_Create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)i [ \_wcreate\_](../c-runtime-library/reference/create-locale-wcreate-locale.md) można ustawić przy użyciu nazw ustawień regionalnych, Języki, kody krajów/regionów i strony kodowe, które są obsługiwane przez NLS API systemu Windows. Argument *locale* przyjmuje następującą formę:

> *locale* :: "*locale-Name*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|"*Język*\[_kraj — region_ . **\_** \[ *strona kodowa*]] "<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|" __.__ *strona kodowa*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|S<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|NULL

Formularz *nazwy ustawień regionalnych* jest krótkim, standardowym ciągiem IETF; na przykład `en-US` dla angielskiej wersji językowej (Stany Zjednoczone `bs-Cyrl-BA` ) lub dla języka bośniackiego (cyrylica, Bośnia i Hercegowina). Te formularze są preferowane. Aby uzyskać listę obsługiwanych nazw ustawień regionalnych według wersji systemu operacyjnego Windows, zobacz kolumnę **tag języka** tabeli w [dodatku a: Zachowanie](https://msdn.microsoft.com/library/cc233982.aspx) produktu w [MS-LCID]: Dokumentacja identyfikatora kodu języka (LCID) systemu Windows. Ten zasób zawiera listę obsługiwanych części nazw ustawień regionalnych: języka, alfabetu i regionu. Aby uzyskać informacje o obsługiwanych nazwach ustawień regionalnych, które mają inne niż domyślne zamówienia sortowania, zobacz kolumnę **Nazwa ustawień regionalnych** w [identyfikatorach kolejności sortowania](/windows/win32/Intl/sort-order-identifiers). W systemie Windows 10 lub nowszym, nazwy regionalne odpowiadające prawidłowym tagów języka [BCP-47](https://tools.ietf.org/html/bcp47) są dozwolone. Na przykład `jp-US` jest prawidłowym tagiem BCP-47, ale efektywnie działa tylko `US` w przypadku funkcji ustawień regionalnych.

_Region_\[ **\_** języka.\[ *strona kodowa*]] formularz jest przechowywany w ustawieniach regionalnych dla kategorii, gdy ciąg języka lub ciąg języka i ciąg kraju lub regionu są używane do tworzenia ustawień regionalnych. Zestaw obsługiwanych ciągów języka jest opisany w ciągach [języka](../c-runtime-library/language-strings.md), a lista obsługiwanych ciągów krajów i regionów jest wymieniona w ciągach [kraju/regionu](../c-runtime-library/country-region-strings.md). Jeśli określony język nie jest skojarzony z określonym krajem lub regionem, język domyślny dla określonego kraju lub regionu jest przechowywany w ustawieniach regionalnych. Nie zaleca się tej formy dla ciągów ustawień regionalnych osadzonych w kodzie lub szeregowanych w pamięci, ponieważ jest bardziej prawdopodobne, że aktualizacja systemu operacyjnego je zmieni, w przeciwieństwie do formy nazwy ustawień regionalnych.

*Strona kodowa* jest stroną kodową ANSI/OEM, która jest skojarzona z ustawieniami regionalnymi. Strona kodowa jest określana automatycznie po określeniu ustawień regionalnych za pomocą wyłącznie języka lub języka i kraju/regionu. Wartość `.ACP` specjalna określa stronę kodową ANSI dla kraju/regionu. Wartość `.OCP` specjalna określa stronę kodową OEM kraju/regionu. Na przykład, jeśli określisz `"Greek_Greece.ACP"` jako ustawienia regionalne, ustawienia regionalne są przechowywane jako `Greek_Greece.1253` (strona kodowa ANSI dla języka greckiego), a jeśli `"Greek_Greece.OCP"` określisz ustawienia regionalne, jest ono przechowywane `Greek_Greece.737` jako (strona kodowa OEM dla języka greckiego). Aby uzyskać więcej informacji na temat stron kodowych, zobacz [strony kodowe](../c-runtime-library/code-pages.md). Aby uzyskać listę obsługiwanych stron kodowych w systemie Windows, zobacz [identyfikatory stron kodowych](/windows/win32/Intl/code-page-identifiers).

Jeśli używasz tylko strony kodowej, aby określić ustawienia regionalne, używany jest domyślny język i kraj/region użytkownika zgłoszone przez [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename) . Na przykład jeśli określisz `".1254"` (turecki ANSI) jako ustawienia regionalne dla użytkownika skonfigurowanego dla języka angielskiego (Stany Zjednoczone), przechowywane są `English_United States.1254`ustawienia regionalne. Nie zaleca się tej formy, ponieważ może to prowadzić do niespójnego zachowania.

Wartość`C` argumentu *ustawień regionalnych* określa minimalne środowisko zgodne ze standardem ANSI dla translacji C. W `C` ustawieniach regionalnych zakłada się, że każdy typ danych **char** ma 1 bajt, a jego wartość jest zawsze mniejsza niż 256. Jeśli *Ustawienia regionalne* wskazują pusty ciąg, ustawienia regionalne to środowisko natywne zdefiniowane w implementacji.

W tym samym czasie można określić wszystkie kategorie ustawień regionalnych dla `setlocale` funkcji i `_wsetlocale` , korzystając z `LC_ALL` kategorii. Kategorie można ustawić na te same ustawienia regionalne lub każdą kategorię można ustawić indywidualnie przy użyciu argumentu ustawień regionalnych, który ma tę formę:

> *LC-All-specyfikator* :: *locale*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|LC_COLLATE =_locale_] \[ \[ **; LC_CTYPE =** locale\[] **; LC_MONETARY =** locale\[] **; LC_NUMERIC =** locale\[] **; LC_TIME =** _locale_]

Można określić wiele typów kategorii, oddzielając je średnikami. Typy kategorii, które nie są określone, używają bieżących ustawień regionalnych. Na przykład ten fragment kodu ustawia bieżące ustawienia regionalne `de-DE`dla wszystkich kategorii na, a następnie ustawia kategorie `LC_MONETARY` na `en-GB` i `LC_TIME`: `es-ES`

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)<br/>
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[Ciągi języka](../c-runtime-library/language-strings.md)<br/>
[Ciągi kraju/regionu](../c-runtime-library/country-region-strings.md)
