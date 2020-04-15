---
title: funkcje _itoa, _itow
ms.date: 4/2/2020
api_name:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- _o__i64toa
- _o__i64tow
- _o__itoa
- _o__itow
- _o__ltoa
- _o__ltow
- _o__ui64toa
- _o__ui64tow
- _o__ultoa
- _o__ultow
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
ms.openlocfilehash: 0cc084076c5e39843ecc1afa08671ce6b2f06d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342703"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Konwertuje całkowitą na ciąg. Dostępne są bezpieczniejsze wersje tych funkcji; zobacz [_itoa_s, _itow_s funkcje](itoa-s-itow-s.md).

## <a name="syntax"></a>Składnia

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These POSIX versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>Parametry

*value*<br/>
Liczba do konwersji.

*Buforu*<br/>
Bufor, który przechowuje wynik konwersji.

*Podstawa*<br/>
Podstawa do konwersji *wartości,* która musi być w zakresie 2-36.

*Rozmiar*<br/>
Długość buforu w jednostkach typu znaku. Ten parametr jest wywnioskowany z argumentu *buforu* w języku C++.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do *buforu*. Nie ma zwracania błędów.

## <a name="remarks"></a>Uwagi

Funkcje **_itoa** **, _ltoa**, **_ultoa**, **_i64toa**i **_ui64toa** konwertują cyfry danego *argumentu wartości* na ciąg znaków zakończony zerem i przechowują wynik (maksymalnie 33 znaki dla **_itoa,** **_ltoa**i **_ultoa**oraz 65 dla **_i64toa** i **_ui64toa)** w *buforze*. Jeśli *radix* jest równy 10, a *wartość* ujemna, pierwszym**-** znakiem zapisanego ciągu jest znak minus ( ). Funkcje **_itow,** **_ltow,** **_ultow,** **_i64tow**i **_ui64tow** są odpowiednio szerokoznakowymi wersjami **_itoa,** **_ltoa,** **_ultoa,** **_i64toa**i **_ui64toa.**

> [!IMPORTANT]
> Te funkcje można zapisywać poza koniec buforu, który jest zbyt mały. Aby zapobiec przekroczeniu buforu, upewnij się, że *bufor* jest wystarczająco duży, aby pomieścić przekonwertowane cyfry oraz końcowego znaku null i znaku. Niewłaściwe użycie tych funkcji może spowodować poważne problemy z zabezpieczeniami w kodzie.

