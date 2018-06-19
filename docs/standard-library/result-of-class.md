---
title: result_of — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
dev_langs:
- C++
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c13dcadc87c23e288c7f8c8a7f5bc9752aae5db7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853654"
---
# <a name="resultof-class"></a>result_of — Klasa

Określa typ zwracany można wywołać typu, który pobiera określone typy argumentów.

## <a name="syntax"></a>Składnia

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>Parametry

`Fn` Typ można wywołać w zapytaniu.

`ArgTypes` Typy z listą argumentów do typu można wywołać w celu zapytania.

## <a name="remarks"></a>Uwagi

Ten szablon służy do określenia w czasie kompilacji typu wyników `Fn`(`ArgTypes`), gdzie `Fn` jest typu można wywołać, odwołania do funkcji lub odwołanie do typu można wywołać, wywoływane przy użyciu listy argumentów typu `ArgTypes`. `type` Elementu członkowskiego klasy szablonu nazwy typu wyników `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` Jeśli wyrażenie nieznanym `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` jest poprawnie sformułowany. W przeciwnym razie klasy szablonu ma elementu członkowskiego `type`. Typ `Fn` i wszystkie typy w pakiecie parametru `ArgTypes` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
