---
title: Allocator&lt;void&gt; klasy
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: 7ac7fbaa8c50eb13457271cf96ddc3412733c833
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245880"
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
