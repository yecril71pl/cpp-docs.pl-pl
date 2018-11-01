---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 8601ebbea6a9ab837c07518b018e83e8c0df226d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604441"
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