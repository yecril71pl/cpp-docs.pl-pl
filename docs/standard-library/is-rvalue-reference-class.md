---
title: is_rvalue_reference — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bbaa215335a299eee8971b113fdcf3860e9b740
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106499"
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
