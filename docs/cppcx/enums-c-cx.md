---
title: Wyliczenia (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: 3bdcff03872dcfe83f0be5752cec4f567fbc6b72
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740212"
---
# <a name="enums-ccx"></a>Wyliczenia (C++/CX)

C++/CX obsługuje `public enum class` słowo kluczowe, które jest analagous do warstwy Standardowa C++ `scoped  enum`. W przypadku użycia modułu wyliczającego, który jest zadeklarowany za pomocą `public enum class` słowa kluczowego, należy użyć identyfikatora wyliczenia do określania zakresu każdej wartości modułu wyliczającego.

### <a name="remarks"></a>Uwagi

Obiekt `public enum class` , który nie ma specyfikatora dostępu, `public`na przykład, jest traktowany jako standardowe C++ [Wyliczenie w zakresie objętym zakresem](../cpp/enumerations-cpp.md).

Deklaracja `public enum class` or`public enum struct` może mieć typ podstawowy dowolnego typu całkowitego, chociaż środowisko wykonawcze systemu Windows sam wymaga, aby typ miał wartość Int32, lub UInt32 dla wyliczenia flag. Poniższa składnia opisuje części `public enum class` klasy lub. `public enum struct`

Ten przykład pokazuje, jak zdefiniować publiczną klasę wyliczeniową:

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

W następnym przykładzie pokazano, jak go wykorzystać:

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Przykłady

W następnych przykładach pokazano, jak zadeklarować Wyliczenie,

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

W następnym przykładzie pokazano, jak rzutować na równoważne wartości liczbowe i wykonać porównania. Należy zauważyć, że użycie modułu `One` wyliczającego jest ograniczone `Enum1` przez identyfikator wyliczenia, a `First` `Enum2`moduł wyliczający jest objęty zakresem.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
