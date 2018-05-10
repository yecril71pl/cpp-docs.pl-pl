---
title: is_lvalue_reference — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_lvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 692c5243a7fe2984d43a1e70fc39616de5cbcc9c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="islvaluereference-class"></a>is_lvalue_reference — Klasa

Testy, jeśli typ odwołania do wartości.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Parametry

`Ty` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienia tego typu predykatu przechowuje wartość PRAWDA, jeśli typ `Ty` jest odwołaniem do obiektu lub funkcji, w przeciwnym razie posiada wartość false. Należy pamiętać, że `Ty` nie może być odwołaniem wartościowanym prawostronnie. Aby uzyskać więcej informacji o rvalues, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
