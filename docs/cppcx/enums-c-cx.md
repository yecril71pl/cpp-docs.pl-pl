---
title: Wyliczenia (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: 54e413e65b3130b9b83e6d1ed56b5ee87b84e0a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225764"
---
# <a name="enums-ccx"></a>Wyliczenia (C++/CX)

C++/CX obsługuje `public enum class` słowo kluczowe, które jest analogiczne do standardowego języka C++ `scoped  enum` . W przypadku użycia modułu wyliczającego, który jest zadeklarowany za pomocą `public enum class` słowa kluczowego, należy użyć identyfikatora wyliczenia do określania zakresu każdej wartości modułu wyliczającego.

### <a name="remarks"></a>Uwagi

Obiekt, `public enum class` który nie ma specyfikatora dostępu, na przykład **`public`** , jest traktowany jako standardowe [Wyliczenie w zakresie](../cpp/enumerations-cpp.md)języka C++.

`public enum class`Deklaracja or `public enum struct` może mieć typ podstawowy dowolnego typu całkowitego, chociaż środowisko wykonawcze systemu Windows sam wymaga, aby typ miał wartość Int32, lub UInt32 dla wyliczenia flag. Poniższa składnia opisuje części klasy `public enum class` lub `public enum struct` .

Ten przykład pokazuje, jak zdefiniować publiczną klasę wyliczeniową:

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

W następnym przykładzie pokazano, jak go wykorzystać:

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Przykłady

W następnych przykładach pokazano, jak zadeklarować Wyliczenie,

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

W następnym przykładzie pokazano, jak rzutować na równoważne wartości liczbowe i wykonać porównania. Należy zauważyć, że użycie modułu wyliczającego `One` jest ograniczone przez `Enum1` Identyfikator wyliczenia, a moduł wyliczający jest objęty `First` zakresem `Enum2` .

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
