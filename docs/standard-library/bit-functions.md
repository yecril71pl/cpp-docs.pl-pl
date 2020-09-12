---
title: '&lt;&gt;funkcje bitowe'
description: Funkcje umożliwiające dostęp, manipulowanie i przetwarzanie poszczególnych bitów i sekwencji bitów
ms.date: 08/28/2020
f1_keywords:
- bit/std::bit_cast
- bit/std::has_single_bit
- bit/std::bit_ceil
- bit/std::bit_floor
- bit/std::bit_width
- bit/std::rotl
- bit/std::rotr
- bit/std::countl_zero
- bit/std::countl_one
- bit/std::countr_zero
- bit/std::countr_one
- bit/std::popcount
helpviewer_keywords:
- std::bit [C++], bit_cast
- std::bit [C++], has_single_bit
- std::bit [C++], bit_ceil
- std::bit [C++], bit_floor
- std::bit [C++], bit_width
- std::bit [C++], rotl
- std::bit [C++], rotr
- std::bit [C++], countl_zero
- std::bit [C++], countl_one
- std::bit [C++], countr_zero
- std::bit [C++], countr_one
- std::bit [C++], popcount
ms.openlocfilehash: a2408df9aa13c6e714f615561871397be17fc4a3
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039818"
---
# <a name="ltbitgt-functions"></a>&lt;&gt;funkcje bitowe

\<bit>Nagłówek zawiera następujące funkcje szablonu, które nie są elementami członkowskimi:

