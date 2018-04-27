---
title: '&lt;ciąg&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
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
ms.workload:
- cplusplus
ms.openlocfilehash: 26fe9fab46beb2333df3fae351f99bb661f6d3e1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltstringgt-functions"></a>&lt;ciąg&gt; funkcji

||||
|-|-|-|
|[getline](#getline)|[stod —](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a>  getline

Wyodrębnij ciągi ze strumienia wejściowego wiersz po wierszu.

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

`is` Strumień wejściowy, z którego ma zostać wyodrębniony ciąg.

`str` Ciąg, do którego są odczytywanie znaków ze strumienia wejściowego.

`delim` Ogranicznik wiersza.

### <a name="return-value"></a>Wartość zwracana

Strumień wejściowy `is`.

### <a name="remarks"></a>Uwagi

Para sygnatury funkcji oznaczone `(1)` Wyodrębnij znaki z `is` do momentu `delim` zostanie znaleziony, przechowywanie ich w `str`.

Para sygnatury funkcji oznaczone `(2)` Użyj nowego wiersza jako domyślnym ogranicznikiem wiersza i zachowywać się jak **getline**( `is`, `str`, `is`. `widen`(' `\n`')).

Druga funkcja każdej pary jest analogowy z pierwszym punktem do obsługi [odwołania do r-wartości](../cpp/lvalues-and-rvalues-visual-cpp.md).

Wyodrębnianie zatrzymywana, gdy wystąpi jedno z następujących czynności:

- Na końcu pliku w którym to przypadku flagę stan wewnętrzny `is` ma ustawioną wartość `ios_base::eofbit`.

- Po funkcji wyodrębnia element, który porównuje równa **delim**, w którym to przypadku element nie jest odłożyć ani dołączane do kontrolowanej sekwencji.

- Po wyodrębnia funkcji `str.` [max_size](../standard-library/basic-string-class.md#max_size) elementów, w którym to przypadku Flaga stan wewnętrzny `is` ma ustawioną wartość `ios_base::failbit`.

- Inny błąd inny niż wymienionego powyżej, w którym to przypadku flagę stan wewnętrzny `is` ma ustawioną wartość `ios_base::badbit`

Uzyskać informacji o flagach stan wewnętrzny, zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Jeśli funkcja wyodrębnia żadnych elementów, stan wewnętrzny flagę `is` ma ustawioną wartość `ios_base::failbit`. W każdym przypadku `getline` zwraca `is`.

Jeśli wyjątek `is` i `str` są pozostawiane w prawidłowym stanie.

### <a name="example"></a>Przykład

Poniższy kod przedstawia `getline()` w dwóch trybach: najpierw z domyślnym ogranicznikiem (nowego wiersza) i drugi spacji, jak ogranicznik. Znak końca pliku (na klawiaturze CTRL-Z) jest używana do sterowania zakończenia while pętle. To ustawienie flagi stanu wewnętrznego z `cin` do `eofbit`, muszą zostać wyczyszczone z [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) przed sekundę, gdy pętla będzie działać prawidłowo.

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

## <a name="stod"></a>  stod —

Konwertuje sekwencję znaków `double`.

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
|`str`|Sekwencja znaków, który ma zostać przekonwertowany.|
|`idx`|Wartość indeksu pierwszego znaku nieprzekonwertowane.|

### <a name="return-value"></a>Wartość zwracana

`double` Wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w `str` wartość `val` typu `double` tak, jakby przez wywołanie `strtod( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem funkcji wewnętrznej. Jeśli ` str.c_str() == *_Eptr` zgłasza typu obiektu `invalid_argument`. Jeśli takie połączenie ustawiał `errno`, zgłasza typu obiektu `out_of_range`. W przeciwnym razie, jeśli `idx` wskaźnika o wartości null, funkcja magazynów nie jest `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stof"></a>  stof —

Konwertuje sekwencja znaków na typ float.

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
|`str`|Sekwencja znaków, który ma zostać przekonwertowany.|
|`idx`|Wartość indeksu pierwszego znaku nieprzekonwertowane.|

### <a name="return-value"></a>Wartość zwracana

Wartość zmiennoprzecinkowa.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w `str` wartość `val` typu `float` tak, jakby przez wywołanie `strtof( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem funkcji wewnętrznej. Jeśli ` str.c_str() == *_Eptr` zgłasza typu obiektu `invalid_argument`. Jeśli takie połączenie ustawiał `errno`, zgłasza typu obiektu `out_of_range`. W przeciwnym razie, jeśli `idx` wskaźnika o wartości null, funkcja magazynów nie jest `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stoi"></a>  stoi —

Konwertuje sekwencja znaków na liczbę całkowitą.

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
|`str`|Sekwencja znaków, który ma zostać przekonwertowany.|
|`idx`|Zawiera indeks pierwszego znaku nieprzekonwertowane przy powrocie.|
|`base`|Podstawowy numer do użycia.|

### <a name="remarks"></a>Uwagi

Funkcja `stoi` konwertuje sekwencja znaków w `str` wartość typu `int` i zwraca wartość. Na przykład po upływie sekwencja znaków "10" zwróciła wartość przez `stoi` jest liczbą całkowitą 10.

`stoi` działa podobnie do funkcji `strtol` znaki jednobajtowe, gdy jest wywoływana w ten sposób `strtol( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem wewnętrznej funkcji; lub `wcstol` dla znaki dwubajtowe, gdy jest wywoływana w podobny sposób `wcstol(Str.c_str(), _Eptr, idx)`. Aby uzyskać więcej informacji, zobacz [strtol —, wcstol —, _strtol_l —, _wcstol_l —](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Jeśli `str.c_str() == *_Eptr`, `stoi` zgłasza wyjątek typu obiektu `invalid_argument`. Jeśli takie połączenie ustawiał `errno`, lub jeśli zwrócona wartość nie może być reprezentowany jako obiekt typu `int`, zgłasza typu obiektu `out_of_range`. W przeciwnym razie, jeśli `idx` wskaźnika o wartości null, funkcja magazynów nie jest `*_Eptr - str.c_str()` w `*idx`.

## <a name="stol"></a>  stol —

Konwertuje sekwencję znaków `long`.

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
|`str`|Sekwencja znaków, który ma zostać przekonwertowany.|
|`idx`|Wartość indeksu pierwszego znaku nieprzekonwertowane.|
|`base`|Podstawowy numer do użycia.|

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita long.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w `str` wartość `val` typu `long` tak, jakby przez wywołanie `strtol( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem funkcji wewnętrznej. Jeśli ` str.c_str() == *_Eptr` zgłasza typu obiektu `invalid_argument`. Jeśli takie połączenie ustawiał `errno`, zgłasza typu obiektu `out_of_range`. W przeciwnym razie, jeśli `idx` wskaźnika o wartości null, funkcja magazynów nie jest `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stold"></a>  stold —

Konwertuje sekwencję znaków `long double`.

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
|`str`|Sekwencja znaków, który ma zostać przekonwertowany.|
|`idx`|Wartość indeksu pierwszego znaku nieprzekonwertowane.|

### <a name="return-value"></a>Wartość zwracana

`long double` Wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w `str` wartość `val` typu `long double` tak, jakby przez wywołanie `strtold( str.c_str(), _Eptr)`, gdzie `_Eptr` jest obiektem funkcji wewnętrznej. Jeśli ` str.c_str() == *_Eptr` zgłasza typu obiektu `invalid_argument`. Jeśli takie połączenie ustawiał `errno`, zgłasza typu obiektu `out_of_range`. W przeciwnym razie, jeśli `idx` wskaźnika o wartości null, funkcja magazynów nie jest `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stoll"></a>  stoll —

Konwertuje sekwencję znaków `long long`.

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
|`str`|Sekwencja znaków, który ma zostać przekonwertowany.|
|`idx`|Wartość indeksu pierwszego znaku nieprzekonwertowane.|
|`base`|Podstawowy numer do użycia.|

### <a name="return-value"></a>Wartość zwracana

`long long` Wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w `str` wartość `val` typu `long long` tak, jakby przez wywołanie `strtoll( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem funkcji wewnętrznej. Jeśli ` str.c_str() == *_Eptr` zgłasza typu obiektu `invalid_argument`. Jeśli takie połączenie ustawiał `errno`, zgłasza typu obiektu `out_of_range`. W przeciwnym razie, jeśli `idx` wskaźnika o wartości null, funkcja magazynów nie jest `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stoul"></a>  stoul —

Konwertuje niepodpisany sekwencja znaków długie.

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
|`str`|Sekwencja znaków, który ma zostać przekonwertowany.|
|`idx`|Wartość indeksu pierwszego znaku nieprzekonwertowane.|
|`base`|Podstawowy numer do użycia.|

### <a name="return-value"></a>Wartość zwracana

Unsigned long całkowitą.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w `str` wartość `val` typu `unsigned long` tak, jakby przez wywołanie `strtoul( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem funkcji wewnętrznej. Jeśli ` str.c_str() == *_Eptr` zgłasza typu obiektu `invalid_argument`. Jeśli takie połączenie ustawiał `errno`, zgłasza typu obiektu `out_of_range`. W przeciwnym razie, jeśli `idx` wskaźnika o wartości null, funkcja magazynów nie jest `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="stoull"></a>  stoull —

Konwertuje sekwencję znaków `unsigned long long`.

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
|`str`|Sekwencja znaków, który ma zostać przekonwertowany.|
|`idx`|Wartość indeksu pierwszego znaku nieprzekonwertowane.|
|`base`|Podstawowy numer do użycia.|

### <a name="return-value"></a>Wartość zwracana

`unsigned long long` Wartość.

### <a name="remarks"></a>Uwagi

Funkcja konwertuje sekwencję elementów w `str` wartość `val` typu `unsigned long long` tak, jakby przez wywołanie `strtoull( str.c_str(), _Eptr, idx)`, gdzie `_Eptr` jest obiektem funkcji wewnętrznej. Jeśli ` str.c_str() == *_Eptr` zgłasza typu obiektu `invalid_argument`. Jeśli takie połączenie ustawiał `errno`, zgłasza typu obiektu `out_of_range`. W przeciwnym razie, jeśli `idx` wskaźnika o wartości null, funkcja magazynów nie jest `*_Eptr -  str.c_str()` w `*idx` i zwraca `val`.

## <a name="swap"></a>  Swap

Zamienia tablic znaki z dwóch ciągów.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Jednego ciągu, których elementy mają być zamieniona na tych z innego ciągu.

`right` Inny ciąg, których elementy mają być zamieniona na pierwszy ciąg.

### <a name="remarks"></a>Uwagi

Funkcja szablonu wykonuje funkcji członkowskiej specjalne *po lewej stronie*.[ wymiany](../standard-library/basic-string-class.md#swap)(*prawo*) dla ciągów, które gwarantuje stałej złożoności.

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

## <a name="to_string"></a>  to_string

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
|`Val`|Wartość do konwersji.|

### <a name="return-value"></a>Wartość zwracana

`string` Reprezentujący wartość.

### <a name="remarks"></a>Uwagi

Konwertuje funkcję `Val` sekwencję elementy przechowywane w tablicy obiektów `Buf` wewnętrznej funkcji tak, jakby przez wywołanie `sprintf(Buf, Fmt, Val)`, gdzie `Fmt` jest

- `"%d"` Jeśli `Val` ma typ `int`

- `"%u"` Jeśli `Val` ma typ `unsigned int`

- `"%ld"` Jeśli `Val` ma typ `long`

- `"%lu"` Jeśli `Val` ma typ `unsigned long`

- `"%lld"` Jeśli `Val` ma typ `long long`

- `"%llu"` Jeśli `Val` ma typ `unsigned long long`

- `"%f"` Jeśli `Val` ma typ `float` lub `double`

- `"%Lf"` Jeśli `Val` ma typ `long double`

Funkcja zwraca `string(Buf)`.

## <a name="to_wstring"></a>  to_wstring —

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

Konwertuje funkcję `Val` sekwencję elementy przechowywane w tablicy obiektów `Buf` wewnętrznej funkcji tak, jakby przez wywołanie `swprintf(Buf, Len, Fmt, Val)`, gdzie `Fmt` jest

- `L"%d"` Jeśli `Val` ma typ `int`

- `L"%u"` Jeśli `Val` ma typ `unsigned int`

- `L"%ld"` Jeśli `Val` ma typ `long`

- `L"%lu"` Jeśli `Val` ma typ `unsigned long`

- `L"%lld"` Jeśli `Val` ma typ `long long`

- `L"%llu"` Jeśli `Val` ma typ `unsigned long long`

- `L"%f"` Jeśli `Val` ma typ `float` lub `double`

- `L"%Lf"` Jeśli `Val` ma typ `long double`

Funkcja zwraca `wstring(Buf)`.

## <a name="see-also"></a>Zobacz także

[\<ciąg >](../standard-library/string.md)<br/>
