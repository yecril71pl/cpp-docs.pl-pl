---
title: '&lt;istream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 0ad27bf849e8d4b9188868b9a29bf423b4cafafa
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458744"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Definiuje klasę basic_istream, która koryguje ekstrakcje dla iostreams i klasy szablonu basic_iostream, która koryguje wstawienia i wyodrębnienia. Nagłówek definiuje także powiązaną Manipulator. Ten plik nagłówka jest zwykle dołączany przez inny nagłówek iostreams; rzadko trzeba dołączyć go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Typ `basic_iostream` wyspecjalizowany dla **znaku**.|
|[istream](../standard-library/istream-typedefs.md#istream)|Typ `basic_istream` wyspecjalizowany dla **znaku**.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Typ `basic_iostream` wyspecjalizowany w **WCHAR**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Typ `basic_istream` wyspecjalizowany w **WCHAR**.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Pomija biały znak w strumieniu.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Wymienia dwa obiekty strumienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Wyodrębnia znaki i ciągi ze strumienia.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Klasa strumienia, która może wykonywać zarówno dane wejściowe, jak i wyjściowe.|
|[basic_istream](../standard-library/basic-istream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia z elementami typu `Elem`, znanym również jako [char_type](../standard-library/basic-ios-class.md#char_type), których cechy znaku są określane przez klasę `Tr`, również znana jako [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
