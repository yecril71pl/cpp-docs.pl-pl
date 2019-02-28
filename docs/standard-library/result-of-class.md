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
ms.openlocfilehash: f60a3ef6528da33fd1117fc940e961e9fe0987df
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006555"
---
# <a name="resultof-class"></a>result_of — Klasa

Określa typ zwracany typ możliwy do wywołania, który przyjmuje określone typy argumentów. Dodane w języku C ++ 14, uznane za przestarzałe w języku C ++ 17.

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

*Fn*<br/>
Wywoływane typ do zapytania.

*ArgTypes*<br/>
Typy argumentów na typ możliwy do wywołania do wykonywania zapytań.

## <a name="remarks"></a>Uwagi

Użyj tego szablonu, aby określić, w czasie kompilacji, typ wyniku `Fn`(`ArgTypes`), gdzie *Fn* jest typ możliwy do wywołania, odwołania do funkcji lub odwołanie do typu możliwy do wywołania, wywoływane przy użyciu listy argumentów typów w  *ArgTypes*. `type` Składowej klasy szablonu, nazwy typ wyniku `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` Jeśli wyrażenie nieobliczonym `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` jest poprawnie sformułowany. W przeciwnym razie klasa szablonu nie ma składowej `type`. Typ *Fn* i wszystkie typy w pakiecie parametr *ArgTypes* muszą być typami pełnymi **void**, lub tablic nieznany powiązane z. Przestarzałe zastąpiona ceną [invoke_result](invoke-result-class.md) w języku C ++ 17.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[Klasa invoke_result](invoke-result-class.md)<br/>
