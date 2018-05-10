---
title: Program przydzielania&lt;void&gt; klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
dev_langs:
- C++
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4179ddae0506d21ca3969559b05c618ab4d73e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="allocatorltvoidgt-class"></a>Program przydzielania&lt;void&gt; — klasa

Specjalizacja szablonu alokatora klasy na typ `void`, definiowanie typów, które sensu, w tym kontekście.

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

Klasa jawnie specjalizuje się klasy szablonu [alokatora](../standard-library/allocator-class.md) dla typu *void.* Operator przypisania and konstruktorów zachowanie takie same jak w przypadku klasy szablonu, ale definiuje on tylko następujących typów:

- [const_pointer](../standard-library/allocator-class.md#const_pointer).

- [wskaźnik](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type).

- [ponownie powiązać](../standard-library/allocator-class.md#rebind), zagnieżdżone klasy szablonu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
