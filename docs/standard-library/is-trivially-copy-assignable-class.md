---
title: Klasa is_trivially_copy_assignable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c36808d375dd774286c3663a02fdc308cc4b2790
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857509"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable — klasa

Sprawdza, czy typ ma operatora przypisania kopii prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest klasa, która ma trivial operatora przypisania kopii, w przeciwnym razie posiada wartość false.

Konstruktor przypisania dla klasy `T` jest proste, jeśli jest niejawnie podany, klasa `T` ma żadnych funkcji wirtualnych klasy `T` ma nie wirtualnych typów podstawowych, klas wszystkich członków danych niestatycznych typu klasy mają prosta Operatory przypisania i klasy wszystkich członków danych niestatycznych tablicy typu klasy mają operatory przypisania prosta.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
