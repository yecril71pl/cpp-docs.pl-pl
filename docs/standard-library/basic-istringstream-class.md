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
ms.openlocfilehash: 53760cd2d69067fd93a76a35b0ba29fcc82a4664
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960072"
---
# <a name="basicistringstream-class"></a>basic_istringstream — Klasa

Opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z bufor strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*ALLOC* klasa alokatora.

*Elem* typ elementu podstawowego ciągu.

*TR* cech przeznaczone specjalnie dla elementu podstawowego ciągu.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z bufor strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, z elementami typu *Elem*, którego cech są określane przez klasę *Tr*, a której elementy są przydzielane przez alokatora klasy  *ALLOC*. Obiekt przechowuje obiekt basic_stringbuf — Klasa < **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_istringstream](#basic_istringstream)|Tworzy obiekt typu `basic_istringstream`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem dla parametru szablonu `Alloc`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca adres buforu strumienia przechowywanych typu `pointer` do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Ustawia lub pobiera tekst w buforze ciąg bez zmiany pozycji zapisu.|
|[swap](#swap)|Wymienia wartości w tym `basic_istringstream` obiektu dla osób, które udostępnionego obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartości do tego `basic_istringstream` obiektu na podstawie parametru obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strumienia >

**Namespace:** standardowe

## <a name="allocator_type"></a>  basic_istringstream::allocator_type

Typ jest synonimem dla parametru szablonu `Alloc`.

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

*_Tryb* jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str* obiektu typu `basic_string`.

*prawy* odwołanie rvalue z `basic_istringstream` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_istream](../standard-library/basic-istream-class.md)(`sb`), gdzie `sb` jest przechowywany obiekt klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md) <  `Elem`, `Tr`, `Alloc`>. Inicjuje również `sb` przez wywołanie metody `basic_stringbuf` <  `Elem`, `Tr`, `Alloc`> ( `_Mode` &#124; `ios_base::in`).

Drugi Konstruktor inicjuje klasę bazową, wywołując `basic_istream(sb)`. Inicjuje również `sb` przez wywołanie metody `basic_stringbuf` <  `Elem`, `Tr`, `Alloc`> ( `str`, `_Mode` &#124; `ios_base::in`).

Trzeci Konstruktor inicjuje obiekt z zawartością *prawo*, traktowane jako odwołanie rvalue.

## <a name="op_eq"></a>  basic_istringstream::operator =

Przypisuje wartości do tego `basic_istringstream` obiektu na podstawie parametru obiektu.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

*prawy* odwołania rvalue do `basic_istringstream` obiektu.

### <a name="remarks"></a>Uwagi

Operator składowy zamienia zawartość treści obiektu *prawo*, traktowanej jako odwołanie rvalue, Przenieś przypisania.

## <a name="rdbuf"></a>  basic_istringstream::rdbuf

Zwraca adres buforu strumienia przechowywanych typu `pointer` do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu strumienia przechowywanych typu `pointer` do basic_stringbuf — < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład, który używa `rdbuf`.

## <a name="str"></a>  basic_istringstream::str

Ustawia lub pobiera tekst w buforze ciąg bez zmiany pozycji zapisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;


void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr* nowego ciągu znaków.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt klasy [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, którego kontrolowanej sekwencji jest kopię sekwencji kontrolowanej przez  **\*to**.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Drugi wywołania funkcji elementu członkowskiego `rdbuf`  ->  **str**( `_Newstr`).

### <a name="example"></a>Przykład

Zobacz [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) przykład, który używa `str`.

## <a name="swap"></a>  basic_istringstream::swap

Wymienia dwie wartości `basic_istringstream` obiektów.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|`lvalue` Odwołanie do `basic_istringstream` obiektu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wymienia wartości tego obiektu i wartości *prawo*.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
