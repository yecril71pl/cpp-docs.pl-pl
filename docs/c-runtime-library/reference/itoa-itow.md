---
title: _itoa —, _itow — funkcje
ms.date: 03/21/2018
apiname:
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: 016f3474345b623415be9fe33556bb9f466542ad
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210539"
---
# <a name="itoa-itoa-ltoa-ltoa-ultoa-ultoa-i64toa-ui64toa-itow-ltow-ultow-i64tow-ui64tow"></a>itoa — _itoa —, ltoa —, _ltoa —, ultoa —, _ultoa —, _i64toa —, _ui64toa —, _itow —, _ltow —, _ultow —, _i64tow —, _ui64tow —

Konwertuje liczbę całkowitą na ciąg. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_itoa_s —, funkcje _itow_s —](itoa-s-itow-s.md).

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

// These Posix versions of the functions have deprecated names:
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
Numer ma zostać przekonwertowany.

*buffer*<br/>
Bufor, który zawiera wynik konwersji.

*radix*<br/>
Podstawowa na potrzeby konwersji *wartość*, które muszą być z zakresu od 2 do 36.

*Rozmiar*<br/>
Długość buforu w jednostkach typu znaków. Ten parametr jest wnioskowany z *buforu* argument w języku C++.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do *buforu*. Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

**_Itoa —**, **_ltoa —**, **_ultoa —**, **_i64toa —**, i **_ui64toa —** funkcji konwertuje cyfry danego *wartość* argument ciąg znaków zakończony znakiem null, a Magazyn wynik (maksymalnie 33 znaków **_itoa —**, **_ltoa —**, i  **_ultoa —** i 65 dla **_i64toa —** i **_ui64toa —**) w *buforu*. Jeśli *podstawy* jest równa 10 i *wartość* jest ujemna, pierwszym znakiem ciągu przechowywane jest znak minus (**-**). **_Itow —**, **_ltow —**, **_ultow —**, **_i64tow —**, i **_ui64tow —** są funkcje znaków dwubajtowych wersje **_itoa —**, **_ltoa —**, **_ultoa —**, **_i64toa —**, i **_ui64toa —**, odpowiednio.

> [!IMPORTANT]
> Te funkcje można napisać poza końcem bufor, który jest za mały. Aby uniknąć przepełnienia buforu, upewnij się, że *buforu* jest wystarczająco duży, aby pomieścić cyfr przekonwertowany znak plus końcowego znaku null, a znak. Niewłaściwe korzystanie z tych funkcji może spowodować problemy z powodu poważnego naruszenia zabezpieczeń w kodzie.

