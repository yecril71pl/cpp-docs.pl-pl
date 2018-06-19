---
title: '&lt;wyjątek&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: 68f95407fe22c7e8b70426e555f46eb0a4c80338
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846262"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;wyjątek&gt; definicje typów

||||
|-|-|-|
|[exception_ptr](#exception_ptr)|[terminate_handler](#terminate_handler)|[unexpected_handler](#unexpected_handler)|

## <a name="exception_ptr"></a>  exception_ptr

Typ, który opisuje wskaźnik do wyjątku.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Uwagi

Nieokreślony wewnętrzny klasy, która służy do implementowania `exception_ptr` typu.

Użyj `exception_ptr` obiekt, aby odwoływać się do bieżącego wyjątku lub wystąpienie wyjątku określone przez użytkownika. W implementacji firmy Microsoft wyjątek jest reprezentowana przez [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) struktury. Każdy `exception_ptr` obiektu zawiera pole odwołania wyjątek wskazujące kopię `EXCEPTION_RECORD` strukturę, która reprezentuje wyjątek.

Gdy zadeklarować `exception_ptr` zmiennej, zmienna nie jest skojarzony z żadnym wyjątku. To znaczy, że pole odwołania wyjątku ma wartość NULL. Takie `exception_ptr` nosi nazwę obiektu *null exception_ptr*.

Użyj `current_exception` lub `make_exception_ptr` przypisanie wyjątek `exception_ptr` obiektu. Po przypisaniu wyjątek `exception_ptr` zmiennej, odwołanie do zmiennej wyjątek pola wskazuje kopię wyjątek. Jeśli jest za mało pamięci, aby skopiować wyjątek, pole odwołania wyjątek wskazuje kopię [std::bad_alloc](../standard-library/bad-alloc-class.md) wyjątku. Jeśli `current_exception` lub `make_exception_ptr` funkcji nie można skopiować wyjątek dla innego powodu, wywołania funkcji **przerwanie** funkcji CRT, aby zamknąć bieżącego procesu.

Pomimo swojej nazwy `exception_ptr` obiektu sam nie jest wskaźnikiem. Nie podlega semantyka wskaźnika i nie można używać z dostęp do elementu członkowskiego wskaźnika ( `->`) lub operatory pośredni (*). `exception_ptr` Obiekt nie ma publicznych elementów członkowskich danych ani funkcji elementów członkowskich.

**Porównania:**

Można użyć równości ( `==`) i nie równości ( `!=`) operatorów, aby porównać dwa `exception_ptr` obiektów. Operatory porównania nie wartość binarna (wzorca bitowego) `EXCEPTION_RECORD` struktur reprezentujących wyjątki. Zamiast tego operatory porównania adres w polu odwołania wyjątek `exception_ptr` obiektów. W rezultacie null `exception_ptr` i porównać jako równe wartości NULL.

## <a name="terminate_handler"></a>  terminate_handler

Typ w tym artykule opisano wskaźnika do funkcji, które są odpowiednie do użycia jako `terminate_handler`.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Uwagi

Typ opisuje wskaźnik do funkcji odpowiedni do użytku jako program obsługi zakończenia.

### <a name="example"></a>Przykład

Zobacz [set_terminate —](../standard-library/exception-functions.md#set_terminate) na przykład użycie `terminate_handler`.

## <a name="unexpected_handler"></a>  unexpected_handler

Typ w tym artykule opisano wskaźnika do funkcji, które są odpowiednie do użycia jako `unexpected_handler`.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Przykład

Zobacz [set_unexpected —](../standard-library/exception-functions.md#set_unexpected) na przykład użycie `unexpected_handler`.

## <a name="see-also"></a>Zobacz także

[\<wyjątku >](../standard-library/exception.md)<br/>
