---
title: '&lt;Klasa void programu przydzielania &gt;'
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: b6ca3f8b994756a21d85860fd8aff429ee38e58b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204934"
---
# <a name="allocatorltvoidgt-class"></a>&lt;Klasa void programu przydzielania &gt;

Specjalizacja alokatora szablonu klasy do typu **`void`** , definiując typy, które mają sens w tym kontekście.

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

Klasa jawnie wyspecjalizowany [Alokator](allocator-class.md) szablonu klasy dla typu **`void`** . Jego konstruktory i operator przypisania zachowują się tak samo jak dla szablonu klasy, ale definiuje tylko następujące typy:

- [const_pointer](allocator-class.md#const_pointer).

- [wskaźnik](allocator-class.md#pointer).

- [value_type](allocator-class.md#value_type).

- ponownie [powiązać](allocator-class.md#rebind)szablon klasy zagnieżdżonej.
