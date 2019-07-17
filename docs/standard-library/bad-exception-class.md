---
title: Klasa bad_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 1795a44d2d31cfbad964b41ef03e4bf65b401352
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246207"
---
# <a name="badexception-class"></a>Klasa bad_exception

Klasa opisuje wyjątek, który może zostać wygenerowany z program obsługi nieoczekiwanych wyjątków.

## <a name="syntax"></a>Składnia

```cpp
class bad_exception : public exception {};

bad_exception();
bad_exception(const bad_exception&);
bad_exception& operator=(const bad_exception&);
const char* what() const override;
```

## <a name="remarks"></a>Uwagi

[Nieoczekiwany](../standard-library/exception-functions.md#unexpected) zgłosi `bad_exception` zamiast przerywa lub zamiast wywoływania innej funkcji określony za pomocą [set_unexpected](../standard-library/exception-functions.md#set_unexpected) Jeśli `bad_exception` znajduje się na liście throw funkcji.

Wartość zwrócona przez obiekt `what` jest ciągiem C zdefiniowanych w implementacji. Żadna z funkcji elementu członkowskiego generuje żadnych wyjątków.

Aby uzyskać listę elementów członkowskich dziedziczonych przez `bad_exception` klasy, zobacz [wyjątek klasy](../standard-library/exception-class.md).

## <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) przykładem użycia [nieoczekiwany](../standard-library/exception-functions.md#unexpected) zgłaszanie `bad_exception`.
