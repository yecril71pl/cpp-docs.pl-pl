---
title: basic_istringstream — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0754ba9dc63f77793ced17e7950c7fc3ea3290d7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="basicistringstream-class"></a>basic_istringstream — Klasa

Zawiera opis obiektu, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **elementu**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

`Alloc` Allocator — klasa.

`Elem` Typ podstawowy elementu ciągu.

*TR* cech znaków specjalizowany w elemencie podstawowe ciągu.

## <a name="remarks"></a>Uwagi

Klasy szablonów opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **elementu**, **Tr**, `Alloc`>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**, i której elementy są przydzielane przez alokatora —Klasa`Alloc`. Obiekt przechowuje obiekt basic_stringbuf — Klasa < **elementu**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_istringstream](#basic_istringstream)|Tworzy obiekt typu `basic_istringstream`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem parametru szablonu `Alloc`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca adres buforu strumienia przechowywanych typu `pointer` do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.|
|[swap](#swap)|Zamienia wartości w tym `basic_istringstream` obiektu tych udostępnionego obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartości do tego `basic_istringstream` obiektu z parametrem obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<sstream — >

**Namespace:** Standard

## <a name="allocator_type"></a>  basic_istringstream::allocator_type

Typ jest synonimem parametru szablonu `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstream"></a>  basic_istringstream::basic_istringstream

Tworzy obiekt typu `basic_istringstream`.

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

`_Mode` Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`str` Obiekt typu `basic_string`.

`right` Odwołanie do r-wartości z `basic_istringstream` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasy podstawowej, przez wywołanie metody [basic_istream —](../standard-library/basic-istream-class.md)( `sb`), gdzie `sb` jest przechowywane obiekt klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md) <  `Elem`, `Tr`, `Alloc`>. Inicjuje również `sb` przez wywołanie metody `basic_stringbuf` <  `Elem`, `Tr`, `Alloc`> ( `_Mode` &#124; `ios_base::in`).

Drugi Konstruktor inicjuje klasy podstawowej, przez wywołanie metody `basic_istream(sb)`. Inicjuje również `sb` przez wywołanie metody `basic_stringbuf` <  `Elem`, `Tr`, `Alloc`> ( `str`, `_Mode` &#124; `ios_base::in`).

Trzeci Konstruktor inicjuje obiekt z zawartością `right`, traktowane jako odwołanie do r-wartości.

## <a name="op_eq"></a>  basic_istringstream::operator =

Przypisuje wartości do tego `basic_istringstream` obiektu z parametrem obiektu.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

`right` Odwołania do r-wartości do `basic_istringstream` obiektu.

### <a name="remarks"></a>Uwagi

Operator członkowski zastępuje zawartość obiektu zawartość `right`, poddanego jako odwołanie do r-wartości Przenieś przypisania.

## <a name="rdbuf"></a>  basic_istringstream::rdbuf

Zwraca adres buforu strumienia przechowywanych typu **wskaźnika** do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **elementu**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu strumienia przechowywanych typu **wskaźnika** do basic_stringbuf — < **elementu**, **Tr**, `Alloc`>.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który używa `rdbuf`.

## <a name="str"></a>  basic_istringstream::str

Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;


void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

`_Newstr` Nowe parametry.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt klasy [basic_string —](../standard-library/basic-string-class.md)< **elementu**, **Tr**, `Alloc`>, którego kopię sekwencji kontrolowane przez jest kontrolowanej sekwencji  **\*to**.

### <a name="remarks"></a>Uwagi

Zwraca pierwszy funkcji członkowskiej [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Drugi wywołania funkcji Członkowskich `rdbuf`  ->  **str**( `_Newstr`).

### <a name="example"></a>Przykład

Zobacz [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) na przykład, który używa **str**.

## <a name="swap"></a>  basic_istringstream::swap

Zamienia wartości dwu `basic_istringstream` obiektów.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`right`|`lvalue` Odwołanie do `basic_istringstream` obiektu.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia wartości tego obiektu i wartości `right`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
