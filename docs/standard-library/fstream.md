---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 20efdc755b7f706fc6ee962daa32bd352df39d45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159772"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

Definiuje kilka klas, które obsługują operacje iostreams w sekwencji przechowywanych w zewnętrznych plikach.

## <a name="syntax"></a>Składnia

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` wyspecjalizowane na **char** parametry szablonu.|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` wyspecjalizowane na **char** parametry szablonu.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` wyspecjalizowane na **char** parametry szablonu.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` wyspecjalizowane na **char** parametry szablonu.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` wyspecjalizowane na **wchar_t** parametry szablonu.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` wyspecjalizowane na **wchar_t** parametry szablonu.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` wyspecjalizowane na **wchar_t** parametry szablonu.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` wyspecjalizowane na **wchar_t** parametry szablonu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Klasa szablonu opisuje buforu strumieni, który kontroluje transmisji elementów typu `Elem`, którego cech są określane przez klasę `Tr`, do i z sekwencji elementów przechowywanych w pliku zewnętrznym.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wstawienia i wydobycia elementów i obiektów zakodowanych przy użyciu bufor strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)\<**Elem**,  **TR**>, z elementami typu `Elem`, którego cech są określane przez klasę `Tr`.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z bufor strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, z elementami typu `Elem`, którego cech są określane przez klasę `Tr`.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wstawiania elementów i zakodowany obiekty do bufora strumienia, klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, z elementami typu `Elem`, którego cech są określane przez klasę `Tr`.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
