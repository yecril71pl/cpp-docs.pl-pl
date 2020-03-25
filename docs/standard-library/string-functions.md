---
title: '&lt;funkcje&gt; ciągu'
ms.date: 11/04/2016
f1_keywords:
- string/std::getline
- string/std::stod
- string/std::stof
- string/std::stoi
- string/std::stol
- string/std::stold
- string/std::stoll
- string/std::stoul
- string/std::stoull
- string/std::swap
- string/std::to_string
- string/std::to_wstring
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
helpviewer_keywords:
- std::getline [C++]
- std::stod [C++]
- std::stof [C++]
- std::stoi [C++]
- std::stol [C++]
- std::stold [C++]
- std::stoll [C++]
- std::stoul [C++]
- std::stoull [C++]
- std::swap [C++]
- std::to_string [C++]
- std::to_wstring [C++]
ms.openlocfilehash: dbcc4a86731bba092d8358a046fd3f9eb949f91f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214971"
---
# <a name="ltstringgt-functions"></a>&lt;funkcje&gt; ciągu

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[wymiany](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>getline

Wyodrębnij ciągi ze strumienia wejściowego w wierszu.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delimiter);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delimiter);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& in_stream,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

*in_stream*\
Strumień wejściowy, z którego ma zostać wyodrębniony ciąg.

*str*\
Ciąg, w którym są odczytywane znaki ze strumienia wejściowego.

\ *ogranicznika*
Ogranicznik wiersza.

### <a name="return-value"></a>Wartość zwracana

Strumień wejściowy *in_stream*.

### <a name="remarks"></a>Uwagi

Para sygnatur funkcji oznaczona `(1)` Wyodrębnij znaki z *in_stream* do momentu znalezienia *ogranicznika* , przechowując je w *str*.

Para sygnatur funkcji oznaczona `(2)` Użyj nowego wiersza jako domyślnego ogranicznika linii i zachowuje się jako `getline(in_stream, str, in_stream. widen('\n'))`.

