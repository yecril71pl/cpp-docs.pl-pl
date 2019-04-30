---
title: invoke_result klasy
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: 7c03240d3ee666fcda30562279a8dbda2ca8dc7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404854"
---
# <a name="invokeresult-class"></a>invoke_result klasy

Określa typ zwracany typ możliwy do wywołania, który ma określone typy argumentów w czasie kompilacji. Dodane w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parametry

*Możliwy do wywołania*<br/>
Wywoływane typ do zapytania.

*Args*<br/>
Typy argumentów na typ możliwy do wywołania do wykonywania zapytań.

## <a name="remarks"></a>Uwagi

Użyj tego szablonu, aby określić typ wyniku *Callable*(*Args*...) w czasie kompilacji, gdzie *Callable* i wszystkie typy w *Args* dowolny typ pełną, tablicę nieznany powiązane z lub prawdopodobnie cv kwalifikowanego `void`. `type` Składowej klasy szablonu, nazwy typu zwracanego *Callable* po wywołaniu, przy użyciu argumentów *Args*... `type` Elementu członkowskiego jest zdefiniowana tylko, jeśli *Callable* może być wywoływana, gdy wywoływany przy użyciu argumentów *Args*... w nieznanym kontekście. W przeciwnym razie klasa szablonu nie ma składowej `type`, co pozwala SFINAE testów na określony zestaw typów argumentów w czasie kompilacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[wywołania](functional-functions.md#invoke)
