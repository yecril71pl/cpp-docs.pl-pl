---
title: localeconv
ms.date: 11/04/2016
api_name:
- localeconv
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
ms.openlocfilehash: ca7113903e1ed6e9ffb94bef79beba41e09bfb71
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953362"
---
# <a name="localeconv"></a>localeconv

Pobiera szczegółowe informacje o ustawieniach regionalnych.

## <a name="syntax"></a>Składnia

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Wartość zwracana

**localeconv** zwraca wskaźnik do wypełnionego obiektu typu [struct lconv](../../c-runtime-library/standard-types.md). Wartości zawarte w obiekcie są kopiowane z ustawień regionalnych w magazynie wątków lokalnych i mogą zostać zastąpione przez kolejne wywołania do **localeconv**. Zmiany wprowadzone w wartościach w tym obiekcie nie modyfikują ustawień ustawień regionalnych. Wywołania metody [setlocaling](setlocale-wsetlocale.md) z wartościami *kategorii* **LC_ALL**, **LC_MONETARY**lub **LC_NUMERIC** zastępują zawartość struktury.

## <a name="remarks"></a>Uwagi

Funkcja **localeconv** pobiera szczegółowe informacje o formatowaniu liczbowym dla bieżących ustawień regionalnych. Te informacje są przechowywane w strukturze typu **lconv**. Struktura **lconv** zdefiniowana w ustawieniach regionalnych. H, zawiera następujących członków:

|Pole|Znaczenie|
|-|-|
decimal_point,<br/>_W_decimal_point|Wskaźnik na znak dziesiętny dla ilości niepieniężnych.
thousands_sep,<br/>_W_thousands_sep|Wskaźnik do znaku, który oddziela grupy cyfr po lewej stronie przecinka dziesiętnego dla ilości niepieniężnych.
grouping|Wskaźnik do liczby całkowitej o rozmiarze **char**, która zawiera rozmiar każdej grupy cyfr w ilościach niepieniężnych.
int_curr_symbol,<br/>_W_int_curr_symbol|Wskaźnik na Międzynarodowy symbol waluty dla bieżących ustawień regionalnych. Pierwsze trzy znaki określają alfabetyczny symbol waluty międzynarodowej zgodnie z definicją w *kodzie ISO 4217 dla reprezentacji standardu walutowego i funduszy* . Czwarty znak (bezpośrednio poprzedzający znak null) oddziela Międzynarodowy symbol waluty od ilości pieniężnej.
currency_symbol,<br/>_W_currency_symbol|Wskaźnik na symbol waluty lokalnej dla bieżących ustawień regionalnych.
mon_decimal_point,<br/>_W_mon_decimal_point|Wskaźnik na znak dziesiętny dla ilości pieniężnych.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Wskaźnik do separatora grup cyfr na lewo od miejsca dziesiętnego w ilościach pieniężnych.
mon_grouping|Wskaźnik do liczby całkowitej o rozmiarze **char**, która zawiera rozmiar każdej grupy cyfr w ilościach pieniężnych.
positive_sign,<br/>_W_positive_sign|Ciąg oznaczający znak w przypadku nieujemnych ilości pieniężnych.
negative_sign,<br/>_W_negative_sign|Ciąg oznaczający znak w przypadku ujemnych ilości pieniężnych.
int_frac_digits|Liczba cyfr z prawej strony punktu dziesiętnego w przypadku szesnastkowie sformatowanych ilości pieniężnych.
frac_digits|Liczba cyfr z prawej strony punktu dziesiętnego w sformatowanych ilościach pieniężnych.
p_cs_precedes|Ustaw wartość 1, jeśli symbol waluty poprzedza wartość wartości dla nieujemnej sformatowanej ilości pieniężnej. Ustaw wartość na 0, jeśli symbol następuje po wartości.
p_sep_by_space|Ustaw wartość 1, jeśli symbol waluty jest rozdzielony spacją od wartości dla nieujemnej sformatowanej ilości pieniężnej. Ustaw wartość 0, jeśli nie ma separacji miejsca.
n_cs_precedes|Ustaw wartość 1, jeśli symbol waluty poprzedza wartość wartości dla ujemnej sformatowanej ilości pieniężnej. Ustawienie wartości 0 powoduje, że symbol kończy się powodzeniem.
n_sep_by_space|Ustaw wartość 1, jeśli symbol waluty jest rozdzielony spacją od wartości dla ujemnie sformatowanej ilości pieniężnej. Ustaw wartość 0, jeśli nie ma separacji miejsca.
p_sign_posn|Pozycja znaku pozytywnego w nieujemnych, sformatowanych ilościach pieniężnych.
n_sign_posn|Pozycja znaku pozytywnego w ujemnych sformatowanych ilościach pieniężnych.

O ile nie określono, członkowie struktury **lconv** , która ma `char *` i `wchar_t *` wersje są wskaźnikami do ciągów. Każdy z tych elementów równy **""** (lub **L ""** dla **wchar_t** <strong>\*</strong>) ma zerową długość lub nie jest obsługiwany w bieżących ustawieniach regionalnych. Należy pamiętać, że **decimal_point** i **_W_decimal_point** są zawsze obsługiwane i o niezerowej długości.

Składowe **znaku** struktury są małymi nieujemnymi liczbami, a nie znakami. Wszystkie te, które są równe **CHAR_MAX** , nie są obsługiwane w bieżących ustawieniach regionalnych.

Wartości **grupowania** i **mon_grouping** są interpretowane zgodnie z następującymi regułami:

- **CHAR_MAX** — nie wykonuj żadnych dalszych grup.

- 0 — użyj poprzedniego elementu dla każdej z pozostałych cyfr.

- *n* -liczba cyfr tworzących bieżącą grupę. Następny element jest sprawdzany w celu określenia rozmiaru następnej grupy cyfr przed bieżącą grupą.

Wartości dla **int_curr_symbol** są interpretowane zgodnie z następującymi regułami:

- Pierwsze trzy znaki określają alfabetyczny symbol waluty międzynarodowej zgodnie z definicją w *kodzie ISO 4217 dla reprezentacji standardu walutowego i środków pieniężnych* .

- Czwarty znak (bezpośrednio poprzedzający znak null) oddziela Międzynarodowy symbol waluty od ilości pieniężnej.

Wartości dla **p_cs_precedes** i **n_cs_precedes** są interpretowane zgodnie z następującymi regułami (reguła **n_cs_precedes** jest w nawiasach):

- 1 — symbol waluty jest następujący: wartość dla nieujemnej (ujemnej) sformatowanej wartości pieniężnej.

- Symbol 1-Walutowy poprzedza wartość nieujemnej (ujemnej) sformatowanej wartości pieniężnej.

Wartości dla **p_sep_by_space** i **n_sep_by_space** są interpretowane zgodnie z następującymi regułami (reguła **n_sep_by_space** jest w nawiasach):

- Symbol 0-walutowy jest oddzielony od wartości przez spację dla nieujemnej (ujemnej) sformatowanej wartości pieniężnej.

- 1 — nie ma odstępu między symbolem waluty a wartością nieujemnej (ujemnej) sformatowanej wartości pieniężnej.

Wartości dla **p_sign_posn** i **n_sign_posn** są interpretowane zgodnie z następującymi regułami:

- 0 — nawiasy — liczba przestrzenny i symbol waluty.

- ciąg znaków 1 poprzedza liczbę i symbol waluty.

- 2 — ciąg znaków jest następujący: ilość i symbol waluty.

- 3 — ciąg znaków bezpośrednio poprzedza symbol waluty.

- 4 — ciąg znaku bezpośrednio następuje po symbolu waluty.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
