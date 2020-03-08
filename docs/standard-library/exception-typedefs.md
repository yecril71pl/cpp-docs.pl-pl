---
title: '&lt;wyjątek&gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: aba17b7bf052b6974bf849f60ff895b8e84a1092
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854913"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;wyjątek&gt; Typedefs

## <a name="exception_ptr"></a>exception_ptr

Typ, który opisuje wskaźnik do wyjątku.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Uwagi

Nieokreślona Klasa wewnętrzna, która jest używana do implementowania typu `exception_ptr`.

Użyj obiektu `exception_ptr`, aby odwołać się do bieżącego wyjątku lub wystąpienia wyjątku określonego przez użytkownika. W implementacji firmy Microsoft wyjątek jest reprezentowany przez strukturę [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) . Każdy obiekt `exception_ptr` zawiera pole odwołania wyjątku wskazujące kopię struktury `EXCEPTION_RECORD`, która reprezentuje wyjątek.

Gdy deklarujesz zmienną `exception_ptr`, zmienna nie jest skojarzona z żadnym wyjątkiem. To znaczy, że pole odwołania wyjątku ma wartość NULL. Taki obiekt `exception_ptr` jest nazywany exception_ptr o *wartości null*.

Użyj funkcji `current_exception` lub `make_exception_ptr`, aby przypisać wyjątek do obiektu `exception_ptr`. Po przypisaniu wyjątku do zmiennej `exception_ptr`, pole odwołania wyjątku zmiennej wskazuje kopię wyjątku. Jeśli nie ma wystarczającej ilości pamięci do skopiowania wyjątku, pole odwołania wyjątku wskazuje kopię wyjątku [std:: bad_alloc](../standard-library/bad-alloc-class.md) . Jeśli funkcja `current_exception` lub `make_exception_ptr` nie może skopiować wyjątku z jakiegokolwiek innego powodu, funkcja wywołuje funkcję `terminate` CRT, aby wyjść z bieżącego procesu.

Pomimo nazwy, obiekt `exception_ptr` nie jest samym wskaźnikiem. Nie przestrzega on semantyki wskaźnika i nie można go używać z operatorami dostępu do elementów członkowskich wskaźnika (`->`) lub pośrednimi (*). Obiekt `exception_ptr` nie ma publicznych składowych danych ani funkcji Członkowskich.

**Porównanie**

Można użyć operatorów równości (`==`) i nie równa się (`!=`) do porównywania dwóch obiektów `exception_ptr`. Operatory nie porównują wartości binarnej (wzorca bitowego) struktur `EXCEPTION_RECORD`, które reprezentują wyjątki. Zamiast tego operatory porównują adresy w polu odwołanie wyjątku dla obiektów `exception_ptr`. W związku z tym wartość null `exception_ptr` i wartości NULL są porównywane jako równe.

## <a name="terminate_handler"></a>terminate_handler

Typ opisuje wskaźnik do funkcji odpowiedniej do użycia jako `terminate_handler`.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Uwagi

Typ opisuje wskaźnik do funkcji odpowiedni do użytku jako program obsługi zakończenia.

### <a name="example"></a>Przykład

Zobacz [set_terminate](../standard-library/exception-functions.md#set_terminate) , aby zapoznać się z przykładem korzystania z `terminate_handler`.

## <a name="unexpected_handler"></a>unexpected_handler

Typ opisuje wskaźnik do funkcji odpowiedniej do użycia jako `unexpected_handler`.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) , aby zapoznać się z przykładem korzystania z `unexpected_handler`.
