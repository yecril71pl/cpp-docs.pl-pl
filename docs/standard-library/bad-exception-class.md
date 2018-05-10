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
ms.openlocfilehash: 41b30763f1382b7a12f68cd6a45b87960f623649
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="badexception-class"></a>Klasa bad_exception

Klasa opisuje wyjątek, który może zostać wygenerowany z nieoczekiwany obsługi.

## <a name="syntax"></a>Składnia

```cpp
class bad_exception    : public exception {};
```

## <a name="remarks"></a>Uwagi

[Nieoczekiwany](../standard-library/exception-functions.md#unexpected) zgłosi `bad_exception` zamiast przerywa lub zamiast kontaktować się z inną funkcję określony za pomocą [set_unexpected —](../standard-library/exception-functions.md#set_unexpected) Jeśli `bad_exception` jest uwzględniony na liście throw funkcji.

Wartość zwrócona przez **co** to ciąg C zdefiniowane w implementacji. Brak funkcji Członkowskich generują żadnych wyjątków.

Aby uzyskać listę członków dziedziczonych przez `bad_exception` , zobacz [wyjątek klasy](../standard-library/exception-class.md).

## <a name="example"></a>Przykład

Zobacz [set_unexpected —](../standard-library/exception-functions.md#set_unexpected) na przykład użycie [nieoczekiwany](../standard-library/exception-functions.md#unexpected) zgłaszanie `bad_exception`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyjątku >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[exception, klasa](../standard-library/exception-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
