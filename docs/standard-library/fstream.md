---
title: '&lt;fstream —&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 46f65f746179740f2d67dd1ada2f96ab3fb6aaf6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203237"
---
# <a name="ltfstreamgt"></a>&lt;fstream —&gt;

Definiuje kilka klas, które obsługują operacje iostreams na sekwencjach przechowywanych w plikach zewnętrznych.

## <a name="syntax"></a>Składnia

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` wyspecjalizowany dla **`char`** parametrów szablonu.|
|[fstream —](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` wyspecjalizowany dla **`char`** parametrów szablonu.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` wyspecjalizowany dla **`char`** parametrów szablonu.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` wyspecjalizowany dla **`char`** parametrów szablonu.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` wyspecjalizowany dla **`wchar_t`** parametrów szablonu.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` wyspecjalizowany dla **`wchar_t`** parametrów szablonu.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` wyspecjalizowany dla **`wchar_t`** parametrów szablonu.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` wyspecjalizowany dla **`wchar_t`** parametrów szablonu.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Szablon klasy opisuje bufor strumienia, który kontroluje przekazywanie elementów typu `Elem` , których cechy znaków są określane przez klasę `Tr` , do i z sekwencji elementów przechowywanych w zewnętrznym pliku.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Szablon klasy opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> , z elementami typu `Elem` , których cechy znaków są określane przez klasę `Tr` .|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Szablon klasy opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> , z elementami typu `Elem` , których cechy znaku są określane przez klasę `Tr` .|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Szablon klasy opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> , z elementami typu `Elem` , których cechy znaku są określane przez klasę `Tr` .|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
