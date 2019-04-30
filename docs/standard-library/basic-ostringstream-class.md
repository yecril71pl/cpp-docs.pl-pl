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
ms.openlocfilehash: 45a7eb1384c70b488e057fb9df8ad4c496272316
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414142"
---
# <a name="basicostringstream-class"></a>basic_ostringstream — Klasa

Opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych do bufora strumienia, klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alokacji*<br/>
Klasa alokatora.

*Elem*<br/>
Typ elementu podstawowego ciągu.

*TR*<br/>
Cechy znaków przeznaczone specjalnie dla elementu podstawowego ciągu.

## <a name="remarks"></a>Uwagi

Klasa opisuje obiekt, który kontroluje wstawiania elementów i zakodowany obiekty do bufora strumienia, elementami typu `Elem`, którego cech są określane przez klasę `Tr`, a której elementy są przydzielane przez alokatora z Klasa `Alloc`. Obiekt przechowuje obiekt basic_stringbuf — Klasa < **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|Tworzy obiekt typu `basic_ostringstream`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem dla parametru szablonu *alokacji*.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca adres buforu strumienia przechowywanych typu `pointer` do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Ustawia lub pobiera tekst w buforze ciąg bez zmiany pozycji zapisu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strumienia >

**Namespace:** standardowe

## <a name="allocator_type"></a>  basic_ostringstream::allocator_type

Typ jest synonimem dla parametru szablonu *alokacji*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstream"></a>  basic_ostringstream::basic_ostringstream

Tworzy obiekt basic_ostringstream — typu.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str*<br/>
Obiekt typu `basic_string`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**), gdzie `sb` jest przechowywany obiekt klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>. Inicjuje również **sb** przez wywołującego basic_stringbuf — < **Elem**, **Tr**, `Alloc`> ( `_Mode` &#124; `ios_base::out`).

Drugi Konstruktor inicjuje klasę bazową basic_ostream wywołującego ( **sb**). Inicjuje również `sb` przez wywołującego basic_stringbuf — < **Elem**, **Tr**, `Alloc`> (_ *Str*, `_Mode` &#124; `ios_base::out`).

## <a name="rdbuf"></a>  basic_ostringstream::rdbuf

Zwraca adres buforu strumienia przechowywanych typu `pointer` do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres bufora strumienia przechowywanych typu `pointer` do basic_stringbuf — < **Elem**, **Tr**, `Alloc`>.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres buforu strumienia przechowywanych typu `pointer` do basic_stringbuf — < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład, który używa `rdbuf`.

## <a name="str"></a>  basic_ostringstream::str

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
