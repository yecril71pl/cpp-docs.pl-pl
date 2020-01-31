---
title: Wyliczenia (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: be11d8d8f38a92fbe4be00eed53dd5226bab0b59
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821756"
---
# <a name="enums-ccx"></a>Wyliczenia (C++/CX)

C++/CX obsługuje słowo kluczowe `public enum class`, które jest analogiczne do `scoped  enum`C++ standardowego. W przypadku korzystania z modułu wyliczającego, który jest zadeklarowany za pomocą słowa kluczowego `public enum class`, należy użyć identyfikatora wyliczenia do określania zakresu każdej wartości modułu wyliczającego.

### <a name="remarks"></a>Uwagi

`public enum class`, która nie ma specyfikatora dostępu, takiego jak `public`, jest traktowana jako standardowe C++ [Wyliczenie w zakresie](../cpp/enumerations-cpp.md).

Deklaracja `public enum class` lub `public enum struct` może mieć typ podstawowy dowolnego typu całkowitego, chociaż środowisko wykonawcze systemu Windows samo wymaga, aby typ miał wartość Int32, lub UInt32 dla wyliczenia flag. Poniższa składnia opisuje części `public enum class` lub `public enum struct`.

Ten przykład pokazuje, jak zdefiniować publiczną klasę wyliczeniową:

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

W następnym przykładzie pokazano, jak go wykorzystać:

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Przykłady

W następnych przykładach pokazano, jak zadeklarować Wyliczenie,

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

W następnym przykładzie pokazano, jak rzutować na równoważne wartości liczbowe i wykonać porównania. Należy zauważyć, że użycie modułu wyliczającego `One` jest objęte zakresem `Enum1` identyfikatorem wyliczenia, a moduł wyliczający `First` jest objęty zakresem `Enum2`.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
