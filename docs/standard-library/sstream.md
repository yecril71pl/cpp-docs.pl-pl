---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 8284e56e8afb1e5518cbcbb772079b4f19d57b18
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451731"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

Definiuje kilka klas szablonów, które obsługują operacje iostreams na sekwencjach przechowywanych w przydzielonym obiekcie array. Takie sekwencje są łatwo konwertowane do i z obiektów klasy szablonu [basic_string](../standard-library/basic-string-class.md).

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
|*left*|Odwołanie do `sstream` obiektu.|
|*right*|Odwołanie do `sstream` obiektu.|

## <a name="remarks"></a>Uwagi

Obiekty typu `char *` mogą korzystać z funkcji w [ \<strstream >](../standard-library/strstream.md) do przesyłania strumieniowego. Strstream > jest jednak przestarzałe i zaleca się \<użycie strumienia >. \<

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|Tworzy typ `basic_istringstream` wyspecjalizowany dla parametru szablonu **char** .|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|Tworzy typ `basic_ostringstream` wyspecjalizowany dla parametru szablonu **char** .|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|Tworzy typ `basic_stringbuf` wyspecjalizowany dla parametru szablonu **char** .|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|Tworzy typ `basic_stringstream` wyspecjalizowany dla parametru szablonu **char** .|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|Tworzy typ `basic_istringstream` wyspecjalizowany dla parametru szablonu **wchar_t** .|
|[wostringstream —](../standard-library/sstream-typedefs.md#wostringstream)|Tworzy typ `basic_ostringstream` wyspecjalizowany dla parametru szablonu **wchar_t** .|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|Tworzy typ `basic_stringbuf` wyspecjalizowany dla parametru szablonu **wchar_t** .|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|Tworzy typ `basic_stringstream` wyspecjalizowany dla parametru szablonu **wchar_t** .|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|Wymienia wartości między dwoma `sstream` obiektami.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|Opisuje bufor strumienia, który kontroluje przekazywanie elementów typu `Elem`, których cechy znaków są określane przez klasę `Tr`, do i z sekwencji elementów przechowywanych w obiekcie array.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|Opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**elem**, **TR**, `Alloc`>, z elementami typu `Elem`, których znak cechy są określane przez klasę `Tr`i których elementy są przydzielane przez Alokator klasy. `Alloc`|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|Opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do bufora strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**elem**, **TR**, `Alloc`>, z elementami typu `Elem`, których cechy znaku są określane przez klasę `Tr`i których elementy są przydzielane przez Alokator klasy. `Alloc`|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|Opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu buforu strumienia klasy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**elem**, **TR** `Alloc`>, z elementami typu `Elem`, których cechy znaków są określane przez klasę `Tr`i których elementy są przydzielane przez Alokator klasy. `Alloc`|

## <a name="requirements"></a>Wymagania

- **Nagłówek:** \<strumienia >

- **Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
