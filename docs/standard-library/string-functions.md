---
title: '&lt;funkcje&gt; ciągów'
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
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455601"
---
# <a name="ltstringgt-functions"></a>&lt;funkcje&gt; ciągów

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

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

*była*\
Strumień wejściowy, z którego ma zostać wyodrębniony ciąg.

*str*\
Ciąg, w którym są odczytywane znaki ze strumienia wejściowego.

*delim*\
Ogranicznik wiersza.

### <a name="return-value"></a>Wartość zwracana

Strumień wejściowy *to*.

### <a name="remarks"></a>Uwagi

Para sygnatur funkcji oznaczonych jako `(1)` Wyodrębnij znaki z *jest* do momentu, w którym zostanie znaleziona *delim* .

Para sygnatur funkcji oznaczonych `(2)` jako domyślny ogranicznik wiersza jest używana jako znak i zachowuje się jak getline ( `is`, `str`, `is`. `widen`(' `\n`')).

Druga funkcja każdej pary jest analogiczna do pierwszej z nich do obsługi [odwołań rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

Ekstrakcja zostaje zatrzymana, gdy wystąpi jedno z następujących wystąpień:

- Na końcu pliku, w którym to przypadku Flaga stanu wewnętrznego *jest* ustawiona na `ios_base::eofbit`.

- Po wyodrębnieniu elementu `delim`, który porównuje równe, w takim przypadku element nie jest umieszczany ani dołączany do kontrolowanej sekwencji.

- Po wyodrębnieniu `str.`przez funkcję elementów [max_size](../standard-library/basic-string-class.md#max_size) , w którym przypadku Flaga stanu wewnętrznego *jest* ustawiona na `ios_base::failbit`.

- Inny błąd inny niż wymienione wcześniej, w którym przypadku Flaga stanu wewnętrznego *jest* ustawiona na`ios_base::badbit`

Aby uzyskać informacje na temat flag stanu wewnętrznego, zobacz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

Jeśli funkcja nie wyodrębnia żadnych elementów, Flaga stanu wewnętrznego *jest* ustawiona na `ios_base::failbit`. W każdym `getline` *przypadku zwraca wartość*.

Jeśli wyjątek jest zgłaszany, a i *str* , *jest* pozostawiony w prawidłowym stanie.

### <a name="example"></a>Przykład

Poniższy kod ilustruje `getline()` dwa tryby: pierwszy z domyślny ogranicznikiem (nowy wiersz) i drugi z odstępem jako ogranicznikiem. Znak końca pliku (CTRL-Z na klawiaturze) służy do sterowania przerwaniem pętli while. Ustawia flagę `cin` stanu wewnętrznego na `eofbit`, która musi zostać wyczyszczona przy użyciu [basic_ios:: Clear ()](../standard-library/basic-ios-class.md#clear) przed drugim, gdy pętla będzie działać prawidłowo.

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
|*idx*|Wartość indeksu pierwszego nieskonwertowanego znaku.|

### <a name="return-value"></a>Wartość zwracana

Wartość **podwójnej precyzji** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na `val` wartość typu **Double** jako if przez wywołanie `strtod( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie zostanie ustawione `errno`, zgłasza obiekt typu. `out_of_range` W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja `*_Eptr -  str.c_str()` przechowuje `*idx` w i `val`zwraca.

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
|*idx*|Wartość indeksu pierwszego nieskonwertowanego znaku.|

### <a name="return-value"></a>Wartość zwracana

Wartość zmiennoprzecinkowa.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na `val` wartość typu **float** jako if przez wywołanie `strtof( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie zostanie ustawione `errno`, zgłasza obiekt typu. `out_of_range` W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja `*_Eptr -  str.c_str()` przechowuje `*idx` w i `val`zwraca.

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
|*idx*|Zawiera indeks pierwszego nieskonwertowanego znaku w zwracaniu.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="remarks"></a>Uwagi

Funkcja `stoi` konwertuje sekwencję znaków w *str* na wartość typu **int** i zwraca wartość. Na przykład, gdy przeszedł sekwencję znaków "10", wartość zwracana przez `stoi` jest liczbą całkowitą 10.

`stoi`zachowuje `strtol` się podobnie do funkcji dla znaków jednobajtowych, gdy jest wywoływana w sposób `strtol( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji; lub `wcstol` dla szerokich znaków, gdy jest wywoływana w podobny sposób, `wcstol(Str.c_str(), _Eptr, idx)`. Aby uzyskać więcej informacji, zobacz [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Jeśli `str.c_str() == *_Eptr` `invalid_argument`, `stoi` zgłasza obiekt typu. Jeśli takie wywołanie zostanie ustawione `errno`lub jeśli zwracana wartość nie może być reprezentowana jako obiekt typu **int**, zgłasza obiekt typu. `out_of_range` W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja `*_Eptr - str.c_str()` zapisuje `*idx`w.

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
|*idx*|Wartość indeksu pierwszego nieskonwertowanego znaku.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="return-value"></a>Wartość zwracana

Wartość Long-Integer.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na `val` wartość typu **Long** , tak jakby przez wywołanie `strtol( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie zostanie ustawione `errno`, zgłasza obiekt typu. `out_of_range` W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja `*_Eptr -  str.c_str()` przechowuje `*idx` w i `val`zwraca.

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
|*idx*|Wartość indeksu pierwszego nieskonwertowanego znaku.|

### <a name="return-value"></a>Wartość zwracana

Wartość **Long Double** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na `val` wartość typu **Long Double** , tak jakby przez wywołanie `strtold( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie zostanie ustawione `errno`, zgłasza obiekt typu. `out_of_range` W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja `*_Eptr -  str.c_str()` przechowuje `*idx` w i `val`zwraca.

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
|*idx*|Wartość indeksu pierwszego nieskonwertowanego znaku.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="return-value"></a>Wartość zwracana

**Długa** wartość Long.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na `val` wartość typu **Long** Long AS IF `strtoll( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie zostanie ustawione `errno`, zgłasza obiekt typu. `out_of_range` W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja `*_Eptr -  str.c_str()` przechowuje `*idx` w i `val`zwraca.

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
|*idx*|Wartość indeksu pierwszego nieskonwertowanego znaku.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="return-value"></a>Wartość zwracana

Nieniepodpisana wartość Long-Integer.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na `val` wartość typu unsigned o  `strtoul( str.c_str(), _Eptr, idx)`Long AS IF, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie zostanie ustawione `errno`, zgłasza obiekt typu. `out_of_range` W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja `*_Eptr -  str.c_str()` przechowuje `*idx` w i `val`zwraca.

## <a name="stoull"></a>stoull

Konwertuje sekwencję znaków na unsigned long **Long**.

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
|*idx*|Wartość indeksu pierwszego nieskonwertowanego znaku.|
|*base*|Podstawa numeru, która ma zostać użyta.|

### <a name="return-value"></a>Wartość zwracana

Nieniepodpisana wartość **Long Long** .

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w *str* na `val` wartość typu unsigned **Long** AS IF `strtoull( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznym dla funkcji. Jeśli ` str.c_str() == *_Eptr` generuje obiekt typu `invalid_argument`. Jeśli takie wywołanie zostanie ustawione `errno`, zgłasza obiekt typu. `out_of_range` W przeciwnym razie, jeśli *IDX* nie jest wskaźnikiem null, funkcja `*_Eptr -  str.c_str()` przechowuje `*idx` w i `val`zwraca.

## <a name="swap"></a>wymiany

Wymienia tablice znaków dwóch ciągów.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Jeden ciąg, którego elementy mają zostać zamienione na inne ciągi.

*Kliknij*\
Inny ciąg, którego elementy mają zostać zamienione na pierwszy ciąg.

### <a name="remarks"></a>Uwagi

Funkcja Template wykonuje wyspecjalizowaną funkcję członkowską . [Zamień](../standard-library/basic-string-class.md#swap) (*prawy*) dla ciągów, które gwarantują stałą złożoność.

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

`string` Reprezentuje wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje wartość *Val* na sekwencję elementów przechowywanych w obiekcie `Buf` Array Internal dla funkcji tak, jakby przez wywołanie `sprintf(Buf, Fmt, Val)`, gdzie `Fmt` is

- `"%d"`Jeśli `Val` ma typ **int**

- `"%u"`Jeśli `Val` typem jest **bez znaku int**

- `"%ld"`Jeśli `Val` ma typ **Long**

- `"%lu"`Jeśli `Val` jest typu **unsigned long**

- `"%lld"`Jeśli `Val` ma typ **Long Long**

- `"%llu"`Jeśli `Val` typ ma unsigned long **Long**

- `"%f"`Jeśli `Val` ma typ **float** lub **Double**

- `"%Lf"`Jeśli `Val` ma typ **Long Double**

Funkcja zwraca wartość `string(Buf)`.

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

Funkcja jest konwertowana `Val` na sekwencję elementów przechowywanych w obiekcie `Buf` Array Internal dla funkcji tak, jakby przez wywołanie `swprintf(Buf, Len, Fmt, Val)`, gdzie `Fmt` is

- `L"%d"`Jeśli `Val` ma typ **int**

- `L"%u"`Jeśli `Val` typem jest **bez znaku int**

- `L"%ld"`Jeśli `Val` ma typ **Long**

- `L"%lu"`Jeśli `Val` jest typu **unsigned long**

- `L"%lld"`Jeśli `Val` ma typ **Long Long**

- `L"%llu"`Jeśli `Val` typ ma unsigned long **Long**

- `L"%f"`Jeśli `Val` ma typ **float** lub **Double**

- `L"%Lf"`Jeśli `Val` ma typ **Long Double**

Funkcja zwraca wartość `wstring(Buf)`.

## <a name="see-also"></a>Zobacz także

[\<ciąg >](../standard-library/string.md)
