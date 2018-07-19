---
title: '&lt;IStream&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
dev_langs:
- C++
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7000bd30e34836466e9f662f9b6b0dd8f2ecde4c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956557"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Definiuje basic_istream klasy szablonu, które przekazuje ekstrakcji dla iostream, i basic_iostream szablonu klasy —, które przekazuje wstawienia i wyodrębniania. Nagłówek definiuje również powiązane manipulatora. Tego pliku nagłówkowego to zazwyczaj uwzględniony dla Ciebie przez inną nagłówka iostream. rzadko trzeba uwzględnić go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <istream>

```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Typ `basic_iostream` wyspecjalizowane na **char**.|
|[istream](../standard-library/istream-typedefs.md#istream)|Typ `basic_istream` wyspecjalizowane na **char**.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Typ `basic_iostream` wyspecjalizowane na **wchar**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Typ `basic_istream` wyspecjalizowane na **wchar**.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Pomija biały znak w strumieniu.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Zamienia dwa obiekty strumienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Wyodrębnia znaki oraz ciągi znaków ze strumienia.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Klasa strumienia, która może wykonać obie czynności danych wejściowych i wyjściowych.|
|[basic_istream](../standard-library/basic-istream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z elementami typu bufor strumienia `Elem`, znane również jako [char_type](../standard-library/basic-ios-class.md#char_type), którego cech są określane przez klasę `Tr`, znane również jako [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
