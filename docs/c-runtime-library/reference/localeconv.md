---
title: localeconv
ms.date: 4/2/2020
api_name:
- localeconv
- _o_localeconv
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
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: a617980d60b3a12c06b30aab6cd457792a1aa770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342143"
---
# <a name="localeconv"></a>localeconv

Pobiera szczegółowe informacje na temat ustawień regionalnych.

## <a name="syntax"></a>Składnia

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Wartość zwracana

**localeconv** zwraca wskaźnik do wypełnionego obiektu typu [struct lconv](../../c-runtime-library/standard-types.md). Wartości zawarte w obiekcie są kopiowane z ustawień ustawień regionalnych w magazynie lokalnym wątku i mogą być zastępowane przez kolejne wywołania **localeconv**. Zmiany wprowadzone w wartościach w tym obiekcie nie modyfikują ustawień ustawień regionalnych. Wywołania [setlocale](setlocale-wsetlocale.md) z wartościami *kategorii* **LC_ALL** **, LC_MONETARY**lub **LC_NUMERIC** zastąpić zawartość struktury.

## <a name="remarks"></a>Uwagi

Funkcja **localeconv** otrzymuje szczegółowe informacje o formatowaniu numerycznym dla bieżących ustawień regionalnych. Informacje te są przechowywane w strukturze typu **lconv**. Struktura **lconv,** zdefiniowana w locale. H, zawiera następujące elementy członkowskie:

|Pole|Znaczenie|
|-|-|
decimal_point,<br/>_W_decimal_point|Wskaźnik do znaku dziesiętnego dla ilości niemonetowych.
thousands_sep,<br/>_W_thousands_sep|Wskaźnik do znaku, który oddziela grupy cyfr na lewo od przecinka dziesiętnego dla ilości niemonetowych.
grouping|Wskaźnik do liczby całkowitej o rozmiarze **char,** który zawiera rozmiar każdej grupy cyfr w ilościach niepieniastych.
int_curr_symbol,<br/>_W_int_curr_symbol|Wskaźnik do symbolu waluty międzynarodowej dla bieżących ustawień regionalnych. Pierwsze trzy znaki określają alfabetyczny symbol waluty międzynarodowej zdefiniowany w *standardzie ISO 4217 dla reprezentacji waluty i funduszy.* Czwarty znak (bezpośrednio poprzedzający znak zerowy) oddziela symbol waluty międzynarodowej od ilości pieniężnej.
currency_symbol,<br/>_W_currency_symbol|Wskaźnik do symbolu waluty lokalnej dla bieżących ustawień regionalnych.
mon_decimal_point,<br/>_W_mon_decimal_point|Wskaźnik do znaku dziesiętnego dla ilości pieniężnych.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Wskaźnik do separatora dla grup cyfr na lewo od miejsca dziesiętnego w ilościach pieniężnych.
mon_grouping|Wskaźnik do liczby całkowitej o rozmiarze **znaku,** który zawiera rozmiar każdej grupy cyfr w ilościach pieniężnych.
positive_sign,<br/>_W_positive_sign|Ciąg oznaczający znak dla nieujemnych ilości pieniężnych.
negative_sign,<br/>_W_negative_sign|Ciąg oznaczający znak dla ujemnych ilości pieniężnych.
int_frac_digits|Liczba cyfr po prawej stronie przecinka dziesiętnego w ilościach pieniężnych sformatowanych międzynarodowo.
frac_digits|Liczba cyfr po prawej stronie przecinka dziesiętnego w sformatowanych ilościach pieniężnych.
p_cs_precedes|Ustaw wartość 1, jeśli symbol waluty poprzedza wartość dla nieujemnej sformatowanej ilości pieniężnej. Ustaw wartość 0, jeśli symbol podąża za wartością.
p_sep_by_space|Ustaw wartość 1, jeśli symbol waluty jest oddzielony spacją od wartości dla nieujemnej sformatowanej ilości pieniężnej. Ustaw na 0, jeśli nie ma separacji przestrzeni.
n_cs_precedes|Ustaw wartość 1, jeśli symbol waluty poprzedza wartość dla ujemnej sformatowanej ilości pieniężnej. Ustaw wartość 0, jeśli symbol zakończy się pomyślnie.
n_sep_by_space|Ustaw wartość 1, jeśli symbol waluty jest oddzielony spacją od wartości dla ujemnej sformatowanej ilości pieniężnej. Ustaw na 0, jeśli nie ma separacji przestrzeni.
p_sign_posn|Pozycja znaku dodatniego w nieujemnych sformatowanych ilościach pieniężnych.
n_sign_posn|Pozycja znaku dodatniego w ujemnych sformatowanych ilościach pieniężnych.

Z wyjątkiem przypadków określonych, elementy członkowskie `char *` struktury `wchar_t *` **lconv,** które mają i wersje są wskaźniki do ciągów. Każdy z nich, który jest równy **""** (lub **L""** dla <strong>\*</strong> **wchar_t)** jest albo zerowej długości lub nie są obsługiwane w bieżącym ustawieniach regionalnych. Należy pamiętać, że **decimal_point** i **_W_decimal_point** są zawsze obsługiwane i niezerowej długości.

Char **char** członków struktury są małe numery nieujemne, a nie znaki. Żadna z tych, która **jest równa CHAR_MAX** nie jest obsługiwana w bieżącym ustawieniach regionalnych.

Wartości **grupowania** i **mon_grouping** są interpretowane zgodnie z następującymi zasadami:

- **CHAR_MAX** - Nie należy wykonywać żadnych dalszych grupowania.

- 0 - Użyj poprzedniego elementu dla każdej z pozostałych cyfr.

- *n* - Liczba cyfr, które składają się na bieżącą grupę. Następny element jest analizowany w celu określenia rozmiaru następnej grupy cyfr przed bieżącą grupą.

Wartości **dla int_curr_symbol** są interpretowane zgodnie z następującymi regułami:

- Pierwsze trzy znaki określają alfabetyczny symbol waluty międzynarodowej zdefiniowany w *standardzie ISO 4217 dla reprezentacji waluty i funduszy.*

- Czwarty znak (bezpośrednio poprzedzający znak zerowy) oddziela symbol waluty międzynarodowej od ilości pieniężnej.

Wartości **dla p_cs_precedes** i **n_cs_precedes** są interpretowane zgodnie z następującymi regułami (reguła **n_cs_precedes** znajduje się w nawiasach):

- 0 - Symbol waluty następuje wartość dla wartości pieniężnej nieujemne (ujemne) sformatowane.

- 1 - Symbol waluty poprzedza wartość nieujemną (ujemną) sformatowaną wartością pieniężną.

Wartości **dla p_sep_by_space** i **n_sep_by_space** są interpretowane zgodnie z następującymi regułami (reguła **n_sep_by_space** znajduje się w nawiasach):

- 0 - Symbol waluty jest oddzielony od wartości spacji dla nieujemnej (ujemnej) sformatowanej wartości pieniężnej.

- 1 - Nie ma separacji odstępów między symbolem waluty a wartością dla nieujemnej (ujemnej) sformatowanej wartości pieniężnej.

Wartości **dla p_sign_posn** i **n_sign_posn** są interpretowane zgodnie z następującymi regułami:

- 0 - Nawiasy otaczają ilość i symbol waluty.

- 1 - Ciąg znaku poprzedza ilość i symbol waluty.

- 2 - Znak ciąg następuje ilość i symbol waluty.

- 3 - Znak ciąg bezpośrednio poprzedza symbol waluty.

- 4 - Znak ciąg bezpośrednio następuje symbol waluty.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**localeconv**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
