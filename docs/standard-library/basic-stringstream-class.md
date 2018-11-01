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
ms.openlocfilehash: 7e39d5dabf27ffbe15e519c006592935076a45c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546539"
---
# <a name="basicstringstream-class"></a>basic_stringstream — Klasa

Opisuje obiekt, który kontroluje wstawienia i wydobycia elementów i obiektów zakodowanych przy użyciu bufor strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alokacji*<br/>
Klasa alokatora.

*Elem*<br/>
Typ elementu podstawowego ciągu.

*TR*<br/>
Cechy znaków przeznaczone specjalnie dla elementu podstawowego ciągu.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który kontroluje wstawienia i wydobycia elementów i obiektów zakodowanych przy użyciu bufor strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, z elementami typu `Elem`, którego cech są określane przez klasę `Tr`, a której elementy są przydzielane przez alokatora klasy `Alloc`. Obiekt przechowuje obiekt basic_stringbuf — Klasa < **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_stringstream](#basic_stringstream)|Tworzy obiekt typu `basic_stringstream`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem dla parametru szablonu `Alloc`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca adres buforu strumienia przechowywanych typu `pointer` do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Ustawia lub pobiera tekst w buforze ciąg bez zmiany pozycji zapisu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strumienia >

**Namespace:** standardowe

## <a name="allocator_type"></a>  basic_stringstream::allocator_type

Typ jest synonimem dla parametru szablonu `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream

Tworzy obiekt typu `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str*<br/>
Obiekt typu `basic_string`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_iostream —](../standard-library/basic-iostream-class.md)( **sb**), gdzie `sb` jest przechowywany obiekt klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>. Inicjuje również `sb` przez wywołującego basic_stringbuf — < **Elem**, **Tr**, `Alloc`> ( `_Mode`).

Drugi Konstruktor inicjuje wywoływania basic_iostream — klasa bazowa ( **sb**). Inicjuje również `sb` przez wywołującego basic_stringbuf — < **Elem**, **Tr**, `Alloc`> (_ *Str*, `_Mode`).

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

Zwraca adres buforu strumienia przechowywanych typu **wskaźnik** do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu strumienia przechowywanych typu `pointer` do basic_stringbuf — < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład, który używa `rdbuf`.

## <a name="str"></a>  basic_stringstream::str

Ustawia lub pobiera tekst w buforze ciąg bez zmiany pozycji zapisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*<br/>
Nowy ciąg.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt klasy [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, którego kontrolowanej sekwencji jest kopię sekwencji kontrolowanej przez  **\*to**.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Drugi wywołania funkcji elementu członkowskiego `rdbuf`  ->  **str**( `_Newstr`).

### <a name="example"></a>Przykład

Zobacz [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) przykład, który używa `str`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
