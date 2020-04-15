---
title: basic_istringstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
ms.openlocfilehash: 6a8ead5f1014e7f750e01988241ab020431312da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376805"
---
# <a name="basic_istringstream-class"></a>basic_istringstream — Klasa

Opisuje obiekt, który steruje wyodrębnianiem elementów i zakodowanych obiektów z buforu strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alloc*\
Klasa alokatora.

*Elem*\
Typ elementu podstawowego ciągu.

*Tr*\
Cechy charakteru wyspecjalizowane na podstawowym elemencie ciągu.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który steruje wyodrębnianiem elementów i zakodowanych obiektów z buforu strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, z elementami typu *Elem*, którego cechy charakteru są określane przez klasę *Tr*i których elementy są przydzielane przez alokatora klasy *Alokatora klasy Alokator*. Obiekt przechowuje obiekt klasy basic_stringbuf< **Elem**, **Tr** `Alloc` ,>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_istringstream](#basic_istringstream)|Konstruuje obiekt `basic_istringstream`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem parametru `Alloc`szablonu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rdbuf](#rdbuf)|Zwraca adres typu buforu przechowywanego `pointer` strumienia do `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`>.|
|[Str](#str)|Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.|
|[Wymiany](#swap)|Wymienia wartości w `basic_istringstream` tym obiekcie dla wartości podanego obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartości do `basic_istringstream` tego obiektu z parametru obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<sstream>

**Przestrzeń nazw:** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a>basic_istringstream::allocator_type

Typ jest synonimem parametru `Alloc`szablonu .

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a>basic_istringstream::basic_istringstream

Konstruuje obiekt `basic_istringstream`typu .

```cpp
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Obiekt typu `basic_string`.

*Prawo*\
Odwołanie do wartości r `basic_istringstream` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje klasę [basic_istream](../standard-library/basic-istream-class.md)podstawową,`sb`wywołując `sb` basic_istream ( ), gdzie jest przechowywanym obiektem [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`klasy , `Tr` `Alloc`>. Inicjuje `sb` również, `basic_stringbuf` <  `Elem` `Tr`dzwoniąc `Alloc` ,>( `_Mode` &#124; `ios_base::in`).

Drugi konstruktor inicjuje klasę `basic_istream(sb)`podstawową, wywołując . `sb` Inicjuje również, `basic_stringbuf` <  `Elem` `Tr`dzwoniąc `Alloc` ,>( `str` `_Mode` , &#124; `ios_base::in`).

Trzeci konstruktor inicjuje obiekt z zawartością *right*, traktowane jako odwołanie rvalue.

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a>basic_istringstream::operator=

Przypisuje wartości do `basic_istringstream` tego obiektu z parametru obiektu.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie do `basic_istringstream` wartości r. do obiektu.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu zawartością *prawa,* traktowaną jako przypisanie przenoszenia odwołania rvalue.

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a>basic_istringstream::rdbuf

Zwraca adres buforu przechowywanego `pointer` strumienia typu [do basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres zapisanego `pointer` buforu strumienia typu do basic_stringbuf< **Elem**, `Alloc` **Tr**,>.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który `rdbuf`używa .

## <a name="basic_istringstreamstr"></a><a name="str"></a>basic_istringstream::str

Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*\
Nowy ciąg.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt klasy [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, którego kontrolowana sekwencja jest kopią sekwencji kontrolowanej przez ** \*ten**.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Druga funkcja elementu `rdbuf`  -> członkowskiego `_Newstr`wywołuje **str**( ).

### <a name="example"></a>Przykład

Zobacz [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) na przykład, który `str`używa .

## <a name="basic_istringstreamswap"></a><a name="swap"></a>basic_istringstream::swap

Wymienia wartości dwóch `basic_istringstream` obiektów.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Prawo*|Odwołanie `lvalue` do `basic_istringstream` obiektu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wymienia wartości tego obiektu i wartości *prawej*.

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
