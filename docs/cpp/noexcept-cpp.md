---
title: noexcept (C++)
ms.date: 01/12/2018
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: cf53aca918e36d18ab7f8aa14b01caaf0e55627c
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69975900"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C++11:** Określa, czy funkcja może zgłaszać wyjątki.

## <a name="syntax"></a>Składnia

> *noexcept-Expression*: &nbsp; &nbsp; &nbsp; noexcept&nbsp;noexcept (wyrażenie stałe &nbsp; &nbsp; &nbsp; &nbsp;  **)**

### <a name="parameters"></a>Parametry

*constant-expression*<br/>
Stałe wyrażenie typu **bool** , które reprezentuje, czy zestaw potencjalnych typów wyjątków jest pusty. Niewarunkowa wersja jest równoważna z `noexcept(true)`.

## <a name="remarks"></a>Uwagi

*Wyrażenie noexcept* jest rodzajem *specyfikacji wyjątku*, sufiksem do deklaracji funkcji, która reprezentuje zestaw typów, które mogą być dopasowane przez program obsługi wyjątków dla dowolnego wyjątku, który opuszcza funkcję. Jednoargumentowy `noexcept(`operator warunkowy *constant_expression* `)` , gdzie *constant_expression* zwraca **wartość true**, a jego niewarunkowy synonim noexcept, określa, że zestaw potencjalnych typów wyjątków, które można wyjść z funkcji jest pusta. Oznacza to, że funkcja nigdy nie zgłasza wyjątku i nigdy nie zezwala na propagowanie wyjątku poza jego zakresem. Operator `noexcept(` *constant_expression*, gdzie constant_expression zwraca wartość false lub brak specyfikacji wyjątku (innej niż dla destruktora lub funkcji cofania alokacji), wskazuje, że`)` zestaw potencjalnych wyjątków, które mogą opuścić funkcję, to zestaw wszystkich typów.

Oznacz funkcję jako **noexcept** tylko wtedy, gdy wszystkie funkcje, które wywołuje, bezpośrednio lub pośrednio, są również noexcept lub **const**. Kompilator nie zawsze sprawdza wszystkie ścieżki kodu dla wyjątków, które mogą oznaczać do funkcji noexcept . Jeśli wyjątek kończy zewnętrzny zakres funkcji oznaczonej `noexcept`, [std:: terminate](../standard-library/exception-functions.md#terminate) jest wywoływana natychmiast i nie ma gwarancji, że destruktory wszystkich obiektów w zakresie będą wywoływane. Użyj **noexcept** zamiast specyfikatora `throw()`wyjątku dynamicznego, który jest obecnie przestarzały w standardzie. Zalecamy zastosowanie `noexcept` do dowolnej funkcji, która nigdy nie umożliwia wyjątku na propagację stosu wywołań. Gdy funkcja jest zadeklarowana **noexcept**, umożliwia kompilatorowi generowanie bardziej wydajnego kodu w kilku różnych kontekstach. Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków](exception-specifications-throw-cpp.md).

## <a name="example"></a>Przykład

Funkcja szablonu, która kopiuje jego argument, może być zadeklarowana jako noexcept w przypadku, gdy kopiowany obiekt jest zwykłym starym typem danych (pod). Taką funkcję można zadeklarować w następujący sposób:

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków języka C++](cpp-exception-handling.md)<br/>
[Specyfikacje wyjątków (throw, noexcept)](exception-specifications-throw-cpp.md)