---
title: Klasa bad_exception | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- exception/std::bad_exception
dev_langs:
- C++
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b1b332b4f76f24f873fd8a57d302fc2643a71f1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
