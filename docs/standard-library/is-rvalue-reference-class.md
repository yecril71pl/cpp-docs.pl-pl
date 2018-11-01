---
title: is_rvalue_reference — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_rvalue_reference
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
ms.openlocfilehash: ea3be02db2a4a840ed8f8b8a253d7409c26cf759
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604141"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference — Klasa

Sprawdza, czy typ jest odwołaniem rvalue.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie tego typu predykatu ma wartość true, jeśli typ *Ty* jest [odwołanie rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
