---
title: '&lt;sstream —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <sstream>
dev_langs:
- C++
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee9beb54dd241c6987b79db238f033f3d169497
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861678"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

Definiuje kilka klas szablonu, które obsługują operacje iostream sekwencji przechowywane w tablicy przydzielone obiektów. Takie sekwencje łatwo są konwertowane do i z obiektów klasy szablonu [basic_string —](../standard-library/basic-string-class.md).

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
|`left`|Odwołanie do `sstream` obiektu.|
|`right`|Odwołanie do `sstream` obiektu.|

## <a name="remarks"></a>Uwagi

Obiekty typu `char *` można używać funkcji [ \<strstream — >](../standard-library/strstream.md) do przesyłania strumieniowego. Jednak \<strstream — > jest przestarzała i użycie \<sstream — > jest zalecane.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|Tworzy typ `basic_istringstream` specjalne na `char` parametru szablonu.|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|Tworzy typ `basic_ostringstream` specjalne na `char` parametru szablonu.|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|Tworzy typ `basic_stringbuf` specjalne na `char` parametru szablonu.|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|Tworzy typ `basic_stringstream` specjalne na `char` parametru szablonu.|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|Tworzy typ `basic_istringstream` specjalne na `wchar_t` parametru szablonu.|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|Tworzy typ `basic_ostringstream` specjalne na `wchar_t` parametru szablonu.|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|Tworzy typ `basic_stringbuf` specjalne na `wchar_t` parametru szablonu.|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|Tworzy typ `basic_stringstream` specjalne na `wchar_t` parametru szablonu.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|Zamienia wartości między dwoma `sstream` obiektów.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|W tym artykule opisano buforu strumienia, który kontroluje przekazywania elementów typu **elementu**, którego cech znaków są określane przez klasę **Tr**, do i z sekwencję elementy przechowywane w tablicy obiektów.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|Zawiera opis obiektu, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)<**elementu**, **Tr**, `Alloc`>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**, a której elementy są przydzielane przez program przydzielania klasy `Alloc`.|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|Opis obiektu, który kontroluje wstawiania elementów i obiektów zakodowanych do buforu strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)<**elementu**, **Tr**, `Alloc`>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**, a której elementy są przydzielane przez program przydzielania klasy `Alloc`.|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|Zawiera opis obiektu, który kontroluje wstawiania i wyodrębniania elementów i obiektów zakodowany przy użyciu buforu strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)<**elementu**, **Tr**, `Alloc`>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**, a której elementy są przydzielane przez program przydzielania klasy `Alloc`.|

## <a name="requirements"></a>Wymagania

- **Nagłówek:** \<sstream — >

- **Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
