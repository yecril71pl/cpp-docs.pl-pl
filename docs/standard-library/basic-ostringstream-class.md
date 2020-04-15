---
title: basic_ostringstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
ms.openlocfilehash: 9e10474d3e4fb2a37e8ab52f77495758c37e8a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376781"
---
# <a name="basic_ostringstream-class"></a>basic_ostringstream — Klasa

Opisuje obiekt, który steruje wstawianiem elementów i zakodowanych obiektów do buforu `Alloc` strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alloc*\
Klasa alokatora.

*Elem*\
Typ elementu podstawowego ciągu.

*Tr*\
Cechy charakteru wyspecjalizowane na podstawowym elemencie ciągu.

## <a name="remarks"></a>Uwagi

Klasa opisuje obiekt, który kontroluje wstawianie elementów i zakodowanych `Elem`obiektów do buforu strumienia, `Tr`z elementami typu , których cechy `Alloc`charakteru są określane przez klasę i których elementy są przydzielane przez alokatora klasy . Obiekt przechowuje obiekt klasy basic_stringbuf< **Elem**, **Tr** `Alloc` ,>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|Konstruuje obiekt `basic_ostringstream`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem parametru szablonu *Alloc*.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rdbuf](#rdbuf)|Zwraca adres typu buforu przechowywanego `pointer` strumienia do `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`>.|
|[Str](#str)|Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<sstream>

**Przestrzeń nazw:** std

## <a name="basic_ostringstreamallocator_type"></a><a name="allocator_type"></a>basic_ostringstream::allocator_type

Typ jest synonimem parametru szablonu *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstreambasic_ostringstream"></a><a name="basic_ostringstream"></a>basic_ostringstream::basic_ostringstream

Konstruuje obiekt typu basic_ostringstream.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Obiekt typu `basic_string`.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje klasę [basic_ostream](../standard-library/basic-ostream-class.md)podstawową, wywołując basic_ostream `sb` **(sb),** gdzie jest przechowywanym obiektem `Alloc` klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>. Inicjuje również **sb,** dzwoniąc basic_stringbuf< **Elem**, `Alloc` **Tr**, `_Mode`>( `ios_base::out`&#124; ).

Drugi konstruktor inicjuje klasę podstawową, wywołując basic_ostream( **sb**). Inicjuje `sb` również, dzwoniąc do basic_stringbuf< **Elem**, `Alloc` **Tr**,>(_ *Str*, `_Mode` &#124; `ios_base::out`).

## <a name="basic_ostringstreamrdbuf"></a><a name="rdbuf"></a>basic_ostringstream::rdbuf

Zwraca adres buforu przechowywanego `pointer` strumienia typu [do basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu `pointer` przechowywanego strumienia, typu basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres buforu `pointer` przechowywanego strumienia typu do basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który `rdbuf`używa .

## <a name="basic_ostringstreamstr"></a><a name="str"></a>basic_ostringstream::str

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

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