Druga funkcja każdej pary jest analogiczna do pierwszej z nich do obsługi [odwołań rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

Ekstrakcja zostaje zatrzymana, gdy wystąpi jedno z następujących wystąpień:

- Na końcu pliku, w którym przypadku Flaga stanu wewnętrznego *in_stream* jest ustawiona na `ios_base::eofbit`.

- Po wyodrębnieniu elementu, który porównuje równe *ogranicznika*. Element nie jest umieszczany lub dołączany do kontrolowanej sekwencji.

- Po wyodrębnieniu przez funkcję `str.`elementów [max_size](../standard-library/basic-string-class.md#max_size) . Flaga stanu wewnętrznego *in_stream* jest ustawiona na `ios_base::failbit`.

- Inne błędy inne niż wymienione wcześniej; Flaga stanu wewnętrznego *in_stream* jest ustawiona na `ios_base::badbit`.

Aby uzyskać informacje na temat flag stanu wewnętrznego, zobacz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

Jeśli funkcja nie wyodrębnia żadnych elementów, Flaga stanu wewnętrznego *in_stream* jest ustawiona na `ios_base::failbit`. W każdym przypadku `getline` zwraca *in_stream*.

Jeśli wyjątek jest zgłaszany, *in_stream* i *str* są pozostawione w prawidłowym stanie.

### <a name="example"></a>Przykład

Poniższy kod ilustruje `getline()` w dwóch trybach: najpierw z Domyślnym ogranicznikiem (nowy wiersz) i drugim z odstępem jako ogranicznikiem. Znak końca pliku (CTRL-Z na klawiaturze) służy do sterowania przerwaniem pętli while. Ta wartość ustawia flagę stanu wewnętrznego `cin` na `eofbit`, która musi zostać wyczyszczona z [basic_ios:: Clear ()](../standard-library/basic-ios-class.md#clear) przed sekundą, gdy pętla będzie działać prawidłowo.

```cpp
// compile with: /EHsc /W4
#include <string>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    string str;
    vector<string> v1;
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.
    // Default delimiter is the newline character.
    while (getline(cin, str)) {
        v1.push_back(str);
    }

    cout << "The following input was stored with newline delimiter:" << endl;
    for (const auto& p : v1) {
        cout << p << endl;
    }

    cin.clear();

    vector<string> v2;
    // Now try it with a whitespace delimiter
    while (getline(cin, str, ' ')) {
        v2.push_back(str);
    }

    cout << "The following input was stored with whitespace as delimiter:" << endl;
    for (const auto& p : v2) {
        cout << p << endl;
    }
}
```

## <a name="stod"></a><a name="stod"></a>stod

Konwertuje sekwencję znaków na **`double`** .

```cpp
double stod(
    const string& str,
    size_t* idx = 0);

double stod(
    const wstring& str,
    size_t* idx = 0
;
```

### <a name="parameters"></a>Parametry

*str*\
Sekwencja znaków do przekonwertowania.

*idx*\
Wartość indeksu pierwszego nieskonwertowanego znaku.

### <a name="return-value"></a>Wartość zwracana

Wartość **`double`** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość typu **`double`** jak if, wywołując `strtod( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli `str.c_str() == *_Eptr`, zgłasza obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca wartość.

## <a name="stof"></a><a name="stof"></a>stof

Konwertuje sekwencję znaków na wartość zmiennoprzecinkową.

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

*str*\
Sekwencja znaków do przekonwertowania.

*idx*\
Wartość indeksu pierwszego nieskonwertowanego znaku.

### <a name="return-value"></a>Wartość zwracana

Wartość **`float`** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość typu **`float`** jak if, wywołując `strtof( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli `str.c_str() == *_Eptr`, zgłasza obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca wartość.

## <a name="stoi"></a><a name="stoi"></a>stoi

Konwertuje sekwencję znaków na liczbę całkowitą.

```cpp
int stoi(
    const string& str,
    size_t* idx = 0,
    int base = 10);

int stoi(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita.

### <a name="parameters"></a>Parametry

*str*\
Sekwencja znaków do przekonwertowania.

*idx*\
Wartość indeksu pierwszego nieskonwertowanego znaku.

\ *podstawowe*
Podstawa numeru, która ma zostać użyta.

### <a name="remarks"></a>Uwagi

Funkcja `stoi` konwertuje sekwencję znaków w *str* na wartość typu **`int`** i zwraca wartość. Na przykład, gdy przeszedł sekwencję znaków "10", wartość zwracana przez `stoi` jest liczbą całkowitą 10.

`stoi` zachowuje się podobnie do `strtol` funkcji dla znaków jednobajtowych, gdy jest wywoływana w sposób `strtol( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji; lub `wcstol` dla szerokich znaków, gdy jest wywoływana w podobny sposób, `wcstol(Str.c_str(), _Eptr, idx)`. Aby uzyskać więcej informacji, zobacz [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Jeśli `str.c_str() == *_Eptr`, `stoi` zgłasza obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, lub jeśli zwracana wartość nie może być reprezentowana jako obiekt typu **`int`** , zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr - str.c_str()` w `*idx`.

## <a name="stol"></a><a name="stol"></a>stol

Konwertuje sekwencję znaków na **`long`** .

```cpp
long stol(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long stol(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parametry

*str*\
Sekwencja znaków do przekonwertowania.

*idx*\
Wartość indeksu pierwszego nieskonwertowanego znaku.

\ *podstawowe*
Podstawa numeru, która ma zostać użyta.

### <a name="return-value"></a>Wartość zwracana

Wartość Long-Integer.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość typu **`long`** jak if, wywołując `strtol( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli `str.c_str() == *_Eptr`, zgłasza obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca wartość.

## <a name="stold"></a><a name="stold"></a>stold

Konwertuje sekwencję znaków na **`long double`** .

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

*str*\
Sekwencja znaków do przekonwertowania.

*idx*\
Wartość indeksu pierwszego nieskonwertowanego znaku.

### <a name="return-value"></a>Wartość zwracana

Wartość **`long double`** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość typu **`long double`** jak if, wywołując `strtold( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli `str.c_str() == *_Eptr`, zgłasza obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca wartość.

## <a name="stoll"></a><a name="stoll"></a>stoll

Konwertuje sekwencję znaków na **`long long`** .

```cpp
long long stoll(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long long stoll(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parametry

*str*\
Sekwencja znaków do przekonwertowania.

*idx*\
Wartość indeksu pierwszego nieskonwertowanego znaku.

\ *podstawowe*
Podstawa numeru, która ma zostać użyta.

### <a name="return-value"></a>Wartość zwracana

Wartość **`long long`** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość typu **`long long`** jak if, wywołując `strtoll( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli `str.c_str() == *_Eptr`, zgłasza obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca wartość.

## <a name="stoul"></a><a name="stoul"></a>stoul

Konwertuje sekwencję znaków na wartość unsigned long.

```cpp
unsigned long stoul(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long stoul(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parametry

*str*\
Sekwencja znaków do przekonwertowania.

*idx*\
Wartość indeksu pierwszego nieskonwertowanego znaku.

\ *podstawowe*
Podstawa numeru, która ma zostać użyta.

### <a name="return-value"></a>Wartość zwracana

Nieniepodpisana wartość Long-Integer.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość typu **`unsigned long`** jak if, wywołując `strtoul( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli `str.c_str() == *_Eptr`, zgłasza obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca wartość.

## <a name="stoull"></a><a name="stoull"></a>stoull

Konwertuje sekwencję znaków na **`unsigned long long`** .

```cpp
unsigned long long stoull(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long long stoull(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parametry

*str*\
Sekwencja znaków do przekonwertowania.

*idx*\
Wartość indeksu pierwszego nieskonwertowanego znaku.

\ *podstawowe*
Podstawa numeru, która ma zostać użyta.

### <a name="return-value"></a>Wartość zwracana

Wartość **`unsigned long long`** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość typu **`unsigned long long`** jak if, wywołując `strtoull( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli `str.c_str() == *_Eptr`, zgłasza obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca wartość.

## <a name="swap"></a><a name="swap"></a>wymiany

Wymienia tablice znaków dwóch ciągów.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Jeden ciąg, którego elementy mają zostać zamienione na elementy innego ciągu.

*prawa*\
Inny ciąg, którego elementy mają zostać zamienione na pierwszy ciąg.

### <a name="remarks"></a>Uwagi

*Funkcja Template*wykonuje wyspecjalizowaną funkcję członkowską. [swap](../standard-library/basic-string-class.md#swap)(*Right*) dla ciągów, które gwarantują stałą złożoność.

### <a name="example"></a>Przykład

```cpp
// string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   swap ( s1 , s2 );
   cout << "\nAfter swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.

After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="to_string"></a><a name="to_string"></a>to_string

Konwertuje wartość na `string`.

```cpp
string to_string(int value);
string to_string(unsigned int value);
string to_string(long value);
string to_string(unsigned long value);
string to_string(long long value);
string to_string(unsigned long long value);
string to_string(float value);
string to_string(double value);
string to_string(long double value);
```

### <a name="parameters"></a>Parametry

\ *wartości*
Wartość do konwersji.

### <a name="return-value"></a>Wartość zwracana

`string`, która reprezentuje wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje *wartość* na sekwencję elementów przechowywanych w obiekcie array, `Buf` wewnętrzna dla funkcji tak jak w przypadku wywoływania `sprintf(Buf, Fmt, value)`, gdzie `Fmt` jest

- `"%d"` Jeśli *wartość* jest typu **`int`**

- `"%u"` Jeśli *wartość* jest typu **`unsigned int`**

- `"%ld"` Jeśli *wartość* jest typu **`long`**

- `"%lu"` Jeśli *wartość* jest typu **`unsigned long`**

- `"%lld"` Jeśli *wartość* jest typu **`long long`**

- `"%llu"` Jeśli *wartość* jest typu **`unsigned long long`**

- `"%f"` Jeśli *wartość* jest typu **`float`** lub **`double`**

- `"%Lf"` Jeśli *wartość* jest typu **`long double`**

Funkcja zwraca `string(Buf)`.

## <a name="to_wstring"></a><a name="to_wstring"></a>to_wstring

Konwertuje wartość na ciąg znaków dwubajtowych.

```cpp
wstring to_wstring(int value);
wstring to_wstring(unsigned int value);
wstring to_wstring(long value);
wstring to_wstring(unsigned long value);
wstring to_wstring(long long value);
wstring to_wstring(unsigned long long value);
wstring to_wstring(float value);
wstring to_wstring(double value);
wstring to_wstring(long double value);
```

### <a name="parameters"></a>Parametry

\ *wartości*
Wartość do konwersji.

### <a name="return-value"></a>Wartość zwracana

Ciąg dwubajtowy, który reprezentuje wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje *wartość* na sekwencję elementów przechowywanych w obiekcie array, `Buf` wewnętrzna dla funkcji tak jak w przypadku wywoływania `swprintf(Buf, Len, Fmt, value)`, gdzie `Fmt` jest

- `L"%d"` Jeśli *wartość* jest typu **`int`**

- `L"%u"` Jeśli *wartość* jest typu **`unsigned int`**

- `L"%ld"` Jeśli *wartość* jest typu **`long`**

- `L"%lu"` Jeśli *wartość* jest typu **`unsigned long`**

- `L"%lld"` Jeśli *wartość* jest typu **`long long`**

- `L"%llu"` Jeśli *wartość* jest typu **`unsigned long long`**

- `L"%f"` Jeśli *wartość* jest typu **`float`** lub **`double`**

- `L"%Lf"` Jeśli *wartość* jest typu **`long double`**

Funkcja zwraca `wstring(Buf)`.

## <a name="see-also"></a>Zobacz też

[\<ciąg >](../standard-library/string.md)
