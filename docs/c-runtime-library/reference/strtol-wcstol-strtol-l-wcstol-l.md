---
title: ':::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::'
ms.date: 4/2/2020
api_name:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- '_o_:::no-loc(_strtol_l):::'
- '_o_:::no-loc(_wcstol_l):::'
- '_o_:::no-loc(strtol):::'
- '_o_:::no-loc(wcstol):::'
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(strtol):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_tcstol_l):::'
helpviewer_keywords:
- ':::no-loc(wcstol)::: function'
- :::no-loc(wcstol):::_l function
- ':::no-loc(_tcstol)::: function'
- string conversion, to integers
- tcstol function
- :::no-loc(strtol):::_l function
- ':::no-loc(_wcstol_l)::: function'
- ':::no-loc(_strtol_l)::: function'
- ':::no-loc(strtol)::: function'
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(LONG_MAX):::'
- ':::no-loc(LONG_MIN):::'
- ':::no-loc(errno):::'
- ':::no-loc(ERANGE):::'
- ':::no-loc(EINVAL):::'
- ':::no-loc(LC_NUMERIC):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(_tcstol_l):::'
- ':::no-loc(localeconv):::'
- ':::no-loc(setlocale):::'
- ':::no-loc(_wsetlocale):::'
- ':::no-loc(strtod):::'
- ':::no-loc(_strtod_l):::'
- ':::no-loc(wcstod):::'
- ':::no-loc(_wcstod_l):::'
- ':::no-loc(strtoll):::'
- ':::no-loc(_strtoll_l):::'
- ':::no-loc(wcstoll):::'
- ':::no-loc(_wcstoll_l):::'
- ':::no-loc(strtoul):::'
- ':::no-loc(_strtoul_l):::'
- ':::no-loc(wcstoul):::'
- ':::no-loc(_wcstoul_l):::'
- ':::no-loc(atof):::'
- ':::no-loc(_atof_l):::'
- ':::no-loc(_wtof):::'
- ':::no-loc(_wtof_l):::'
ms.openlocfilehash: a5265b434f14f299532d6f5ebb65c83d75ea63ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232407"
---
# <a name="no-locstrtol-no-locwcstol-no-loc_strtol_l-no-loc_wcstol_l"></a>:::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::

Konwertuje ciągi na **`long`** wartość całkowitą.

## <a name="syntax"></a>Składnia

