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
ms.openlocfilehash: fd2ab79466c01343cbdadbcb649e3b05eee3c2a0
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561781"
---
# <a name="basic_istringstream-class"></a>basic_istringstream — Klasa

Opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **elem**, **TR** `Alloc`>.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alokacj*\
Klasa alokatora.

*Elem*\
Typ podstawowego elementu ciągu.

*Zdawczy*\
Cechy znaków wyspecjalizowane dla elementu Basic ciągu.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **elem**, **TR**, `Alloc`>, z elementami typu *elem*, których cechy znakowe są określane przez klasę *TR*i których elementy są przydzielane przez alokatora klasy *Alloc*. Obiekt przechowuje obiekt klasy basic_stringbuf< **elem**, **TR**, `Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[basic_istringstream](#basic_istringstream)|Konstruuje obiekt typu `basic_istringstream` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem dla parametru szablonu `Alloc` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca adres buforu zapisanego strumienia typu `pointer` do [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem` , `Tr` , `Alloc`>.|
|[str](#str)|Ustawia lub pobiera tekst w buforze ciągów bez zmiany pozycji zapisu.|
|[wymiany](#swap)|Wymienia wartości w tym `basic_istringstream` obiekcie dla podanego obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje wartości do tego `basic_istringstream` obiektu z parametru Object.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<sstream>

**Przestrzeń nazw:** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a> basic_istringstream:: allocator_type

Typ jest synonimem dla parametru szablonu `Alloc` .

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a> basic_istringstream:: basic_istringstream

Konstruuje obiekt typu `basic_istringstream` .

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

*_Mode*\
Jedno z wyliczeń w [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*str*\
Obiekt typu `basic_string`.

*Kliknij*\
Odwołanie rvalue do `basic_istringstream` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_istream](../standard-library/basic-istream-class.md)( `sb` ), gdzie `sb` jest przechowywany obiekt klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem` , `Tr` , `Alloc`>. Jest on również inicjowany `sb` przez wywołanie `basic_stringbuf` <  `Elem` , `Tr` , `Alloc`> ( `_Mode` &#124; `ios_base::in` ).

Drugi Konstruktor inicjuje klasę bazową, wywołując `basic_istream(sb)` . Jest on również inicjowany `sb` przez wywołanie `basic_stringbuf` <  `Elem` , `Tr` , `Alloc`> ( `str` , `_Mode` &#124; `ios_base::in` ).

Trzeci Konstruktor inicjuje obiekt z zawartością *prawa*, traktowany jako odwołanie rvalue.

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a> basic_istringstream:: operator =

Przypisuje wartości do tego `basic_istringstream` obiektu z parametru Object.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie rvalue do `basic_istringstream` obiektu.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu zawartością z *prawej strony*, traktowaną jako odwołanie rvalue przenoszenia.

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a> basic_istringstream:: rdbuf

Zwraca adres buforu zapisanego strumienia typu `pointer` do [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **elem**, **TR**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu zapisanego strumienia typu `pointer` do basic_stringbuf< **elem**, **TR**, `Alloc`>.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem, który używa `rdbuf` .

## <a name="basic_istringstreamstr"></a><a name="str"></a> basic_istringstream:: str

Ustawia lub pobiera tekst w buforze ciągów bez zmiany pozycji zapisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*\
Nowy ciąg.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt klasy [basic_string](../standard-library/basic-string-class.md) <  **elem**, **TR** `Alloc`>, którego kontrolowana sekwencja jest kopią sekwencji kontrolowanej przez ** \* ten**element.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca [rdbuf](#rdbuf)  ->  [str](../standard-library/basic-stringbuf-class.md#str). Druga funkcja członkowska wywołuje `rdbuf`  ->  **str**( `_Newstr` ).

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str) `str` .

## <a name="basic_istringstreamswap"></a><a name="swap"></a> basic_istringstream:: swap

Wymienia wartości dwóch `basic_istringstream` obiektów.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie lvalue do `basic_istringstream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wymienia wartości tego obiektu i wartości z *prawej strony*.

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
