---
title: basic_stringstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
ms.openlocfilehash: f08689b1080837f042abfb3c4c52bb0ad558a448
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364867"
---
# <a name="basic_stringstream-class"></a>basic_stringstream — Klasa

W tym artykule opisano obiekt sterujący wstawianiem i wyodrębnianiem elementów oraz zakodowanych obiektów przy użyciu buforu strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alloc*\
Klasa alokatora.

*Elem*\
Typ elementu podstawowego ciągu.

*Tr*\
Cechy charakteru wyspecjalizowane na podstawowym elemencie ciągu.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który steruje wstawianiem i wyodrębnianiem elementów i zakodowanych `Alloc` obiektów przy użyciu buforu `Elem`strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, `Tr` **Tr**,>, z elementami typu, których cechy charakteru są określane przez klasę i których elementy są przydzielane przez alokatora klasy `Alloc`. Obiekt przechowuje obiekt klasy basic_stringbuf< **Elem**, **Tr** `Alloc` ,>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_stringstream](#basic_stringstream)|Konstruuje obiekt `basic_stringstream`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem parametru `Alloc`szablonu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rdbuf](#rdbuf)|Zwraca adres typu buforu przechowywanego `pointer` strumienia do `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`>.|
|[Str](#str)|Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<sstream>

**Przestrzeń nazw:** std

## <a name="basic_stringstreamallocator_type"></a><a name="allocator_type"></a>basic_stringstream::allocator_type

Typ jest synonimem parametru `Alloc`szablonu .

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstreambasic_stringstream"></a><a name="basic_stringstream"></a>basic_stringstream::basic_stringstream

Konstruuje obiekt `basic_stringstream`typu .

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Obiekt typu `basic_string`.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje klasę podstawową, wywołując [basic_iostream](../standard-library/basic-iostream-class.md) `sb` **(sb),** gdzie jest przechowywanym obiektem klasy `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>. Inicjuje `sb` również, dzwoniąc do basic_stringbuf< **Elem**, `Alloc` **Tr**, `_Mode`>( ).

Drugi konstruktor inicjuje klasę podstawową, wywołując basic_iostream( **sb**). `sb` Inicjuje również, dzwoniąc do basic_stringbuf< **Elem**, `Alloc` **Tr**,>(_ *Str*, `_Mode`).

## <a name="basic_stringstreamrdbuf"></a><a name="rdbuf"></a>basic_stringstream::rdbuf

Zwraca adres przechowywanego buforu strumienia **wskaźnika** typu [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres zapisanego `pointer` buforu strumienia typu do basic_stringbuf< **Elem**, `Alloc` **Tr**,>.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który `rdbuf`używa .

## <a name="basic_stringstreamstr"></a><a name="str"></a>basic_stringstream::str

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
