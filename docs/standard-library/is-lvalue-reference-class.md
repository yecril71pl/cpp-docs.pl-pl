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
ms.openlocfilehash: d21fcc27b5b4f92b690d8fae7669a18a5fcc1c46
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964941"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference — Klasa

Sprawdza, czy typ jest odwołaniem lvalue.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Parametry

*Ty* typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie tego typu predykatu ma wartość true, jeśli typ *Ty* jest odwołaniem do obiektu lub funkcji, w przeciwnym razie przechowuje wartość false. Należy pamiętać, że *Ty* nie może być odwołaniem rvalue. Aby uzyskać więcej informacji o rvalue, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
