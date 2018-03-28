---
title: _itoa —, _itow — funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a471e0df86dbfd5e8c267c463684a088b400863
ms.sourcegitcommit: 604907f77eb6c5b1899194a9877726f3e8c2dabc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="itoa-itoa-ltoa-ltoa-ultoa-ultoa-i64toa-ui64toa-itow-ltow-ultow-i64tow-ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Konwertuje liczbę całkowitą na ciąg. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_itoa_s —, funkcje _itow_s —](../../c-runtime-library/reference/itoa-s-itow-s.md).

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
Numer do skonwertowania.

*buffer*<br/>
Bufor przechowujący wynik konwersji.

*radix*<br/>
Podstawa do użycia na potrzeby konwersji *wartość*, która musi być w zakresie od 2 36.

*Rozmiar*<br/>
Długość buforu w jednostkach typu znaków. Ten parametr jest wywnioskowany na podstawie *buforu* argument w języku C++.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji, zwraca wskaźnik do *buforu*. Nie ma żadnych zwracany błąd.

## <a name="remarks"></a>Uwagi

`_itoa`, `_ltoa`, `_ultoa`, `_i64toa`, I `_ui64toa` funkcji konwertuje cyfr z danym *wartość* argumentu na ciąg znaków zakończony znakiem null i zapisać wynik (maksymalnie 33 znaki dla `_itoa`, `_ltoa`, i `_ultoa`i 65 dla `_i64toa` i `_ui64toa`) w *buforu*. Jeśli *radix* równa 10 i *wartość* jest ujemna, pierwszego znaku ciągu przechowywanych jest znak minus (**-**). `_itow`, `_ltow`, `_ultow`, `_i64tow`, I `_ui64tow` funkcje są wersje znaków dwubajtowych `_itoa`, `_ltoa`, `_ultoa`, `_i64toa`, i `_ui64toa`odpowiednio.

> [!IMPORTANT]
> Funkcje te można napisać poza koniec buforu, który jest za mały. Aby uniknąć przepełnienia buforu, upewnij się, że *buforu* jest wystarczająco duży, aby pomieścić przekonwertowanego cyfr oraz końcowego znaku null i znak. Nieprawidłowe użycie tych funkcji mogą powodować problemy zabezpieczenia w kodzie.

