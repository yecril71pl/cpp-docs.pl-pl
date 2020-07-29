---
title: '&lt;strumienia&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 6ab2164e4969a2320f67d479062808b33b0869f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212140"
---
# <a name="ltsstreamgt"></a>&lt;strumienia&gt;

Definiuje kilka szablonów klas, które obsługują operacje iostreams na sekwencjach przechowywanych w przydzielonym obiekcie array. Takie sekwencje są łatwo konwertowane do i z obiektów [basic_string](../standard-library/basic-string-class.md)szablonu klas.

## <a name="syntax"></a>Składnia

```cpp
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lewym*|Odwołanie do `sstream` obiektu.|
|*Kliknij*|Odwołanie do `sstream` obiektu.|

## <a name="remarks"></a>Uwagi

Obiekty typu `char *` mogą korzystać z funkcji w programie w [\<strstream>](../standard-library/strstream.md) celu przesyłania strumieniowego. Jednak \<strstream> jest przestarzałe, a korzystanie z programu \<sstream> jest zalecane.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[istringstream —](../standard-library/sstream-typedefs.md#istringstream)|Tworzy typ `basic_istringstream` wyspecjalizowany dla **`char`** parametru szablonu.|
|[ostringstream —](../standard-library/sstream-typedefs.md#ostringstream)|Tworzy typ `basic_ostringstream` wyspecjalizowany dla **`char`** parametru szablonu.|
|[stringbuf —](../standard-library/sstream-typedefs.md#stringbuf)|Tworzy typ `basic_stringbuf` wyspecjalizowany dla **`char`** parametru szablonu.|
|[stringstream —](../standard-library/sstream-typedefs.md#stringstream)|Tworzy typ `basic_stringstream` wyspecjalizowany dla **`char`** parametru szablonu.|
|[wistringstream —](../standard-library/sstream-typedefs.md#wistringstream)|Tworzy typ `basic_istringstream` wyspecjalizowany dla **`wchar_t`** parametru szablonu.|
|[wostringstream —](../standard-library/sstream-typedefs.md#wostringstream)|Tworzy typ `basic_ostringstream` wyspecjalizowany dla **`wchar_t`** parametru szablonu.|
|[wstringbuf —](../standard-library/sstream-typedefs.md#wstringbuf)|Tworzy typ `basic_stringbuf` wyspecjalizowany dla **`wchar_t`** parametru szablonu.|
|[wstringstream —](../standard-library/sstream-typedefs.md#wstringstream)|Tworzy typ `basic_stringstream` wyspecjalizowany dla **`wchar_t`** parametru szablonu.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[wymiany](../standard-library/sstream-functions.md#sstream_swap)|Wymienia wartości między dwoma `sstream` obiektami.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|Opisuje bufor strumienia, który kontroluje przekazywanie elementów typu `Elem` , których cechy znaków są określane przez klasę `Tr` , do i z sekwencji elementów przechowywanych w obiekcie array.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|Opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc`>, z elementami typu `Elem` , których cechy znaków są określane przez klasę `Tr` , i których elementy są przydzielane przez Alokator klasy `Alloc` .|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|Opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do bufora strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc`>, z elementami typu `Elem` , których cechy znaków są określane przez klasę `Tr` , i których elementy są przydzielane przez Alokator klasy `Alloc` .|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|Opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu bufora strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc`>, z elementami typu `Elem` , których cechy znaków są określane przez klasę `Tr` i których elementy są przydzielane przez Alokator klasy `Alloc` .|

## <a name="requirements"></a>Wymagania

- **Nagłówek:**\<sstream>

- **Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
