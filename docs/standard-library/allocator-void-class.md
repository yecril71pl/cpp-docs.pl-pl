---
title: Allocator&lt;void&gt; klasy
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: 5591570527946895d1e0456b23327d7fabc4bef5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646117"
---
# <a name="allocatorltvoidgt-class"></a>Allocator&lt;void&gt; klasy

Specjalizacja alokatora klasy szablonu do typu **void**, definiowanie typów, które są uwzględnione w tym kontekście.

## <a name="syntax"></a>Składnia

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>Uwagi

Klasa jawnie specjalizuje się klasy szablonu [alokatora](../standard-library/allocator-class.md) dla typu **void**. Jego konstruktorów i operator przypisania działają takie same jak dla klasy szablonu, ale definiuje on tylko następujących typów:

- [const_pointer](../standard-library/allocator-class.md#const_pointer).

- [wskaźnik](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type).

- [ponownie powiązać](../standard-library/allocator-class.md#rebind), szablon klasy zagnieżdżonej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
