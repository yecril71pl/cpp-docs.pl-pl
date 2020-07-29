---
title: Klasa invoke_result
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: e3e1a28310660ad1fbdae4dd58973de378ddf364
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233135"
---
# <a name="invoke_result-class"></a>Klasa invoke_result

Określa zwracany typ wywoływanego typu, który przyjmuje określone typy argumentów w czasie kompilacji. Dodano w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<class Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parametry

*Żądanie*\
Typ możliwy do zapytania.

*Argumentów*\
Typy listy argumentów dla wywoływanego typu do zapytania.

## <a name="remarks"></a>Uwagi

Użyj tego szablonu, aby określić typ wyniku możliwego *do przeprowadzenia (**args*...) w czasie kompilacji *, gdzie możliwe* jest dokończenie i wszystkie typy w *args* , tablica nieznanej granicy lub prawdopodobnie kwalifikowana CV **`void`** . `type`Element członkowski szablonu klasy nazywa zwracany typ, który jest wywoływany w przypadku wywołania przy użyciu *Args*argumentów argumenty.... *Callable* `type`Element członkowski jest definiowany tylko wtedy *, gdy* można wywołać wywoływanie przy użyciu argumentów *Args*argumenty... w nieoszacowanym kontekście. W przeciwnym razie szablon klasy nie ma elementu członkowskiego `type` , który umożliwia testowanie SFINAE na określonym zestawie typów argumentów w czasie kompilacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)\
[wywołuje](functional-functions.md#invoke)
