---
title: iterator — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 64c9be76cb92d818e40714dd141ded3a8cc17c8a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455622"
---
# <a name="iterator-struct"></a>iterator — Struktura

Pusta struktura podstawowa używana do upewnienia się, że Klasa iteratora zdefiniowana przez użytkownika działa `iterator_trait`prawidłowo z s.

## <a name="syntax"></a>Składnia

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>Uwagi

Struktura szablonu służy jako typ podstawowy dla wszystkich iteratorów. Definiuje typy elementów członkowskich

- `iterator_category`(synonim dla parametru `Category`szablonu).

- `value_type`(synonim dla parametru `Type`szablonu).

- `difference_type`(synonim dla parametru `Distance`szablonu).

- `distance_type`(synonim dla parametru `Distance`szablonu)

- `pointer`(synonim dla parametru `Pointer`szablonu).

- `reference`(synonim dla parametru `Reference`szablonu).

Należy zauważyć `value_type` , że nie powinien być typem stałym `pointer` , nawet jeśli punkty w obiekcie **const** `Type` i Reference wyznaczają obiekt **const** `Type`.

## <a name="example"></a>Przykład

Zobacz [iterator_traits](../standard-library/iterator-traits-struct.md) , aby zapoznać się z przykładem sposobu deklarowania typów w klasie bazowej iteratora i korzystania z nich.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
