---
title: _bstr_t::Dołącz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eddbc7a01be66430759bb84c3ce6d840f37d098
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111215"
---
# <a name="bstrtattach"></a>_bstr_t::Attach

**Microsoft Specific**

Linki `_bstr_t` opakowanie `BSTR`.

## <a name="syntax"></a>Składnia

```
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>Parametry

*s*<br/>
A `BSTR` skojarzony lub przypisane do, `_bstr_t` zmiennej.

## <a name="remarks"></a>Uwagi

Jeśli `_bstr_t` był wcześniej przypisany do innego `BSTR`, `_bstr_t` spowoduje oczyszczenie `BSTR` zasobu, jeśli żadne inne `_bstr_t` używają zmiennych `BSTR`.

## <a name="example"></a>Przykład

Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) dla przykłady dotyczące używania **Dołącz**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_bstr_t, klasa](../cpp/bstr-t-class.md)