Ze względu na ich potencjał problemów z zabezpieczeniami, domyślnie te funkcje powodują ostrzeżenie o wycofanie [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Ta funkcja lub zmienna może być niebezpieczna. Zamiast tego należy rozważyć użycie** *safe_function.* ** Aby wyłączyć wycofanie, użyj _CRT_SECURE_NO_WARNINGS.** Zaleca się zmianę kodu źródłowego, aby użyć *safe_function* sugerowane przez komunikat ostrzegawczy. Bardziej bezpieczne funkcje nie zapisują więcej znaków niż określony rozmiar buforu. Aby uzyskać więcej informacji, zobacz [_itoa_s, _itow_s funkcje](itoa-s-itow-s.md).

Aby użyć tych funkcji bez ostrzeżenia o deprecation, należy zdefiniować makro preprocesora **_CRT_SECURE_NO_WARNINGS** przed dołączeniem nagłówków CRT. Można to zrobić w wierszu polecenia w wierszu polecenia dewelopera, dodając opcję **kompilatora /D_CRT_SECURE_NO_WARNINGS** do polecenia **cl.** W przeciwnym razie zdefiniuj makro w plikach źródłowych. Jeśli używasz wstępnie skompilowanych nagłówków, zdefiniuj makro u góry wstępnie skompilowanego nagłówka include file, *pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych). Aby zdefiniować makro w kodzie źródłowym, należy użyć **dyrektywy #define** przed dołączeniem dowolnego nagłówka CRT, jak w tym przykładzie:

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują ich odpowiedniki bezpieczniejsze. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Posix nazwy **itoa**, **ltoa**i **ultoa** istnieją jako aliasy dla **_itoa,** **_ltoa**i **_ultoa** funkcji. Nazwy POSIX są przestarzałe, ponieważ nie są zgodne z konwencjami nazw funkcji globalnych specyficznych dla implementacji iso C. Domyślnie te funkcje powodują ostrzeżenie o usunięciu [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Nazwa POSIX dla tego elementu jest przestarzała. Zamiast tego należy użyć nazwy zgodności ISO C i C++:** *new_name*. Zalecamy zmianę kodu źródłowego w celu korzystania z bezpieczniejszych wersji tych funkcji, **_itoa_s** **, _ltoa_s**lub **_ultoa_s**. Aby uzyskać więcej informacji, zobacz [_itoa_s, _itow_s funkcje](itoa-s-itow-s.md).

W celu przenoszenia kodu źródłowego można zachować nazwy POSIX w kodzie. Aby użyć tych funkcji bez ostrzeżenia o deprecation, przed dołączeniem nagłówków CRT należy zdefiniować zarówno **makra preprocesora _CRT_NONSTDC_NO_WARNINGS,** jak i **_CRT_SECURE_NO_WARNINGS.** Można to zrobić w wierszu polecenia w wierszu polecenia dewelopera, dodając **/D_CRT_SECURE_NO_WARNINGS** i **/D_CRT_NONSTDC_NO_WARNINGS** opcje kompilatora do polecenia **cl.** W przeciwnym razie zdefiniuj makra w plikach źródłowych. Jeśli używasz wstępnie skompilowanych nagłówków, zdefiniuj makra u góry wstępnie skompilowanego nagłówka dołączanego pliku. Aby zdefiniować makra w kodzie źródłowym, należy użyć **dyrektyw #define** przed dołączeniem dowolnego nagłówka CRT, jak w tym przykładzie:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Maksymalna liczba makr konwersji

Aby ułatwić tworzenie bezpiecznych buforów dla konwersji, CRT zawiera kilka wygodnych makr. Określają one rozmiar buforu wymaganego do konwersji najdłuższej możliwej wartości każdego typu liczby całkowitej, w tym znaku zerowego i znaku, dla kilku wspólnych podstaw. Aby upewnić się, że bufor konwersji jest wystarczająco duży, aby otrzymać konwersję w bazie określonej przez *radix,* użyj jednego z tych zdefiniowanych makr podczas przydzielania buforu. Pomaga to zapobiec błędom przepełnienia buforu podczas konwertowania typów całkowitych na ciągi. Te makra są definiowane po dodaniu do źródła pliku stdlib.h lub wchar.h.

Aby użyć jednego z tych makr w funkcji konwersji ciągu, zadeklaruj bufor konwersji odpowiedniego typu znaku i użyj wartości makra dla typu i podstawy całkowitej jako wymiaru buforu. W tej tabeli wymieniono makra odpowiednie dla każdej funkcji dla wymienionych baz:

||||
|-|-|-|
|Funkcje|Podstawa|Makra|
|**_itoa** **, _itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa** **, _ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa** **, _ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

W tym przykładzie użyto makra liczby konwersji do zdefiniowania buforu wystarczająco dużego, aby zawierał **niepodpisaną długą długość** w podstawie 2:

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**itoa**, **ltoa**, **ultoa**|\<>|
|**_itoa** **, _ltoa,** **_ultoa,** **_i64toa,** **_ui64toa**|\<>|
|**_itow** **, _ltow,** **_ultow,** **_i64tow,** **_ui64tow**|\<> lub \<wchar.h>|

Te funkcje i makra są specyficzne dla firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie pokazano użycie niektórych funkcji konwersji liczby całkowitej. Należy zwrócić uwagę na użycie **makra _CRT_SECURE_NO_WARNINGS** do wyciszenia ostrzeżenia C4996.

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[funkcje _itoa_s, _itow_s](itoa-s-itow-s.md)<br/>
