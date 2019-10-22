---
title: '&lt;fstream &gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 1f85367b9ae527c9387d085acc1496bfbbf7cc9e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688038"
---
# <a name="ltfstreamgt"></a>&lt;fstream &gt;

Definiuje kilka klas, które obsługują operacje iostreams na sekwencjach przechowywanych w plikach zewnętrznych.

## <a name="syntax"></a>Składnia

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` wyspecjalizowany w parametrach szablonu **char** .|
|[fstream —](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` wyspecjalizowany w parametrach szablonu **char** .|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` wyspecjalizowany w parametrach szablonu **char** .|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` wyspecjalizowany w parametrach szablonu **char** .|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` wyspecjalizowany w parametrach szablonu **wchar_t** .|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` wyspecjalizowany w parametrach szablonu **wchar_t** .|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` wyspecjalizowany w parametrach szablonu **wchar_t** .|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` wyspecjalizowany w parametrach szablonu **wchar_t** .|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Szablon klasy opisuje bufor strumienia, który kontroluje transmisję elementów typu `Elem`, których cechy znaku są określane przez klasę `Tr`, do i z sekwencji elementów przechowywanych w zewnętrznym pliku.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Szablon klasy opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, z elementami typu `Elem`, których znak cechy są określane przez klasę `Tr`.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Szablon klasy opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, z elementami typu `Elem`, których cechy znaku są określone przez klasę `Tr`.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Szablon klasy opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do buforu strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, z elementami typu `Elem`, których cechy znaków są określone według klasy `Tr`.|

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
