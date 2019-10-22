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
ms.openlocfilehash: 8cd72e62fcb65209482fd9677afcc2ec83356feb
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689517"
---
# <a name="invoke_result-class"></a>Klasa invoke_result

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

*Możliwy* do \
Typ możliwy do zapytania.

*Argumenty* \
Typy listy argumentów dla wywoływanego typu do zapytania.

## <a name="remarks"></a>Uwagi

Użyj tego szablonu, aby określić typ wyniku możliwego *do przeprowadzenia (* *args*...) w czasie kompilacji *, gdzie możliwe* są wszystkie typy w argumentach, w których są dowolnych typów, tablicę nieznanego powiązania lub prawdopodobnie `void` *kwalifikowana za pomocą* CV. @No__t_0 element członkowski szablonu klasy nazwa zwracanego typu wywoływanego w *przypadku wywołania przy użyciu* *argumentów argumenty..* .. Element członkowski `type` jest zdefiniowany *tylko wtedy, gdy można wywołać* wywoływanie przy *użyciu argumentów argumenty..* . w nieoszacowanym kontekście. W przeciwnym razie szablon klasy nie ma żadnych elementów członkowskich `type`, co umożliwia testy SFINAE na określonym zestawie typów argumentów w czasie kompilacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md) \
[wywołuje](functional-functions.md#invoke)