```C
long :::no-loc(strtol):::(
   const char *string,
   char **end_ptr,
   int base
);
long :::no-loc(wcstol):::(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long :::no-loc(_strtol_l):::(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long :::no-loc(_wcstol_l):::(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*parametry*\
Ciąg zakończony znakiem null do przekonwertowania.

*end_ptr*\
Parametr wyjściowy, ustawiony na wartość wskaż znak po ostatnim interpretowanym znaku. Ignorowany, jeśli **wartość jest równa null**.

*opiera*\
Numer bazowy do użycia.

*ustawienie*\
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**:::no-loc(strtol):::**, **:::no-loc(wcstol):::** , **:::no-loc(_strtol_l):::** i **:::no-loc(_wcstol_l):::** zwracają wartość reprezentowaną w *ciągu*. Zwraca wartość 0, jeśli konwersja nie jest możliwa. Gdy reprezentacja spowoduje przepełnienie, zwracają **:::no-loc(LONG_MAX):::** lub **:::no-loc(LONG_MIN):::** .

**:::no-loc(errno):::** jest ustawiona na wartość **:::no-loc(ERANGE):::** , jeśli występuje przepełnienie lub nadmiar. Jest ustawiona na **:::no-loc(EINVAL):::** Jeśli *ciąg* ma **wartość null**. Lub, jeśli wartość *podstawowa* jest różna od zera i mniejsza niż 2 lub większa niż 36. Aby uzyskać więcej informacji na temat **:::no-loc(ERANGE):::** , **:::no-loc(EINVAL):::** i innych kodów powrotnych, zobacz [_dos :::no-loc(errno)::: , :::no-loc(errno)::: , _sys_errlist i _sys_nerr](../../c-runtime-library/:::no-loc(errno):::-dos:::no-loc(errno):::-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**:::no-loc(strtol):::** Funkcje, **:::no-loc(wcstol):::** , **:::no-loc(_strtol_l):::** i **:::no-loc(_wcstol_l):::** konwertują *ciąg* na **`long`** . Nie mogą oni przetrzymywać odczytywania *ciągu* przy pierwszym znaku, który nie jest rozpoznawany jako część liczby. Może to być znak kończący o wartości null lub pierwszy znak alfanumeryczny większy lub równy *Base*.

**:::no-loc(wcstol):::** i **:::no-loc(_wcstol_l):::** są wersjami znaków dwubajtowych **:::no-loc(strtol):::** i **:::no-loc(_strtol_l):::** . *Ciąg* znaków dwubajtowych jest ciągiem szerokim. Funkcje te zachowują się identycznie z **:::no-loc(strtol):::** i **:::no-loc(_strtol_l):::** w inny sposób. **:::no-loc(LC_NUMERIC):::** Ustawienie kategorii ustawień regionalnych określa rozpoznawanie znaku podstawy (znacznik Ułamkowy lub dziesiętny) w *ciągu*. Funkcje **:::no-loc(strtol):::** i **:::no-loc(wcstol):::** używają bieżących ustawień regionalnych. **:::no-loc(_strtol_l):::** i **:::no-loc(_wcstol_l):::** zamiast tego użyj przekazaną wartość ustawienia regionalne. Aby uzyskać więcej informacji, zobacz [ :::no-loc(setlocale)::: ] i [Ustawienia regionalne](../../c-runtime-library/locale.md).

Gdy *end_ptr* ma **wartość null**, jest ignorowana. W przeciwnym razie wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji wskazywanej przez *end_ptr*. Konwersja nie jest możliwa, jeśli nie odnaleziono prawidłowych cyfr lub określono nieprawidłową podstawę. Wartość *ciągu* jest następnie przechowywana w lokalizacji wskazywanej przez *end_ptr*.

**:::no-loc(strtol):::** oczekuje, że *ciąg* ma wskazywać ciąg o następującej postaci:

> [*odstęp*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*alfanumeryczne*]

Nawiasy kwadratowe ( `[ ]` ) otaczają opcjonalne elementy. Nawiasy klamrowe i pionowy pasek ( `{ | }` ) otaczają alternatywy dla pojedynczego elementu. *odstępy* mogą zawierać spacje i znaki tabulacji, które są ignorowane. *alfanumeryczne* są cyframi dziesiętnymi lub literami od "a" do "z" (lub od "a" do "z"). Pierwszy znak, który nie pasuje do tego formularza, zatrzyma skanowanie. Jeśli *baza* jest z przedziału od 2 do 36, jest używana jako podstawa liczby. Jeśli *Base* ma wartość 0, początkowe znaki ciągu wskazywane przez *ciąg* są używane do określenia podstawy. Jeśli pierwszym znakiem jest 0, a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako Szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "a" do "z" (lub "A" do "z") mają przypisane wartości od 10 do 35. Skanowanie zezwala tylko na litery, których wartości są mniejsze niż *podstawowe*. Pierwszy znak poza zakresem podstawy powoduje zatrzymanie skanowania. Na przykład załóżmy, że *ciąg* rozpoczyna się od "01". Jeśli *Base* ma wartość 0, skaner zakłada, że jest to ósemkowa liczba całkowita. Znak "8" lub "9" uniemożliwia skanowanie.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**:::no-loc(_tcstol):::**|**:::no-loc(strtol):::**|**:::no-loc(strtol):::**|**:::no-loc(wcstol):::**|
|**:::no-loc(_tcstol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_wcstol_l):::**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**:::no-loc(strtol):::**|\<stdlib.h>|
|**:::no-loc(wcstol):::**|\<stdlib.h> lub \<wchar.h>|
|**:::no-loc(_strtol_l):::**|\<stdlib.h>|
|**:::no-loc(_wcstol_l):::**|\<stdlib.h> lub \<wchar.h>|

**:::no-loc(_strtol_l):::** Funkcje i **:::no-loc(_wcstol_l):::** są specyficzne dla firmy Microsoft, nie jest częścią standardowej biblioteki C. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [:::no-loc(strtod):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md) .

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../data-conversion.md)\
[Ustawienie](../locale.md)\
[:::no-loc(localeconv):::](:::no-loc(localeconv):::.md)\
[:::no-loc(setlocale):::, :::no-loc(_wsetlocale):::](:::no-loc(setlocale):::-w:::no-loc(setlocale):::.md)\
[Funkcje ciągu do wartości numerycznych](../string-to-numeric-value-functions.md)\
[:::no-loc(strtod):::, :::no-loc(_strtod_l):::, :::no-loc(wcstod):::, :::no-loc(_wcstod_l):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md)\
[:::no-loc(strtoll):::, :::no-loc(_strtoll_l):::, :::no-loc(wcstoll):::, :::no-loc(_wcstoll_l):::](:::no-loc(strtoll):::-:::no-loc(strtoll):::-l-:::no-loc(wcstoll):::-:::no-loc(wcstoll):::-l.md)\
[:::no-loc(strtoul):::, :::no-loc(_strtoul_l):::, :::no-loc(wcstoul):::, :::no-loc(_wcstoul_l):::](:::no-loc(strtoul):::-:::no-loc(strtoul):::-l-:::no-loc(wcstoul):::-:::no-loc(wcstoul):::-l.md)\
[:::no-loc(atof):::, :::no-loc(_atof_l):::, :::no-loc(_wtof):::, :::no-loc(_wtof_l):::](:::no-loc(atof):::-:::no-loc(atof):::-l-wtof-wtof-l.md)
