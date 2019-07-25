---
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: 8de66718dab10b5c95e8c1ab7fd0bd17e9b4ee5e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448168"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Definiuje klasę [basic_ostream](../standard-library/basic-ostream-class.md), która koryguje wstawienia dla iostreams. Nagłówek definiuje również kilka powiązanych manipulowania. (Ten nagłówek jest zazwyczaj dołączany przez inny iostreams nagłówków. Rzadko trzeba dołączyć go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Tworzy typ `basic_ostream` , który jest wyspecjalizowany w  znakach `char_traits` i wyspecjalizowany dla **znaku**.|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Tworzy typ `basic_ostream` , który jest wyspecjalizowany w **wchar_t** i `char_traits` wyspecjalizowany w **wchar_t**.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Kończy wiersz i opróżnia bufor.|
|[celów](../standard-library/ostream-functions.md#ends)|Kończy ciąg.|
|[flush](../standard-library/ostream-functions.md#flush)|Opróżnia bufor.|
|[swap](../standard-library/ostream-functions.md#swap)|Wymienia wartości parametru lewego `basic_ostream` obiektu dla tych z parametrem właściwego `basic_ostream` obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[< operatora <](../standard-library/ostream-operators.md#op_lt_lt)|Zapisuje różne typy w strumieniu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do buforu strumienia.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
