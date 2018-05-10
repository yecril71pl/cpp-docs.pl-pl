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
ms.openlocfilehash: 1b3e55aaa8cfc659672632a897efc7543effaf26
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Definiuje basic_istream szablonu klasy —, które przekazuje ekstrakcje dla iostream, i basic_iostream szablonu klasy —, które przekazuje zarówno wstawienia i ekstrakcje. Nagłówek definiuje również manipulatora pokrewne. Ten plik nagłówka jest zwykle dołączone dla Ciebie przez inny nagłówek iostream; rzadko musi zawierać go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <istream>

```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Typ `basic_iostream` specjalne na `char`.|
|[istream](../standard-library/istream-typedefs.md#istream)|Typ `basic_istream` specjalne na `char`.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Typ `basic_iostream` specjalne na **wchar**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Typ `basic_istream` specjalne na **wchar**.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Pomija biały znak w strumieniu.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Zamienia dwa obiekty stream.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Wyodrębnia znaki i ciągi ze strumienia.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Klasy strumienia, który można wykonać obie czynności danych wejściowych i wyjściowych.|
|[basic_istream](../standard-library/basic-istream-class.md)|Klasy szablonu opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia elementami typu **elementu**, znanej także jako [char_type](../standard-library/basic-ios-class.md#char_type), są którego cech znaków Określona klasa **Tr**, znanej także jako [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
