---
title: '&lt;ostream &gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: 3838e215ffac42ec6902ab6a9837f638153cf184
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689164"
---
# <a name="ltostreamgt"></a>&lt;ostream &gt;

Definiuje szablon klasy [basic_ostream](../standard-library/basic-ostream-class.md), który koryguje wstawienia dla iostreams. Nagłówek definiuje również kilka powiązanych manipulowania. (Ten nagłówek jest zazwyczaj dołączany przez inny iostreams nagłówków. Rzadko trzeba dołączyć go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Tworzy typ z `basic_ostream`, który jest wyspecjalizowany dla **znaków** i `char_traits` wyspecjalizowany dla **char**.|
|[wostream —](../standard-library/ostream-typedefs.md#wostream)|Tworzy typ z `basic_ostream`, który jest wyspecjalizowany w **wchar_t** i `char_traits` wyspecjalizowany w **wchar_t**.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Kończy wiersz i opróżnia bufor.|
|[celów](../standard-library/ostream-functions.md#ends)|Kończy ciąg.|
|[płukan](../standard-library/ostream-functions.md#flush)|Opróżnia bufor.|
|[wymiany](../standard-library/ostream-functions.md#swap)|Wymienia wartości `basic_ostream` lewego parametru obiektu dla tych z parametrem `basic_ostream` obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[< operatora <](../standard-library/ostream-operators.md#op_lt_lt)|Zapisuje różne typy w strumieniu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|Szablon klasy opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do buforu strumienia.|

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
