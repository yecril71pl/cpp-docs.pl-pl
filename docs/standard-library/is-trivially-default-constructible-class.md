---
title: is_trivially_default_constructible — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f2bd65fa7145325fd4c5c2f1a2483851d0738b7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible — klasa

Testy, jeśli typ ma konstruktora domyślnego prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parametry

`Ty` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma trivial Konstruktor, w przeciwnym razie posiada wartość false.

Domyślny konstruktor dla klasy `Ty` jest prosta jeśli:

- jest niejawnie zadeklarowany Konstruktor domyślny

- Klasa `Ty` ma żadnych funkcji wirtualnych

- Klasa `Ty` ma nie wirtualnych typów podstawowych

- wszystkie bezpośrednio podstawowych klasy `Ty` mieć konstruktorów prosta

- klasy wszystkich członków danych niestatycznych typu klasy mają trivial konstruktorów

- klasy wszystkich członków danych niestatycznych tablicy typu klasy mają trivial konstruktorów

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
