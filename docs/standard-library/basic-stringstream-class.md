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
ms.openlocfilehash: ebf9b87b60cf790a2ca032eb805095f277324178
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866288"
---
# <a name="basic_stringstream-class"></a>basic_stringstream — Klasa

Opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu buforu strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**, `Alloc`>.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

\ *alokacji*
Klasa alokatora.

*Elem*\
Typ podstawowego elementu ciągu.

\ *TR*
Cechy znaków wyspecjalizowane dla elementu Basic ciągu.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu bufora strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**, `Alloc`>, z elementami typu `Elem`, których cechy znaków są określane przez klasę `Tr`, a których elementy są przydzielane przez Alokator klasy `Alloc`. Obiekt przechowuje obiekt klasy basic_stringbuf < **elem**, **TR**`Alloc`>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_stringstream](#basic_stringstream)|Konstruuje obiekt typu `basic_stringstream`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem dla parametru szablonu `Alloc`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca adres buforu zapisanego strumienia typu `pointer` do [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Ustawia lub pobiera tekst w buforze ciągów bez zmiany pozycji zapisu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strumienia >

**Przestrzeń nazw:** std

## <a name="allocator_type"></a>basic_stringstream:: allocator_type

Typ jest synonimem dla parametru szablonu `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstream"></a>basic_stringstream:: basic_stringstream

Konstruuje obiekt typu `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Mode*\
Jedno z wyliczeń w [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*str*\
Obiekt typu `basic_string`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_iostream](../standard-library/basic-iostream-class.md)( **SB**), gdzie `sb` jest przechowywanym obiektem klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**, `Alloc`>. Inicjuje również `sb` przez wywołanie basic_stringbuf < **elem**, **Tr**, `Alloc`> (`_Mode`).

Drugi Konstruktor inicjuje klasę bazową, wywołując basic_iostream ( **SB**). Inicjuje również `sb` przez wywołanie basic_stringbuf < **elem**, **Tr**, `Alloc`> (_ *str*, `_Mode`).

## <a name="rdbuf"></a>basic_stringstream:: rdbuf

Zwraca adres buforu zapisanego strumienia typu **wskaźnik** do [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**`Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu zapisanego strumienia typu `pointer` do basic_stringbuf < **elem**, **TR**`Alloc`>.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem korzystającym z `rdbuf`.

## <a name="str"></a>basic_stringstream:: str

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

Zwraca obiekt klasy [basic_string](../standard-library/basic-string-class.md)< **elem**, **TR**, `Alloc`>, którego kontrolowana sekwencja jest kopią sekwencji kontrolowanej przez **\*** .

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Druga funkcja członkowska wywołuje `rdbuf` -> **str**(`_Newstr`).

### <a name="example"></a>Przykład

Przykład, który używa `str`, znajduje się w [basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str) .

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
