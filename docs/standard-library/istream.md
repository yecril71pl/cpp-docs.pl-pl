---
title: '&lt;IStream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 15d955aca1406183cc348395068ba042b75d7417
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846462"
---
# <a name="ltistreamgt"></a>&lt;IStream&gt;

Definiuje basic_istream szablonu klasy, który koryguje ekstrakcje dla iostreams i basic_iostream szablon klasy, który koryguje wstawienia i wyodrębnienia. Nagłówek definiuje także powiązaną Manipulator. Ten plik nagłówka jest zwykle dołączany przez inny nagłówek iostreams; rzadko trzeba dołączyć go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Typ `basic_iostream` wyspecjalizowany dla **`char`** .|
|[IStream](../standard-library/istream-typedefs.md#istream)|Typ `basic_istream` wyspecjalizowany dla **`char`** .|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Typ `basic_iostream` wyspecjalizowany w **WCHAR**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Typ `basic_istream` wyspecjalizowany w **WCHAR**.|

### <a name="manipulators"></a>Manipulatory

|Nazwa|Opis|
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Pomija biały znak w strumieniu.|
|[wymiany](../standard-library/istream-functions.md#istream_swap)|Wymienia dwa obiekty strumienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[>>operatora ](../standard-library/istream-operators.md#op_gt_gt)|Wyodrębnia znaki i ciągi ze strumienia.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Klasa strumienia, która może wykonywać zarówno dane wejściowe, jak i wyjściowe.|
|[basic_istream](../standard-library/basic-istream-class.md)|Szablon klasy opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia z elementami typu `Elem` , znanym również jako [char_type](../standard-library/basic-ios-class.md#char_type), których cechy znaku są określane przez klasę `Tr` , znane także jako [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
