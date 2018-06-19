---
title: Klasa is_literal_type | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_literal_type
dev_langs:
- C++
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b123144643fd50b019853d21e4140ba2d931f7c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844988"
---
# <a name="isliteraltype-class"></a>is_literal_type — klasa

Sprawdza, czy typ mogą być używane jako `constexpr` zmiennej lub skonstruowany, używany przez lub zwrócony z `constexpr` funkcji.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest *literalne*, w przeciwnym razie ma wartość false. Jest typem literału, albo `void`, typem skalarnym, typu odwołania, tablicy typu literału lub typie klasy literałów. Typie klasy literałów jest typem klasy, który ma destruktor trivial, jest łączny typu lub ma co najmniej jeden z systemem innym niż z move bez kopiowania `constexpr` Konstruktor i wszystkie jej klasy podstawowe i elementy członkowskie danych niestatyczna są trwałej typy literału. Typ literału zawsze jest typem literału, koncepcja literału typu obejmuje wszystkie elementy, które kompilator może służyć do oceny jako `constexpr` w czasie kompilacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
