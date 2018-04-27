---
title: '&lt;ostream&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
dev_langs:
- C++
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 620017d55c00ebca2be29bc855f9e77413941961
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Definiuje klasę szablonu [basic_ostream —](../standard-library/basic-ostream-class.md), która przekazuje wstawienia dla iostream. Nagłówek definiuje również kilka manipulatory pokrewne. (Ten nagłówek jest zwykle dołączone dla Ciebie przez inną nagłówków iostream. Rzadko należy dołączyć go bezpośrednio.)

## <a name="syntax"></a>Składnia

```cpp
#include <ostream>

```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Tworzy typ z `basic_ostream` które jest przeznaczone na `char` i `char_traits` specjalne na `char`.|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Tworzy typ z `basic_ostream` które jest przeznaczone na `wchar_t` i `char_traits` specjalne na `wchar_t`.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Przerywa wiersza i opróżnia bufor.|
|[kończy się](../standard-library/ostream-functions.md#ends)|Kończy się ciągiem.|
|[flush](../standard-library/ostream-functions.md#flush)|Opróżnia bufor.|
|[swap](../standard-library/ostream-functions.md#swap)|Zamienia wartości po lewej stronie `basic_ostream` obiekt parametru do tych praw `basic_ostream` obiekt parametru.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[Operator <<](../standard-library/ostream-operators.md#op_lt_lt)|Zapisuje różnych typów w strumieniu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|Klasy szablonów opisano obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych w buforze strumienia.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
