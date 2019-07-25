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
ms.openlocfilehash: 2b2051b0c854151cff9b439f5ec0a951c25a6387
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447642"
---
# <a name="invokeresult-class"></a>Klasa invoke_result

Określa zwracany typ wywoływanego typu, który przyjmuje określone typy argumentów w czasie kompilacji. Dodano w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parametry

*Żądanie*\
Typ możliwy do zapytania.

*Argumentów*\
Typy listy argumentów dla wywoływanego typu do zapytania.

## <a name="remarks"></a>Uwagi

Użyj tego szablonu, aby określić typ wyniku możliwego do *przeprowadzenia (* *args*...) w czasie *kompilacji, gdzie możliwe* jest dokończenie i wszystkie typy w *args* , tablica nieznanej granicy lub prawdopodobnie kwalifikowana `void`CV. Element członkowski klasy Template name zwraca typ *możliwy* do wywołania, gdy zostanie wywołane przy użyciu argumentów *argumenty..* .. `type` Element `type` członkowski jest definiowany tylko wtedy, *gdy można wywołać* wywoływanie przy użyciu argumentów *argumenty..* . w nieoszacowanym kontekście. W przeciwnym razie Klasa szablonu nie ma elementu `type`Członkowskiego, który umożliwia SFINAE testy na określonym zestawie typów argumentów w czasie kompilacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[wywołuje](functional-functions.md#invoke)
