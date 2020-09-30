---
title: '&lt;&gt;funkcje charconv'
description: Opisuje <charconv> funkcje biblioteki, które konwertują wartości całkowite lub zmiennoprzecinkowe na znaki lub z nich.
ms.date: 08/20/2020
f1_keywords:
- charconv/std::to_chars
- charconv/std::from_chars
helpviewer_keywords:
- std::charconv [C++], to_chars
- std::charconv [C++], from_chars
ms.openlocfilehash: cde2ae6b6275543ec74d859b9a953f8673da9c2b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507742"
---
# <a name="ltcharconvgt-functions"></a>&lt;&gt;funkcje charconv

\<charconv>Nagłówek zawiera następujące funkcje, które nie są elementami członkowskimi:

| **Funkcje nieczłonkowskie** | **Opis** |
|-|-|
|[to_chars](#to_chars) | Przekonwertuj liczbę całkowitą lub wartość zmiennoprzecinkową na sekwencję **`char`** . |
|[from_chars](#from_chars) | Konwertuj sekwencję **`char`** do wartości całkowitej lub zmiennoprzecinkowej. |

Te funkcje konwersji są dostrajane pod kątem wydajności, a także obsługują najkrótsze zachowanie. Zachowanie funkcji najkrótszej rundy oznacza, że gdy liczba jest konwertowana na znaki, jest zapisywana tylko wystarczająca precyzja, aby umożliwić odzyskiwanie pierwotnej liczby podczas konwertowania tych znaków z powrotem na zmiennoprzecinkową.

- Podczas konwertowania znaków na liczbę, wartość numeryczna nie musi być zakończona wartością null. Podobnie podczas konwertowania liczby na znaki, wynik nie jest zakończony znakiem null.
- Funkcje konwersji nie przydzielają pamięci. W każdym przypadku jesteś właocicielem buforu.
- Funkcje konwersji nie generują. Zostanie zwrócony wynik, za pomocą którego można określić, czy konwersja powiodła się.
- Funkcje konwersji nie są zależne od trybu zaokrąglania środowiska uruchomieniowego.
- Funkcje konwersji nie obsługują ustawień regionalnych. Zawsze drukują i analizują punkty dziesiętne jako `'.'` , i nigdy jako "," dla ustawień regionalnych, które używają przecinków.

## `to_chars`

Przekonwertuj liczbę całkowitą lub wartość zmiennoprzecinkową na sekwencję **`char`** .

Konwertuje `value` na ciąg znaków, wypełniając zakres \[ `first` , `last` ), gdzie \[ `first` , `last` ) musi być prawidłowym zakresem.
Zwraca [strukturę to_chars_result](to-chars-result-structure.md). Jeśli konwersja zakończyła się pomyślnie, jak wskazano przez `to_char_result.ec` , element członkowski `ptr` jest wskaźnikiem jednokrotnym do końca pisanych znaków. W przeciwnym razie `to_char_result.ec` ma wartość `errc::value_too_large` , `to_char_result.ptr` ma wartość `last` i zawartość zakresu \[ `first` , `last` ) nie są określone.

Jedynym sposobem, który `to_chars` może się nie powieść, jest zapewnienie niewystarczającego dużego buforu do przechowywania wyniku.

```cpp
// integer to chars

to_chars_result to_chars(char* first, char* last, char value, int base = 10);
to_chars_result to_chars(char* first, char* last, signed char value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned char value, int base = 10);
to_chars_result to_chars(char* first, char* last, short value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned short value, int base = 10);
to_chars_result to_chars(char* first, char* last, int value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned int value, int base = 10);
to_chars_result to_chars(char* first, char* last, long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long value, int base = 10);
to_chars_result to_chars(char* first, char* last, long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, bool value, int base = 10) = delete;

// floating-point to chars

to_chars_result to_chars(char* first, char* last, float value);
to_chars_result to_chars(char* first, char* last, double value);
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Wskazuje początek buforu do wypełnienia.

*ostatniego*\
Wskazuje jeden znak poza końcem buforu do wypełnienia.

*wartościami*\
Wartość do konwersji. Jeśli `value` jest ujemna, reprezentacja zaczyna się od `-` .

*opiera*\
W przypadku konwersji liczb całkowitych baza jest używana podczas konwertowania `value` na znaki. Musi zawierać się w przedziale od 2 do 36 włącznie. Nie będzie żadnych zer wiodących. Cyfry z zakresu 10.. 35 (włącznie) są reprezentowane małymi literami a.. porządku

*FMT*\
W przypadku konwersji zmiennoprzecinkowych maska bitów określa format konwersji, który ma być używany, na przykład naukowy, stały lub szesnastkowy. Aby uzyskać szczegółowe informacje, zobacz [chars_format](chars-format-class.md) .

*dokładne*\
W przypadku konwersji zmiennoprzecinkowych liczba cyfr dokładności dla skonwertowanej wartości.

### <a name="return-value"></a>Wartość zwracana

[To_chars_result](to-chars-result-structure.md) zawierający wynik konwersji.

### <a name="remarks"></a>Uwagi

Funkcja pobierająca parametr [chars_format](chars-format-class.md) określa specyfikator konwersji tak, jakby był używany `printf()` w następujący sposób: specyfikator konwersji to IF, if is, `'f'` `fmt` `chars_format::fixed` `'e'` `fmt` `chars_format::scientific` `'a'` (bez wiodącego `0x` w wyniku), jeśli jest `fmt` `chars_format::hex` , i `'g'` Jeśli `fmt` jest `chars_format::general` . Określenie najkrótszej notacji stałej może nadal powodować długotrwałe dane wyjściowe, ponieważ może to być najkrótsza możliwa reprezentacja, gdy wartość jest bardzo duża lub bardzo mała.

W poniższej tabeli opisano zachowanie konwersji przy użyciu różnych kombinacji `fmt` parametrów i `precision` . Termin "zachowanie najkrótszej rundy" oznacza zapisanie najmniejszej liczby cyfr, które są niezbędne, aby analizowanie tej reprezentacji przy użyciu odpowiedniej `from_chars` funkcji odzyskał wartość dokładnie.

| `fmt` i `precision` kombinacja | Dane wyjściowe |
|--|--|
|  Żadna | W zależności od stałej lub wykładniczej notacji jest krótszy, poprzedzony prefiksem ustalonym jako wczesnego.</br>To zachowanie nie może być symulowane przez żadne Przeciążenie, które pobiera `fmt` parametr. |
| `fmt` | Najkrótsze zachowanie dla określonego formatu, takie jak najkrótszy format naukowy. |
| `fmt` i `precision` | Używa danej precyzji, następującego `printf()` stylu, bez najkrótszych zachowań. |

### <a name="example"></a>Przykład

```cpp
#include <charconv>
#include <stdio.h>
#include <system_error>

template <typename T> void TestToChars(const T t)
{
    static_assert(std::is_floating_point_v<T>);
    constexpr bool IsFloat = std::is_same_v<T, float>;

    char buf[100]; // 100 is large enough for double and long double values because the longest possible outputs are "-1.23456735e-36" and "-1.2345678901234567e-100".
    constexpr size_t size = IsFloat ? 15 : 24;
    const std::to_chars_result res = std::to_chars(buf, buf + size, t);  // points to buffer area it can use. Must be char, not wchar_t, etc.

    if (res.ec == std::errc{}) // no error
    {
        // %.*s provides the exact number of characters to output because the output range, [buf, res.ptr), isn't null-terminated
        printf("success: %.*s\n", static_cast<int>(res.ptr - buf), buf);
    }
    else // probably std::errc::value_too_large
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }
}

int main()
{
    TestToChars(123.34);
    return 0;
}
```

## `from_chars`

Konwertuj sekwencję **`char`** do wartości całkowitej lub zmiennoprzecinkowej.

```cpp
// char to an integer value

from_chars_result from_chars(const char* first, const char* last, char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, signed char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long long& value, int base = 10);

// char to a floating-point value

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Wskazuje początek buforu znaków do przekonwertowania.

*ostatniego*\
Wskazuje jeden element poza elementem końcowym buforu znaków do przekonwertowania.

*wartościami*\
Jeśli konwersja zakończy się pomyślnie, zawiera wynik konwersji.

*opiera*\
W przypadku konwersji liczb całkowitych baza jest używana podczas konwersji. Musi zawierać się w przedziale od 2 do 36 włącznie.

*FMT*\
W przypadku konwersji zmiennoprzecinkowych format sekwencji konwertowanych znaków. Aby uzyskać szczegółowe informacje, zobacz [chars_format](chars-format-class.md) .

### <a name="remarks"></a>Uwagi

`from_chars()`Funkcja analizuje ciąg \[ `first` , `last` ) dla wzorca liczbowego, gdzie \[ `first` , `last` ) musi być prawidłowym zakresem.

Podczas analizowania znaków znak odstępu nie jest ignorowany. W przeciwieństwie `strtod()` do, na przykład, bufor musi rozpoczynać się od prawidłowej reprezentacji liczbowej.

Zwraca [strukturę from_chars_result](from-chars-result-structure.md).

Jeśli żadne znaki nie pasują do wzorca liczby, nie `value` jest modyfikowane, `from_chars_result.ptr` wskazuje na `first` , i `from_chars_result.ec` is `errc::invalid_argument` .

Jeśli tylko niektóre znaki pasują do wzorca liczb, `from_chars_result.ptr` wskazuje pierwszy znak, który nie pasuje do wzorca lub ma wartość `last` parametru, jeśli wszystkie znaki są zgodne.

Jeśli przeanalizowana wartość nie jest w zakresie, który można zaprezentować przez typ `value` , `value` nie jest modyfikowany i `from_chars_result.ec` jest `errc::result_out_of_range` .

W przeciwnym razie `value` jest ustawiona na wartość przeanalizowana, po zaokrągleniu i `from_chars_result.ec` jest równa `errc{}` .

### <a name="example"></a>Przykład

```cpp
#include <charconv>
#include <stdio.h>
#include <string_view>
#include <system_error>

double TestFromChars(const std::string_view sv)
{
    const char* const first = sv.data();
    const char* const last = first + sv.size();
    double dbl;

    const std::from_chars_result res = std::from_chars(first, last, dbl);

    if (res.ec == std::errc{}) // no error
    {
        printf("success: %g\n", dbl);
    }
    else
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }

    return dbl;
}

int main()
{
    double dbl = TestFromChars("123.34");
    return 0;
}
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<charconv>

**Przestrzeń nazw:** std

wymagany jest/std: c++ 17 lub nowszy.

## <a name="see-also"></a>Zobacz też

[\<charconv>](charconv.md)  
[Krótki ciąg dziesiętny, który dzieli](https://www.exploringbinary.com/the-shortest-decimal-string-that-round-trips-examples/) 
 się na rundy [specyfikatory formatu printf ()](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)
