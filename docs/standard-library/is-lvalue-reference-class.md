---
title: is_lvalue_reference — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: e032522e790b7027886ba1a6199ed7fdf86c0936
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460180"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference — Klasa

Sprawdza, czy typ jest odwołaniem lvalue.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie tego typu predykatu ma wartość true, jeśli typ *Ty* jest odwołaniem do obiektu lub funkcji, w przeciwnym razie przechowuje wartość false. Należy pamiętać, że *Ty* nie może być odwołaniem rvalue. Aby uzyskać więcej informacji o rvalue, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
