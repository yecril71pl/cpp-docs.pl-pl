---
title: Klasa bad_exception | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- exception/std::bad_exception
dev_langs:
- C++
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3813fae7a9ae6105d4a3dfe4e72ac1773a10e65
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954659"
---
# <a name="badexception-class"></a>Klasa bad_exception

Klasa opisuje wyjątek, który może zostać wygenerowany z program obsługi nieoczekiwanych wyjątków.

## <a name="syntax"></a>Składnia

```cpp
class bad_exception    : public exception {};
```

## <a name="remarks"></a>Uwagi

[Nieoczekiwany](../standard-library/exception-functions.md#unexpected) zgłosi `bad_exception` zamiast przerywa lub zamiast wywoływania innej funkcji określony za pomocą [set_unexpected](../standard-library/exception-functions.md#set_unexpected) Jeśli `bad_exception` znajduje się na liście throw funkcji.

Wartość zwrócona przez obiekt `what` jest ciągiem C zdefiniowanych w implementacji. Żadna z funkcji elementu członkowskiego generuje żadnych wyjątków.

Aby uzyskać listę elementów członkowskich dziedziczonych przez `bad_exception` klasy, zobacz [wyjątek klasy](../standard-library/exception-class.md).

## <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) przykładem użycia [nieoczekiwany](../standard-library/exception-functions.md#unexpected) zgłaszanie `bad_exception`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyjątku >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[exception, klasa](../standard-library/exception-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
