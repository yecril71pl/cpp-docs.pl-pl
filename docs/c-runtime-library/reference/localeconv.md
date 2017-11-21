---
title: "localeconv — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: localeconv
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
apitype: DLLExport
f1_keywords: localeconv
dev_langs: C++
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aa001a4c8dde1337eb576ae3a2c78108e4cb3199
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="localeconv"></a>localeconv
Pobiera szczegółowe informacje na temat ustawień regionalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct lconv *localeconv( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `localeconv`Zwraca wskaźnik do obiektu wypełniane typu [lconv — struktura](../../c-runtime-library/standard-types.md). Wartości zawartych w tym obiekcie są kopiowane z ustawień regionalnych w magazynu wątków lokalnych i mogą zostać zastąpione przez kolejne wywołania `localeconv`. Zmiany wprowadzone do wartości w tym obiekcie nie należy modyfikować ustawienia regionalne. Wywołuje się [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) z `category` wartości `LC_ALL`, `LC_MONETARY`, lub `LC_NUMERIC` zastąpienie zawartości struktury.  
  
## <a name="remarks"></a>Uwagi  
 `localeconv` Funkcja pobiera szczegółowe informacje na temat formatowanie dla bieżących ustawień regionalnych. Te informacje są przechowywane w strukturze typu `lconv`. `lconv` Struktury zdefiniowane w ustawieniach regionalnych. H, zawiera następujące składniki:  
  
 `char *decimal_point, wchar_t *_W_decimal_point`  
 Znak punktu dziesiętnego niewalutowych ilości.  
  
 `char *thousands_sep, wchar_t *_W_thousands_sep`  
 Znak oddzielający grup cyfr w lewą stronę od punktu dziesiętnego niewalutowych ilości.  
  
 `char *grouping`  
 Wskaźnik do `char`— rozmiar całkowitą, która zawiera rozmiar każdej grupie cyfr w niewalutowych ilości.  
  
 `char *int_curr_symbol, wchar_t *_W_int_curr_symbol`  
 Symbol waluty międzynarodowych bieżące ustawienia regionalne. Pierwsze trzy znaki określić symbol waluty międzynarodowych alfabetyczne, zgodnie z definicją w *ISO 4217 kodów dla reprezentacji waluty i funduszy* standardowa. Czwarty (natychmiast poprzedni znak null) rozdziela symbol waluty międzynarodowych od ilości finansowe.  
  
 `char *currency_symbol, wchar_t *_W_currency_symbol`  
 Symbol waluty lokalnej bieżące ustawienia regionalne.  
  
 `char *mon_decimal_point, wchar_t *_W_mon_decimal_point`  
 Znak punktu dziesiętnego dla ilości finansowe.  
  
 `char *mon_thousands_sep, wchar_t *_W_mon_thousands_sep`  
 Separator grup cyfr lewą stronę od przecinka pieniężnego ilości.  
  
 `char *mon_grouping`  
 Wskaźnik do `char`— rozmiar całkowitą, która zawiera rozmiar każdej grupie cyfr w ilości finansowe.  
  
 `char *positive_sign, wchar_t *_W_positive_sign`  
 Parametry określające znak nieujemna ilości finansowe.  
  
 `char *negative_sign, wchar_t *_W_negative_sign`  
 Ciąg oznaczający znak ilości pieniężnego ujemne.  
  
 `char int_frac_digits`  
 Liczba cyfr prawo dziesiętnego międzynarodowych sformatowany ilości finansowe.  
  
 `char frac_digits`  
 Liczba cyfr prawo dziesiętnego sformatowany ilości finansowe.  
  
 `char p_cs_precedes`  
 Wartość 1, jeśli wartość nieujemna sformatowany ilość pieniężnego poprzedza symbol waluty. Wartość 0, jeśli symbol następuje po wartości.  
  
 `char p_sep_by_space`  
 Wartość 1, jeśli symbol waluty jest oddzielona od wartości dla nieujemna sformatowany pieniężnego ilości miejsca. Ustawiona na 0, jeśli istnieje bez spacji miejsca.  
  
 `char n_cs_precedes`  
 Wartość 1, jeśli symbol waluty poprzedza wartość sformatowany pieniężnego ujemną. Wartość 0, jeśli symbol wartość zakończy się pomyślnie.  
  
 `char n_sep_by_space`  
 Wartość 1, jeśli symbol waluty jest oddzielona od wartości dla sformatowanego pieniężnego ujemną miejsca. Ustawiona na 0, jeśli istnieje bez spacji miejsca.  
  
 `char p_sign_posn`  
 Położenie znaku dodatnią nieujemna sformatowany ilości finansowe.  
  
 `char n_sign_posn`  
 Położenie znaku dodatnią wartością ujemną sformatowany ilości finansowe.  
  
Z wyjątkiem członków określonej, `lconv` struktury, która ma `char *` i `wchar_t *` wersje są wskaźnikami do ciągów. Żadnego z tych, które jest równe `""` (lub `L""` dla `wchar_t *`) jest o zerowej długości lub nie jest obsługiwana w bieżących ustawień regionalnych. Należy pamiętać, że `decimal_point` i `_W_decimal_point` są zawsze obsługiwane i niezerową długość.  
  
`char` Małych nieujemna cyfry, znaki nie są elementy członkowskie struktury. Żadnego z tych, które jest równe `CHAR_MAX` nie jest obsługiwany w bieżących ustawień regionalnych.  
  
Wartości `grouping` i `mon_grouping` interpretowania zgodnie z następującymi zasadami:  
  
- `CHAR_MAX`-Nie wykonuj żadnych dalszych grupowanie.  
  
- 0 - Użyj poprzedniego elementu, dla każdej z pozostałych znaków.  
  
- *n*-Liczba cyfr, które składają się na bieżącej grupie. Następny element jest sprawdzony w celu określenia rozmiaru następnej grupy cyfr przed bieżącą grupę.  
  
Wartości `int_curr_symbol` interpretowania zgodnie z następującymi zasadami:  
  
-   Pierwsze trzy znaki określić symbol waluty międzynarodowych alfabetyczne, zgodnie z definicją w *ISO 4217 kodów dla reprezentacji waluty i funduszy* standardowa.  
  
-   Czwarty znak (bezpośrednio przed znakiem pustym) oddziela symbol waluty międzynarodowych od ilości finansowe.  
  
Wartości `p_cs_precedes` i `n_cs_precedes` interpretowania zgodnie z następującymi zasadami ( `n_cs_precedes` reguła jest w nawiasach):  
  
- 0 — symbol waluty następuje wartość nieujemną (ujemne) sformatowany finansowe.  
  
- 1 - symbol waluty poprzedza wartość nieujemną (ujemne) sformatowany finansowe.  
  
Wartości `p_sep_by_space` i `n_sep_by_space` interpretowania zgodnie z następującymi zasadami ( `n_sep_by_space` reguła jest w nawiasach):  
  
- 0 — symbol waluty jest oddzielona od wartości przez wpisanie nieujemna (ujemnej) sformatowany wartości walutowej.  
  
- 1 - nie ma żadnych rozdzielenie miejsca symbol waluty, a wartość nieujemną (ujemnej) sformatowany wartości walutowej.  
  
Wartości `p_sign_posn` i `n_sign_posn` interpretowania zgodnie z następującymi zasadami:  
  
- 0 - nawiasy otaczające symbol ilości i waluty.  
  
- 1 - Ciąg znak poprzedza symbol ilości i waluty.  
  
- 2 - ciąg znak następuje symbol ilości i waluty.  
  
- 3 - ciąg znak bezpośrednio poprzedza symbol waluty.  
  
- 4 - znak natychmiast ciągu symbol waluty w następujący sposób.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`localeconv`|\<Locale.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [setLocale](../../preprocessor/setlocale.md)   
 [strcoll — funkcje](../../c-runtime-library/strcoll-functions.md)   
 [strftime —, wcsftime —, _strftime_l — _wcsftime_l —](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm —, wcsxfrm —, _strxfrm_l — _wcsxfrm_l —](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)