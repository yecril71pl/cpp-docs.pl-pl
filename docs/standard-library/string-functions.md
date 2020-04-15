---
title: '&lt;funkcje ciągu&gt;'
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
ms.openlocfilehash: 3f1dca71a6bb9d5461150378191b9373f907ecd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376658"
---
# <a name="ltstringgt-functions"></a>&lt;funkcje ciągu&gt;

||||
|-|-|-|
|[Getline](#getline)|[stod ( stod )](#stod)|[z o.o.](#stof)|
|[stoisk](#stoi)|[Stol](#stol)|[stold (schylać)](#stold)|
|[Stoll](#stoll)|[stoul (stoul)](#stoul)|[stoull (włas iem](#stoull)|
|[Wymiany](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>Getline

Wyodrębnij ciągi z wejściowego strumienia wiersz po wierszu.

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

*Str*\
Ciąg, do którego są odczytywane znaki ze strumienia wejściowego.

*Ogranicznik*\
Ogranicznik linii.

### <a name="return-value"></a>Wartość zwracana

Strumień wejściowy *in_stream*.

### <a name="remarks"></a>Uwagi

Para podpisów funkcji `(1)` oznaczonych znaków wyodrębniania z *in_stream* aż do *ogranicznika* zostanie znaleziony, przechowując je w *str*.

Para oznaczonych podpisów `(2)` funkcyjnych używa nowej linii jako `getline(in_stream, str, in_stream. widen('\n'))`domyślnego ogranicznika linii i zachowuje się jak .

Druga funkcja każdej pary jest analogowa do pierwszej, która obsługuje [odwołania do rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

Ekstrakcja zatrzymuje się, gdy wystąpi jedna z następujących sytuacji:

- Na końcu pliku, w którym to *in_stream* przypadku wewnętrzna flaga `ios_base::eofbit`państwa in_stream jest ustawiona na .

- Po funkcji wyodrębnia element, który porównuje równe *ogranicznika*. Element nie zostanie odłożony lub dołączone do kontrolowanej sekwencji.

- Po funkcji `str.` [wyodrębnia max_size](../standard-library/basic-string-class.md#max_size) elementów. Wewnętrzna flaga państwa *in_stream* jest `ios_base::failbit`ustawiona na .

- Inny błąd inny niż ten, który był wcześniej wymieniony; wewnętrzna flaga państwa *in_stream* jest `ios_base::badbit`ustawiona na .

Aby uzyskać informacje na temat wewnętrznych flag państwowych, zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Jeśli funkcja nie wyodrębni żadnych elementów, *in_stream* wewnętrzna flaga `ios_base::failbit`stanu in_stream jest ustawiona na . W każdym `getline` przypadku zwraca *in_stream*.

Jeśli wyjątek, *in_stream* i *str* pozostają w prawidłowym stanie.

### <a name="example"></a>Przykład

Poniższy kod `getline()` jest demonstrowany w dwóch trybach: po pierwsze z domyślnym ogranicznikiem (nowa linia), a drugi z odstępem jako ogranicznik. Znak końca pliku (CTRL-Z na klawiaturze) służy do sterowania zakończeniem pętli while. Ta wartość ustawia wewnętrzną `cin` `eofbit`flagę stanu na , która musi zostać wyczyszczona za pomocą [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) przed wykonaniem drugiej pętli.

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

## <a name="stod"></a><a name="stod"></a>stod ( stod )

Konwertuje sekwencję **`double`** znaków na .

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

*Str*\
Sekwencja znaków do konwersji.

*Idx*\
Wartość indeksu pierwszego nieprzekonwertowanego znaku.

### <a name="return-value"></a>Wartość zwracana

Wartość. **`double`**

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję *str* elementów w str **`double`** do wartości `strtod( str.c_str(), _Eptr)`typu, tak jakby przez wywołanie , gdzie `_Eptr` jest obiektem wewnętrznym do funkcji. Jeśli `str.c_str() == *_Eptr`, rzuca obiekt typu `invalid_argument`. Jeśli takie wywołanie `errno`zostanie ustawione , rzuca `out_of_range`obiekt typu . W przeciwnym razie jeśli *idx* nie jest `*_Eptr -  str.c_str()` wskaźnikiem zerowym, funkcja przechowuje `*idx` i zwraca wartość.

## <a name="stof"></a><a name="stof"></a>z o.o.

Konwertuje sekwencję znaków na float.

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

*Str*\
Sekwencja znaków do konwersji.

*Idx*\
Wartość indeksu pierwszego nieprzekonwertowanego znaku.

### <a name="return-value"></a>Wartość zwracana

Wartość. **`float`**

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję *str* elementów w str **`float`** do wartości `strtof( str.c_str(), _Eptr)`typu, tak jakby przez wywołanie , gdzie `_Eptr` jest obiektem wewnętrznym do funkcji. Jeśli `str.c_str() == *_Eptr`, rzuca obiekt typu `invalid_argument`. Jeśli takie wywołanie `errno`zostanie ustawione , rzuca `out_of_range`obiekt typu . W przeciwnym razie jeśli *idx* nie jest `*_Eptr -  str.c_str()` wskaźnikiem zerowym, funkcja przechowuje `*idx` i zwraca wartość.

## <a name="stoi"></a><a name="stoi"></a>stoisk

Konwertuje sekwencję znaków na całkowitą.

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

*Str*\
Sekwencja znaków do konwersji.

*Idx*\
Wartość indeksu pierwszego nieprzekonwertowanego znaku.

*Podstawowej*\
Podstawa liczbowa do użycia.

### <a name="remarks"></a>Uwagi

Funkcja `stoi` konwertuje sekwencję znaków w *str* **`int`** na wartość typu i zwraca wartość. Na przykład po przekazaniu sekwencji znaków "10", wartość zwracana jest `stoi` całkowitej 10.

`stoi`zachowuje się podobnie do `strtol` funkcji dla znaków jedno bajtowych, `strtol( str.c_str(), _Eptr, idx)`gdy `_Eptr` jest wywoływana w sposób , gdzie jest obiektem wewnętrznym funkcji; lub `wcstol` dla szerokich znaków, gdy jest `wcstol(Str.c_str(), _Eptr, idx)`nazywany w podobny sposób, . Aby uzyskać więcej informacji, zobacz [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Jeśli `str.c_str() == *_Eptr` `stoi` , rzuca obiekt `invalid_argument`typu . Jeśli takie wywołanie `errno`zostanie ustawione lub jeśli zwrócona wartość nie może **`int`** być reprezentowana jako `out_of_range`obiekt typu, zgłasza obiekt typu . W przeciwnym razie, jeśli *idx* nie jest `*_Eptr - str.c_str()` `*idx`wskaźnikiem zerowym, funkcja jest magazynowa w pliku .

## <a name="stol"></a><a name="stol"></a>Stol

Konwertuje sekwencję **`long`** znaków na .

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

*Str*\
Sekwencja znaków do konwersji.

*Idx*\
Wartość indeksu pierwszego nieprzekonwertowanego znaku.

*Podstawowej*\
Podstawa liczbowa do użycia.

### <a name="return-value"></a>Wartość zwracana

Wartość długiej liczby całkowitej.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję *str* elementów w str **`long`** do wartości `strtol( str.c_str(), _Eptr, idx)`typu, tak jakby przez wywołanie , gdzie `_Eptr` jest obiektem wewnętrznym do funkcji. Jeśli `str.c_str() == *_Eptr`, rzuca obiekt typu `invalid_argument`. Jeśli takie wywołanie `errno`zostanie ustawione , rzuca `out_of_range`obiekt typu . W przeciwnym razie jeśli *idx* nie jest `*_Eptr -  str.c_str()` wskaźnikiem zerowym, funkcja przechowuje `*idx` i zwraca wartość.

## <a name="stold"></a><a name="stold"></a>stold (schylać)

Konwertuje sekwencję **`long double`** znaków na .

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

*Str*\
Sekwencja znaków do konwersji.

*Idx*\
Wartość indeksu pierwszego nieprzekonwertowanego znaku.

### <a name="return-value"></a>Wartość zwracana

Wartość. **`long double`**

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję *str* elementów w str **`long double`** do wartości `strtold( str.c_str(), _Eptr)`typu, tak jakby przez wywołanie , gdzie `_Eptr` jest obiektem wewnętrznym do funkcji. Jeśli `str.c_str() == *_Eptr`, rzuca obiekt typu `invalid_argument`. Jeśli takie wywołanie `errno`zostanie ustawione , rzuca `out_of_range`obiekt typu . W przeciwnym razie jeśli *idx* nie jest `*_Eptr -  str.c_str()` wskaźnikiem zerowym, funkcja przechowuje `*idx` i zwraca wartość.

## <a name="stoll"></a><a name="stoll"></a>Stoll

Konwertuje sekwencję **`long long`** znaków na .

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

*Str*\
Sekwencja znaków do konwersji.

*Idx*\
Wartość indeksu pierwszego nieprzekonwertowanego znaku.

*Podstawowej*\
Podstawa liczbowa do użycia.

### <a name="return-value"></a>Wartość zwracana

Wartość. **`long long`**

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję *str* elementów w str **`long long`** do wartości `strtoll( str.c_str(), _Eptr, idx)`typu, tak jakby przez wywołanie , gdzie `_Eptr` jest obiektem wewnętrznym do funkcji. Jeśli `str.c_str() == *_Eptr`, rzuca obiekt typu `invalid_argument`. Jeśli takie wywołanie `errno`zostanie ustawione , rzuca `out_of_range`obiekt typu . W przeciwnym razie jeśli *idx* nie jest `*_Eptr -  str.c_str()` wskaźnikiem zerowym, funkcja przechowuje `*idx` i zwraca wartość.

## <a name="stoul"></a><a name="stoul"></a>stoul (stoul)

Konwertuje sekwencję znaków na niepodpisaną długą.

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

*Str*\
Sekwencja znaków do konwersji.

*Idx*\
Wartość indeksu pierwszego nieprzekonwertowanego znaku.

*Podstawowej*\
Podstawa liczbowa do użycia.

### <a name="return-value"></a>Wartość zwracana

Niepodpisaną wartość długiej liczby całkowitej.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję *str* elementów w str **`unsigned long`** do wartości `strtoul( str.c_str(), _Eptr, idx)`typu, tak jakby przez wywołanie , gdzie `_Eptr` jest obiektem wewnętrznym do funkcji. Jeśli `str.c_str() == *_Eptr`, rzuca obiekt typu `invalid_argument`. Jeśli takie wywołanie `errno`zostanie ustawione , rzuca `out_of_range`obiekt typu . W przeciwnym razie jeśli *idx* nie jest `*_Eptr -  str.c_str()` wskaźnikiem zerowym, funkcja przechowuje `*idx` i zwraca wartość.

## <a name="stoull"></a><a name="stoull"></a>stoull (włas iem

Konwertuje sekwencję **`unsigned long long`** znaków na .

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

*Str*\
Sekwencja znaków do konwersji.

*Idx*\
Wartość indeksu pierwszego nieprzekonwertowanego znaku.

*Podstawowej*\
Podstawa liczbowa do użycia.

### <a name="return-value"></a>Wartość zwracana

Wartość. **`unsigned long long`**

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję *str* elementów w str **`unsigned long long`** do wartości `strtoull( str.c_str(), _Eptr, idx)`typu, tak jakby przez wywołanie , gdzie `_Eptr` jest obiektem wewnętrznym do funkcji. Jeśli `str.c_str() == *_Eptr`, rzuca obiekt typu `invalid_argument`. Jeśli takie wywołanie `errno`zostanie ustawione , rzuca `out_of_range`obiekt typu . W przeciwnym razie jeśli *idx* nie jest `*_Eptr -  str.c_str()` wskaźnikiem zerowym, funkcja przechowuje `*idx` i zwraca wartość.

## <a name="swap"></a><a name="swap"></a>Wymiany

Wymienia tablice znaków dwóch ciągów.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Jeden ciąg, którego elementy mają być zamienione z elementami innego ciągu.

*Prawo*\
Inny ciąg, którego elementy mają być zamienione z pierwszym ciągiem.

### <a name="remarks"></a>Uwagi

Funkcja szablonu wykonuje funkcję wyspecjalizowanego elementu członkowskiego *w lewo*. [swap](../standard-library/basic-string-class.md#swap)(*prawo*) dla ciągów, co gwarantuje stałą złożoność.

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

Konwertuje wartość `string`na .

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

*Wartość*\
Wartość do konwersji.

### <a name="return-value"></a>Wartość zwracana

Który `string` reprezentuje wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje *wartość* na sekwencję elementów `Buf` przechowywanych w obiekcie `sprintf(Buf, Fmt, value)`tablicy wewnętrznej do funkcji, tak jakby przez wywołanie , gdzie `Fmt` jest

- `"%d"`jeśli *wartość* jest typu**`int`**

- `"%u"`jeśli *wartość* jest typu**`unsigned int`**

- `"%ld"`jeśli *wartość* jest typu**`long`**

- `"%lu"`jeśli *wartość* jest typu**`unsigned long`**

- `"%lld"`jeśli *wartość* jest typu**`long long`**

- `"%llu"`jeśli *wartość* jest typu**`unsigned long long`**

- `"%f"`jeśli *wartość* jest **`float`** typu lub**`double`**

- `"%Lf"`jeśli *wartość* jest typu**`long double`**

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

*Wartość*\
Wartość do konwersji.

### <a name="return-value"></a>Wartość zwracana

Ciąg dwubajtowy, który reprezentuje wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje *wartość* na sekwencję elementów `Buf` przechowywanych w obiekcie `swprintf(Buf, Len, Fmt, value)`tablicy wewnętrznej do funkcji, tak jakby przez wywołanie , gdzie `Fmt` jest

- `L"%d"`jeśli *wartość* jest typu**`int`**

- `L"%u"`jeśli *wartość* jest typu**`unsigned int`**

- `L"%ld"`jeśli *wartość* jest typu**`long`**

- `L"%lu"`jeśli *wartość* jest typu**`unsigned long`**

- `L"%lld"`jeśli *wartość* jest typu**`long long`**

- `L"%llu"`jeśli *wartość* jest typu**`unsigned long long`**

- `L"%f"`jeśli *wartość* jest **`float`** typu lub**`double`**

- `L"%Lf"`jeśli *wartość* jest typu**`long double`**

Funkcja zwraca `wstring(Buf)`.

## <a name="see-also"></a>Zobacz też

[\<>ciągu](../standard-library/string.md)
