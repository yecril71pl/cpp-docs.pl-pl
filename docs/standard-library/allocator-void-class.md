---
title: Alokator &lt;void &gt; klasy
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: c8d787fe03dfe6f67fb8e228308ec74b6e7f620a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688529"
---
# <a name="allocatorltvoidgt-class"></a>Alokator &lt;void &gt; klasy

Specjalizacja alokatora szablonu klasy do typu **void**, definiując typy, które mają sens w tym kontekście.

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

Klasa jawnie wyspecjalizowany [Alokator](../standard-library/allocator-class.md) szablonu klasy dla typu **void**. Jego konstruktory i operator przypisania zachowują się tak samo jak dla szablonu klasy, ale definiuje tylko następujące typy:

- [const_pointer](../standard-library/allocator-class.md#const_pointer).

- [wskaźnik](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type).

- ponownie [powiązać](../standard-library/allocator-class.md#rebind)szablon klasy zagnieżdżonej.