Ze względu na ich potencjalnych problemów z zabezpieczeniami, domyślnie, te funkcje powodują ostrzeżenie [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **tej funkcji lub zmienna może być niebezpieczne. Należy rozważyć użycie** *safe_function* **zamiast tego. Aby wyłączyć amortyzacja, należy użyć _CRT_SECURE_NO_WARNINGS.** Zaleca się zmienić kod źródłowy, aby używał *safe_function* zasugerowany przez komunikat ostrzegawczy. Funkcje bezpieczniejsze nie zapisuj więcej znaków niż określony rozmiar buforu. Aby uzyskać więcej informacji, zobacz [_itoa_s —, funkcje _itow_s —](../../c-runtime-library/reference/itoa-s-itow-s.md).

Aby korzystać z tych funkcji bez ostrzeżenia dotyczące zaniechania, zdefiniuj **_CRT_SECURE_NO_WARNINGS** makro preprocesora przed dołączeniem wszelkie nagłówki CRT. Można to zrobić w wierszu polecenia w wierszu polecenia dewelopera, dodając **/D_CRT_SECURE_NO_WARNINGS** — opcja kompilatora do **cl** polecenia. W przeciwnym razie należy zdefiniować makra w plikach źródłowych. Jeśli używasz prekompilowanych nagłówków, zdefiniuj makra w górnej części prekompilowany nagłówek pliku, zwykle stdafx.h dołączenia. Aby zdefiniować makra w kodzie źródłowym, należy użyć **#define** dyrektywy przed wprowadzeniem nagłówek dowolnej CRT, jak w poniższym przykładzie:

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

W języku C++ te funkcje mają przeciążenia szablonów, które wywołują ich odpowiedniki bezpieczniejsze. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

Nazwy Posix `itoa`, `ltoa`, i `ultoa` istnieje jako aliasów `_itoa`, `_ltoa`, i `_ultoa` funkcji. Nazwy Posix są przestarzałe, ponieważ nie wykonuj konkretnej implementacji funkcji konwencji nazw ISO c. Domyślnie te funkcje powodują ostrzeżenie [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **POSIX nazwę tego elementu jest przestarzałe. Zamiast tego użyj nazwy zgodność ISO C i C++:** *nowa_nazwa*. Zaleca się zmiany kodu źródłowego na używanie bezpieczniejsze wersji tych funkcji, `_itoa_s`, `_ltoa_s`, lub `_ultoa_s`. Aby uzyskać więcej informacji, zobacz [_itoa_s —, funkcje _itow_s —](../../c-runtime-library/reference/itoa-s-itow-s.md).

Przenośność kodu źródłowego można zachować nazw Posix w kodzie. Aby korzystać z tych funkcji bez ostrzeżenia dotyczące zaniechania, zdefiniuj zarówno **_CRT_NONSTDC_NO_WARNINGS** i **_CRT_SECURE_NO_WARNINGS** makra preprocesora przed dołączeniem wszelkie nagłówki CRT. Można to zrobić w wierszu polecenia w wierszu polecenia dewelopera, dodając **/D_CRT_SECURE_NO_WARNINGS** i **/D_CRT_NONSTDC_NO_WARNINGS** opcji kompilatora **cl**polecenia. W przeciwnym razie należy zdefiniować makra w plikach źródłowych. Jeśli używasz prekompilowanych nagłówków, zdefiniuj dostępne są następujące makra w górnej części prekompilowany nagłówek pliku, zwykle stdafx.h. Aby zdefiniować makra w kodzie źródłowym, należy użyć **#define** dyrektywy przed wprowadzeniem nagłówek dowolnej CRT, jak w poniższym przykładzie:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Konwersja maksymalna liczba makra

Ułatwiające tworzenie bezpiecznej buforów dla konwersji, CRT zawiera niektóre wygodny makra. Te zdefiniować rozmiar buforu wymaganych do przekonwertowania najdłuższym możliwa wartość każdego typu Liczba całkowita, włącznie z terminatorem null i zaloguj się znak, dla kilku wspólnej bazy. W celu zapewnienia wystarczająco duże, aby odbierać wszelkiej konwersji w podstawowym określonego przez użytkownika buforu konwersji *radix*, użyj jednej z tych zdefiniowanego makra podczas alokacji buforu. Pozwala to zapobiec błędy przepełnienia buforu podczas konwersji typów całkowitych na ciągi. Następujące makra są definiowane po dołączeniu stdlib.h lub wchar.h w źródle.

Użycia jednej z tych makr w funkcji konwersji ciągu, deklarowanie z buforu konwersji typu odpowiedni znak i użyj wartości makra dla typu Liczba całkowita i base jako wymiar buforu. Poniższa tabela zawiera makra, które są odpowiednie dla każdej funkcji dla zasad wymienione:

||||
|-|-|-|
|Funkcje|radix|Makra|
|`_itoa`, `_itow`|16<br/>10<br/>8<br/>2|`_MAX_ITOSTR_BASE16_COUNT`<br/>`_MAX_ITOSTR_BASE10_COUNT`<br/>`_MAX_ITOSTR_BASE8_COUNT`<br/>`_MAX_ITOSTR_BASE2_COUNT`|
|`_ltoa`, `_ltow`|16<br/>10<br/>8<br/>2|`_MAX_LTOSTR_BASE16_COUNT`<br/>`_MAX_LTOSTR_BASE10_COUNT`<br/>`_MAX_LTOSTR_BASE8_COUNT`<br/>`_MAX_LTOSTR_BASE2_COUNT`|
|`_ultoa`, `_ultow`|16<br/>10<br/>8<br/>2|`_MAX_ULTOSTR_BASE16_COUNT`<br/>`_MAX_ULTOSTR_BASE10_COUNT`<br/>`_MAX_ULTOSTR_BASE8_COUNT`<br/>`_MAX_ULTOSTR_BASE2_COUNT`|
|`_i64toa`, `_i64tow`|16<br/>10<br/>8<br/>2|`_MAX_I64TOSTR_BASE16_COUNT`<br/>`_MAX_I64TOSTR_BASE10_COUNT`<br/>`_MAX_I64TOSTR_BASE8_COUNT`<br/>`_MAX_I64TOSTR_BASE2_COUNT`|
|`_ui64toa`, `_ui64tow`|16<br/>10<br/>8<br/>2|`_MAX_U64TOSTR_BASE16_COUNT`<br/>`_MAX_U64TOSTR_BASE10_COUNT`<br/>`_MAX_U64TOSTR_BASE8_COUNT`<br/>`_MAX_U64TOSTR_BASE2_COUNT`|

W tym przykładzie użyto makro Liczba konwersji do definiowania buforu wystarczająco duży, aby zawierała **unsigned long long** w podstawowej 2:

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
|`_itot`|`_itoa`|`_itoa`|`_itow`|
|`_ltot`|`_ltoa`|`_ltoa`|`_ltow`|
|`_ultot`|`_ultoa`|`_ultoa`|`_ultow`|
|`_i64tot`|`_i64toa`|`_i64toa`|`_i64tow`|
|`_ui64tot`|`_ui64toa`|`_ui64toa`|`_ui64tow`|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`itoa`, `ltoa`, `ultoa`|\<stdlib.h>|
|`_itoa`, `_ltoa`, `_ultoa`, `_i64toa`, `_ui64toa`|\<stdlib.h>|
|`_itow`, `_ltow`, `_ultow`, `_i64tow`, `_ui64tow`|\<stdlib.h > lub \<wchar.h >|

Te funkcje i makra są specyficzne dla firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono użycie niektórych funkcji konwersja liczby całkowitej. Zwróć uwagę na użycie **_CRT_SECURE_NO_WARNINGS** makro o wyłączeniu ostrzeżenie C4996.

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
[_itoa_s —, _itow_s — funkcje](../../c-runtime-library/reference/itoa-s-itow-s.md)<br/>
