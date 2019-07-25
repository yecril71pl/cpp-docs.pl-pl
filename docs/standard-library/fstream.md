---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: ba6a4152b8d37f5b0186f9d05c6ba850e8c2e54c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454017"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

Definiuje kilka klas, które obsługują operacje iostreams na sekwencjach przechowywanych w plikach zewnętrznych.

## <a name="syntax"></a>Składnia

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` wyspecjalizowany dla parametrów szablonu **char** .|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` wyspecjalizowany dla parametrów szablonu **char** .|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` wyspecjalizowany dla parametrów szablonu **char** .|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` wyspecjalizowany dla parametrów szablonu **char** .|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` wyspecjalizowany dla parametrów szablonu **wchar_t** .|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` wyspecjalizowany dla parametrów szablonu **wchar_t** .|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` wyspecjalizowany dla parametrów szablonu **wchar_t** .|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` wyspecjalizowany dla parametrów szablonu **wchar_t** .|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Klasa szablonu opisuje bufor strumienia, który kontroluje przekazywanie elementów typu `Elem`, których cechy znaków są określane przez klasę `Tr`, do i z sekwencji elementów przechowywanych w zewnętrznym pliku.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**elem**, **TR**>, z elementami typu `Elem`, których cechy znaków są określane przez klasę `Tr`.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**elem**, **TR**>, z elementami typu `Elem`, których cechy znaku są określane przez klasę `Tr`.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**elem**, **TR**>, z elementami typu `Elem`, których cechy znaku są określane przez klasę `Tr`.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