Ze względu na ich ryzyko związane z zabezpieczeniami, domyślnie, te funkcje spowodować, że ostrzeżenie o zakończeniu obsługi [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Ta funkcja lub zmienna może być niebezpieczne. Należy rozważyć użycie** *safe_function* **zamiast tego. Aby wyłączyć wycofywania, należy użyć _CRT_SECURE_NO_WARNINGS.** Firma Microsoft zaleca zmianę kodu źródłowego do użycia *safe_function* zaproponowana przez komunikat ostrzegawczy. Funkcje bardziej bezpieczne nie zapisują więcej znaków niż określony rozmiar buforu. Aby uzyskać więcej informacji, zobacz [_itoa_s —, funkcje _itow_s —](itoa-s-itow-s.md).

Aby korzystać z tych funkcji bez ostrzeżenie o zakończeniu obsługi, należy zdefiniować **_CRT_SECURE_NO_WARNINGS** makro preprocesora, przed dołączeniem wszelkie nagłówki CRT. Można to zrobić w wierszu polecenia w wierszu polecenia dla deweloperów, dodając **/D_CRT_SECURE_NO_WARNINGS** opcji kompilatora **cl** polecenia. W przeciwnym razie zdefiniuj makro w plikach źródłowych. Jeśli używasz wstępnie skompilowanych nagłówków, zdefiniuj makro, które w górnej części prekompilowanego pliku nagłówkowego dołączyć plik, zwykle w pliku stdafx.h. Aby zdefiniować makro w kodzie źródłowym, należy użyć **#define** dyrektywy przed wprowadzeniem dowolny nagłówek CRT, jak w poniższym przykładzie:

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

W języku C++ funkcje te mają przeciążenia szablonu, które wywołują ich bezpieczniejsze odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

POSIX — nazwy **itoa —**, **ltoa —**, i **ultoa —** istnieje jako aliasów **_itoa —**, **_ltoa —**, i **_ultoa —** funkcji. Nazw Posix są przestarzałe, ponieważ nie podlegają Konwencji nazwy funkcji specyficzne dla implementacji ISO C. Domyślnie, te funkcje spowodować, że ostrzeżenie o zakończeniu obsługi [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Nazwa modelu POSIX dla tego elementu jest przestarzały. Zamiast tego należy użyć nazwy zgodność ISO C i C++:** *nowa_nazwa*. Firma Microsoft zaleca zmianę kodu źródłowego do użycia bezpieczniejsze wersje tych funkcji, **_itoa_s —**, **_ltoa_s —**, lub **_ultoa_s —**. Aby uzyskać więcej informacji, zobacz [_itoa_s —, funkcje _itow_s —](itoa-s-itow-s.md).

Przenośność kodu źródłowego możesz zachować nazw Posix w kodzie. Aby korzystać z tych funkcji bez ostrzeżenie o zakończeniu obsługi, zdefiniuj zarówno **_CRT_NONSTDC_NO_WARNINGS** i **_CRT_SECURE_NO_WARNINGS** makra preprocesora, przed dołączeniem wszelkie nagłówki CRT. Można to zrobić w wierszu polecenia w wierszu polecenia dla deweloperów, dodając **/D_CRT_SECURE_NO_WARNINGS** i **/D_CRT_NONSTDC_NO_WARNINGS** opcji kompilatora, aby **cl**polecenia. W przeciwnym razie zdefiniuj makr w plikach źródłowych. Jeśli używasz wstępnie skompilowanych nagłówków, zdefiniuj plik, zwykle w pliku stdafx.h dostępne są następujące makra w górnej części prekompilowany plik nagłówkowy. Aby zdefiniować makra w kodzie źródłowym, należy użyć **#define** dyrektyw przed wprowadzeniem dowolny nagłówek CRT, jak w poniższym przykładzie:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Makra liczbę maksymalną konwersją

Pomaga tworzyć bezpieczne buforów dla konwersji, CRT obejmuje niektóre wygodne makra. Te może zdefiniować rozmiar buforu wymaganych do przekonwertowania najdłuższy możliwa wartość każdego typu Liczba całkowita, łącznie z terminatorem null, a następnie zaloguj znaków dla kilku typowych zasad. Aby upewnić się, czy usługi buforu konwersji jest wystarczająco duży, aby otrzymać każda konwersja na podstawie określonej przez *podstawy*, użyj jednej z tych zdefiniowanych makra podczas alokacji buforu. Pomaga to zapobiec błędy przepełnienia buforu, podczas konwersji typów całkowitych na ciągi. Te makra są definiowane przy dodawaniu stdlib.h lub wchar.h w źródle.

Aby użyć jednego z tych makr w funkcję konwersji ciągu, Zadeklaruj swoje buforu konwersji typu odpowiedniego znaku i użyj wartości — makro dla typu Liczba całkowita i base jako wymiar buforu. Poniższa tabela zawiera makra, które są odpowiednie dla każdej funkcji dla wymienionych baz:

||||
|-|-|-|
|Funkcje|radix|Makra|
|**_itoa —**, **_itow —**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa —**, **_ltow —**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa —**, **_ultow —**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa —**, **_i64tow —**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa —**, **_ui64tow —**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

W tym przykładzie użyto makr Liczba konwersji do definiowania bufor wystarczająco duży, aby zawierała **unsigned long long** w podstawie 2:

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
|**_itot —**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**itoa**, **ltoa**, **ultoa**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<stdlib.h> or \<wchar.h>|

Te funkcje i makra są specyficzne dla firmy Microsoft. Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Niniejszy przykład pokazuje użycie niektórych funkcji konwersji liczby całkowitej. Zwróć uwagę na użycie **_CRT_SECURE_NO_WARNINGS** makra o wyłączeniu ostrzeżenie C4996.

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

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s —, _itow_s — funkcje](itoa-s-itow-s.md)<br/>
