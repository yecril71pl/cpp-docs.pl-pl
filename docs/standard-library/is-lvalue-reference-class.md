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
ms.openlocfilehash: ecd065ff80b5c45bca863534e28bc467b3a4105c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105383"
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
