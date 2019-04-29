---
title: Nazwy lokalne, języki i ciągi Kraj / Region
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
ms.openlocfilehash: f6df36aafde9a61a1fd590a7f60b3c17131aadbb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342747"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>Nazwy UCRT lokalne, języki i Kraj/Region ciągów

*Ustawień regionalnych* argument [setlocale, \_wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md), [ \_tworzenie\_ustawień regionalnych](../c-runtime-library/reference/create-locale-wcreate-locale.md), i [ \_wcreate\_ustawień regionalnych](../c-runtime-library/reference/create-locale-wcreate-locale.md) funkcje można ustawić za pomocą nazw ustawień regionalnych, języków, kodów krajów/regionów i stron kodowych, które są obsługiwane przez Windows NLS API. *Ustawień regionalnych* argument ma następującą postać:

> *Ustawienia regionalne* :: "*nazwy ustawień regionalnych*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "*języka*\[**\_**_kraj / region_\[__.__ *strony kodowej*]] "<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "__.__  *strony kodowej*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "C"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| ""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| WARTOŚĆ NULL

*Nazwy ustawień regionalnych* formularz jest krótka, standaryzowane IETF ciągu, na przykład `en-US` dla języka angielskiego (Stany Zjednoczone) lub `bs-Cyrl-BA` dla bośniackiego (cyrylica, Bośnia i Hercegowina). Te formularze są preferowane. Aby uzyskać listę nazw ustawień regionalnych obsługiwanych przez wersję systemu operacyjnego Windows, zobacz **tagu języka** kolumny tabeli w [dodatek A: Zachowanie produktu](https://msdn.microsoft.com/library/cc233982.aspx) w [MS-LCID]: Dokumentacja identyfikator (LCID) Windows języka kodu. Ten zasób zawiera listę obsługiwanych części nazw ustawień regionalnych: języka, alfabetu i regionu. Aby uzyskać informacje o obsługiwanych nazw ustawień regionalnych, które mają inne niż domyślne, zobacz **nazwy ustawień regionalnych** kolumny w [identyfikatory kolejności sortowania](/windows/desktop/Intl/sort-order-identifiers). W obszarze nazw 10 lub nowszym, ustawienia regionalne systemu Windows, które odpowiadają na prawidłowe [BCP 47](https://tools.ietf.org/html/bcp47) tagów języka są dozwolone. Na przykład `jp-US` jest poprawny tag BCP 47, ale jest efektywne tylko `US` dla funkcji ustawień regionalnych.

*Języka*\[**\_**_kraj / region_\[__.__ *strony kodowej*]] formularza są przechowywane w ustawieniach regionalnych dla kategorii, gdy ciąg języka lub ciąg języka i ciąg kraju lub regionu, służy do tworzenia ustawień regionalnych. Zestaw obsługiwanych ciągów języka jest opisany w [Language Strings](../c-runtime-library/language-strings.md), a lista obsługiwanych ciągów kraju i regionu znajduje się w [ciągi Kraj/Region](../c-runtime-library/country-region-strings.md). Jeśli określony język nie jest skojarzony z określonym kraju lub regionu, język domyślny dla określonego kraju lub regionu jest przechowywany w ustawieniach regionalnych. Nie zaleca się tej formy dla ciągów ustawień regionalnych osadzonych w kodzie lub szeregowanych w pamięci, ponieważ jest bardziej prawdopodobne, że aktualizacja systemu operacyjnego je zmieni, w przeciwieństwie do formy nazwy ustawień regionalnych.

*Strony kodowej* jest strona kodowa ANSI/OEM, który jest skojarzony z ustawieniami regionalnymi. Strona kodowa jest określana automatycznie po określeniu ustawień regionalnych za pomocą wyłącznie języka lub języka i kraju/regionu. Specjalna wartość `.ACP` Określa stronę kodową ANSI dla kraju/regionu. Specjalna wartość `.OCP` Określa stronę kodową OEM dla kraju/regionu. Na przykład, jeśli określisz `"Greek_Greece.ACP"` jako ustawienie regionalne, ustawienie regionalne jest przechowywane jako `Greek_Greece.1253` (na stronę kodową ANSI dla języka greckiego), a jeśli określisz `"Greek_Greece.OCP"` jako ustawienie regionalne, jest przechowywany jako `Greek_Greece.737` (stronę kodową OEM dla języka greckiego). Aby uzyskać więcej informacji dotyczących stron kodowych, zobacz [stron kodowych](../c-runtime-library/code-pages.md). Aby uzyskać listę stron kodowych obsługiwanych w Windows, zobacz [kodu strony identyfikatory](/windows/desktop/Intl/code-page-identifiers).

Jeśli używasz tylko strony kodowej Aby określić ustawienia regionalne, domyślny język i kraj/region użytkownika zgłoszonej przez [GetUserDefaultLocaleName](/windows/desktop/api/winnls/nf-winnls-getuserdefaultlocalename) są używane. Na przykład, jeśli określisz `".1254"` (turecki ANSI) jako ustawienie regionalne dla użytkownika, który jest skonfigurowany dla języka angielskiego (Stany Zjednoczone), ustawienia regionalne, który jest przechowywany jest `English_United States.1254`. Nie zaleca się tej formy, ponieważ może to prowadzić do niespójnego zachowania.

A *ustawień regionalnych* wartość argumentu `C` określa minimalne środowisko odpowiadające ANSI dla translacji C. `C` Ustawień regionalnych zakłada, że każdy **char** — typ danych jest 1 bajt i jego wartość jest zawsze mniejsza niż 256. Jeśli *ustawień regionalnych* wskazuje na pusty ciąg, ustawienia regionalne są natywnym środowiskiem zdefiniowanych w implementacji.

Można określić wszystkie kategorie ustawień regionalnych, w tym samym czasie dla `setlocale` i `_wsetlocale` funkcji przy użyciu `LC_ALL` kategorii. Kategorie można ustawić na te same ustawienia regionalne lub każdą kategorię można ustawić indywidualnie przy użyciu argumentu ustawień regionalnych, który ma tę formę:

> *LC-ALL-specifier* :: *ustawień regionalnych*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| \[**LC_COLLATE =**_ustawień regionalnych_]\[**; LC_CTYPE =**_ustawień regionalnych_]\[**; LC_MONETARY =**_ustawień regionalnych_]\[**; LC_NUMERIC =**_ustawień regionalnych_]\[**; LC_TIME =**_ustawień regionalnych_]

Można określić wiele typów kategorii, oddzielając je średnikami. Typy kategorii, które nie są określone, używają bieżących ustawień regionalnych. Na przykład, następujący fragment kodu ustawia bieżące ustawienia regionalne dla wszystkich kategorii na `de-DE`, a następnie ustawia kategorie `LC_MONETARY` do `en-GB` i `LC_TIME` do `es-ES`:

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
[Ciągi Kraj/Region](../c-runtime-library/country-region-strings.md)
