---
title: localeconv | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- localeconv
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
- localeconv
dev_langs:
- C++
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4e8a20ef31f4379e7ddf6b7425fd7ecc70294a
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42464936"
---
# <a name="localeconv"></a>localeconv

Pobiera szczegółowe informacje na temat ustawień regionalnych.

## <a name="syntax"></a>Składnia

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Wartość zwracana

**localeconv** zwraca wskaźnik do obiektu wypełniane typu [lconv — struktura](../../c-runtime-library/standard-types.md). Wartości zawarte w obiekcie są kopiowane z ustawień regionalnych w lokalny magazyn wątków i może zostać zastąpiona przez kolejne wywołania **localeconv**. Zmiany wprowadzone do wartości w tym obiekcie nie należy modyfikować ustawienia regionalne. Wywołania [setlocale](setlocale-wsetlocale.md) z *kategorii* wartości **LC_ALL**, **LC_MONETARY**, lub **LC_NUMERIC** Zastąp zawartość struktury.

## <a name="remarks"></a>Uwagi

**Localeconv** funkcja pobiera szczegółowe informacje na temat formatowanie liczbowe bieżących ustawień regionalnych. Te informacje są przechowywane w strukturze typu **lconv —**. **Lconv —** struktury, zdefiniowanego w ustawieniach regionalnych. Godz., zawiera następujące składniki:

|Pole|Znaczenie|
|-|-|
decimal_point —,<br/>_W_decimal_point|Wskaźnik na znak na ilości niewalutowych dziesiętny.
thousands_sep —,<br/>_W_thousands_sep|Wskaźnik znaku, który oddziela grup cyfr po lewej stronie przecinka dziesiętnego dla niewalutowych ilości.
grouping|Wskaźnik do **char**-liczba całkowita, która zawiera rozmiar każdej grupy cyfry w ilości niewalutowych wielkości.
int_curr_symbol,<br/>_W_int_curr_symbol|Wskaźnik na symbol waluty międzynarodowych dla bieżących ustawień regionalnych. Pierwsze trzy znaki określić symbol waluty międzynarodowe, zgodnie z definicją w *ISO 4217 kodów dla reprezentacji walut i środków pieniężnych* standardowych. Czwarty znak (bezpośrednio poprzedzającego znaku null) oddziela symbol waluty międzynarodowych od ilości pieniężnych.
currency_symbol,<br/>_W_currency_symbol|Wskaźnik do symbolu waluty lokalnej dla bieżących ustawień regionalnych.
mon_decimal_point,<br/>_W_mon_decimal_point|Wskaźnik do dziesiętnego znak dla ilości pieniężnych.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Wskaźnik do separatora grup cyfr w lewo dziesiętnego w ilościach pieniężnych.
mon_grouping|Wskaźnik do **char**-o rozmiarze liczba całkowita, która zawiera rozmiar każdej grupy cyfry w ilości pieniężnych.
positive_sign —,<br/>_W_positive_sign|Ciąg oznaczający logowania dla nieujemna ilości pieniężnych.
negative_sign —,<br/>_W_negative_sign|Ciąg oznaczający znak ujemny ilości pieniężnych.
int_frac_digits|Liczba cyfr z prawej strony punktu dziesiętnego w wielu krajach sformatowane ilościach pieniężnych.
frac_digits|Liczba cyfr z prawej strony punktu dziesiętnego w ilościach pieniężnych sformatowany.
p_cs_precedes|Wartość 1, jeśli symbol waluty poprzedza wartość nieujemna sformatowane ilość pieniężnych. Wartość 0, jeśli symbol jest zgodna wartość.
p_sep_by_space|Wartość 1, jeśli symbol waluty jest oddzielona od wartości dla nieujemna sformatowane ilości pieniężnych miejsca. W przypadku bez separacji miejsca, należy ustawić na 0.
n_cs_precedes|Wartość 1, jeśli symbol waluty poprzedza wartość sformatowane pieniężnych ujemną. Jeśli symbol wartość zakończy się powodzeniem, należy ustawić na 0.
n_sep_by_space|Wartość 1, jeśli symbol waluty jest oddzielona od wartości sformatowane pieniężnych ujemną miejsca. W przypadku bez separacji miejsca, należy ustawić na 0.
p_sign_posn|Pozycja znaku dodatniego nieujemna sformatowane ilości pieniężnych.
n_sign_posn|Pozycja znaku dodatniego w ilości ujemne pieniężnych sformatowany.

Z wyjątkiem jako członkowie określonej, **lconv —** strukturę, która ma `char *` i `wchar_t *` wersje są wskaźnikami do ciągów. Żadnego z tych, które jest równa **""** (lub **L ""** dla **wchar_t \*** ) jest o zerowej długości lub nie jest obsługiwana przy bieżących ustawieniach regionalnych. Należy pamiętać, że **decimal_point —** i **_W_decimal_point** są zawsze obsługiwane i długości wartość różną od zera.

**Char** elementy członkowskie struktury są małymi liczbami nieujemna nie znaków. Żadnego z tych, które jest równa **CHAR_MAX** nie jest obsługiwana przy bieżących ustawieniach regionalnych.

Wartości **grupowanie** i **mon_grouping** są interpretowane zgodnie z następującymi zasadami:

- **CHAR_MAX** — nie należy wykonywać dalsze grupowania.

- 0 — Użyj poprzedni element dla każdego z pozostałych znaków.

- *n* — liczba cyfr, które tworzą bieżącą grupę. Następny element jest sprawdzane w celu określenia rozmiaru następną grupę cyfr przed bieżącą grupę.

Wartości **int_curr_symbol** są interpretowane zgodnie z następującymi zasadami:

- Pierwsze trzy znaki określić symbol waluty międzynarodowe, zgodnie z definicją w *ISO 4217 kodów dla reprezentacji walut i środków pieniężnych* standardowych.

- Czwarty znak (bezpośrednio poprzedzający znak null) oddziela symbol waluty międzynarodowych od ilości pieniężnych.

Wartości **p_cs_precedes** i **n_cs_precedes** są interpretowane zgodnie z następującymi zasadami ( **n_cs_precedes** reguła znajduje się w nawiasach):

- 0 — symbol waluty jest zgodna wartość nieujemną (negatywna) sformatowaną wartość pieniężną.

- 1 - symbol waluty poprzedza wartość nieujemną (negatywna) sformatowaną wartość pieniężną.

Wartości **p_sep_by_space** i **n_sep_by_space** są interpretowane zgodnie z następującymi zasadami ( **n_sep_by_space** reguła znajduje się w nawiasach):

- 0 — symbol waluty jest oddzielony od wartości przez wpisanie nieujemna (negatywna) sformatowaną wartość pieniężną.

- 1 — Brak Brak oddzielenia przestrzeni symbol waluty i wartość nieujemną (negatywna) sformatowaną wartość pieniężną.

Wartości **p_sign_posn** i **n_sign_posn** są interpretowane zgodnie z następującymi zasadami:

- 0 - nawiasy otaczające symbol ilości i waluty.

- 1 — Logowanie ciągu poprzedza symbol ilości i waluty.

- 2 — ciąg logowanie następuje symbol ilości i waluty.

- 3 - ciąg sign znajdującego się bezpośrednio przed symbolem waluty.

- 4 — logowanie natychmiast ciągu poniżej symbolu waluty.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
