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
ms.openlocfilehash: a1c32311109ee19056c0a73d922ab1a965e3fbbb
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954128"
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

Nieokreślona Klasa wewnętrzna, która jest używana do zaimplementowania `exception_ptr` typu.

Użyj `exception_ptr` obiekt, aby odwoływać się do bieżącego wyjątku lub wystąpienia wyjątku określonego przez użytkownika. W implementacji firmy Microsoft wyjątek jest reprezentowany przez [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) struktury. Każdy `exception_ptr` obiekt zawiera pole odwołania wyjątku wskazuje kopię `EXCEPTION_RECORD` strukturę, która reprezentuje wyjątek.

Kiedy Deklarujesz `exception_ptr` zmiennej, zmienna nie jest skojarzony z żadnym wyjątkiem. To znaczy, że pole odwołania wyjątku ma wartość NULL. Takie `exception_ptr` obiekt jest nazywany *null exception_ptr*.

Użyj `current_exception` lub `make_exception_ptr` funkcję, aby przypisać wyjątek do `exception_ptr` obiektu. Podczas przypisywania wyjątku do `exception_ptr` zmiennej, pole odwołania wyjątku zmiennej wskazuje kopię wyjątku. W przypadku braku pamięci, aby skopiować wyjątek, pole odwołania wyjątku wskazuje kopię [std::bad_alloc](../standard-library/bad-alloc-class.md) wyjątku. Jeśli `current_exception` lub `make_exception_ptr` funkcji nie może skopiować wyjątku jakiegokolwiek innego powodu, wywołania funkcji `terminate` funkcji CRT, aby zakończyć bieżący proces.

Pomimo swojej nazwy `exception_ptr` obiektu sam nie jest wskaźnikiem. Go nie stosuje semantyki wskaźnika i nie można używać z dostępu do elementu członkowskiego wskaźnika ( `->`) lub operatory pośrednie (*). `exception_ptr` Obiekt nie ma publicznych elementów członkowskich danych ani funkcji elementów członkowskich.

**Porównania:**

Możesz użyć równości ( `==`) i nierówności ( `!=`) operatory do porównywania dwóch `exception_ptr` obiektów. Operatory nie porównują wartość binarna (wzorca bitowego) `EXCEPTION_RECORD` struktur, które reprezentują wyjątki. Zamiast tego, operatory porównują adresy w polu odwołania do wyjątku `exception_ptr` obiektów. W związku z tym, o wartości null `exception_ptr` i porównywane równe wartości NULL.

## <a name="terminate_handler"></a>  terminate_handler

Typ opisuje wskaźnik do funkcji odpowiedni do użytku jako `terminate_handler`.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Uwagi

Typ opisuje wskaźnik do funkcji odpowiedni do użytku jako program obsługi zakończenia.

### <a name="example"></a>Przykład

Zobacz [set_terminate](../standard-library/exception-functions.md#set_terminate) przykładem użycia `terminate_handler`.

## <a name="unexpected_handler"></a>  unexpected_handler

Typ opisuje wskaźnik do funkcji odpowiedni do użytku jako `unexpected_handler`.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) przykładem użycia `unexpected_handler`.

## <a name="see-also"></a>Zobacz także

[\<wyjątku >](../standard-library/exception.md)<br/>
