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
ms.openlocfilehash: 5a3265cfe4b2629bf02925ea6e3eeb0c4acb1e0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451214"
---
# <a name="resultof-class"></a>result_of — Klasa

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

Użyj tego szablonu, aby określić w `Fn`czasie kompilacji typ wyniku (`ArgTypes`), gdzie *Fn* jest typem możliwym do wywołania, odwołaniem do funkcji lub odwołaniem do żądanego typu, wywoływane przy użyciu listy argumentów typów w *ArgTypes*. Element członkowski klasy szablonu nazywa `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` typ wyniku, jeśli wyrażenie `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` nieoceniane jest poprawnie sformułowane. `type` W przeciwnym razie Klasa szablonu nie ma żadnego `type`elementu członkowskiego. Typ *Fn* i wszystkie typy w pakiecie parametrów *ArgTypes* muszą być pełnymi typami, **void**lub tablicami nieznanego powiązania. Przestarzałe na korzyść [invoke_result](invoke-result-class.md) w języku c++ 17.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[Klasa invoke_result](invoke-result-class.md)
