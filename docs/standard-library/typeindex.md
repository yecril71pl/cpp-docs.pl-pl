---
title: '&lt;typeindex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <typeindex>
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
ms.openlocfilehash: 237356a0862ec3fc591264b482b23e62ef2c51cb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455062"
---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;

Uwzględnij standardowy nagłówek \<typeindex >, aby zdefiniować klasę i funkcję, która obsługuje indeksowanie obiektów klasy [type_info](../cpp/type-info-class.md).

## <a name="syntax"></a>Składnia

```cpp
#include <typeindex>
```

## <a name="remarks"></a>Uwagi

[Struktura skrótu](../standard-library/hash-structure.md) definiuje `hash function` odpowiednie do mapowania wartości typu [type_index](../standard-library/type-index-class.md) na rozkład wartości indeksu.

Klasa otacza wskaźnik `type_info` do obiektu, aby pomóc w indeksowaniu. `type_index`

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
