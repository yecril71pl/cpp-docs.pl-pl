---
title: noexcept (C++)
ms.date: 11/19/2019
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: 5e8d58ed246b0143dc3d3be545cd796a4c3d60ed
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245626"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C++ 11:** Określa, czy funkcja może zgłaszać wyjątki.

## <a name="syntax"></a>Składnia

> *noexcept-Expression*: &nbsp;&nbsp;&nbsp;&nbsp;**noexcept** &nbsp;&nbsp;&nbsp;&nbsp;**noexcept (** *wyrażenie stałe* **)**

### <a name="parameters"></a>Parametry

*wyrażenie stałe*<br/>
Stałe wyrażenie typu **bool** , które reprezentuje, czy zestaw potencjalnych typów wyjątków jest pusty. Bezwarunkowa wersja jest równoważna `noexcept(true)`.

## <a name="remarks"></a>Uwagi

*Wyrażenie noexcept* jest rodzajem *specyfikacji wyjątku*, sufiksem do deklaracji funkcji, która reprezentuje zestaw typów, które mogą być dopasowane przez program obsługi wyjątków dla dowolnego wyjątku, który opuszcza funkcję. Jednoargumentowy operator warunkowy `noexcept(`*constant_expression*`)` gdzie *constant_expression* daje **wartość true**, a jego niewarunkowy synonim **noexcept**, określa, że zestaw potencjalnych typów wyjątków, które mogą opuścić funkcję, jest pusty. Oznacza to, że funkcja nigdy nie zgłasza wyjątku i nigdy nie zezwala na propagowanie wyjątku poza jego zakresem. Operator `noexcept(`*constant_expression*`)` gdzie *constant_expression* zwraca **wartość false**lub brak specyfikacji wyjątku (innej niż dla destruktora lub funkcji cofania alokacji) wskazuje, że zestaw potencjalnych wyjątków, które mogą opuścić funkcję, jest zestaw wszystkich typów.

Oznacz funkcję jako **noexcept** tylko wtedy, gdy wszystkie funkcje, które wywołuje, bezpośrednio lub pośrednio, są również **noexcept** lub **const**. Kompilator nie zawsze sprawdza wszystkie ścieżki kodu dla wyjątków, które mogą oznaczać do funkcji **noexcept** . Jeśli wyjątek kończy zewnętrzny zakres funkcji oznaczonej `noexcept`, [std:: terminate](../standard-library/exception-functions.md#terminate) jest wywoływana natychmiast i nie ma gwarancji, że destruktory jakichkolwiek obiektów w zakresie będą wywoływane. Użyj **noexcept** zamiast `throw()`specyfikatora wyjątku dynamicznego, który jest obecnie przestarzały w standardzie. Zalecamy stosowanie `noexcept` do dowolnej funkcji, która nigdy nie umożliwia wyjątku na propagację stosu wywołań. Gdy funkcja jest zadeklarowana **noexcept**, umożliwia kompilatorowi generowanie bardziej wydajnego kodu w kilku różnych kontekstach. Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków](exception-specifications-throw-cpp.md).

## <a name="example"></a>Przykład

Funkcja szablonu, która kopiuje jego argument, może być zadeklarowana jako **noexcept** w przypadku, gdy kopiowany obiekt jest zwykłym starym typem danych (pod). Taką funkcję można zadeklarować w następujący sposób:

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Zobacz także

[Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](errors-and-exception-handling-modern-cpp.md)<br/>
[Specyfikacje wyjątków (throw, noexcept)](exception-specifications-throw-cpp.md)