| **Funkcje nieczłonkowskie** | **Opis** |
|--------|---------|
|[bit_cast](#bit_cast) | Ponownie interpretuje reprezentację obiektu z jednego typu na inny. |
|[bit_ceil](#bit_ceil) | Znajdź najmniejszą potęgę większą lub równą wartości. |
|[bit_floor](#bit_floor) | Znajdź największą potęgę nieprzekraczającą wartości. |
|[bit_width](#bit_width) | Znajdź najmniejszą liczbę bitów, które są konieczne do reprezentowania wartości. |
|[countl_zero](#countl_zero) | Zlicz liczbę kolejnych bitów ustawionych na zero, rozpoczynając od najbardziej znaczącego bitu. |
|[countl_one](#countl_one) | Zlicz liczbę kolejnych bitów ustawionych na jeden, rozpoczynając od najbardziej znaczącego bitu. |
|[countr_zero](#countr_zero) | Zlicz liczbę kolejnych bitów ustawionych na zero, rozpoczynając od najmniej znaczącego bitu. |
|[countr_one](#countl_one) | Zlicz liczbę kolejnych bitów ustawionych na jeden, rozpoczynając od najmniej znaczącego bitu. |
|[has_single_bit](#has_single_bit) | Sprawdź, czy wartość ma tylko jeden bit ustawiony jako jeden. Jest to takie samo, jak testowanie, czy wartość jest potęgą liczby 2. |
|[popcount](#popcount) | Liczba bitów ustawionych na jeden. |
|[rotl](#rotl) | Oblicza wynik lewego obrotu. |
|[rotr](#rotr) | Oblicza wynik bezprawnego obrotu. |

## <a name="bit_cast"></a>`bit_cast`

Skopiuj wzorzec bitowy z obiektu typu `From` do nowego obiektu typu `To` .

```cpp
template <class To, class From>
[[nodiscard]] constexpr To bit_cast(const From& from) noexcept;
```

### <a name="parameters"></a>Parametry

*Do*\
Typ danych wyjściowych.

*Wniosek*\
Typ wartości do przekonwertowania.

*wniosek*\
Wartość do konwersji.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu `To`.

Każdy bit w wyniku jest zgodny z odpowiadającym mu bitem `from` , chyba że istnieją bity uzupełniania w programie `To` , w tym przypadku te bity w wyniku nie są określone.

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <iostream>

int main()
{
    float f = std::numeric_limits<float>::infinity();
    int i = std::bit_cast<int>(f);
    std::cout << "float f = " << std::hex << f
              << "\nstd::bit_cat<int>(f) = " << std::hex << i << '\n';
    return 0;
}
```

```Output
float f = inf
std::bit_cat<int>(f) = 7f800000
```

### <a name="remarks"></a>Uwagi

Kod niskiego poziomu często musi interpretować obiekt z jednym typem jako inny typ. Reinterpretowany obiekt ma taką samą reprezentację bitową jak oryginalna, ale jest innym typem.

Zamiast używać `reinterpret_cast` , lub `memcpy()` , `bit_cast()` jest lepszym sposobem dokonania konwersji. Lepszym rozwiązaniem jest:
- `bit_cast()` to `constexpr`
- `bit_cast()` wymaga, aby typy były jednocześnie kopiujące i miały ten sam rozmiar. Zapobiega to potencjalnym problemom, które można napotkać przy użyciu `reinterpret_cast` i `memcpy` ponieważ mogą one być używane do przypadkowego i niepoprawnie konwersji typów, które nie są możliwe do kopiowania. Ponadto, `memcpy()` może być używany do przypadkowego kopiowania typów, które nie mają tego samego rozmiaru. Na przykład podwójna (8 bajtów) do niepodpisanej int (4 bajty) lub w inny sposób.

To Przeciążenie uczestniczy tylko w rozwiązaniu przeciążenia, jeśli:
-  `sizeof(To) == sizeof(From)`
- `To` i `From` są [is_trivially_copyable](is-trivially-copyable-class.md).

Ten szablon funkcji jest `constexpr` if i tylko wtedy `To` , gdy, `From` i typy ich podobiektów są:
- nie jest typem Unii ani wskaźnikiem
- nie jest wskaźnikiem do typu elementu członkowskiego
- nietrwałe — kwalifikowana
- Brak niestatycznej składowej danych, która jest typem referencyjnym

## <a name="bit_ceil"></a>`bit_ceil`

Znajdź najmniejszą potęgę większą lub równą wartości. Na przykład, podaje `3` `4` .

```cpp
template<class T>
[[nodiscard]] constexpr T bit_ceil(T value);
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

 Najmniejsza potęga większa niż lub równa `value` .

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_ceil() takes an unsigned integer type
    {
        auto nextClosestPowerOf2 = std::bit_ceil(i);
        std::cout << "\nbit_ceil(0b" << std::bitset<4>(i) << ") = "
                  << "0b" << std::bitset<4>(nextClosestPowerOf2);
    }
    return 0;
}
```

```Output
bit_ceil(0b0000) = 0b0001
bit_ceil(0b0001) = 0b0001
bit_ceil(0b0010) = 0b0010
bit_ceil(0b0011) = 0b0100
bit_ceil(0b0100) = 0b0100
bit_ceil(0b0101) = 0b1000
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="bit_floor"></a>`bit_floor`

Znajdź największą potęgę nieprzekraczającą wartości. Na przykład, podaje `5` `4` .

```cpp
template< class T >
[[nodiscard]] constexpr T bit_floor(T value) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

Największą potęgą dwóch, która nie jest większa niż `value` . \
Jeśli `value` jest równa zero, zwraca zero.

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_floor() takes an unsigned integer type
    {
        auto previousPowerOf2 = std::bit_floor(i);
        std::cout << "\nbit_floor(0b" << std::bitset<4>(i) << ") = 0b"
                  << std::bitset<4>(previousPowerOf2);
    }
    return 0;
}
```

```Output
bit_floor(0b0000) = 0b0000
bit_floor(0b0001) = 0b0001
bit_floor(0b0010) = 0b0010
bit_floor(0b0011) = 0b0010
bit_floor(0b0100) = 0b0100
bit_floor(0b0101) = 0b0100
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="bit_width"></a>`bit_width`

Znajdź najmniejszą liczbę bitów, które są konieczne do reprezentowania wartości.

Na przykład, uwzględniając 5 (0b101), zwraca wartość 3, ponieważ trwa 3 binarne bity do wyrażenia wartości 5.

```cpp
template<class T>
[[nodiscard]] constexpr T bit_width(T value) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

Liczba bitów wymaganych do reprezentowania `value` . \
Jeśli `value` jest równa zero, zwraca zero.

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <iostream>

int main()
{
    for (unsigned i=0u; i <= 8u; ++i)
    {
        std::cout << "\nbit_width(" << i << ") = "
                  << std::bit_width(i);
    }
    return 0;
}
```

```Output
bit_width(0) = 0
bit_width(1) = 1
bit_width(2) = 2
bit_width(3) = 2
bit_width(4) = 3
bit_width(5) = 3
bit_width(6) = 3
bit_width(7) = 3
bit_width(8) = 4
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="countl_zero"></a>`countl_zero`

Zlicz liczbę kolejnych bitów ustawionych na zero, rozpoczynając od najbardziej znaczącego bitu.

```cpp
template<class T>
[[nodiscard]] constexpr int countl_zero(T value) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

Liczba kolejnych bitów równych zero, zaczynając od najbardziej znaczącego bitu. \
Jeśli wartość `value` jest równa zero, liczba bitów w typie `value` .

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountl_zero(0b" << std::bitset<8>(result) << ") = " << std::countl_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countl_zero(0b00000000) = 8
countl_zero(0b00000001) = 7
countl_zero(0b00000010) = 6
countl_zero(0b00000100) = 5
countl_zero(0b00001000) = 4
countl_zero(0b00010000) = 3
countl_zero(0b00100000) = 2
countl_zero(0b01000000) = 1
countl_zero(0b10000000) = 0
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="countl_one"></a>`countl_one`

Zlicz liczbę kolejnych bitów ustawionych na jeden, rozpoczynając od najbardziej znaczącego bitu.

```cpp
template<class T>
[[nodiscard]] constexpr int countl_one(T value) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

Liczba kolejnych bitów ustawionych dla jednej, rozpoczynając od najbardziej znaczącego bitu.

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
    for (unsigned char bit = 128; bit > 0; bit /= 2)
    {
        value |= bit;
        std::cout << "\ncountl_one(0b" << std::bitset<8>(value) << ") = "
                  << std::countl_one(value);
    }
    return 0;
}
```

```Output
countl_one(0b10000000) = 1
countl_one(0b11000000) = 2
countl_one(0b11100000) = 3
countl_one(0b11110000) = 4
countl_one(0b11111000) = 5
countl_one(0b11111100) = 6
countl_one(0b11111110) = 7
countl_one(0b11111111) = 8
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="countr_zero"></a>`countr_zero`

Zlicz liczbę kolejnych bitów ustawionych na zero, rozpoczynając od najmniej znaczącego bitu.

```cpp
template<class T>
[[nodiscard]] constexpr int countr_zero(T value) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

Liczba kolejnych bitów równych zero, zaczynając od najmniej znaczącego bitu. \
Jeśli wartość `value` jest równa zero, liczba bitów w typie `value` .

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountr_zero(0b" << std::bitset<8>(result) << ") = "
                  << std::countr_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countr_zero(0b00000000) = 8
countr_zero(0b00000001) = 0
countr_zero(0b00000010) = 1
countr_zero(0b00000100) = 2
countr_zero(0b00001000) = 3
countr_zero(0b00010000) = 4
countr_zero(0b00100000) = 5
countr_zero(0b01000000) = 6
countr_zero(0b10000000) = 7
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="countr_one"></a>`countr_one`

Zlicz liczbę kolejnych bitów ustawionych na jeden, rozpoczynając od najmniej znaczącego bitu.

```cpp
template<class T>
[[nodiscard]] constexpr int countr_one(T value) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

Liczba kolejnych bitów ustawionych dla jednej, rozpoczynając od najmniej znaczącego bitu.

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
    for (int bit = 1; bit <= 128; bit *= 2)
    {
        value |= bit;
        std::cout << "\ncountr_one(0b" << std::bitset<8>(value) << ") = "
                  << std::countr_one(value);
    }
    return 0;
}
```

```Output
countr_one(0b00000001) = 1
countr_one(0b00000011) = 2
countr_one(0b00000111) = 3
countr_one(0b00001111) = 4
countr_one(0b00011111) = 5
countr_one(0b00111111) = 6
countr_one(0b01111111) = 7
countr_one(0b11111111) = 8
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="has_single_bit"></a>`has_single_bit`

Sprawdź, czy wartość ma tylko jeden zestaw bitów. Jest to takie samo, jak testowanie, czy wartość jest potęgą liczby 2.
 
```cpp
template <class T>
[[nodiscard]] constexpr bool has_single_bit(T value) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli `value` ma tylko jeden zestaw bitów, co oznacza, że `value` jest potęgą dwóch. W przeciwnym razie wartość `false`.

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>
#include <iomanip>

int main()
{
    for (auto i = 0u; i < 10u; ++i)
    {
        std::cout << "has_single_bit(0b" << std::bitset<4>(i) << ") = "
                  << std::boolalpha << std::has_single_bit(i) << '\n';
    }
    return 0;
}
```

```Output
has_single_bit(0b0000) = false
has_single_bit(0b0001) = true
has_single_bit(0b0010) = true
has_single_bit(0b0011) = false
has_single_bit(0b0100) = true
has_single_bit(0b0101) = false
has_single_bit(0b0110) = false
has_single_bit(0b0111) = false
has_single_bit(0b1000) = true
has_single_bit(0b1001) = false
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="popcount"></a>`popcount`

Liczba bitów ustawionych na jedną wartość w postaci liczby całkowitej bez znaku.
 
```cpp
template<class T>
[[nodiscard]] constexpr int popcount(T value) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

Liczba bitów ustawiona na jeden w `value` .

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
   for (unsigned char value = 0; value < 16; value++)
    {
        std::cout << "\npopcount(0b" << std::bitset<4>(value) << ") = "
                  << std::popcount(value);
    }
    return 0;
}
```

```Output
popcount(0b0000) = 0
popcount(0b0001) = 1
popcount(0b0010) = 1
popcount(0b0011) = 2
popcount(0b0100) = 1
popcount(0b0101) = 2
popcount(0b0110) = 2
popcount(0b0111) = 3
popcount(0b1000) = 1
popcount(0b1001) = 2
popcount(0b1010) = 2
popcount(0b1011) = 3
popcount(0b1100) = 2
popcount(0b1101) = 3
popcount(0b1110) = 3
popcount(0b1111) = 4
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="rotl"></a>`rotl`

Obraca bity wartości liczby całkowitej bez znaku, pozostawioną określoną liczbę razy. Bity "spadek" bitu z lewej strony są obracane na bit z prawej strony.
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotl(T value, int s) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do obrócenia.

*wolumin*\
Liczba lewych obrotów do wykonania.

### <a name="return-value"></a>Wartość zwracana

Wynik obrócenia `value` lewo, `s` Times. \
Jeśli `s` jest równa zero, zwraca `value` . \
Jeśli `s` jest ujemna, to `rotr(value, -s)` . Bity "spadek wartości" bitu z prawej strony są obracane do bitu z najwcześniejszym bitem.

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 1;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotl(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotl(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotl(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotl(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotl(0b00000001, 1) = 0b00000010
rotl(0b00000010, 1) = 0b00000100
rotl(0b00000100, 1) = 0b00001000
rotl(0b00001000, 1) = 0b00010000
rotl(0b00010000, 1) = 0b00100000
rotl(0b00100000, 1) = 0b01000000
rotl(0b01000000, 1) = 0b10000000
rotl(0b10000000, 1) = 0b00000001
rotl(0b00000001,-1) = 0b10000000
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="rotr"></a>`rotr`

Obraca bity o `value` określoną liczbę razy. Bity "spadek" bitu z prawej strony są obracane z powrotem do bitu z lewej strony.
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotr(T value, int s) noexcept;
```

### <a name="parameters"></a>Parametry

*wartościami*\
Wartość liczby całkowitej bez znaku do obrócenia.

*wolumin*\
Liczba praw do wykonania.

### <a name="return-value"></a>Wartość zwracana

Wynik rotacji `value` po prawej, `s` Times. \
Jeśli `s` jest równa zero, zwraca `value` . \
Jeśli `s` jest ujemna, to `rotl(value, -s)` . Bity "spadek" bitu z lewej strony są obracane z powrotem do bitu z prawej strony.

### <a name="example"></a>Przykład

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 128;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotr(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotr(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotr(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotr(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotr(0b10000000, 1) = 0b01000000
rotr(0b01000000, 1) = 0b00100000
rotr(0b00100000, 1) = 0b00010000
rotr(0b00010000, 1) = 0b00001000
rotr(0b00001000, 1) = 0b00000100
rotr(0b00000100, 1) = 0b00000010
rotr(0b00000010, 1) = 0b00000001
rotr(0b00000001, 1) = 0b10000000
rotr(0b10000000,-1) = 0b00000001
```

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest częścią tylko rozpoznawania przeciążenia `T` , jeśli jest typem liczb całkowitych bez znaku. Na przykład: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` i tak dalej.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<bit>

**Przestrzeń nazw:** std

[/std: wymagany jest język c + +](../build/reference/std-specify-language-standard-version.md) .

## <a name="see-also"></a>Zobacz także

[\<bit>](bit.md)