---
title: result_of — Klasa
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: 54806f965cc46058e3c82b4863bb45782abe079e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202314"
---
# <a name="result_of-class"></a>result_of — Klasa

Określa zwracany typ wywoływanego typu, który przyjmuje określone typy argumentów. Dodano w języku C++ 14, przestarzałe w języku C++ 17.

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

*Fn*\
Typ możliwy do zapytania.

*ArgTypes*\
Typy listy argumentów dla wywoływanego typu do zapytania.

## <a name="remarks"></a>Uwagi

Użyj tego szablonu, aby określić w czasie kompilacji typ wyniku `Fn` ( `ArgTypes` ), gdzie *Fn* jest typem możliwym do wywołania, odwołaniem do funkcji lub odwołaniem do żądanego typu, wywoływane przy użyciu listy argumentów typów w *ArgTypes*. `type`Element członkowski szablonu klasy nazywa typ wyniku, `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` Jeśli wyrażenie nieoceniane `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` jest poprawnie sformułowane. W przeciwnym razie szablon klasy nie ma żadnego elementu członkowskiego `type` . Typ *Fn* i wszystkie typy w pakiecie parametrów *ArgTypes* muszą być kompletnymi typami, **`void`** lub tablicami nieznanego powiązania. Przestarzałe na rzecz [invoke_result](invoke-result-class.md) w języku c++ 17.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)\
[invoke_result, klasa](invoke-result-class.md)
