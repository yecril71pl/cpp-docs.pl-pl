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
ms.openlocfilehash: eb73c77f0e2658cf750cf17ca85549a09d1cbe51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370934"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Definiuje klasę szablonu [basic_ostream](../standard-library/basic-ostream-class.md), która pośredniczy wstawienia dla iostream. Nagłówek definiuje również kilka powiązanych manipulatory. (Tego pliku nagłówkowego jest zazwyczaj uwzględniony dla Ciebie żadnego innego nagłówków iostream. Rzadko należy dołączyć go bezpośrednio.)

## <a name="syntax"></a>Składnia

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Tworzy typ z `basic_ostream` które jest przeznaczone na **char** i `char_traits` wyspecjalizowane na **char**.|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Tworzy typ z `basic_ostream` które jest przeznaczone na **wchar_t** i `char_traits` wyspecjalizowane na **wchar_t**.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Kończy działanie wiersza i opróżnia bufor.|
|[kończy się](../standard-library/ostream-functions.md#ends)|Kończy ciąg.|
|[flush](../standard-library/ostream-functions.md#flush)|Opróżnia bufor.|
|[swap](../standard-library/ostream-functions.md#swap)|Wymienia wartości lewej strony `basic_ostream` obiektu parametr dla osób, które po prawej stronie `basic_ostream` obiektu parametru.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[Operator <<](../standard-library/ostream-operators.md#op_lt_lt)|Zapisuje różnych typów w strumieniu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wstawiania elementów i zakodowany obiekty do buforu strumienia.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
