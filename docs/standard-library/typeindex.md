---
title: '&lt;typeindex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <typeindex>
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
ms.openlocfilehash: e22ce63c01185112ed512217156470e6f2948cd5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566624"
---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;

Dołączyć standardowy nagłówek \<typeindex > do definiowania klas i funkcji, która obsługuje indeksowanie obiektów klasy [type_info](../cpp/type-info-class.md).

## <a name="syntax"></a>Składnia

```cpp
#include <typeindex>
```

## <a name="remarks"></a>Uwagi

[Hash, struktura](../standard-library/hash-structure.md) definiuje `hash function` który nadaje się do mapowania wartości typu [type_index](../standard-library/type-index-class.md) do rozłożenia wartości indeksu.

`type_index` Klasy otacza wskaźnik do `type_info` obiektu, aby pomóc w indeksowaniu.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
