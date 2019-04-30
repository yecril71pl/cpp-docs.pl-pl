---
title: Enums (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: f16a288a0b928b74ef42de5781fd1b54930927d6
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345818"
---
# <a name="enums-ccx"></a>Enums (C++/CX)

C++Obsługuje /CX `public enum class` — słowo kluczowe, czyli analagous do standardowego C++ `scoped  enum`. Kiedy używasz moduł wyliczający, który jest zadeklarowana za pomocą `public enum class` — słowo kluczowe, musi być identyfikatorem wyliczenia zakresu z każdą wartość modułu wyliczającego.

### <a name="remarks"></a>Uwagi

A `public enum class` , która nie ma specyfikatora dostępu, takich jak `public`, jest traktowany jako standard C++ [zakresie](../cpp/enumerations-cpp.md).

A `public enum class` lub `public enum struct` deklaracja może mieć typu podstawowego typu całkowitego, mimo że środowisko wykonawcze Windows wymaga typu int32 lub uint32 dla wyliczenia flag. Następująca składnia opisuje części `public enum class` lub `public enum struct`.

Ten przykład pokazuje, jak zdefiniować klasę publicznym typie wyliczeniowym:

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

To Następny przykład pokazuje sposób wykorzystywania go:

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Przykłady

W następnych przykładach pokazano, jak zadeklarować wyliczenia

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

Następny przykład pokazuje, jak Rzutowanie na odpowiedniki liczbowych i wykonywać porównania. Należy zauważyć, że użycie modułu wyliczającego `One` jest objęte zakresem `Enum1` identyfikatorem wyliczenia, a moduł wyliczający `First` jest objęte zakresem `Enum2`.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
