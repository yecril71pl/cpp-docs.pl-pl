---
title: Nazwy lokalne, Języki i ciągi krajów i regionów
ms.date: 12/10/2018
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
ms.openlocfilehash: 704da410ee6386027a7528c0c73a89ef31557a77
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842953"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>UCRT nazwy ustawień regionalnych, Języki i ciągi kraj/region

Argument *locale* dla funkcji [setlocals, \_ wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md), [ \_ create \_ locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)i [ \_ wcreate \_ ](../c-runtime-library/reference/create-locale-wcreate-locale.md) można ustawić przy użyciu nazw regionalnych, języków, kodów krajów/regionów i stron kodowych, które są obsługiwane przez NLS API systemu Windows. Argument *locale* przyjmuje następującą formę:

> *locale* :: "*locale-Name*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|"*Język* \[ **\_** _kraj — region_ \[ __.__ *strona kodowa*]] "<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|"__.__ *strona kodowa*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| S<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| ""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| NULL

Formularz *nazwy ustawień regionalnych* jest krótkim, standardowym ciągiem IETF; na przykład `en-US` dla angielskiej wersji językowej (Stany Zjednoczone) lub `bs-Cyrl-BA` dla języka bośniackiego (cyrylica, Bośnia i Hercegowina). Te formularze są preferowane. Aby uzyskać listę obsługiwanych nazw ustawień regionalnych według wersji systemu operacyjnego Windows, zobacz kolumnę **tag języka** tabeli w [dodatku a: zachowanie produktu](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) w \[ MS-LCID]: dokumentacja identyfikatora kodu języka (LCID) systemu Windows. Ten zasób zawiera listę obsługiwanych części nazw ustawień regionalnych: języka, alfabetu i regionu. Aby uzyskać informacje o obsługiwanych nazwach ustawień regionalnych, które mają inne niż domyślne zamówienia sortowania, zobacz kolumnę **Nazwa ustawień regionalnych** w [identyfikatorach kolejności sortowania](/windows/win32/Intl/sort-order-identifiers). W systemie Windows 10 lub nowszym, nazwy regionalne odpowiadające prawidłowym tagów języka [BCP-47](https://tools.ietf.org/html/bcp47) są dozwolone. Na przykład `jp-US` jest prawidłowym TAGIEM BCP-47, ale efektywnie działa tylko `US` w przypadku funkcji ustawień regionalnych.

Region *języka* \[ **\_** _country-region_ \[ __.__ *strona kodowa*]] formularz jest przechowywany w ustawieniach regionalnych dla kategorii, gdy ciąg języka lub ciąg języka i ciąg kraju lub regionu są używane do tworzenia ustawień regionalnych. Zestaw obsługiwanych ciągów języka jest opisany w [ciągach języka](../c-runtime-library/language-strings.md), a lista obsługiwanych ciągów krajów i regionów jest wymieniona w [ciągach kraju/regionu](../c-runtime-library/country-region-strings.md). Jeśli określony język nie jest skojarzony z określonym krajem lub regionem, język domyślny dla określonego kraju lub regionu jest przechowywany w ustawieniach regionalnych. Nie zaleca się tej formy dla ciągów ustawień regionalnych osadzonych w kodzie lub szeregowanych w pamięci, ponieważ jest bardziej prawdopodobne, że aktualizacja systemu operacyjnego je zmieni, w przeciwieństwie do formy nazwy ustawień regionalnych.

*Strona kodowa* jest stroną kodową ANSI/OEM, która jest skojarzona z ustawieniami regionalnymi. Strona kodowa jest określana automatycznie po określeniu ustawień regionalnych za pomocą wyłącznie języka lub języka i kraju/regionu. Wartość specjalna `.ACP` określa stronę kodową ANSI dla kraju/regionu. Wartość specjalna `.OCP` określa stronę kodową OEM kraju/regionu. Na przykład, jeśli określisz `"Greek_Greece.ACP"` jako ustawienia regionalne, ustawienia regionalne są przechowywane jako `Greek_Greece.1253` (strona kodowa ANSI dla języka greckiego), a jeśli określisz `"Greek_Greece.OCP"` Ustawienia regionalne, jest ono przechowywane jako `Greek_Greece.737` (strona kodowa OEM dla języka greckiego). Aby uzyskać więcej informacji na temat stron kodowych, zobacz [strony kodowe](../c-runtime-library/code-pages.md). Aby uzyskać listę obsługiwanych stron kodowych w systemie Windows, zobacz [identyfikatory stron kodowych](/windows/win32/Intl/code-page-identifiers).

Jeśli używasz tylko strony kodowej, aby określić ustawienia regionalne, używany jest domyślny język i kraj/region użytkownika zgłoszone przez [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename) . Na przykład jeśli określisz `".1254"` (turecki ANSI) jako ustawienia regionalne dla użytkownika skonfigurowanego dla języka angielskiego (Stany Zjednoczone), przechowywane są ustawienia regionalne `English_United States.1254` . Nie zaleca się tej formy, ponieważ może to prowadzić do niespójnego zachowania.

Wartość argumentu *ustawień regionalnych* `C` określa minimalne środowisko zgodne ze standardem ANSI dla translacji C. W `C` ustawieniach regionalnych przyjęto, że każdy **`char`** Typ danych ma 1 bajt, a jego wartość jest zawsze mniejsza niż 256. Jeśli *Ustawienia regionalne* wskazują pusty ciąg, ustawienia regionalne to środowisko natywne zdefiniowane w implementacji.

W tym samym czasie można określić wszystkie kategorie ustawień regionalnych dla `setlocale` funkcji i, `_wsetlocale` korzystając z `LC_ALL` kategorii. Kategorie można ustawić na te same ustawienia regionalne lub każdą kategorię można ustawić indywidualnie przy użyciu argumentu ustawień regionalnych, który ma tę formę:

> *LC-All-specyfikator* :: *locale*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|\[ **LC_COLLATE =**_locale_] \[ **; LC_CTYPE =**_locale_] \[ **; LC_MONETARY =**_locale_] \[ **; LC_NUMERIC =**_locale_] \[ **; LC_TIME =**_locale_]

Można określić wiele typów kategorii, oddzielając je średnikami. Typy kategorii, które nie są określone, używają bieżących ustawień regionalnych. Na przykład ten fragment kodu ustawia bieżące ustawienia regionalne dla wszystkich kategorii na `de-DE` , a następnie ustawia kategorie `LC_MONETARY` na `en-GB` i `LC_TIME` `es-ES` :

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```


## <a name="utf-8-support"></a>Obsługa UTF-8

Obsługę UTF-8 można włączyć przy użyciu strony kodowej UTF-8 w ciągu ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [sekcję `setlocale` Obsługa standardu UTF-8](../c-runtime-library/reference/setlocale-wsetlocale.md#utf-8-support) .


## <a name="see-also"></a>Zobacz też

[Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)<br/>
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[Ciągi języka](../c-runtime-library/language-strings.md)<br/>
[Ciągi kraju/regionu](../c-runtime-library/country-region-strings.md)
