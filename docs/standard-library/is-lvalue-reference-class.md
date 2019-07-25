---
title: is_lvalue_reference — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: 5bcd5c8333f011475cb11a452759c8986ab22215
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456202"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference — Klasa

Testuje, czy typ jest odwołaniem lvalue.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie tego predykatu typu ma wartość true, jeśli typ *ty* jest odwołaniem do obiektu lub funkcji, w przeciwnym razie ma wartość false. Zwróć uwagę, że *ty* nie może być odwołaniem do rvalue. Aby uzyskać więcej informacji na temat rvalues, zobacz [rvalue Reference deklarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[Wartości Lvalue i Rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)
