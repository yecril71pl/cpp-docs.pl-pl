---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: cc08fb426df289b3478ad9d29b03f9a6dd5d3978
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412478"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

Definiuje kilka klas szablonów, które obsługują operacje iostreams w sekwencji przechowywanych w obiekcie przydzielanej tablicy. Takie sekwencje łatwo są konwertowane do i z obiektów klasy szablonu [basic_string](../standard-library/basic-string-class.md).

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

Obiekty typu `char *` może korzystać z funkcji w [ \<strstream — >](../standard-library/strstream.md) do przesyłania strumieniowego. Jednak \<strstream — > jest przestarzała i użycie \<strumienia > jest zalecane.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|Tworzy typ `basic_istringstream` wyspecjalizowane na **char** parametru szablonu.|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|Tworzy typ `basic_ostringstream` wyspecjalizowane na **char** parametru szablonu.|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|Tworzy typ `basic_stringbuf` wyspecjalizowane na **char** parametru szablonu.|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|Tworzy typ `basic_stringstream` wyspecjalizowane na **char** parametru szablonu.|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|Tworzy typ `basic_istringstream` wyspecjalizowane na **wchar_t** parametru szablonu.|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|Tworzy typ `basic_ostringstream` wyspecjalizowane na **wchar_t** parametru szablonu.|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|Tworzy typ `basic_stringbuf` wyspecjalizowane na **wchar_t** parametru szablonu.|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|Tworzy typ `basic_stringstream` wyspecjalizowane na **wchar_t** parametru szablonu.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|Wymienia wartości pomiędzy dwoma `sstream` obiektów.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|W tym artykule opisano buforu strumieni, który kontroluje transmisji elementów typu `Elem`, którego cech są określane przez klasę `Tr`, do i z sekwencji elementów przechowywanych w tablicy obiektów.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|Opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z bufor strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`>, z elementami typu `Elem`, którego cech są określane przez klasę `Tr`, a której elementy są przydzielane przez alokatora klasy `Alloc`.|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|Opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych do bufora strumienia, klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`>, z elementami typu `Elem`, którego cech są określane przez klasę `Tr`, a której elementy są przydzielane przez alokatora klasy `Alloc`.|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|Opisuje obiekt, który kontroluje wstawienia i wydobycia elementów i obiektów zakodowanych przy użyciu bufor strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`>, z elementami typu `Elem`, którego cech są określane przez klasę `Tr`, a której elementy są przydzielane przez alokatora klasy `Alloc`.|

## <a name="requirements"></a>Wymagania

- **Nagłówek:** \<strumienia >

- **Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
