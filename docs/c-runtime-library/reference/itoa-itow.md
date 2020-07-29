---
title: _itoa, funkcje _itow
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 28e6e2300c96e6236ffc4fd927d8153a1f8bcd13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216937"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Konwertuje liczbę całkowitą na ciąg. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_itoa_s, _itow_s funkcje](itoa-s-itow-s.md).

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

*wartościami*<br/>
Liczba do przekonwertowania.

*buforu*<br/>
Bufor, który przechowuje wynik konwersji.

*podstawy*<br/>
Baza, która ma zostać użyta do konwersji *wartości*, która musi znajdować się w zakresie 2-36.

*zmienia*<br/>
Długość buforu w jednostkach typu znaku. Ten parametr jest wywnioskowany na podstawie argumentu *buforu* w języku C++.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do *buforu*. Brak powrotu błędu.

## <a name="remarks"></a>Uwagi

Funkcje **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**i **_ui64toa** konwertują cyfry danego argumentu *wartości* na ciąg znaków zakończony znakiem null i przechowują wynik (do 33 znaków dla **_itoa**, **_ltoa**i **_ultoa**oraz 65 dla **_i64toa** i **_ui64toa**) w *buforze*. Jeśli *podstawy* jest równe 10, a *wartość* jest ujemna, pierwszy znak przechowywanego ciągu jest znakiem minus ( **-** ). **_Itow**, **_ltow**, **_ultow**, **_i64tow**i **_ui64tow** są wersjami znaków dwubajtowych **_itoa**, **_ltoa**, _ultoa, **_ultoa** **_i64toa**i **_ui64toa**.

> [!IMPORTANT]
> Te funkcje mogą zapisywać poza końcem bufora, który jest zbyt mały. Aby zapobiec przepełnieniu buforów, upewnij się, że *bufor* jest wystarczająco duży, aby pomieścić przekonwertowane cyfry oraz końcowy znak null i znak. Użycie tych funkcji może spowodować poważne problemy z zabezpieczeniami w kodzie.

Ze względu na ryzyko związane z zabezpieczeniami, domyślnie te funkcje powodują [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)ostrzeżenia o zaniechaniu: **Ta funkcja lub zmienna może być niebezpieczna. Zamiast tego Rozważ użycie** *safe_function* **. Aby wyłączyć przestarzałość, użyj _CRT_SECURE_NO_WARNINGS.** Zalecamy zmianę kodu źródłowego tak, aby używał *safe_function* sugerowanego przez komunikat ostrzegawczy. Bezpieczniejsze funkcje nie zapisują więcej znaków niż określony rozmiar buforu. Aby uzyskać więcej informacji, zobacz [_itoa_s, _itow_s funkcje](itoa-s-itow-s.md).

Aby korzystać z tych funkcji bez ostrzeżenia o zaniechaniu, zdefiniuj makro preprocesora **_CRT_SECURE_NO_WARNINGS** przed dołączeniem wszystkich nagłówków CRT. Można to zrobić w wierszu polecenia w wierszu polecenia dewelopera, dodając opcję kompilatora **/D_CRT_SECURE_NO_WARNINGS** do polecenia **CL** . W przeciwnym razie Zdefiniuj makro w plikach źródłowych. Jeśli używasz prekompilowanych nagłówków, zdefiniuj makro w górnej części prekompilowanego nagłówka pliku, *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i jego wcześniejszych). Aby zdefiniować makro w kodzie źródłowym, użyj dyrektywy **#define** przed dołączeniem dowolnego nagłówka CRT, jak w poniższym przykładzie:

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują ich bezpieczniejsze odpowiedniki. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Nazwy POSIX **itoa**, **ltoa**i **ultoa** istnieją jako aliasy dla funkcji **_itoa**, **_ltoa**i **_ultoa** . Nazwy POSIX są przestarzałe, ponieważ nie są zgodne z konwencjami globalnej nazwy funkcji specyficznych dla implementacji ISO C. Domyślnie te funkcje powodują [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)z ostrzeżeniem o zaniechaniu: **Nazwa POSIX tego elementu jest przestarzała. Zamiast tego należy użyć nazwy zgodnej ze standardem ISO C i C++:** *new_name*. Zalecamy zmianę kodu źródłowego tak, aby korzystał z bezpieczniejsze wersje tych funkcji, **_itoa_s**, **_ltoa_s**lub **_ultoa_s**. Aby uzyskać więcej informacji, zobacz [_itoa_s, _itow_s funkcje](itoa-s-itow-s.md).

W przypadku przenośności kodu źródłowego warto zachować nazwy POSIX w kodzie. Aby korzystać z tych funkcji bez ostrzeżenia o zaniechaniu, należy zdefiniować makra preprocesora **_CRT_NONSTDC_NO_WARNINGS** i **_CRT_SECURE_NO_WARNINGS** przed uwzględnieniem dowolnych nagłówków CRT. Można to zrobić w wierszu polecenia w wierszu polecenia dewelopera, dodając opcje kompilatora **/D_CRT_SECURE_NO_WARNINGS** i **/D_CRT_NONSTDC_NO_WARNINGS** do polecenia **CL** . W przeciwnym razie Zdefiniuj makra w plikach źródłowych. Jeśli używasz prekompilowanych nagłówków, zdefiniuj makra w górnej części prekompilowanego pliku nagłówkowego. Aby zdefiniować makra w kodzie źródłowym, należy użyć dyrektyw **#define** przed dołączeniem dowolnego nagłówka CRT, jak w poniższym przykładzie:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Maksymalna liczba przeliczeń makr

Aby ułatwić tworzenie bezpiecznych buforów dla konwersji, CRT obejmuje niektóre wygodne makra. Definiują rozmiar buforu wymaganego do przekonwertowania najdłuższej możliwej wartości poszczególnych typów całkowitych, łącznie z terminatorem wartości null i znakiem znaku, dla kilku typowych baz. Aby zapewnić, że bufor konwersji jest wystarczająco duży, aby otrzymać konwersję w bazie danych określonej przez *podstawy*, użyj jednego z tych zdefiniowanych makr podczas alokowania buforu. Pozwala to zapobiec błędom przepełnienia buforu podczas konwertowania typów całkowitych na ciągi. Te makra są definiowane w przypadku dołączenia do źródła STDLIB. h lub WCHAR. h.

Aby użyć jednego z tych makr w funkcji konwersji ciągów, zadeklaruj bufor konwersji odpowiedniego typu, a następnie użyj wartości makro dla typu integer i podstawowego jako wymiaru bufor. Ta tabela zawiera listę makr, które są odpowiednie dla każdej funkcji dla wymienionych baz danych:

||||
|-|-|-|
|Funkcje|podstawy|Makra|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

W tym przykładzie do definiowania bufora wystarczająco duże, aby zawierała wartość **`unsigned long long`** w podstawie 2:

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
|**itoa**, **ltoa**, **ultoa**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<stdlib.h> lub \<wchar.h>|

Te funkcje i makra są specyficzne dla firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten przykład ilustruje użycie niektórych funkcji konwersji liczb całkowitych. Zwróć uwagę na użycie makra **_CRT_SECURE_NO_WARNINGS** , aby wyciszyć ostrzeżenie C4996.

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
[_itoa_s, funkcje _itow_s](itoa-s-itow-s.md)<br/>
