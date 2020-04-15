---
title: '&lt;definicje&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: f71c03e0c0a2e7ea4f37a85e85628ccf630ea317
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368727"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;definicje&gt; typedefs

## <a name="exception_ptr"></a><a name="exception_ptr"></a>Exception_ptr

Typ, który opisuje wskaźnik do wyjątku.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Uwagi

Nieokreślona klasa wewnętrzna, która `exception_ptr` jest używana do implementacji typu.

Użyj `exception_ptr` obiektu, aby odwołać się do bieżącego wyjątku lub wystąpienia wyjątku określonego przez użytkownika. W implementacji firmy Microsoft wyjątek jest reprezentowany przez strukturę [EXCEPTION_RECORD.](/windows/win32/api/winnt/ns-winnt-exception_record) Każdy `exception_ptr` obiekt zawiera pole odwołania wyjątku, `EXCEPTION_RECORD` które wskazuje kopię struktury, która reprezentuje wyjątek.

Podczas deklarowania `exception_ptr` zmiennej zmienna nie jest skojarzona z żadnym wyjątkiem. To znaczy, że pole odwołania wyjątku ma wartość NULL. Taki `exception_ptr` obiekt jest nazywany *exception_ptr null*.

Użyj `current_exception` funkcji `make_exception_ptr` lub przypisać wyjątek `exception_ptr` do obiektu. Po przypisaniu wyjątku `exception_ptr` do zmiennej pole odwołania do wyjątku jest punktem odniesienia do kopii wyjątku. Jeśli nie ma wystarczającej ilości pamięci do skopiowania wyjątku, pole odwołania wyjątku wskazuje na kopię [wyjątku std::bad_alloc.](../standard-library/bad-alloc-class.md) Jeśli `current_exception` funkcja `make_exception_ptr` lub nie może skopiować wyjątek z `terminate` jakiegokolwiek innego powodu, funkcja wywołuje funkcję CRT, aby zakończyć bieżący proces.

Pomimo swojej nazwy `exception_ptr` obiekt nie jest sam w sobie wskaźnikiem. Nie jest posłuszny semantyki wskaźnika i nie można `->`używać z operatorami elementu członkowskiego wskaźnika ( ) lub pośrednie (*). Obiekt `exception_ptr` nie ma elementów członkowskich danych publicznych ani funkcji członkowskich.

**Porównania:**

Do porównania dwóch `==` `!=` `exception_ptr` obiektów można użyć operatorów equal ( ) i not-equal ( ). Operatory nie porównują wartości binarnej (wzorca bitowego) `EXCEPTION_RECORD` struktur, które reprezentują wyjątki. Zamiast tego operatorzy porównać adresy w `exception_ptr` polu odwołania wyjątku obiektów. W związku z `exception_ptr` tym null i NULL wartość porównać jako równe.

## <a name="terminate_handler"></a><a name="terminate_handler"></a>terminate_handler

Typ opisuje wskaźnik do funkcji nadaje się `terminate_handler`do użycia jako .

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Uwagi

Typ opisuje wskaźnik do funkcji odpowiedni do użytku jako program obsługi zakończenia.

### <a name="example"></a>Przykład

Zobacz [set_terminate](../standard-library/exception-functions.md#set_terminate) na przykład użycia pliku `terminate_handler`.

## <a name="unexpected_handler"></a><a name="unexpected_handler"></a>unexpected_handler

Typ opisuje wskaźnik do funkcji nadającej `unexpected_handler`się do użycia jako .

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) na przykład użycia pliku `unexpected_handler`.
