---
title: Klasa is_move_assignable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adda28e4c6cc2a7ba7a387e125bd873b2107b687
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ismoveassignable-class"></a>is_move_assignable — klasa

Testy, jeśli typ można przenieść przypisane.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Typ jest przeniesienie można przypisać, jeśli odwołania do r-wartości na typ można przypisać do odwołania do typu. Predykat typów jest odpowiednikiem `is_assignable<T&, T&&>`. Przenieś można przypisać typy referenceable typów skalarnych i operatory przypisania przenoszenia typy klas, którzy generowane przez kompilator lub zdefiniowanej przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
