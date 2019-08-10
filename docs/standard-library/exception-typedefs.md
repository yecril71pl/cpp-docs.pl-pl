---
title: '&lt;definicje&gt; typów wyjątków'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: 58fc19b7cdf9656a4c2978a43a5c77092cc6716d
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916993"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;definicje&gt; typów wyjątków

## <a name="exception_ptr"></a>exception_ptr

Typ, który opisuje wskaźnik do wyjątku.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Uwagi

Nieokreślona Klasa wewnętrzna, która jest używana do implementowania `exception_ptr` typu.

`exception_ptr` Użyj obiektu, aby odwołać się do bieżącego wyjątku lub wystąpienia wyjątku określonego przez użytkownika. W implementacji firmy Microsoft wyjątek jest reprezentowany przez strukturę [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-exception_record) . Każdy `exception_ptr` obiekt zawiera pole odwołania wyjątku, które wskazuje kopię `EXCEPTION_RECORD` struktury, która reprezentuje wyjątek.

Podczas deklarowania `exception_ptr` zmiennej zmienna nie jest skojarzona z żadnym wyjątkiem. To znaczy, że pole odwołania wyjątku ma wartość NULL. Taki obiekt jest nazywany exception_ptr o *wartości null.* `exception_ptr`

Użyj funkcji `make_exception_ptr` `exception_ptr` or, aby przypisać wyjątek do obiektu. `current_exception` Po przypisaniu wyjątku do `exception_ptr` zmiennej pole odwołania wyjątku zmiennej wskazuje kopię wyjątku. Jeśli nie ma wystarczającej ilości pamięci do skopiowania wyjątku, pole odwołania wyjątku wskazuje kopię wyjątku [std:: bad_alloc](../standard-library/bad-alloc-class.md) . Jeśli funkcja `make_exception_ptr` `terminate` or nie może skopiować wyjątku z jakiegokolwiek innego powodu, funkcja wywołuje funkcję CRT, aby wyjść z bieżącego procesu. `current_exception`

Pomimo nazwy, `exception_ptr` obiekt nie jest samo wskaźnikiem. Nie przestrzega on semantyki wskaźnika i nie można go używać z operatorami dostępu do elementów `->`członkowskich wskaźnika () ani pośrednich (*). `exception_ptr` Obiekt nie ma publicznych składowych danych ani funkcji Członkowskich.

**Porównanie**

Do porównywania dwóch `==` `exception_ptr` obiektów można użyć operatorów równości () i `!=`nierówności (). Operatory nie porównują wartości binarnej (wzorca bitowego) `EXCEPTION_RECORD` struktur, które reprezentują wyjątki. Zamiast tego operatory porównują adresy w polu `exception_ptr` odwołanie wyjątku obiektów. W związku z tym wartość `exception_ptr` null i wartości null są porównywane jako równe.

## <a name="terminate_handler"></a>terminate_handler

Typ opisuje wskaźnik do funkcji odpowiedniej do użycia jako `terminate_handler`.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Uwagi

Typ opisuje wskaźnik do funkcji odpowiedni do użytku jako program obsługi zakończenia.

### <a name="example"></a>Przykład

Zobacz [set_terminate](../standard-library/exception-functions.md#set_terminate) , aby zapoznać się z przykładem `terminate_handler`użycia.

## <a name="unexpected_handler"></a>unexpected_handler

Typ opisuje wskaźnik do funkcji odpowiedniej do użycia jako `unexpected_handler`.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) , aby zapoznać się z przykładem `unexpected_handler`użycia.
