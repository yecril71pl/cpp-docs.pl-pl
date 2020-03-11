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
ms.openlocfilehash: 828aeb975178850f5c0a7ea3b7e982bbadd6e7c4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856619"
---
# <a name="ltstringgt-functions"></a>&lt;funkcje&gt; ciągu

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[wymiany](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a>getline

Wyodrębnij ciągi ze strumienia wejściowego w wierszu.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delim);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& is,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delim);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& is,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

*jest*\
Strumień wejściowy, z którego ma zostać wyodrębniony ciąg.

*str*\
Ciąg, w którym są odczytywane znaki ze strumienia wejściowego.

*delim*\
Ogranicznik wiersza.

### <a name="return-value"></a>Wartość zwracana

Strumień wejściowy *to*.

### <a name="remarks"></a>Uwagi

Para sygnatur funkcji oznaczona `(1)` Wyodrębnij znaki z *jest* do momentu znalezienia *delim* , przechowywanie ich w *str*.

Para sygnatur funkcji oznaczona `(2)` używać nowego wiersza jako ogranicznika linii domyślnej i zachowuje się jak **getline**(`is`, `str``is`. `widen`("`\n`").

Druga funkcja każdej pary jest analogiczna do pierwszej z nich do obsługi [odwołań rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

Ekstrakcja zostaje zatrzymana, gdy wystąpi jedno z następujących wystąpień:

- Na końcu pliku, w którym przypadku Flaga stanu wewnętrznego *jest* ustawiona na `ios_base::eofbit`.

- Po wyodrębnieniu elementu, który porównuje wartość równą `delim`, w takim przypadku element nie jest umieszczany ani dołączany do kontrolowanej sekwencji.

- Gdy funkcja wyodrębnia `str.`elementy [max_size](../standard-library/basic-string-class.md#max_size) , w tym przypadku Flaga stanu wewnętrznego *jest* ustawiona na `ios_base::failbit`.

- Inne błędy inne niż wymienione wcześniej, w tym przypadku Flaga stanu wewnętrznego *jest* ustawiona na `ios_base::badbit`

Aby uzyskać informacje na temat flag stanu wewnętrznego, zobacz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

Jeśli funkcja nie wyodrębnia żadnych elementów, Flaga stanu wewnętrznego *jest* ustawiona na `ios_base::failbit`. W każdym przypadku *`getline` zwraca wartość*.

Jeśli wyjątek jest zgłaszany, a i *str* , *jest* pozostawiony w prawidłowym stanie.

### <a name="example"></a>Przykład

Poniższy kod ilustruje `getline()` w dwóch trybach: najpierw z Domyślnym ogranicznikiem (nowy wiersz) i drugim z odstępem jako ogranicznikiem. Znak końca pliku (CTRL-Z na klawiaturze) służy do sterowania przerwaniem pętli while. Ustawia flagę stanu wewnętrznego `cin` na `eofbit`, która musi zostać wyczyszczona z [basic_ios:: Clear ()](../standard-library/basic-ios-class.md#clear) przed sekundą, gdy pętla będzie działać prawidłowo.

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

## <a name="stod"></a>stod

Konwertuje sekwencję znaków na wartość typu **Double**.

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

|Parametr|Opis|
|---------------|-----------------|
|*str*|Sekwencja znaków do przekonwertowania.|
|*IDX*|Wartość indeksu pierwszego nieskonwertowanego znaku.|

### <a name="return-value"></a>Wartość zwracana

Wartość **podwójnej precyzji** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość `val` typu **Double** jako IF, wywołując `strtod( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stof"></a>stof

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

|Parametr|Opis|
|---------------|-----------------|
|*str*|Sekwencja znaków do przekonwertowania.|
|*IDX*|Wartość indeksu pierwszego nieskonwertowanego znaku.|

### <a name="return-value"></a>Wartość zwracana

Wartość zmiennoprzecinkowa.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość `val` typu **float** jako IF, wywołując `strtof( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stoi"></a>stoi

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

|Parametr|Opis|
|---------------|-----------------|
|*str*|Sekwencja znaków do przekonwertowania.|
|*IDX*|Zawiera indeks pierwszego nieskonwertowanego znaku w zwracaniu.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="remarks"></a>Uwagi

Funkcja `stoi` konwertuje sekwencję znaków w *str* na wartość typu **int** i zwraca wartość. Na przykład, gdy przeszedł sekwencję znaków "10", wartość zwracana przez `stoi` jest liczbą całkowitą 10.

`stoi` zachowuje się podobnie do `strtol` funkcji dla znaków jednobajtowych, gdy jest wywoływana w sposób `strtol( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji; lub `wcstol` dla szerokich znaków, gdy jest wywoływana w podobny sposób, `wcstol(Str.c_str(), _Eptr, idx)`. Aby uzyskać więcej informacji, zobacz [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Jeśli `str.c_str() == *_Eptr`, `stoi` zgłasza obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`lub jeśli zwracana wartość nie może być reprezentowana jako obiekt typu **int**, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr - str.c_str()` w `*idx`.

## <a name="stol"></a>stol

Konwertuje sekwencję znaków na wartość typu **Long**.

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

|Parametr|Opis|
|---------------|-----------------|
|*str*|Sekwencja znaków do przekonwertowania.|
|*IDX*|Wartość indeksu pierwszego nieskonwertowanego znaku.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="return-value"></a>Wartość zwracana

Wartość Long-Integer.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość `val` typu **Long** as IF, wywołując `strtol( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stold"></a>stold

Konwertuje sekwencję znaków na wartość typu **Long Double**.

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*str*|Sekwencja znaków do przekonwertowania.|
|*IDX*|Wartość indeksu pierwszego nieskonwertowanego znaku.|

### <a name="return-value"></a>Wartość zwracana

Wartość **Long Double** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość `val` typu **Long Double** jako IF, wywołując `strtold( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stoll"></a>stoll

Konwertuje sekwencję znaków na **długą długą**.

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

|Parametr|Opis|
|---------------|-----------------|
|*str*|Sekwencja znaków do przekonwertowania.|
|*IDX*|Wartość indeksu pierwszego nieskonwertowanego znaku.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="return-value"></a>Wartość zwracana

**Długa** wartość Long.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość `val` typu **Long** Long as IF, wywołując `strtoll( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stoul"></a>stoul

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

|Parametr|Opis|
|---------------|-----------------|
|*str*|Sekwencja znaków do przekonwertowania.|
|*IDX*|Wartość indeksu pierwszego nieskonwertowanego znaku.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="return-value"></a>Wartość zwracana

Nieniepodpisana wartość Long-Integer.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na wartość `val` typu **unsigned long** as IF, wywołując `strtoul( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stoull"></a>stoull

Konwertuje sekwencję znaków na **unsigned long long**.

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

|Parametr|Opis|
|---------------|-----------------|
|*str*|Sekwencja znaków do przekonwertowania.|
|*IDX*|Wartość indeksu pierwszego nieskonwertowanego znaku.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="return-value"></a>Wartość zwracana

Nieniepodpisana wartość **Long Long** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* do `val` wartości typu **unsigned long long** as IF, wywołując `strtoull( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie ustawi `errno`, zgłasza obiekt typu `out_of_range`. W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja przechowuje `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="swap"></a>wymiany

Wymienia tablice znaków dwóch ciągów.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Jeden ciąg, którego elementy mają zostać zamienione na inne ciągi.

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

## <a name="to_string"></a>to_string

Konwertuje wartość na `string`.

```cpp
string to_string(int Val);
string to_string(unsigned int Val);
string to_string(long Val);
string to_string(unsigned long Val);
string to_string(long long Val);
string to_string(unsigned long long Val);
string to_string(float Val);
string to_string(double Val);
string to_string(long double Val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Użyte*|Wartość do konwersji.|

### <a name="return-value"></a>Wartość zwracana

`string`, która reprezentuje wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje wartość *Val* na sekwencję elementów przechowywanych w obiekcie array `Buf` wewnętrzna dla funkcji tak, jakby przez wywoływanie `sprintf(Buf, Fmt, Val)`, gdzie `Fmt` jest

- `"%d"`, jeśli `Val` ma typ **int**

- `"%u"`, jeśli `Val` ma typ **int bez znaku**

- `"%ld"`, jeśli `Val` ma typ **Long**

- `"%lu"`, jeśli `Val` ma typ **unsigned long**

- `"%lld"`, jeśli `Val` typu **Long** Long

- `"%llu"`, jeśli `Val` ma typ **unsigned long long**

- `"%f"`, jeśli `Val` ma typ **float** lub **Double**

- `"%Lf"`, jeśli `Val` ma typ **Long Double**

Funkcja zwraca `string(Buf)`.

## <a name="to_wstring"></a>to_wstring

Konwertuje wartość na ciąg znaków dwubajtowych.

```cpp
wstring to_wstring(int Val);
wstring to_wstring(unsigned int Val);
wstring to_wstring(long Val);
wstring to_wstring(unsigned long Val);
wstring to_wstring(long long Val);
wstring to_wstring(unsigned long long Val);
wstring to_wstring(float Val);
wstring to_wstring(double Val);
wstring to_wstring(long double Val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Val`|Wartość do konwersji.|

### <a name="return-value"></a>Wartość zwracana

Ciąg dwubajtowy, który reprezentuje wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje `Val` na sekwencję elementów przechowywanych w obiekcie array `Buf` wewnętrzna dla funkcji tak, jakby przez wywoływanie `swprintf(Buf, Len, Fmt, Val)`, gdzie `Fmt` jest

- `L"%d"`, jeśli `Val` ma typ **int**

- `L"%u"`, jeśli `Val` ma typ **int bez znaku**

- `L"%ld"`, jeśli `Val` ma typ **Long**

- `L"%lu"`, jeśli `Val` ma typ **unsigned long**

- `L"%lld"`, jeśli `Val` typu **Long** Long

- `L"%llu"`, jeśli `Val` ma typ **unsigned long long**

- `L"%f"`, jeśli `Val` ma typ **float** lub **Double**

- `L"%Lf"`, jeśli `Val` ma typ **Long Double**

Funkcja zwraca `wstring(Buf)`.

## <a name="see-also"></a>Zobacz także

[\<ciąg >](../standard-library/string.md)
